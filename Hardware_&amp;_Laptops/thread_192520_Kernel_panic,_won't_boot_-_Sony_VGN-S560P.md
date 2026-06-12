---
title: "Kernel panic, won't boot - Sony VGN-S560P"
date: 2006-06-08
forum: Hardware &amp; Laptops
---

### Post by leaded on 2006-06-08
Hey everyone. I've been posting a lot lately about getting Ubuntu working on my Sony VAIO S560 (VGN-S560P). I finally got Ubuntu to install using the alternate CD and the text-mode install. But now I can't get it to boot.

The first reboot after installing I was able to log into Gnome but the whole system locked up shortly after that. I shut it down forcefully and started it again. This time it got to the login screen and froze. Now, it doesn't boot. I get what looks like kernel panic messages whenever I boot the machine. I tried the Grub option for recovery mode and I get the same errors. 

I tried options like noacpi and acpi=off and all of the others I could find online but none helped. I think after I used acpi=off I was prompted to restart with pcb-bios=off or *something* and to update my laptop's firmware. Well, the kernel option didn't work and my BIOS was already up to date per Sony. I started it once without the quiet option and saw all kinds of messages but I don't know which is important.

Is there any way for me to capture a log of the boot messages to try and get some help? Or, is there some other way I can get my laptop to boot? Could it be drivers? How can I diagnose the problem?

Please help, thanks!!!!!

---

### Post by Zathrus on 2006-06-09
Hi again leaded, this problem sounds familiar to me also. If you recall my last post in response to you the only linux system I could get running was debain using 2.6.12 kernel. After I installed it I did a kernel upgrade to 2.6.15, everything seemed to work fine when I booted up but before I could do anything the hdd goes crazy and the system hangs. I thought I was going crazy because I also was able to log into kde at first but not actually able to do anything. Subsequent reboots it didn't get so far.

Some people claim to have had success by going into bios and turning their sata drives onto compatibility mode but these sony laptops give you almost no control in the bios over anything.

Anyway I'd just like to add this to the discussion in the hopes that someone might know of a fix for this because it sounds like it would solve my problems too :)

The thing that confuses me is that it appears to boot ok for a while, it's got to be something that the kernel is loading because for it to start loading at all it needs to be able to see the disk. Unfortunately I dont have the expertise or time to try to track this down, any help would be much appreciated.

---

### Post by djorzgul on 2006-06-09
hello to all. 
unfortunately I must confirm everything stated here. It looks like, for now, it's impossible to have ubuntu installed. I have vgn a317m, and I manage to install till now only mandriva/mandrake and suse 10.1...
It would be nice to hear someone much more experienced on this matter

---

### Post by leaded on 2006-06-10
I remember your post Zathrus, it's interesting to think that the newer improved kernels kill support for certain VAIOs. Maybe reverting to older kernels is the only way to get by.

Hmm... CentOS is based off RHEL 4 and is still using a 2.6.9 kernel. I just may give that a shot. Bummer though- I really like all of the laptop-friendly features of Ubuntu :(

Linux experts- is there any way to install Ubuntu with an older kernel!???

---

### Post by leaded on 2006-06-10
Could it be possible to rebuild the Ubuntu kernel without some SATA feature? I've never done that before... 

Could I install Ubuntu to a vmware instance someone, build a new kernel, and then somehow transfer that kernel onto my laptop with a liveCD?????

---

### Post by leaded on 2006-06-13
Anyone? I'm about ready to give up and wait for Edgy...

---

