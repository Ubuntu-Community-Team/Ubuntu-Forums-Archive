---
title: "/etc/resolv.conf"
date: 2009-05-07
forum: Installation &amp; Upgrades
---

### Post by m5a5l3m on 2009-05-07
I just installed 9.04 Xubuntu and my network connection is not working..
One of the instructions suggested "editing" /etc/resolv.conf. However, I don't have that file on my machine. Is that something I need to pay attention to while debugging this networking issue?

---

### Post by compnut41 on 2009-05-07
try typing in the terminal: sudo less /etc/resolv.conf

This should post the contents of the file (if it exists as it does on my machine). it is hidden to your user so you have to open it as the root user. (ergo the sudo command)

---

### Post by WarrenKarl on 2009-05-07
I don't have any wireless internet.  I saw the same post and I don't have the file either.  I do have a file that is (I think) called resolvconf.  I looked at that file and it did not need
any editing.  So I still don't have any internet connection.

---

### Post by m5a5l3m on 2009-05-07
I always used sudo.. The file isn't there...

---

### Post by kaibob on 2009-05-07
I don't know anything about the /etc/resolv.conf file except that there is one on my computer, but you may want to have a look at the following (somewhat dated) thread which simply suggests creating the file. It only takes a minute or so and is worth a try.

[http://ubuntuforums.org/showthread.php?t=698262](http://ubuntuforums.org/showthread.php?t=698262)

BTW, the title of your thread says Ubuntu and your post says Xubuntu. It's probably not important, but you may want to clarify this.

---

