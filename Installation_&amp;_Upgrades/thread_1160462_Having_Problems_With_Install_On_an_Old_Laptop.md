---
title: "Having Problems With Install On an Old Laptop"
date: 2009-05-15
forum: Installation &amp; Upgrades
---

### Post by Rory Williams on 2009-05-15
I am trying to install ubuntu 9.04 on an old laptop with no cd-rom and no ability to boot from USB. The computer is a Compaq Presario 1700 with the following:
Around 1Ghz Pentium 3 Processor
192MB DDR RAM 
5GB Hard Drive 
NO Optical Drive
Windows 98 SE 

Since I couldn't use the Live CD version of Ubuntu Linux 9.04, I have tried the following: 

Downloaded the Ubuntu Linux 9.04.iso and put it on the root drive c:

Tried the Linux installer UNetbootin, but it failed. 

Attempted a manual install by creating the folder c:/boot and following [these instructions]("http://www.instantfundas.com/2007/08/install-any-linux-distro-directly-from.html")  This failed, as well.

Frustrated, I opened windows explorer and moved all the system files (including hidden) from the root to a folder on the root, leaving only boot.ini and grldr.

Rebooted and got this, "Invalid System Disk, replace the disk then press any key." Windows now does not boot. (yay?) 

Next I downloaded a Grub boot floppy and booted from that. This worked, and I reviewed the Linux install options. Opening the menu.lst file from my c/boot folder, I selected the Install Linux command I had created earlier. It found and loaded the Kernel file vmlinuz, but failed to find the initrd. 

I opened up a grub command line and after playing around with some commands, figured out how to load the kernel with "grub> kernel (hd0,0)/boot/vmlinuz"and initrd with "grub> initrd (hd0,0)/boot/initrd.gz after loading these, I typed "boot", hit enter, and success! Well, sort of. Linux loads, a bunch of code flys accross the screen, and I'm thinking that I should see a graphical interface pretty soon. 

I was wrong. The flying code hangs at "waiting for root device" and after about thirty seconds, gives me the error, "gave up waiting for root device" and falls into a BusyBox console with an "(initrdfs)_" prompt. I typed in "exit" but this just gives me the same error again.

A freind explained that this is because the HD is in the wrong format, but if I format it, I will lose the data on the disk, right? I have an external HD and CD drive, but since they are USB, I don't think I can boot from them unless there are drivers. 

Should I just give up?

---

### Post by jerrrys on 2009-05-15
what i see is a 5gig hard drive...ubuntu 8.04 takes 8.5gig...

---

### Post by Dex73 on 2009-05-15
I agree. I once tried to partition my laptop with vista and Hardy, giving Hardy only 8 gigs, went bad obviously. Also depends on how many files you have you could need more that even 8.5 gigs. I've definitely seen some similar threads in the past. You should be able to get a lot more info if you search some more.

---

### Post by Rory Williams on 2009-05-15
so I should try Xubuntu?

How would I install it?

---

