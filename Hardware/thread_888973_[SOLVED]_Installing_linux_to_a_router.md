---
title: "[SOLVED] Installing linux to a router"
date: 2008-08-13
forum: Hardware
---

### Post by MunkyJunky on 2008-08-13
I have a D-link DSL-G624T router, which is at the moment causing some major stress. Since I'm hopefully getting a new one soon, it seems a waste to not use my current one. 

Would it be possible to install linux onto it? I mean, I know linux runs on everything, but how would I go about doing it?

---

### Post by tubbygweilo on 2008-08-13
MunkyJunky, I know Linux runs on some of the [WRT54G]("http://en.wikipedia.org/wiki/WRT54G") family of routers as I have loaded the open source [Tomato Firmware]("http://en.wikibooks.org/wiki/Tomato_Firmware") on my [WRT54GL]("http://en.wikipedia.org/wiki/WRT54G#WRT54GL") and it all works rather well together.

---

### Post by ilrudie on 2008-08-13
Also look into dd-wrt and openwrt.  I use dd-wrt and have been extremely happy with it.  Its very stable and feature rich.

---

### Post by finer recliner on 2008-08-13
linksys models that end with an 'L' use the linux kernel.

look into DD-WRT to hack your router's firmware for more fun than linksys gives you out-of-the-box.

---

### Post by MunkyJunky on 2008-08-13
My router is D-link, not Linksys. Would that make much difference? I know my router is running linux though. By connecting via telnet, if I 

```
# cat /proc/version
```

I get output:
```
Linux version 2.4.17_mvl21-malta-mips_fp_le (jenny@FD5) (gcc version 2.95.3 20010315 (release/MontaVista)) #1 Wed Feb 8 17:16:13 CST 2006
```

Also, I'll have a look into DD-Wrt and OpenWrt. Thanks for the help so far guys!


**EDIT:**
After a quick look, DD-Wrt doesn't look like it yet supports my router, but OpenWrt has mine under 'work in progress', which offers a little more hope. Thanks for pointing them out!

---

### Post by ilrudie on 2008-08-14
Look at the dd-wrt site to see if they support your router.  They have a very nice matrix of supported brands/models.

[http://www.dd-wrt.com/wiki/index.php/Supported_Devices](http://www.dd-wrt.com/wiki/index.php/Supported_Devices)

---

