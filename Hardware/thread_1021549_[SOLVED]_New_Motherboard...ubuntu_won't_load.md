---
title: "[SOLVED] New Motherboard...ubuntu won't load"
date: 2008-12-25
forum: Hardware
---

### Post by Sesshomaru on 2008-12-25
Hey all,

I had a motherboard go out on me and had to replace it.  And of course I can't get back into ubuntu.  Is there any way to get ubuntu to recognize everything or do I have to reinstall?

Just a couple of notes:
Switched from an AGP mobo to a PCI.
Switched from an AMD to Intel.

About the only things that are the same are the sound card, hard drive, and 2 CD-Roms.  Everything else was replaced.

Any help is much appreciated.

A little background about my Linux proficency:
Long time Windows hostage and Linux dabbler.  Recently made the switch completely to ubuntu, so you'll have to baby me a bit with the command line info, though I am fairly comfortable with it (reminds me of the DOS days).  But when you give me some steps to follow, please don't leave anything out assuming I'll know...because I won't :P

Thanks all and Merry Christmas.

---

### Post by Sesshomaru on 2008-12-26
Anyone?  No one out there to help?

---

### Post by cariboo on 2008-12-26
It would help if you included any error messages you get when trying to boot Ubuntu. Changing motherboards shouldn't make any difference, as most of the drivrs needed are included with the kernel. If you are using a graphical boot turn it off by removing the quiet splash from the kernel line in grub, to edit the kernel line, press **e** when highlighting a menu select in grub and remove **quiet splash**.

Jim

---

### Post by Sef on 2008-12-26
> Anyone?  No one out there to help?
Please wait 24 hours before bumping your thread.  Thank you.


What motherboard did you get?

---

### Post by Sesshomaru on 2008-12-26
> **Sef said:**
> Please wait 24 hours before bumping your thread.  Thank you.


What motherboard did you get?

Sorry, will do that on future posts.


Motherboard is ASUS P5Q3.  *EDIT had a 4 instead of a 5*


The error I get when I start to boot into ubuntu is:
Boot from (hd0,0) ext3 57575051-06d1-4405-80db-b94523afc4c9
Starting up...
[         0.380222] PCI: BIOS BUG #0[00000031] found
Loading, please wait...
Gave up waiting for root device. Common problem:
-Boot args (cat /proc/cmdline)
   -Check rootdelay= (did the system wait long enough?)
   -Check root= did the system wait for the right device?)
-Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/57575051-06d1-4405-80db-b94523afc4c9 does not ext. Dropping to a shell!

BusyBox v1.10.2 yadda yadda yadda
(initramfs)



The system attempts to load ubuntu, but then drops to the shell.

---

### Post by cariboo on 2008-12-26
Your problem is pretty obvious, grub can't find your root partition:

> ALERT! /dev/disk/by-uuid/57575051-06d1-4405-80db-b94523afc4c9 does not ext. Dropping to a shell!

Could you boot from the LiveCD and post the output of:

```
sudo fdisk -l
```

The above command must be done in a Applications-->Accessories-->Terminal.

Also in the same terminal type:

```
blkid
```

Paste the output of both commands in your next post.

Jim

---

### Post by RJARRRPCGP on 2008-12-26
> **Sesshomaru said:**
> Sorry, will do that on future posts.


Motherboard is ASUS P4Q3.


The error I get when I start to boot into ubuntu is:
Boot from (hd0,0) ext3 57575051-06d1-4405-80db-b94523afc4c9
Starting up...
[         0.380222] PCI: BIOS BUG #0[00000031] found
Loading, please wait...
Gave up waiting for root device. Common problem:
-Boot args (cat /proc/cmdline)
   -Check rootdelay= (did the system wait long enough?)
   -Check root= did the system wait for the right device?)
-Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/57575051-06d1-4405-80db-b94523afc4c9 does not ext. Dropping to a shell!

BusyBox v1.10.2 yadda yadda yadda
(initramfs)



The system attempts to load ubuntu, but then drops to the shell.

Looks like the kernel failed to detect the IDE (also SATA) controller.

---

### Post by Sesshomaru on 2008-12-26
Alright,

So I tried to boot from the live CD, but I got the following:
> 
[      0.388222] PCI: BIOS BUG #0[00000031] found
Loading, please wait...

BusyBox yadda yadda...
Enter 'help' yadda yadda...

(initramfs)

Now what? :)

---

### Post by RJARRRPCGP on 2008-12-26
> **Sesshomaru said:**
> Alright,

So I tried to boot from the live CD, but I got the following:


Now what? :)

Probably failed to detect your disk controller! 

Even though Ubuntu Intrepid Ibex never gave me problems with detection. 

And even the IDE controllers on my Asus P5QL Pro are detected, thus, I'm puzzled why it goes to BusyBox with your PC. (other than I know that the uuid detection failed)

---

### Post by Sesshomaru on 2008-12-27
I get this error whether I try to boot from the HDD or the LiveCD:

> [ 0.380222] PCI: BIOS BUG #0[00000031] found

And if I cannot boot from the LiveCD, how do I fix this issue:

> ALERT! /dev/disk/by-uuid/57575051-06d1-4405-80db-b94523afc4c9 does not ext. Dropping to a shell!

Thanks.

---

### Post by Sesshomaru on 2008-12-29
Anyone have any further help or am I up the creek?

---

### Post by Sesshomaru on 2008-12-29
Figured it out!

The > [ 0.380222] PCI: BIOS BUG #0[00000031] found  seems to have been caused by the having the hard drive plugged into the SATA_E connector instead of the ICH10R SATA connector on the ASUS motherboard.  

After I swapped the connector, it boots into Ubuntu flawlessly. \\:D/

Thanks for your help all...I'm sure I'll be back :cool:

---

### Post by bgiannes on 2009-06-03
last night i started getting this error, followed with a kernal panic at boot, (nothing is pluged into the sata-e port)

every 10th boot it starts....

---

### Post by Sesshomaru on 2009-06-03
I am by far no expert on the subject of Ubuntu, but I would check for the latest BIOS update and driver updates for your MOBO.

Do you have an ASUS P5Q3 as well?

If you are getting this error "[ 0.380222] PCI: BIOS BUG #0[00000031] found"
then I suspect it is a hardware issue an not an Ubuntu issue.


Again, I have very little experience with Ubuntu or Linux in general.  I've made the transition from Windows about a year ago, and I've figured out a lot about fixing things in Ubuntu, but as far as understanding the error codes and such like I used to in Windows, I'm a long way off in Ubuntu.

I will tell you what the next person with any true Ubuntu knowledge will likely say: "Post the error and your system specs"

---

### Post by jms1989 on 2009-06-03
I have a ASUS P5QC mobo and I keep encountering the same error but the system still boot fine. I'm not sure what it might be related to but I suspect it could be a sata issue. I have the latest bios updates and have tried both the acpi sata option and the regular ide type. I haven't tried the raid since none of my drives are setup in raid.

---

