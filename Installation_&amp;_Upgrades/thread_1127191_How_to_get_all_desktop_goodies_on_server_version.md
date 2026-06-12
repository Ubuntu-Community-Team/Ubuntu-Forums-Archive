---
title: "How to get all desktop goodies on server version ?"
date: 2009-04-16
forum: Installation &amp; Upgrades
---

### Post by zshanthi on 2009-04-16
Hi All

I need all the utilities of a server version so Im downloading the server version ubuntu 10

BUT I need all the goodies of the desktop version too

Can anyone please advise me the fastest method by which I can get all the desktop goodies into my installed ubuntu server version ??

Thanks

Shanthi

---

### Post by Anthon on 2009-04-16
If you have a desktop version somewhere that has all the goodies you want/need/like, you can do dpkg --list | fgrep ii | cut -d' ' -f 3 > /var/tmp/pkg.lst
and then use that file on the server with 
  apt-get install pkg.lst

---

### Post by damis648 on 2009-04-16
After installation, just
```
sudo apt-get install ubuntu-desktop
```
and you should be good to go. :popcorn:

---

### Post by Mulenmar on 2009-04-16
sudo apt-get update && sudo apt-get install ubuntu-desktop

Will give you a standard Ubuntu desktop, even on Server edition methinks. Enjoy!

---

### Post by senile2 on 2009-04-16
Is there a way to do that in reverse?  I have a solid desktop build that I would like to install the server framework on so that I can take advantage of the server tools (LAMP, SSH, net monitoring, etc), but I like the look and feel of my current desktop.

Thanks

---

