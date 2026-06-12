---
title: "Ubuntu Feisty packages for ThinkPads"
date: 2007-04-20
forum: Hardware &amp; Laptops
---

### Post by moixa on 2007-04-20
I built some packages to make some features working on my ThinkPad, I guess I might as well post them since they are made and are working on my T60. 
 
 [http://axiomatization.googlepages.com/ubuntufeistydebpackagesforthinkpads](http://axiomatization.googlepages.com/ubuntufeistydebpackagesforthinkpads)
 
 For Intel wifi, you can re-use your old daemon, firmware by sym-linking, no re-compilation needed.

---

### Post by mjukis on 2007-04-25
I tried your patched kernel but with no luck. I have an Intel wifi and have no clue how to symlync the files needed. I don't know which files.

But even when I booted up with the patched kernel "hdaps -d sda"  gave me en error saying i missed the file /sys/devices/platform/hdaps/protect

An hints on how to proceed?

---

### Post by moixa on 2007-06-15
> **mjukis said:**
> I tried your patched kernel but with no luck. I have an Intel wifi and have no clue how to symlync the files needed. I don't know which files.

But even when I booted up with the patched kernel "hdaps -d sda"  gave me en error saying i missed the file /sys/devices/platform/hdaps/protect

An hints on how to proceed?

If you have the Intel chip, you can do the following

ln -s /sbin/ipw3945d-2.6.20-15-generic /sbin/ipw3945d-2.6.20.3-ubuntu1-custom
ln -s /lib/firmware/2.6.20-15-generic /lib/firmware/2.6.20.3-ubuntu1-custom

(make sure you have -15 kernel instead of -16)

for hdaps, you need to load the module first "modprobe hdaps"
Let me know how it works out.

Sorry for the late reply, I think I forgot to subscript this thread.

---

