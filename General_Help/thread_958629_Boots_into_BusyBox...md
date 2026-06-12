---
title: "Boots into BusyBox..?"
date: 2008-10-25
forum: General Help
---

### Post by jameswhite15 on 2008-10-25
Only recently installed Ubuntu on my old pc to just to try it out.

Worked fine the first time but after I rebooted it it came up with this message:

"BusyBox v1.1.3 ( Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter help for a list of built in commands

(initramfs)"

No idea what to do, please help :)

---

### Post by Divider on 2008-10-26
> **jameswhite15 said:**
> Only recently installed Ubuntu on my old pc to just to try it out.

Worked fine the first time but after I rebooted it it came up with this message:

"BusyBox v1.1.3 ( Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter help for a list of built in commands

(initramfs)"

No idea what to do, please help :)

 
I am having the same problem with a server of mine, I attempt to load hardy server and desktop on this system, and nothing happens. I think this might have something to do with SCSI drives. What hardware are you running?

---

### Post by mkhattab on 2008-10-26
Hi guys,
I've the same problem as jameswhite15 
Some times the system boots correctly and others I boot to the busybox built in shell 
Could any one tell us how to enter the user GUI from the busybox shell?
Thanks in advance

---

### Post by themattinator on 2008-11-08
same problem here! well, mine happened after reboot after system updates :(

---

### Post by GuitarRocker2562 on 2008-11-08
Sorry to inform you, but when the system boots into BusyBox, something isn't right. And usually, it is a large error. T fix it your best bet is to use the live CD.

---

### Post by themattinator on 2008-11-08
right well i just hit escape during the countdown. There was two kernels that said recovery mode. I picked one, and here I am back in Ubuntu. I'm kinda scared to restart though.

---

### Post by kleeman on 2008-11-08
I have had this problem on 2 boxes both of which have scsi hard drives

[https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/244608](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/244608)

In my case I typed "exit" into the busybox prompt and got a normal boot.

Feel free to add to the bugreport as it is a very annoying problem. I tried the hardy kernel in intrepid and the problem didn't occur so it is a kernel problem. Probably the scsi driver/module..

---

### Post by broonsparrow on 2008-11-08
I've got this problem running a LIVE CD!

Any ideas?

Should say it's 9.10 and the PC has a SCSI drive.
installed 8.10 on a HD and it fails to boot (Error 17) so tried booting from LIVE CD and got this busybox problem.....tried waiting and enetring exit....no luck :-(

---

### Post by kleeman on 2008-11-09
Try using hardy 8.04 and then upgrade. I found using the 2.6.24 kernel (i.e. the hardy kernel) in intrepid worked fine. The upgrade leaves the hardy kernel available.....

---

