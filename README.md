# docker-wordpress-ssl
## Wordpress remote development environment with local https (ssl) using nginx reverse proxy and docker-compose.</br>
### Run with ssl with one command. [docker-compose up]
### Prerequites: docker, docker-compose

setup in under 10 minutes...
1. add init.sql file to root directory with a dump of your production wordpress database.
2. change 'site_url' and 'home' values in wp_options table in init.sql to 'https://workspace.dev'
3. using openssl create your own, local certificate authority and identify it to your development broswer.
4. using openssl generate a site-specific certificate/key pair called 'workspace.dev.key & workspace.dev.crt' in the .certs/ directory.
*(see here for more info on steps 2 & 3: https://deliciousbrains.com/ssl-certificate-authority-for-local-https-development/)*
5. clone your production wordpress site repo into the site/ directory
6. run docker-compose up

the local site will be available at https://workspace.dev/

if you want to change the development url you will need to...
1. update site_url & home values in wp_options table
2. rename access and error logs to match your desired development url
3. update conf.d/nginx.conf replacing 'workspace.dev' with your desired url

feel free to post issues here or suggestions as to how this environment could be further abstracted.
