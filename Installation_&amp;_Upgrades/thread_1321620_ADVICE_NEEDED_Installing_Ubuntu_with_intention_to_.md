---
title: "ADVICE NEEDED: Installing Ubuntu with intention to triple boot with Vista &amp; XP"
date: 2009-11-10
forum: Installation &amp; Upgrades
---

### Post by Gleep on 2009-11-10
To explain the situation...

I currently have a machine which came with Vista already installed, with a second drive with XP installed.

This was because my old pc's motherboard died, and in the end I was better off buying a whole new machine, so just popped the drive with XP in this one because it has my files on it. So I am using Vista, and accessing my files from the XP drive.

Only problem there is, the other machine also had a drive with Ubuntu on, which I have left without a home.

Because I was originally dual booting XP and Ubuntu, accross two drives, I now can't boot up XP because grub is broken.

I would like to be able to boot into XP again, so I'm guessing I'd need to 'fix' grub to do so.

But I also miss having Ubuntu, and feel that if I  can triple boot and fix grub so I'm able to boot into XP again at the same time, that would be excellent.

BUT I'm not sure what the best way of going about it would be, and because I don't want to break anything I thought I would ask for advice here first. Usually I'd just shrink some space on my Vista drive(the Vista drive is 300gb, 169gb of which Vista has named 'Data', and I have left unused, whereas the XP drive is only 149gb and has 43gb free space), pop in the Ubuntu Livecd and get installing, but I just wanted to know if that was gonna cause problems, or whether I'd even be better off buying a splitter so I can put the 80gb drive in too and just using that instead?

Any advice much appreciated :)

---

### Post by darkod on 2009-11-10
Sounds like you have a lot of options. If I understand correctly, the Ubuntu drive is not even plugged in right now. As you say you could just plug it in, set it as a first drive (I guess grub is installed there) for boot, and add entries in grub for Vista and XP (should be already there since you were dual booting them before).

I didn't understand what kind of splitter are you talking about, is that for the power cable for the drive?

You could also leave your Ubuntu drive out of your PC, and just work with the two currently inside. Don't see why it wouldn't work. Installing Ubuntu would probably detect both Vista and XP and fill in grub correctly.

If you are asking about partitions advice, probably you are the best person to know your requirements, and what size you need your partitions to be.

---

### Post by Gleep on 2009-11-10
Ah yes sorry, the splitter would be for the power cable :)

That is reassuring then, as long as the fact there is still some sort of... remnant of grub still on the xp drive wouldn't affect things, I may just go ahead and install do a fresh install tonight :)

---

### Post by fenario on 2009-11-10
Hello, I haven't got an easy solution to this. I have a triplr boot machine: windows7, XP and Ubuntu. It was messy but eventually I got it working. 
you may have to rescue your files with a Linux CD and then, reinstall it all.
Look into a small .exe application called: EasyBCD v1.7.2; it will reinstall the vista bootloader (same in windows7 as vista) because after adding XP to Windows7 it will lose the loader. So EasyBCD will reconstruct it. It will install neo-grub and that can be directed to the grub menu.list. I installed a menu list into a tiny partition by itself so that I can re-install ubuntu without changing the location of that menu. Ubuntus grub menu will only direct you to one windows bootloader, not the two we'd like (as far as I'm aware).

---

### Post by darkod on 2009-11-10
He already has everything installed on different hard drives, as far as I understood.

If all three drives are installed in the PC you just have to decide which will be the first boot option, adjust in BIOS, and install grub on that drive (if not already there). If grub is already there just make sure it points to correct Ubuntu, Vista and XP partitions to start and that's it.

---

### Post by Gleep on 2009-11-10
Thanks for everybody's replies!

> **darkod said:**
> He already has everything installed on different hard drives, as far as I understood.

If all three drives are installed in the PC you just have to decide which will be the first boot option, adjust in BIOS, and install grub on that drive (if not already there). If grub is already there just make sure it points to correct Ubuntu, Vista and XP partitions to start and that's it.
This sounds like the easiest and most *safe* option, think I'll buy a splitter for the power and just stick my third drive in :D

---

