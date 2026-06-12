---
title: "htaccess and password help"
date: 2008-08-06
forum: General Help
---

### Post by norjms on 2008-08-06
Hello,
I currently have a webserver setup and I'm having issues setting up htaccess for a cgi script. I've tried setting what I "think" should be in apache2/sites-enabled/ssl and created a htaccess file in the root of the cgi bin but, you can still access the file.

Here is exactly what I'm trying to do maybe someone can walk me through how exactly to set this up.

server path to cgi bin
/usr/lib/cgi-bin

server path to file
/usr/lib/cgi-bin/nph-work.cgi

web path to to file
[https://example.com/cgi-bin/nph-work.cgi](https://example.com/cgi-bin/nph-work.cgi)

I really don't want to password protect the whole cgi-bin...just the file. If it matters I have normal directories already password protected if I can use the same .htpasswd file would make it easier for user management.

Thanks for the help.

Ryan

---

### Post by hvac3901 on 2008-08-06
[http://johnbokma.com/mexit/2007/01/09/password-protecting-single-file-htaccess.html](http://johnbokma.com/mexit/2007/01/09/password-protecting-single-file-htaccess.html)

Does that help?

---

### Post by norjms on 2008-08-06
Thanks I checked the site you linked and it worked great....I thought it didn't work at first because it would let me go straight to the site but, I was using an ajax term to make the modifications to the files and I had already authenticated so, it wasn't asking for the password... Thanks again for your help

---

### Post by hvac3901 on 2008-08-06
Cool.

---

