---
title: "[jupiter] buggy 1024x768 display"
date: 2012-02-09
forum: Hardware
---

### Post by bikepunk on 2012-02-09
Runing updated Lubuntu 11.10 on a EeePC 1015PN (jupiter 0.0.53 and
jupiter-support-eee see : ), with normal resolution=1024x600.
Picking 1024x768 from jupiter applet in "Screen Resolutions" seems working
BUT I can not access the lower part of the screen anymore.
And thats a problem because now I cant point the pointer at the applet
to change it back to 1024*600.

workaroud :
```
sudo rm /var/jupiter/reso*
xrandr --output LVDS1 --mode 1024x600
sudo reboot
```

It makes possible to recover normal 1024x600 resolution without uninstalling/reinstalling
jupiter

also reported there : [http://bbs.archbang.org/viewtopic.php?id=2176](http://bbs.archbang.org/viewtopic.php?id=2176)

[http://www.jupiterapplet.org/](http://www.jupiterapplet.org/)
[https://launchpad.net/~webupd8team/+archive/jupiter](https://launchpad.net/~webupd8team/+archive/jupiter)

---

### Post by Miotas on 2012-02-10
I have the same problem. 

Uninstalling Jupiter resolved the issue (the only way to resolve the issue), however, when I resinstalled Jupiter, the same issue happened again on reboot, even though I was sure to set the screen resolution to 1024x600, via Jupiter's menu. 

I have a Asus Eee PC 1001px

---

### Post by Sepirio on 2012-03-12
does anyone solved problem with this blocked lower area?

---

