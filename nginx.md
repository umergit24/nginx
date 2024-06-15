# basic concept
- web server
- used as reverse proxy, load balancer etc
- between server and client
- client send request to nginx
	- and then nginx decides accordingly which server to forward the request to

# installing nginx
- on ubuntu vm

```
		sudo apt-get update
		sudo apt-get install nginx
```

		nginx -v    # to check verison
		
		sudo nginx       # to start nginx
		
or go to localhost:80 in the browser to view default nginx homepage. 80 is the default nginx port but we can map it too is we run it as container. 
	
> [!NOTE] Title
> for any website, in inspect elements, check the response headers to see which server is handling the website

- a folder is created for nginx having nginx conf file, access it via

		ls /etc/nginx/
		cd /etc/nginx
		ls -lh
		nano nginx.conf
		
# creating our own nginx.conf file	

- whats inside nginx.conf
	- a http { } block to make the server
- steps to make ur own conf file and run

```
sudo mv nginx.conf nginx-backup.conf
sudo nano nginx.conf
nginx -s reload
nginx
```

==nginx.conf==
```configfile
events {

}

# nginx has to listen on a particlar port 
# so create a http server
# it can furhter have many servers inside

http {
	server {
		listen 80;
		server_name _;   
		# server name means what request type is to be handled  
		# _ specifies it to handle everything
		location / {
			return 200 "hELLO FROM NGINX CONF FILE";
		}
		
	}
}

```


![alt text](https://github.com/umergit24/nginx/blob/master/Pasted%20image%2020240615191552.png)

[![[Pasted image 20240615191552.png]]]
(https://github.com/umergit24/nginx/blob/master/Pasted%20image%2020240615191552.png)



![[Pasted image 20240615191756.png]]

- can have multiple servers running on multiple ports.



