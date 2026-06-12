---
title: "GRUB, Ubuntu, and Windows XP"
date: 2008-09-16
forum: General Help
---

### Post by kd7jur on 2008-09-16
So here's what i did. I installed Ubuntu on an existing xp system as a dual boot. This apparently installed grub. 

i have decided to redo my install within windows using wubi. but now my problem lies that grub is still there. 

when i try to use my xp disc to fix the MBR i get a corrupt file error 

[COLOR="Navy"]The file cpqarray.sys is corrupted.

Press any key to continue.[/COLOR]

then it says on the lil white bar at the bottom:

[COLOR="navy"]Setup failed. Press any key to restart your computer.[/COLOR]

and then it restarts.

I got grub reinstalled. had to install ubuntu to do this though. is there any other way to uninstall grub on an xp system that apparenty the repair option is out from the disk?

---

### Post by oygle on 2008-09-16
Try [this Google search]("http://www.google.com.au/search?hl=en&q=uninstall+grub+on+an+xp&btnG=Google+Search&meta=") , quite a few ways to do it.

---

### Post by caljohnsmith on 2008-09-16
Kd7jur, if you can get into the "recovery console" (command line) from your Windows CD, just run:
```
fixmbr
```
That will overwrite Grub with the Windows MBR. Let me know how it goes.

---

### Post by kd7jur on 2008-09-16
The only problem with all that is i can't get far enough in the XP cd to even get to the repair utility. it gives me the corrupt file error before i ever get to that, and i don't know if it is my CD or my computer. cyberciti.biz says that i can try this:

> Using Linux
You can also use dd command from Linux itself (it removes partition table):
# dd if=/dev/null of=/dev/sdX bs=512 count=1
Just remove MBR, without the partition table (see comment below):
# dd if=/dev/null of=/dev/sdX bs=446 count=1
Replace /dev/hdX with your actual device name such as /dev/hda. Use fdisk -l command to find out device name:
# fdisk -lOutput: 

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      104391   83  Linux
/dev/sda2              14       30384   243955057+  83  Linux
/dev/sda3           30385       30515     1052257+  82  Linux swap
 
The only problem here is that i don't know enought about linux to even be able to do this. i just got it installed. played a little then went to bed. haven't had time since because of work and school. thnx for any input so far though guys. if any other ideas plz reply.

---

### Post by caljohnsmith on 2008-09-16
I hate to be the one to break the bad news, but from your fdisk output it only shows your HDD has only linux partitions--no Windows partition. When you did the installation, did you choose "use entire disk"?

EDIT: Wait, is the above quote your own fdisk output or cyberciti.bi's fdisk output?

---

### Post by kd7jur on 2008-09-16
> **caljohnsmith said:**
> I hate to be the one to break the bad news, but from your fdisk output it only shows your HDD has only linux partitions--no Windows partition. When you did the installation, did you choose "use entire disk"?

EDIT: Wait, is the above quote your own fdisk output or cyberciti.bi's fdisk output?

No that was not MY fdisk output. that was found at cyberciti.biz ([http://www.cyberciti.biz/faq/linux-how-to-uninstall-grub/](http://www.cyberciti.biz/faq/linux-how-to-uninstall-grub/)). it's just an example from their website that i coppied. sorry about the confusion

---

### Post by caljohnsmith on 2008-09-16
Personally I wouldn't try to use Ubuntu with Wubi inside of Windows, as I know quite a number of people who have had problems with it, including myself. Wubi just adds another layer of complexity that increases the chances of something going wrong. So are you sure you want to go that route? Most likely it will only be harder, not easier, than using Ubuntu from its own partition. If you really want to get rid of your Ubuntu partition and use Wubi though, let me know, and I can give you help reinstalling the Windows MBR from the Ubuntu Live CD (if you have that). Or if you can download it, an easier way to reinstall the Windows MBR is to use [Super Grub Disk]("http://www.supergrubdisk.org/"); I would recommend that first.

---

### Post by kd7jur on 2008-09-16
Ok so i got my Ubuntu to actually boot the correct way. 2 partitions and all that jazz. Now my next task is installing programs. like i said im new to linux so i don't understand what is being said. Two programs i want to install are WINE and TeamSpeak2. Just to have them there. I play alot of WoW (surprise surprise). and i know that you can run WoW through Wine. any help would be appriciated. Thanks

---

### Post by mb_webguy on 2008-09-16
You can install Wine using Add/Remove Programs, but it's an old version.  You can get the newest version by following the instructions on [this page]("http://www.winehq.org/site/download-deb").

I don't know much about Teamspeak, but you can install the client by opening a terminal and typing "sudo apt-get install teamspeak-client", and you can install the server by typing "sudo apt-get install teamspeak-server".  I've read on a couple of posts about people having problems getting Teamspeak to work when other audio applications are open.  This sounds like a problem with Teamspeak working with PulseAudio (which is the sound server used by Ubuntu).  Following the instructions found in the "PulseAudio Fixes for Hardy Heron" link in my signature *should* fix that problem (as well as similar problems with other audio applications).

---

### Post by kd7jur on 2008-09-17
ok. apparently i must not understand. i don't know what the terminal is, or how to access it. oh well i'll figure it out.

---

