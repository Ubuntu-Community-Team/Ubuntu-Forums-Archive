---
title: "multiple domains on one ip address?"
date: 2008-08-02
forum: General Help
---

### Post by dxlwebs on 2008-08-02
hey all,

ok so yes before you say it i have read (a lot) of guides even the webmin guide and i have to say i am more confused than when i started!

i have a static ip address from my ISP and i want to run more than one website off that one ip address! i have around 3-4 websites all with their own domain name and i know that i need to direct them to that one ip address but i dont know how to set it up that when you type in say example1.com it will come up with the example1 site on my server and the same for example2 and the rest!

i am using webmin which does have bind dns which i hear it is possible to do it through but i have no idea on how!

im sorry if this sounds confusing and if any one knows how to do this i would be very grateful for the info!

thanks for your help

---

### Post by spiderbatdad on 2008-08-02
virtual hosts: /sites-available/your_www

point to as many pages as you like, contained within named folders inside the directory /your_sites

---

### Post by dxlwebs on 2008-08-02
ok i looked for that in webmin and was not able to find what you types also if i could get some kind of baby step by step guide that would be great

---

### Post by russlar on 2008-08-02
You're just making folders under the root folder of the web server.

---

### Post by dxlwebs on 2008-08-02
ok so in the folder var/www if i add a new file called example.com and then i pointed firefox to example.com it would show that site ?

---

### Post by russlar on 2008-08-02
No. you's need to make a directory under /var/www, and put the web site's files in that new directory.

---

### Post by x1a4 on 2008-08-02
Hi,

Are you using Apache?  If so you need to configure virtual hosts.  See [this article]("http://www.apacheweek.com/features/vhost") on how to do it.  Also have a look at the [Apache Documentation]("http://httpd.apache.org/docs/").

A typical configuration would look something like this:
```

<VirtualHost *xxx.xxx.xx.xxx*>
  DocumentRoot /www/domain1
  ServerName  www.domain1.com
</VirtualHost>
<VirtualHost *xxx.xxx.xx.xxx*>
  DocumentRoot /www/domain2
  ServerName  www.domain2.com
</VirtualHost>

```
Where *xxx.xxx.xx.xxx* is your IP address.

---

### Post by mbeach on 2008-08-02
basically you want to create a folder for each site pretty much anywhere, I recommend in your home folder.

so
/home/you/site1
/home/you/site2
/home/you/..
/home/you/..

then create config files in 
/etc/apache2/sites-available/
copying the Default file that is in there and renaming it accordingly, and making the necessary changes for each instance.

Then use the 
a2ensite 
command to enable the sites

use 
sudo /etc/init.d/apache2 reload

to reload the configuration changes.

You want to be searching for something like:
apache ubuntu virtual host

Quick search result:
[http://www.tequilafish.com/2007/08/02/apache-virtualhost-on-ubuntu/](http://www.tequilafish.com/2007/08/02/apache-virtualhost-on-ubuntu/)
[http://articles.slicehost.com/2008/4/29/ubuntu-hardy-apache-virtual-hosts-1](http://articles.slicehost.com/2008/4/29/ubuntu-hardy-apache-virtual-hosts-1)

and from these forums:
[http://ubuntuforums.org/showthread.php?t=810133](http://ubuntuforums.org/showthread.php?t=810133)

---

### Post by dxlwebs on 2008-08-03
thank you for the info so once i done that when i type in domain1.com it will show that domain even if they are all on the same ip address right

---

### Post by Rakeshvijayan on 2012-10-18
> **dxlwebs said:**
> thank you for the info so once i done that when i type in domain1.com it will show that domain even if they are all on the same ip address right
  did you get the answer ,if it is yes please share your knowledge about this topic ,I am wandering for this case

---

### Post by dazman19 on 2012-10-18
yes, you are creating NameVirtualHosts in this instance.

When the request comes in on port 80, the web server will read the HTTP header and use the virtualhost dependant on the header.

If you google NameVirtualHosts examples there will be examples on how to layout the virtual host file.

I would make a seperate file for each virtual host and pop it in my /etc/apache2/sites-available directory.

Then run a2ensite "sitename" where sitename is the name of the file. 

Then restart apache2.

---

### Post by lisati on 2012-10-18
Although recent answers are still largely relevant, this is an old thread that has sprung back to life.

---

