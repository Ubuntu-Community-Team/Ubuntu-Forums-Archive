---
title: "multiple websites to one webserver?"
date: 2008-08-09
forum: General Help
---

### Post by gazz1982 on 2008-08-09
ok, I have 2 websites hosted on my ubuntu server

[www.example1.co.uk](www.example1.co.uk)
and
[www.example2.co.uk](www.example2.co.uk)

I want example1 to have a docroot of www/example1/
and example2 www/example2/

currently my server only listens on port 80 and this sends both web addresses to eamaple1

How do i get the example2 site to access example2 as docroot?

Thanks

---

### Post by spiderbatdad on 2008-08-09
Are you using the virtual hosts: /sites-available/example1  /site-available/example2

---

### Post by ww711 on 2008-08-09
Configure your virtual hosts file for your apache server....[http://httpd.apache.org/docs/2.0/vhosts/examples.html](http://httpd.apache.org/docs/2.0/vhosts/examples.html) would be a starting point.

---

### Post by x1a4 on 2008-08-09
> **gazz1982 said:**
> 
How do i get the example2 site to access example2 as docroot?

 <VirtualHost *:80>
DocumentRoot /www/example1
ServerName [www.example1.com](www.example1.com)

# Other directives here

</VirtualHost>

<VirtualHost *:80>
DocumentRoot /www/example2
ServerName [www.example2.org](www.example2.org)

# Other directives here

</VirtualHost>
> 
Thanks
You're welcome.
Good luck.

---

