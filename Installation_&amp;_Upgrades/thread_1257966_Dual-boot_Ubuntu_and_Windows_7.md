---
title: "Dual-boot Ubuntu and Windows 7"
date: 2009-09-04
forum: Installation &amp; Upgrades
---

### Post by alexluong on 2009-09-04
Just installed Ubuntu on my computer. I love it! Super stable, fast, some great programs pre-installed! Still, I need the full compatibility of some Windows programs. I'm aware of Wine, but I think it would be best to dual-boot. I've never done this before, so I'd like to know how much space I should set aside to install Windows 7 and a few programs on it. My hard drive is around 250GB, and I never go under like 90GB. Let me know! Thanks.

---

### Post by presence1960 on 2009-09-04
> **alexluong said:**
> Just installed Ubuntu on my computer. I love it! Super stable, fast, some great programs pre-installed! Still, I need the full compatibility of some Windows programs. I'm aware of Wine, but I think it would be best to dual-boot. I've never done this before, so I'd like to know how much space I should set aside to install Windows 7 and a few programs on it. My hard drive is around 250GB, and I never go under like 90GB. Let me know! Thanks.

if you only need it for a few programs half of that 90 GB would still be overkill!

Just remember that if you install Windows after Linux on the same hard disk you will have to reinstall GRUB to MBR as windows will write it's bootloader to the MBR. But that is a simple 45 second fix like this:

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

In #6 use setup (hd0) to put GRUB onto MBR


```

If you are putting windows on a separate hard disk no need to restore GRUB. Just be sure to put the Windows disk as first in hard disk boot order in BIOS, Then install Windows and when done check that it boots directly into windows. if it does reboot, switch the disk with Ubuntu to first in hard disk order in BIOS so GRUB comes up when you boot. You may have to add the windows entry for GRUB in menu.lst. If you don't know how post back.

---

### Post by alexluong on 2009-09-06
So what do you recommend? I want it mostly Ubuntu. I hear some people even create a third partition for storage between the two operating systems. How should I split up my 250GB? :)

---

### Post by presence1960 on 2009-09-06
> **alexluong said:**
> So what do you recommend? I want it mostly Ubuntu. I hear some people even create a third partition for storage between the two operating systems. How should I split up my 250GB? :)

I would say give Windows 7 30 GB & create a NTFS partition for shared data. The size depends on how much data you want to share between Ubuntu & Windows.

---

