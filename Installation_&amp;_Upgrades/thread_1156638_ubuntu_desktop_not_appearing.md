---
title: "ubuntu desktop not appearing"
date: 2009-05-11
forum: Installation &amp; Upgrades
---

### Post by RedRingRico on 2009-05-11
I recently installed Ubuntu 9.04 Netbook Remix on my hp mini 1000. It was working fine until I restarted it after performing some updates. Now after I login, the desktop does not load. I can move the mouse and can perform right-click operations, but nothing else. Does anyone know what can be the issue?

---

### Post by pastalavista on 2009-05-11
Probably some broken packages. Reboot and at the first screen, hit escape and keep hitting it until the boot menu comes up. Then select the second option -Recovery Mode. Then you can try to repair different elements of the installation. I'd try "broken packages" first. Then reboot. If that doesn't work, Do recovery mode again, select the root console with networking and type 
```
sudo apt-get install ubuntu-netbook-remix-default
```
and if that doesn't work, come back and let us know

---

### Post by RedRingRico on 2009-05-11
I tried repairing the broken packages but it had nothing to fix. I next tried to do sudo apt-get install ubuntu-netbook-remix-default but I got the following error message:

E: Couldn't find package ubuntu-netbook-remix-default

What could I do now?

---

### Post by pastalavista on 2009-05-11
Were you able to get networking going? You might have to either connect with cable or boot from the live CD to fix it. When you were at the boot menu, was there more than one kernel to boot into? You could see if the older one still works.

---

### Post by RedRingRico on 2009-05-11
Yeah I was able to get the networking to work. No there were no other kernels to choose from since I decided to overwrite the previous ubuntu version with this newer version.

---

### Post by pastalavista on 2009-05-12
OK then still not hopeless. This time, boot into reovery again and again and try to fix xserver (last item in the list) or enter this into the root terminal:
```
sudo dpkg reconfigure -a xserver-xorg
```


edit: and before when I had you reinstall netbook remix package I may have picked the wrong one... try this one instead:

```
sudo apt-get remove ubuntu-netbook-remix --purge
``` and then 
```
sudo apt-get install ubuntu-netbook-remix
```

---

### Post by Brandon Williams on 2009-05-12
Please search before posting! This has been covered several times. Most notably [here](http://ubuntuforums.org/showthread.php?p=7253643#post7253643) in the "known bugs in Jaunty" thread.

---

