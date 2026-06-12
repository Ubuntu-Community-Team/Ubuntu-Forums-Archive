---
title: "Combo USB keyboard + mouse: mouse doesn't work (Dapper)"
date: 2006-05-07
forum: Hardware &amp; Laptops
---

### Post by model on 2006-05-07
Hi:

I have a combo keyboard + optical mouse, both sharing the same recipient, withc an USB connection.

In Ubuntu 5.10 they worked right, but now, I had upgraded to 6.06 beta 2 and my mouse doesn't work properly. When I move the mouse, the cursor moves, but its movement is totally over-excited. I tried to reconfigure the xserver with dpkg-reconfigure xserver-xorg, but it didn't work, and also that spoiled the configuration of the keyboard.

I downloaded the LiveCD of such version and works perfectly. I copied the xorg.conf to my hard disk installation and didn't work. Also I tryed to load the same modules, but i didn't work also.

Do you know what can I do?

Did you have the same problem?

Is there any way to do that my hard disk installation does the same hardware recognition and configuration like the LiveCD does?

Thank you.

---

### Post by model on 2006-05-09
Hi:

Finally I found the solution. I had installled the linux686 package and this solved the problem. Possibly I had installed the kernel package, but not the linux686 <i>metapackage</i>, so when I did an apt-get dist-upgrade, that package didn't get upgraded.

Now, with the new kernel, both keyboard and mouse work fine.

Regards.

---

