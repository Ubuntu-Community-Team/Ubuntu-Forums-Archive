---
title: "help me to configure gmailfs"
date: 2008-09-20
forum: General Help
---

### Post by brijith on 2008-09-20
Hai,
I am trying to configure gmailfs in my Debian system. I did it as in the doc given in the [[COLOR="Blue"]link[/COLOR]]("https://wiki.ubuntu.com/GmailFS"). When I try to mount I got the following error 

```
 mount -a
09/20/08 09:47:53 ERROR      Unable to find GMail account configuration
09/20/08 09:47:53 WARNING    Using default file system (Dangerous!)
Ignored option :rw
HTTP Error 400: Bad Request
fusermount: failed to open /dev/fuse: No such file or directory
fuse: reading device: Bad file descriptor
09/20/08 09:48:03 ERROR      gmailfs child died, exiting...

```

Please help Me !!!!!!!!!!!!1



**[COLOR="Sienna"]Thanks[/COLOR]**

---

### Post by HacDan on 2008-09-20
I just followed the link in your post to the T and it worked flawlessly the first time around. The HTTP 400 error you are receiving, according to the site, is an error from an out of date libgmail. You can update this by running ```
sudo easy_install --upgrade libgmail
``` in a terminal window.

Also when editing /etc/fstab make sure when you add the line to /etc/fstab you replace the username and password with your gmail username and password. I'm going to be honest I don't know what goes in where it says fsname but I used another randomly generated password and it worked. Hope this helps

::Edit:: Not sure if this is what you're looking for, and it's probably not enough space, but I have to recommend [Dropbox ]("http://www.getdropbox.com/")You receive 2 gigs of free online storage basically accessible from as many computers as the software is installed on. It is also accessible from the web. Just something to consider.

---

