---
title: "Apache --&gt; /var/www/ functionality in another location"
date: 2008-10-27
forum: General Help
---

### Post by supergrover1981 on 2008-10-27
Hi gang,

I'd like to switch a bunch of websites I keep on my local Apache 2 server (/var/www/) across to an external HDD (/media/disk/Websites/). I'm wondering how to do it so that the 'localhost' reference, MySQL, PEAR repositories etc all function the same as if located in /var/www/?

Tried googling, but couldn't find anything too useful. Any suggestions deeply appreciated.

Currently running Hardy. :-)

Cheers,
       - JB

---

### Post by jamieh on 2008-10-27
You can change the directory in one of the .conf files. in OS X it's the httpd.conf file, but in my ubuntu server, that file is blank :confused::confused:

---

