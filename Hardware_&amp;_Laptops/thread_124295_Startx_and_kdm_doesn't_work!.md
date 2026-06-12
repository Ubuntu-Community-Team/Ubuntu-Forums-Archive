---
title: "Startx and kdm doesn't work!"
date: 2006-02-01
forum: Hardware &amp; Laptops
---

### Post by BanskuZ on 2006-02-01
Hello. I'm using Ubuntu Breezy and KDE 3.5.

KDM doesn't work. It works, but I can't login. :-k 
In "consolemode", I tried:
$ startx
but X doesn't start. "sudo startx" works.

/var/log/Xorg.0.log file: [http://paste.servut.us/index.php?id=29633408843e095494a08b](http://paste.servut.us/index.php?id=29633408843e095494a08b)

---

### Post by MartinG on 2006-02-01
In your X.org.0.log file, there is an error (line 812) which is preventing X starting.  It appears from earlier entries (line 350) that you are using the free driver nv, which doesn't support glx. Try editing your /etc/X11/xorg.conf by commenting out the line: Load "glx", in Section "Module" (to do this put a # at the start of the line).

If this works, you may want to upgrade to a non-free driver.  To do this, see:
[http://www.ubuntuforums.org/showthread.php?t=75074](http://www.ubuntuforums.org/showthread.php?t=75074)

---

### Post by BanskuZ on 2006-02-01
My /home/ folder was full :oops: 

I replaced driver "nv" --> "nvidia"
Removed some files in ~/
Chmoded ~/.ICEAuthority file 777.

---

