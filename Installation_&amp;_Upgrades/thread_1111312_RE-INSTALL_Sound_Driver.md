---
title: "RE-INSTALL Sound Driver"
date: 2009-03-30
forum: Installation &amp; Upgrades
---

### Post by joshjh on 2009-03-30
Hey everyone,
   I have had what seems to be a common problem. My sound did not work when i installed ubuntu 10. Now upon trying to fix this i apparently uninstalled my sound driver. Doesn anyone know how to reinstall this? I am totally lost on how to do this any help would be great. Thanks

---

### Post by khelben1979 on 2009-03-30
```
sudo dmesg
```
and post the output here.

If your Linux kernel have sound for your sound- chip/card inbuilt, then you just need to adjust the volume meters using [alsamixer]("http://en.wikipedia.org/wiki/Alsamixer"). 

If it comes as a module, this sound module must be activated by either using the insmod or modprobe command for this.

```
man insmod
``` and ```
man modprobe
``` for documentation on how to use these commands. You need to know the name of the module which could be ```
sudo modprobe sb
``` if it is an old soundblaster chip/card.

---

### Post by OldManRiver on 2009-03-30
> **joshjh said:**
> Hey everyone,
   I have had what seems to be a common problem. My sound did not work when i installed ubuntu 10. Now upon trying to fix this i apparently uninstalled my sound driver. Doesn anyone know how to reinstall this? I am totally lost on how to do this any help would be great. Thanks

J,

Some MB sound chipsets are not in the standard kernel source, so have to be looked up, downloaded and installed seperately.  I had this problem on one MB setup.

There are commands that will put the addition code into your kernel build, but forgot them.  On my MB sound problem I mentioned, I was installing something, forgot what, which caused Grub errors, so kept loosing the sound drivers, as was starting over from scratch each time.  Recommend a good recovery program, installed and rec-CD burnt, before tackling the sound patch, so you won't have to start over, like I did on that one (3 times, before I got smart).

OMR

---

