---
title: "Installing Ubuntu after Win7"
date: 2009-08-20
forum: Installation &amp; Upgrades
---

### Post by roypk on 2009-08-20
Hi,

I was running Ubuntu 9.04 64 and XP64 on my machine.  Both coexisted without any problems until the HD died.  I got a new HD and decided to have a go with Win7 64 instead of XP64.  I installed Win7 and then Ubuntu.  Ubuntu recognised Win7 as Vista and proceeded with the installation.  I didn't expect any problems as Ubuntu used to be on this machine.  I was wrong.  Although, the installation went smoothly, I didn't get the menu to choose the OS at boot time.  The system booted straight into Win7.  I had noway to boot Ubuntu.  I tried using GParted to change the boot partition to Ubuntu.  That didn't work either.  Now, I'm stuck.  Any advices on the issue would be greatly appreciated.  I really want to get the Ubuntu up and running.  One thing I might add is that.  When I installed Win7, I used a pre-partitioned space so that Win7 didn't create the hidden partition. I don't know whether this is a factor or not.

Best regards,
Roy

---

### Post by Herman on 2009-08-20
Ubuntu doesn't need the boot flag, so you can use GParted to set that back in your Windows partition if you like.

Try downloading Super Grub Disk and make it into a CD or floppy disk or USB, according to what type of Super Grub Disk file you choose. Then try booting Ubuntu with Super Grub Disk.
Once Ubuntu has booted, you can try installing GRUB again from your running Ubuntu system and it should (hopefully) install okay.

Let me know if you want a more detailed answer and I'll try harder to describe what to do if you need me to.

---

### Post by presence1960 on 2009-08-20
Boot from Ubuntu live Cd & choose "Try Ubuntu without any changes", when the desktop loads open a terminal and run this command ```
sudo fdisk -l
```
that is a lowercase L at the end. post the output back here please.

Super Grub Disk may work as well. If not run that command and post the output.

---

