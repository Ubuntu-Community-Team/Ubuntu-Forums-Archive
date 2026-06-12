---
title: "Reinstall Jaunty on a Hardy/Jaunty Dual Boot"
date: 2009-06-04
forum: Installation &amp; Upgrades
---

### Post by frogotronic on 2009-06-04
Hello,

I have installed Jaunty as a dual boot on my Hardy system.  But I do not have an entry in GRUB with which to choose Jaunty.

Jaunty is installed on a 30GB partition on my single drive (laptop) - see GParted Screen Shot.

Q) Can I repair GRUB so that it "sees" the Jaunty install?

Q2)  How do I "reinstall" Jaunty using the liveCD(?)/alternateCD(?) overtop of the existing Jaunty install?

Thanks,
CH

---

### Post by presence1960 on 2009-06-04
I would do this:

```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition # is, to install GRUB to a 
   partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.
```

At # 4 you should get (hd0,0) & (hd0,1). The latter is Jaunty. 
At # 5 I would use root (hd0,1)
At # 6 setup (hd0)

 No need to reinstall unless after this you find jaunty is messed up. But you won't know until you get it in GRUB & try to boot it.

---

### Post by frogotronic on 2009-06-05
Hello,

Thanks for that - tried it and didn't work.  I did reinstall Jaunty and it worked.  I feel like an idiot for not seeing the *slider* that allows one to increase the Jaunty install from 2.5 GB to a much larger size.  I did a reinstall and it worked.

- CH

---

### Post by presence1960 on 2009-06-05
> **cement_head said:**
> Hello,

Thanks for that - tried it and didn't work.  I did reinstall Jaunty and it worked.  I feel like an idiot for not seeing the *slider* that allows one to increase the Jaunty install from 2.5 GB to a much larger size.  I did a reinstall and it worked.

- CH
We learn from our mistakes. I make enough mistakes but I look at it as a learning experience. If you play it safe you will never learn anything. You took that step into the unknown and installed a new OS. So you botched an install. Now you learned what went wrong and you fixed it. Now you know something you didn't prior to the mistake. So it was a good thing that mistake wasn't it?

---

### Post by frogotronic on 2009-06-07
yep, it was WAY easier than I was trying to make it.  I couldn't believe there was a slider (it was a redesigned GUI)!  Ha.

Pretty swank installer once I figured it out.

- CH   ):P

---

