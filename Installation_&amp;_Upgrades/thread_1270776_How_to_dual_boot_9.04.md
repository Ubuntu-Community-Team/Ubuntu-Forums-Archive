---
title: "How to dual boot 9.04?"
date: 2009-09-20
forum: Installation &amp; Upgrades
---

### Post by WatTwo on 2009-09-20
okay, so i have an 80gb hard drive, i already made a partition ready for ubuntu, (wubi install atm)

but the partition is _15Gb_, and the amount of free space i have on my windows, is _31Gb_.

I don't want to do a wubi install. (what i have now)

So how do i set this up?

Because if i select the "largest free space" option, it would install on my windows partition right?

Help.

---

### Post by raymondh on 2009-09-20
> **WatTwo said:**
> okay, so i have an 80gb hard drive, i already made a partition ready for ubuntu, (wubi install atm)

but the partition is _15Gb_, and the amount of free space i have on my windows, is _31Gb_.

I don't want to do a wubi install. (what i have now)

So how do i set this up?

Because if i select the "largest free space" option, it would install on my windows partition right?

Help.

My suggestions:

1.  back-up your files
2.  [Uninstall your WUBI-Ubuntu]("https://wiki.ubuntu.com/WubiGuide") ... ensuring that you also edit your current boot.ini file to remove the wubi related line (**ONLY THE WUBI-UBUNTU RELATED LINE** or you risk not booting into windows as well)
3.  Defrag your windows (2x if possible)
4.  Boot into the liveCD and install ubuntu in its' own partition.  Since you have prepared space already for it, you choose "largest free space".

If you are not happy with the space you allocated for Ubuntu ..... after step 3 above you:

a.  Use the windows disk management tool to enlarge windows
b.  Boot into the liveCD and when you install, you can choose "side-by-side".  When you choose this option, you are given a SLIDER (see visual attached) which you GRAB and SLIDE to allocate partition sizes you prefer.

[http://ubuntuforums.org/attachment.php?attachmentid=121997&d=1248267874](http://ubuntuforums.org/attachment.php?attachmentid=121997&d=1248267874)

Grub would auto install in either method and give you the option to choose which OS at start-up.

Back-up. You may want to [download and burn]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") this first (if you are using Vista) just in case the install misfires and you have problems booting into windows.

Good luck.  Post back success or error.

---

### Post by WatTwo on 2009-09-20
Well i might try that in the future, what i did was just uninstall the wubi, reinstalled as wubi with more space for now

---

### Post by raymondh on 2009-09-20
> **WatTwo said:**
> Well i might try that in the future, what i did was just uninstall the wubi, reinstalled as wubi with more space for now

Excellent.  Keep windows sterile and organized (virus free and defragged) and you should have a positive Ubuntu experience.

Happy ubuntu-ing.

---

