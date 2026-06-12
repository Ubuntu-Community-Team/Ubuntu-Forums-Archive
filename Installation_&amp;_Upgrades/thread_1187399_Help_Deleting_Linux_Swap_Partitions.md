---
title: "Help Deleting Linux Swap Partitions"
date: 2009-06-14
forum: Installation &amp; Upgrades
---

### Post by Katman000 on 2009-06-14
To explain my prediciment quickly, I have loved ubuntu, but am going back to XP for various reasons. Unfortunately I cannot due to the Linux Swap partitions that Gparted cant edit, why i dont know. I have tried various live cds that format the drivebut none have worked. The XP disk gives back a blue screen of death. Is there some way to format the disk that doesnt involve the partiton editor, and that I can use the live CD for?
Thanks

---

### Post by dnairb on 2009-06-14
Using gparted, right-click the swap partitition and select "swapoff" in the drop-down menu.
The swap partition will then be inactive and unused and you can safely delete it.

---

### Post by arielCo on 2009-06-14
> **Katman000 said:**
> To explain my prediciment quickly, I have loved ubuntu, but am going back to XP for various reasons.
You can have both; the Ubuntu installer detects  your Windows installation, and allows you to leave it untouched, adding a suitable entry to the GRUB (boot manager) menu. That's called dualbooting. If you want to keep Ubuntu, just resize your Linux partitions and create a new one for Windows; in my experience 4-5 GB should be enough.

> **Katman000 said:**
> Unfortunately I cannot due to the Linux Swap partitions that Gparted cant edit, why i dont know.
Odd. Please post the exact error message. Also, go to [http://sourceforge.net/projects/bootinfoscript](http://sourceforge.net/projects/bootinfoscript), download the script and run it from either the installed Ubuntu or the Live CD. It will output a comprehensive report of your partitions and operating systems found; copy and paste it here. 

> **Katman000 said:**
> I have tried various live cds that format the drivebut none have worked. The XP disk gives back a blue screen of death. Is there some way to format the disk that doesnt involve the partiton editor, and that I can use the live CD for?
Thanks
Okay, you don't format a "disk" as such, but rather partitions (what Windows calls "logical drives"). If you want to remove a partition you need a partition editor. You may try the Recovery Console in your XP installation CD. Anyway, I suspect something's funky with your partitions, so please follow the steps above.

---

### Post by raymondh on 2009-06-14
> **dnairb said:**
> Using gparted, right-click the swap partitition and select "swapoff" in the drop-down menu.
The swap partition will then be inactive and unused and you can safely delete it.


Hello Katman,

+1 .... remember that when using the liveCD, swap needs to be unmounted as gparted will not handle/touch any partition that is mounted .... hence give you greyed-out options.

You can also use the terminal

```
sudo swapoff -a
```

Good luck.

---

### Post by Katman000 on 2009-06-15
Thanks so much.
I cant believe I didn't see the swapoff option in the partition editor. Everything is going smoothly and I hope to have XP back up soon.

I could dual boot, if I had the hard drive space. I have a very old, homemade computer. The drive is 32 gb and I have had to reformat the computer of 4-5 times because of homemade viruses (yes I know it's stupid), random crap that I have had fun with that end up destroying my OS, and switching to Ubuntu. 

The main reason I'm switching back, is because I miss Starcraft, the only game my machine has run well, that I own.

Again, Thanks a bunch.

---

