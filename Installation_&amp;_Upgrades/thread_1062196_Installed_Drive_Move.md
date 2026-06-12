---
title: "Installed Drive Move?"
date: 2009-02-06
forum: Installation &amp; Upgrades
---

### Post by rljames@psualum.com on 2009-02-06
I've installed Ubuntu 5.10 on a newly formatted hard drive attached to a 400Mhz Pentium II based motherboard. Can I now just physically move this drive to a 2Ghz Pentium 4 board?

If not, how do I make the install work under the new "environment"? 

(BTW, I can't seem to get v8.10 to work on either system...)

---

### Post by lemming465 on 2009-02-09
> Can I now just physically move this drive ...

Try it; the main possible glitch is likely to be boot problems with drivers, particularly video.  Assuming that the new disk controller is supported, you can boot in rescue mode (single user), and then try ```

/etc/init.d/network start
update-initramfs -u
dpkg-reconfigure xserver-xorg
```

---

