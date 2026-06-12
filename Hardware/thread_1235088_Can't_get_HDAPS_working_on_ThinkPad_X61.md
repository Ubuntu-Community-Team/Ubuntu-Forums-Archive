---
title: "Can't get HDAPS working on ThinkPad X61"
date: 2009-08-08
forum: Hardware
---

### Post by Epaminond on 2009-08-08
It's the second I'm trying to make HDASP working. I followed [this]("http://code.google.com/p/tp-smapi-dkms-module/wiki/Install") guide. Fixed a problem with invertion in hdaps-gl using [this]("http://www.krizka.net/2008/01/23/thinkpad-x61-tablet-tilt-detection-and-ubuntu-hardy-heron/") tip. Also installed an applet. Thought everything was OK, but can't understand why HD doesn't stop when moving laptop. I suppose that this's because when installing hdapsd I didn't manage to patch kernel. I'm using 2.6.30.4. Am I supposed to?

Also I've edited /etc/modules, but hdaps still doesn't start when booting.

Please help me to make it working!

---

### Post by rCXer on 2009-08-08
What does hdapsd print out when you run...
```

sudo hdapsd -d sda -s 15 -a -v -y 

```
By the way, [these instructions](http://www.thinkwiki.org/wiki/Installing_Ubuntu_9.04_(Jaunty_Jackalope)_on_a_ThinkPad_T61#Enabling_Active_Protection_System), although longer, worked for me.

---

### Post by Epaminond on 2009-08-09
2rCXer
The output changes, when moving laptop. The hdaps-gl command seems to work properly either. I've already tried to follow these instructions. When trying to delete existing kernel modules at the begining I get the messege "No such file or directory". Everything else was done.

[Here]("http://www.thinkwiki.org/wiki/How_to_protect_the_harddisk_through_APS") the "note" sais, that "Starting with kernel 2.6.28 a generic disc protection feature is built into the libata driver". Does it mean I'm not supposed to patch the kernel?

---

### Post by rCXer on 2009-08-09
> **Epaminond said:**
> 2rCXer
[Here]("http://www.thinkwiki.org/wiki/How_to_protect_the_harddisk_through_APS") the "note" sais, that "Starting with kernel 2.6.28 a generic disc protection feature is built into the libata driver". Does it mean I'm not supposed to patch the kernel?

You don't have to patch the kernel. I didn't and I have 2.6.28. I've herd it takes hours to build it. Just to be sure, does the applet's output change from play to pause when you run hdapsd?

Do you have a "/sys/block/**[COLOR="Red"]s[/COLOR]**da/queue/" or an "/sys/block/**[COLOR="Red"]h[/COLOR]**da/queue/" directory? If so you have file called "protect" or "unload_heads" in that directory?

---

### Post by Epaminond on 2009-08-09
No, but I have /sys/block/sda/device/unload_heads. And the value is >0 when moving laptop.

I've followed all those guides one more time and now everything seems to work like it has to. Thank you. :)

---

