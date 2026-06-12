---
title: "Windows XP won't boot, boots GRUB instead. Need help"
date: 2008-08-18
forum: General Help
---

### Post by Trax415 on 2008-08-18
Hello. 

I have had Ubuntu on my older laptop for a while. However, I recently sold it online, and the person wanted Windows XP to be on it. That was fine. 

I went into the Bios and made sure the first boot priority went to my DVD/CD drive. Saved the settings, and booted up Ubuntu. I then put the Windows XP cd in the drive, and re-started my computer. Instead of booting up Windows XP install CD, GRUB boots. 

This never happened to me under the older 7.** versions of Ubuntu. Now I am stuck. 

Is there anyway to fix this problem? or boot the Windows XP CD from inside of Ubuntu? 

I really need help. Thanks.,

---

### Post by Inane_Asylum on 2008-08-18
Are you sure the CD/DVD drive is first in the boot priority in the BIOS?  If that doesn't work, try hitting F12 (I think...it may be different among computers) and selecting to boot from CD/DVD manually.  Mine says "press any key to boot from CD" and gives me a few seconds to confirm that I actually do want to.

---

### Post by Trax415 on 2008-08-18
> **Inane_Asylum said:**
> Are you sure the CD/DVD drive is first in the boot priority in the BIOS?  If that doesn't work, try hitting F12 (I think...it may be different among computers) and selecting to boot from CD/DVD manually.  Mine says "press any key to boot from CD" and gives me a few seconds to confirm that I actually do want to.

I am 100 percent sure it is set in the Bios. 

When I hit F12, and select DVD/CD, it still boots up GRUB.

This happens with every single CD/DVD I have, EXCEPT The Ubuntu 8.0.4. CD I burned.

---

### Post by Inane_Asylum on 2008-08-18
I don't know...

Since you're going to do a fresh install of XP anyway, maybe you could make a boot floppy with a fixmbr program on it so you can take GRUB out of the picture.  That would at least tell you whether GRUB is the problem, or if it's a hardware issue.

I don't see how GRUB **could** override the BIOS boot priority, though.

Strange...

---

### Post by Inane_Asylum on 2008-08-18
Maybe some of the more Ubuntu-genius types should weigh in on this issue, as this would effectively keep Ubuntu from loading...

---

### Post by caljohnsmith on 2008-08-18
Can you boot from a floppy? If you can do that, there's a great program called "Smart Boot Manager" that you can install onto a floppy, and when you boot the floppy, it will give you a choice to boot your CD-ROM. I've used it on a computer with a really old BIOS that wouldn't boot a CD-ROM, and it worked great. If you want more details let me know.

---

### Post by Trax415 on 2008-08-18
Sadly I can't boot from a floppy, because the Laptop does not have a flopp drive. 

I have been searching the net for a few hours, and nobody seems to have this problem. (Most people have a problem with dual boot, but they can at least get their XP CD to boot in the first place). 

I have asked a friend to lend me his newer copy of Xp to see if that boots. However outside of that, I am really at a loss right now.

---

### Post by -Zeus- on 2008-08-18
sorry to bum you off but I have a really hard time believing that this has **anything** to do with ubuntu...

---

### Post by Inane_Asylum on 2008-08-18
> **Trax415 said:**
> This happens with every single CD/DVD I have, EXCEPT The Ubuntu 8.0.4. CD I burned.

What CD's are you trying to boot exactly (besides Ubuntu and WinXP)?

---

### Post by Trax415 on 2008-08-19
> **Inane_Asylum said:**
> What CD's are you trying to boot exactly (besides Ubuntu and WinXP)?

BartPE
Vista
etc..

---

### Post by bingoUV on 2008-08-19
1. Nothing to do with ubuntu
2. Other CDs are bad. To make sure, completely disable hard disk as a boot device i.e. not just lower its priority but remove hard disk from boot device list in BIOS.
Now boot from the CDs. It should not boot at all.

---

### Post by mcduck on 2008-08-19
That is definitely a BIOS issue, and has nothing to do with Ubuntu/Grub. The boot order is handled by BIOS before the Grub is even loaded, so there's no way Ubuntu or Grub could affect your boot at that point...

Either you don't have correct boot order configured in BIOS, or your discs are not bootable.

---

### Post by ajohnson2289 on 2008-08-22
I believe this issue has something to do with having multiple partitions on your hd, and the xp cd not liking that. check out this post for more details.

[http://www.ozzu.com/mswindows-forum/won-boot-t73477.html#p470341](http://www.ozzu.com/mswindows-forum/won-boot-t73477.html#p470341)

---

### Post by caljohnsmith on 2008-08-22
> **ajohnson2289 said:**
> I believe this issue has something to do with having multiple partitions on your hd, and the xp cd not liking that. check out this post for more details.

[http://www.ozzu.com/mswindows-forum/won-boot-t73477.html#p470341](http://www.ozzu.com/mswindows-forum/won-boot-t73477.html#p470341)
+1 for ajohnson2289's idea. :) Trax415, that tutorial above may seem a little lengthy, so to try it, all you really need to do is the following from your Ubuntu partition or a Live CD:
```
sudo fdisk -lu
```
Find which partitions are Linux (Ubuntu), and then do:
```
sudo grub
grub> hide (hdX,Y)
```
Where (hdX,Y) is your Linux partition, and repeat above for each linux partition you have. If that works and you can boot your Win XP CD, then you can unhide them afterwards:
```
sudo grub
grub> unhide (hdX,Y)
```
If you need more details, let me know.

---

