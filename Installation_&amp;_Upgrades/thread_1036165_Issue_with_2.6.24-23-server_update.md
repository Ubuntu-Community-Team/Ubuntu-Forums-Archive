---
title: "Issue with 2.6.24-23-server update"
date: 2009-01-10
forum: Installation &amp; Upgrades
---

### Post by kewlpics on 2009-01-10
I usually update everything when there are new updates.  I was out of the town for a week, and there were quite a few updates.  So I went ahead updated everything as usual. 

It required system restart.  So, I did.  My ubuntu 8.04 server could not get fully boot up.  If it is working correctly, I would see the login screen.  I am not able to get there.  I see a distorted screen.  

So, I restarted the box, and press ESC during the loading of GRUB, I chose the previous kernel, 2.6.24-22-server, Ubuntu loads up fine.

I am wondering if it is because my ATI video driver is not compatible with 2.6.24-23-server kernel.  And how can I fix this?

---

### Post by kewlpics on 2009-01-30
Still no luck with the above.  Can anyone help me fix this?  I think it is my video driver not compatible.  Are there anyway I can rebuild the ATI driver using the 2.6.24-23-server kernel, while I am actually started with 2.6.24-22-server kernel?

---

### Post by kewlpics on 2009-01-31
Nevermind.. I got it fixed.  

1. go to the recovery mode with new kernel. reconfig the X server to default setting.
2. boot up with the new kernel normally.
3. follow the method 2 in this link.. [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

This will build the ATI driver under the new kernel.

---

### Post by cariboo on 2009-01-31
If you use [webmin]("http:///www.webmin.com/") to administer you server, you wouldn't have graphic driver problems, and you could get rid of the desktop.

Jim

---

### Post by byraul on 2009-01-31
I have the same problem with the last kernel and ati card.

---

