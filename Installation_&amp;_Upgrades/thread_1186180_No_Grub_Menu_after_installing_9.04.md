---
title: "No Grub Menu after installing 9.04"
date: 2009-06-13
forum: Installation &amp; Upgrades
---

### Post by skozzy on 2009-06-13
I have several HDDs in my computer, I selected a 1 TB drive as the one I wanted Ubuntu installed to (shows as the 3rd drive in BIOS), that drive has Windows 7 installed, so I was expecting after installing Ubuntu 9.04 to see a Grub menu to select either Windows 7 or Ubuntu.

But, I don't get a grub menu, it just loads Windows 7.

This is my 2nd attempt to install Ubuntu and the 1st attempt said there was a Fatal Error installing Grub and exited with no further messages.

The 1st HDD in BIOS is my 64gig SSD which has Windows Vista, being only 64gig there isn't enough space to install Ubuntu, so I changed the bios boot order to select this 1TB drive, and this is where I believe my problem is.

During the install for Ubuntu the partition manager wanted to install over the top of my Vista drive (the 64gig SSD), I selected manual install, selected the correct drive where I wanted Ubutu install, made the two partitions (ext3 and swap) in the free space on the drive, selected the ext3 mount point as /

Even though I changed the order of drives in bios for the boot drive the Ubuntu partition manager doesn't see the drives in that order, it has it's own order.

So what might have happened to the installing of Grub, how can I find which drive it may have been installed to, or how can I re-install it to the drive I choose.

---

### Post by gradinaruvasile on 2009-06-13
Go here and see if it helps...

[http://ubuntuforums.org/showthread.php?t=1035999]("http://ubuntuforums.org/showthread.php?t=1035999")

---

### Post by skozzy on 2009-06-13
After reading many of the post and following some instructions I now have the problem I tried to no have.

My Vista install is on a 64gig SSD (listed in bios as the first drive)
My Windows 7 install is on a 1TB drive (listed in bios as the third drive)

In bios I have the SSD drive as the boot drive for Vista. When I want to use Windows 7, I go in to bios and select drive 3 as the boot drive.

This drive 3 with Windows 7 is where I also installed Ubuntu 9.04, and I wanted a grub menu on it to choose between Windows 7 and Ubuntu. I did the following and it didn't happen, what I got now (which I didn't want) is when I have the SSD drive as the boot drive in bios it now loads GRUB and I don't have access to my Vista install any more (Bootmgr error).
I am sure I will get it to boot again after trial an error, but just how hard is it for someone relativly new to Ubuntu to get it to install the OS and Grub to the drive they select in bios.

This is what I did to nerf my Vista drive.
I booted the live CD, opened terminal and typed:
sudo grub
find /boot/grub/stage1

The reply showed hd3,2

So I typed:
root (hd3,2)
setup (hd0)
quit

These were the instructions mentioned several times in the link supplied from the reply to this thread.

The screen displayed usefull information that said everything worked (basiclly).

I rebooted and still Windows 7 loaded and no grub menu.

So I wanted to give up and have a coffee and went back to bios and selected the SSD drive as the boot so I could get back in to Vista. But when I rebooted I got a grub menu, Vista won't load, I get a bootmgr error, but I can load Ubuntu.

Not what I wanted.

So where did I go wrong, was it the command setup (hd0) the nerfed my Vista disk with grub ? or will grub only install to the first drive in bios reguardless of the order I select for the boot device.

I will assume I can get my Vista boot loader replaced with the recovery option on the Vista DVD, so I won't panic yet, but when I select drive 3 as the boot drive in bios how to I get grub in that drives boot sector ?

---

### Post by skozzy on 2009-06-13
After another reboot I no longer get a bootmgr error when trying to load my Vista, but as a bonus I can now load all 3 OS's, Vista, Win7 and Ubuntu from Grub without changing the boot drive in bios.

One thing it effected was Hibernate on Vista, it reports a bad shutdown. But for now I can live with that.

But I would still like to know how to get Grub on drive 3 and not drive 0 so I can leave my Vista install alone.

---

### Post by gradinaruvasile on 2009-06-13
Maybe 
root (hd3,2)
setup (hd[COLOR="Red"]3[/COLOR])
quit
?

---

### Post by skozzy on 2009-06-13
That is what I was thinking of trying next, but wanted to see if someone confirmed it before I make anything worse.

---

