---
title: "I can't get Ubuntu to start up"
date: 2007-08-03
forum: Hardware &amp; Laptops
---

### Post by Mardok45 on 2007-08-03
I just upgraded my motherboard and CPU to an Asus P5B Deluxe and a Core 2 Duo E4400.

I have two hard drives in my system connected via ATA and a DVD drive connected via SATA.  My BIOS can detect all my drives perfectly fine.  However, when I boot into Ubuntu's installation CD, it can't detect my hard drives.

I went back into my BIOS and selected IDE configuration.  I selected "Configure SATA as", and changed it from IDE to AHCI.  I rebooted and Ubuntu detected my hard drives perfectly fine.

So after I installed Ubuntu and rebooted, GRUB would throw an Error 22 at me.  I can't remember what I did afterwards but I know I reinstalled Ubuntu on both hard drives (it was late).  Now I can boot into Ubuntu but when it finishes loading, it freezes when it starts up X.

Does anyone know what's going on?

---

### Post by dougfractal on 2007-08-03
Two methods 
one commandline (quicker)
one graphical

from [http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)

> apps4apps
November 13th, 2005, 04:55 PM
Aaargh!! Thank you guys!! Very very very much!! You saved my virtual life!

I lost my Grub / MBR and YOU restored it!

After searching too much time on the web, I fell on this topic. I read it completely and applied a mix of your solutions.

Here's the steps I followed to restore GRUB / my initial MBR:

1. Boot with any live CD (I've done it with Ubuntu Live DVD)
2. Get a root shell -> Applications / System Tools / Root Terminal
3. Make a folder -> mkdir /mnt/ubuntu
4. Check the Ubuntu partition -> fdisk -l (Mine is /dev/hda4)
5. Mount the root partition of Ubuntu -> mount -t ext3 /dev/hda4 /mnt/ubuntu (replace /dev/hda4 by your Ubuntu partition determined at the step 4)
6. Chroot the mounted partition -> chroot /mnt/ubuntu
7. Restore Grub / the initial MBR -> grub-install /dev/hda
8. Exit the shell
9. Reboot

That did the trick for me.

Thank you very much again to all of you! ( :bigsmack: )

Hi All,

I ran out of space on my original HD and am trying to get a cloned version on a larger drive running but am hitting a large brick wall. The closest I seem to have come so far is to boot with the live CD and try the suggestion above. The problem that I'm running into however is that it won't seem to let me mount the partition. Using fdisk -l to get the partition info to mount I see /dev/hda5 as Linux LVM with an id of 8e. When I try and mount /dev/hda5 I get: /dev/hda5 already mounted or /mnt/ubuntu busy
> 
Any suggestions would be greatly appreciated...
theswan
November 14th, 2005, 01:30 AM
Restore GRUB quite simple in Ubuntu, instead going through all the "gain root access" and play with shell commands, you can use the Ubuntu installation CD to restore it without going through all kinds of hassles.

Here are the steps:

1. Boot your computer up with Ubunto CD
2. Go through all the process until you reech "[!!!] Disk Partition"
3. Select Manual Partition
4. Mount your appropriate linux partions

/
/boot
swap
.....

5. DO NOT FORMAT THEM.
6. Finish the manual partition
7. Say "Yes" when it asks you to save the changes
8. It will give you errors saying that "the system couldn't install ....." after that
9. Ignore them, keep select "continue" until you get back to the Ubuntu installation menu
10. Jump to "Install Grub ...."
11. Once it is finished, just restart your computer

Good luck!.


hello there!
at first time my GRUB works fine...but when i get back to Windows XP and use partitionmagic to do some partioning on some unused space (not the linux drive or swap), then my GRUB failed to work...=( at start i get an ERROR 22.

@vnbuddy2002: i think i'll better follow your instructions as the only LIVE cd i've got is the one that comes with OpenCD. also, i'm not yet really familiar with commandlines thingy in Linux.

just like to ask what do you mean by number 4 in your instructions above?
do you mean the error in number 8 is like 'cannot install because no root directory is found'?

thanks for any help. cheers!

---

