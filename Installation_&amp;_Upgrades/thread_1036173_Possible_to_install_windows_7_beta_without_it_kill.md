---
title: "Possible to install windows 7 beta without it killin ubu partition?"
date: 2009-01-10
forum: Installation &amp; Upgrades
---

### Post by josephellengar on 2009-01-10
Now that the beta is legal, I thought I'd re-ask this question.  I've got a hard drive with xp and ubuntu.  I'd like to try out windows 7 and overwrite my xp install because I don't use it anymore, so is there any way to do this without the beta killing my ubuntu partition?  Thanks!

---

### Post by cwsnyder on 2009-01-10
I am planning to install the Win7 beta in a VirtualBox virtual machine to sandbox it, preventing it from contaminating both my WinXP and my Linux partitions.

---

### Post by josephellengar on 2009-01-10
> **cwsnyder said:**
> I am planning to install the Win7 beta in a VirtualBox virtual machine to sandbox it, preventing it from contaminating both my WinXP and my Linux partitions.

That's a good idea, but my virtualbox almost always freezes or doesn't work when I try to get it to read iso files from my hard disk.  Do you know why this might be?  I thought about doing it, but every other time that I've tried to install something in vbox, it hasn't worked.

---

### Post by cwsnyder on 2009-01-17
I don't know why VirtualBox is crashing for you.

On another forum, I have read of people installing dual boot XP/Win7, since the beta is a limited shelf-life product.  Since you already have the disk partitioned for XP and Ubuntu, you should be able to install Win7 on your XP partition, just don't let Win7 change the partitioning.  You probably will have to re-install GRUB to be able to switch back to Ubuntu, but you can re-install GRUB from your Ubuntu install disk.

cwsnyder2

---

### Post by Mark Phelps on 2009-01-19
Just a quick "heads-up" -- so you don't set your expectations too high regarding Windows 7 ...

Despite earlier pronouncements, it appears that Seven is based on Vista -- much the same drivers, very similar GUI, very similar features.    Which is another way of saying, if some hardware or application didn't work with Vista, it most probably won't work with Seven, either.

Also, at least for this Beta, there is no upgrade path from XP, instead, you must be running Vista SP1 to do an upgrade.  Whether this limitation will persist to the actual release, MS isn't saying.

So, once you get Seven installed (if it DOES install), don't be terribly surprised if you then have major driver issues.  I have a working Vista SP1 partition, and it took Seven a couple of reboots to update my Vista drivers before they would work properly.

---

### Post by cariboo on 2009-01-19
So far I've run into quite a few compatibility problems. Microsoft programs seem to work OK (Office 2003), but a lot of 3rd party apps don't work. As usual the default drivers work, but only just. I used the Vista 64bit drivers from the manufacturers (sound card, video card and network) and happily they work quite well. Unhappily my Logitech Quickcam Messanger does not work, even with the latest drivers from Logitech.

Why can't Windows be more like Linux and include drivers for most hardware? :)

When I installed Windows7 it wiped out the MBR so I had to reinstall grub, I used [SuperGrub Disk]("http://www.supergrubdisk.org/") to repair grub, it only took a couple of minutes.

Jim

---

