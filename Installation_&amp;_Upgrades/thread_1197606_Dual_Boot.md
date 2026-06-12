---
title: "Dual Boot"
date: 2009-06-26
forum: Installation &amp; Upgrades
---

### Post by Twittery on 2009-06-26
I have been using Ubuntu Jaunty for about 3 month and I thought why not give fedora a try alongside with Ubuntu . As both use grub do I have to make some changes for it to work.  If this was the wrong place I apologize.  Sorry .

Note : I am still quite new to Linux . So help is appreciated. Thanks.

---

### Post by keplerspeed on 2009-06-26
No, you will not have to do anything specific. Just install fedora on a spare partition, it will detect ubuntu, and both options will apear in the new fedora grub menu.

---

### Post by Twittery on 2009-06-26
Thanks but a few years ago when I tried to install Ubuntu on my Fedora PC , the grub was unable to find Fedora and it was a hell of a mess . Just didn't want to repeat the same old mistake .

---

### Post by keplerspeed on 2009-06-26
Grub has come a long way, and it pretty reliable with detecting other OS's.

Even if the fedora install will not detect ubuntu (Im am 99.9% sure it will) you can boot to ubuntu live cd, and reinstate the ubuntu grub menu, and that will detect fedora. See restoring grub [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by raymondh on 2009-06-26
> **keplerspeed said:**
> Grub has come a long way, and it pretty reliable with detecting other OS's.  

you can boot to ubuntu live cd, and reinstate the ubuntu grub menu, and that will detect fedora. 

+ 1.

Another link for (another) reference

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Have fun and happy ubuntu-ing (as well as fedora-ing)

---

### Post by Twittery on 2009-06-26
Thanks all

---

### Post by presence1960 on 2009-06-26
install fedora's GRUB to fedora's partition **not MBR**. This will leave Ubuntu's GRUB in MBR and in control when you boot. Then edit Ubuntu's menu.lst to chainload fedora much like you would windows. Example:

```
title         Fedora
rootnoverify  (hdx,y)
chainloader   +1
```

This will pass off to Fedora's GRUB when you choose Fedora's chainload entry. An advantage to this is when Fedora upgrades it's kernel you will not have to edit Ubuntu's menu.lst since you are chainloading Fedora. The new kernel will be included in Fedora's menu.lst automatically with the kernel upgrade. The other way it will not automatically be included in Ubuntu's menu.lst and will require manual editing with each new Fedora kernel. And the other way around if you put Fedora in MBR, you will have to edit fedora's menu.lst to include any Ubuntu kernel upgrades. Chainloading the second OS is the way to go!

---

