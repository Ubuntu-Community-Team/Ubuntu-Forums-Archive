---
title: "Xampp"
date: 2009-11-08
forum: Installation &amp; Upgrades
---

### Post by yorkshireflatcap on 2009-11-08
All,

After much head scratching and lots of coffee, I have managed to install 9.10 successfully. Hurrah!!!!!

However, when I installed XAMPP using the following tutorial: [http://ubuntuforums.org/showthread.php?t=223410](http://ubuntuforums.org/showthread.php?t=223410)

I get the test screen when I do [http://username](http://username), but it seems that when I try and display the index.php page within my linked directory I get a **403 Error:Forbidden.**  It's telling me that I don't have access.

I look at the permissions on this particular directory and it has the owner as **root**!! :confused: It's my directory, created by me under my username, so I don't understand why the owner is root.  

Anyway, I change the ownership to my username and the directory permissions (chmod 777) to see if I view my webpage.

It still having a **403 Forbidden** error!!  Does anyone have any ideas As to why I am getting this?

Regards

Yorki

---

### Post by headlessspider on 2009-11-16
this is happening to me also and i've tried reinstalling xampp but that didn't work either. the permissions are fine. the error logs say:

[Tue Nov 17 06:36:25 2009] [error] [client 127.0.0.1] (13)Permission denied: access to / denied

my httpd-vhosts.conf is the same exact conf file i used with xampp 1.7.2 under 9.04. the httpd.conf file includes the httpd-vhosts.conf file too. my own hosts file has a named entry for the localwebhost. so i'm stumped too.

anybody out there who knows more than us? please?

---

### Post by headlessspider on 2009-11-17
to anyone who stumbles into this thread, i think i figured it out. [the steps are here]("http://noel.alanguilan.com/2009/11/17/xampp-and-the-koala/"). in short, i moved my development data--html, php pages along with its associated files under the Public folder and then applied the permissions of the Public folder recursively. i had to change my document roots but that's a minor thing.

---

