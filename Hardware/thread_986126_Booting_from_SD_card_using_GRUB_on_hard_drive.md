---
title: "Booting from SD card using GRUB on hard drive"
date: 2008-11-18
forum: Hardware
---

### Post by argie on 2008-11-18
I have a Dell XPS M1330 which has an SD card which is seen by Ubuntu properly. All is well. Except for one thing. This laptop cannot boot off the SD card. What I plan to do to work around this is:

1. Boot a kernel with SD card drivers from the hard drive.
2. Use that to boot up from the card reader.

Is this possible? Can anyone who knows assist?

---

### Post by freqhack on 2008-12-06
Have you had any luck with this yet? I'm trying to figure out how to do the same thing.

---

### Post by caljohnsmith on 2008-12-06
> **freqhack said:**
> Have you had any luck with this yet? I'm trying to figure out how to do the same thing.
If you want, I can help you do that, but how about first posting:
```
sudo fdisk -lu
```
And please identify all your partitions, including the partition on the HDD where you plan on putting the boot files.

---

### Post by argie on 2008-12-11
Never did get this working. But would be happy to try now.

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      160649       80293+  de  Dell Utility
/dev/sda2          161792    21133311    10485760    7  HPFS/NTFS
/dev/sda3        21141540   240155684   109507072+   7  HPFS/NTFS
/dev/sda4   *   240155685   312576704    36210510    f  W95 Ext'd (LBA)
/dev/sda5       240155748   273040739    16442496   83  Linux
/dev/sda6       273040803   311259374    19109286   83  Linux
/dev/sda7       311259438   312576704      658633+  82  Linux swap / Solaris

```

From the top that is:
Dell Utility Partition
Dell Restore Partition
C: on Vista
Extended Partition (Booted with MediaDirect)
/ on Ubuntu (grub files rest in /boot/ here)
/home on Ubuntu
swap

I have it currently set up so that hitting the MediaDirect button boots GRUB and lists the Ubuntu options.

Is it possible to add this feature with losing any functionality?

---

### Post by caljohnsmith on 2008-12-11
Do you know if your BIOS recognizes your SD card on start up? How about first plugging in your SD card, reboot, and when you get the Grub menu on start up, press "c" to go to the command line, and do:
```
grub> geometry (hd0)
grub> geometry (hd1)
```
Each of those commands will report the size and partitions of BIOS drives (hd0) and (hd1). Most likely (hd0) will be your internal sda drive. So use the output of the above commands to deduce if either (hd0) or (hd1) is your SD card, and let me know, because that might greatly simplify fixing your SD card booting problem.

---

### Post by argie on 2008-12-15
Hi, I'm sorry I took so long to reply. 

The first one lists my partitions on the drive inside. The second one gives me an error saying that the device couldn't be found.

---

### Post by sdennie on 2008-12-15
If you had a separate /boot partition on your hard drive, you could boot the kernel from the hard drive but mount the root partition from the SD drive.  I believe that as long as your initrd has the drivers for the SD card reader, this should be fairly straight forward (in fact, it can be done with the normal Ubuntu installer even).

---

### Post by caljohnsmith on 2008-12-15
> **argie said:**
> Hi, I'm sorry I took so long to reply. 

The first one lists my partitions on the drive inside. The second one gives me an error saying that the device couldn't be found.
That means then that your SD card is not recognized on start up, so I don't think there is much hope of directly booting it. You can workaround it by doing as Vor suggests and make a /boot partition on your internal drive. Or if you don't want to do that, and if you can boot from a CD, you could instead make a boot CD for the SD card. Or maybe if you are lucky there is a BIOS upgrade available for your computer that would make it possible to access the SD card on start up. Good luck and let us know if you would like more help.

---

### Post by argie on 2008-12-15
Thanks.

Is it essential to have a /boot partition for that to work? I wouldn't mind trying that. Would that allow me to use different distributions with different cards?

---

### Post by caljohnsmith on 2008-12-15
> **argie said:**
> Thanks.

Is it essential to have a /boot partition for that to work? I wouldn't mind trying that. Would that allow me to use different distributions with different cards?
In theory that should work fine; I know others who have set up separate /boot partitions in order to boot USB drives for example that can't be booted by BIOS, but since I've not tried it with an SD card myself, I can't personally vouch for whether it would work or not. When you boot the Live CD, does it recognize your SD card without any extra effort on your part? If so, I think you have a good chance of being successful with the /boot partition method to boot the SD card. Good luck and let us know how it goes.

---

### Post by argie on 2008-12-15
Interestingly enough, my laptop's BIOS works just fine for booting off a USB drive, but the manufacturer says that they have no plans to update it to allow booting off the SD card reader. Unfortunate.

From the LiveCD, the SD card is recognized right off.

Hmm, I'll try that later then. Exams this week.

---

### Post by specialcharacter on 2008-12-15
Wow, snap. I have exact same laptop and have been trying to boot from sd card so I can get it booting quicker. 

Does anyone know if using vor's method of using a /boot partition on a hard drive looses the benefit of speeding up boot time?

---

### Post by sdennie on 2008-12-15
Only 2 or 3 files totaling about 10M worth of data need to be read off the hard drive before the boot process would pass control onto the SD card so, I don't think you'll notice the difference between this hybrid setup and a pure SD solution.

---

### Post by specialcharacter on 2008-12-15
Bah. I tried your suggestion Vor, but it cannot find the volume. I couldn't see the drive in /dev/disk anywhere so I assume it isn't loaded until later.

Is there a way to get round this, or find more information about the problem?

---

### Post by sdennie on 2008-12-15
> **specialcharacter said:**
> Bah. I tried your suggestion Vor, but it cannot find the volume. I couldn't see the drive in /dev/disk anywhere so I assume it isn't loaded until later.

Is there a way to get round this, or find more information about the problem?

My guess is the kernel modules for the SD reader aren't in the initrd image.  I don't have an SD card with me at the moment so can't test this but, edit the file /etc/initramfs-tools/modules and add the following lines to it:

```

mmc_block
mmc_core
sdhci

```

Make sure you have a backup kernel before doing the following (it should be safe but, it's best to have a backup kernel if this goes wrong):

```

sudo update-initramfs -u

```

Reboot and see if you can use the SD as the root partition now.

---

### Post by specialcharacter on 2008-12-16
Phew, got it! Cheers Vor, I wouldn't have had a chance without your post!

I had to add 2 other modules for it to work, ricoh_mmc and sdhci_pci. I'm not sure if ricoh_mmc is needed, as I added it before trying sdhci_pci.

```

mmc_block
mmc_core
sdhci
ricoh_mmc
sdhci_pci

```

Now just need to download the normal DamnSmallLinux instead of the embedded version. I'll be back to let you know about improved boot time!

---

### Post by anfy on 2008-12-28
I'm trying to do something similar on my aspire one... how do you  point the /boot folder to the SD card?  Can I do the same thing, but put the /boot folder in an existing Ubuntu partition? (in another folder, like /boot2 or something)?

---

### Post by PavelMan on 2009-04-14
Guys! I have an exact same setup -- XPS1330 with build-in card reader.

Just booting from a flash drive and trying to add the card's UUID (as it shows up when already booted into Linux) does not help. This device is not recognized at that stage yet.

So yes, I need to move my windows partition on a hard drive a bit and make some room for at least a /boot partition there. 

But I do not have a complete understanding what else should be there. Instructions above mention editing something in /etc -- does it have to be on that partition as well?

Those who managed to pull this off -- please, help me to create a little guide, "how-to" on this topic? It would be super cool to be able to do such a thing, since may people hate a usb dongle sticking out...

Please, help.

---

### Post by parti on 2010-12-03
Hello.
I were able to install Ubuntu on a diskless (broken ATA bus) netbook using the information in the posts here.
To sum things up, this is what I did:
1. Install Ubuntu using:
/ on sdcard
/boot on USB Memory
Installing GRUB on the USB memory.
2. Reboot into installer cd, "try ubuntu".
3. Mounting sd card as /mnt
4. Mounting usb memory as /mnt/boot
5. chrooting into /mnt
6. editing /etc/initramfs-tools/modules, adding the modules (including tifm_sd)
7. update-initramfs -u
8. Reboot!

Not too specific on commands and such. Ill edit it to provide the commands that I used if someone asks.
Thanks for the thread!

---

### Post by JigglyWiggly_ on 2011-05-05
I will bump this, BECAUSE ALL OF YOU DESERVE AN AWARD. Got it working :popcorn:

---

### Post by Sandbomb on 2012-04-29
Sorry to be such a noob, but this still is not making sense to me. it looks like it is saying to add the modules to the SD card not the usb. So how will it be able to load the modules from a sd card that it cant see untill the modules are loaded? My laptop does not support booting from the built in SD slot. Ubuntu 12.04 has no problen installing to SD just cant boot to it because bios does not support it. So what I want to do is use a usb stick as a sort of boot key, containing whatever drivers are needed to get the SD mounted and then boot to it. I tried a tutorial here [http://a110wiki.de/wiki/Booting_from_SD](http://a110wiki.de/wiki/Booting_from_SD), but this is specific to the a110 and grub, not grub2, so I wasn't sure how exactly to change the script, or edit the grub.conf file. It seems like what your doing here is the same thing without using kexec. I'm not seeing how this can work though,  Seems like I need the modules and grub2 on the usb which will load whatever it needs to get the SD going and then boot from it. If anyone knows how to do this, maybe you could post a step by step tutorial that is a little easier to understand for all us idiots that dont want the dongle hanging off the side of our laptops. Any Help would be much appreciated. Thanks.

---

### Post by gecco on 2012-05-07
@Sandbomb:  Yes, me too. I've also been confused by some parts of the previous descriptions. So I read the [GRUB manual]("http://www.gnu.org/software/grub/manual/grub.html")  to better understand the content of the GRUB config file  "/boot/grub/grub.cfg". Adding this to that what I've learned in this  threat and earlier lead me to success.

Here the result:


**The Problem**

PC does not accept a SD-card as boot device. But I want to have my alternative OS being located on a SD-card partition.


**Assumptions**

[LIST]
[*]The PC has a bootable device
I  have installed a previous version of Ubuntu on it. Ubuntu is not  necessary, but like this I can refer on it and only you have to deal  with your variations.
[*]GRUB 2 is propperly installed on that bootable device (that's *_not_* the GRUB of the SD-card installation)
[*]The PC cannot boot using the SD-card as boot device (the initial problem)
[*]You already have installed your new Linux with GRUB 2 on your SD-card (and are frustrated because it does not boot...)
[/LIST]

**Notes**

Only  you yourself are responsible for any lost data or any other  inconveniances that might result from your actions by following these  words. So don't forget to make the necessary backups of your data and  update your emergency disks for the worst case.
Please read and understand the whole thing, before you start!
Be  aware, that this is only a step-by-step guide for a proof of concept.  The result of this solution is not suitable for production use, as it  requires manual updates after each kernel-update the Linux on  the SD-card.



**Method to solve the problem**

[LIST=1]
[*]We extend the "initrd" to support the sd-card hardware.
[*]Then we place the files, required to boot Linux, on a device that is accessable for GRUB.
[*]Finally we patch the configuration of the GRUB 2 residing on the bootable device to have the correct menu entry for our OS.
[/LIST]
*For  those guys, that are proficient in configuring GRUB and Linux in the  terminal, just jump to the bottom of the guide (end of ****III.**) to see the sample and the  pointing out of the essential trick.*




**Step by Step**


***I.   Add the modules for SD-card support to the "initrd"-file of your SD-card Linux.***
[INDENT]As the SD-card linux does not boot, we have to do that with an other  Linux and use the "chroot" feature.

[LIST=1]
[*]Boot to a Linux
[*]Insert the SD-card with the not-bootable Linux
[*]Mount the SD-card partition with the Linux, if the automounter does not do the job.
I assume the mount at "/media/sdcard". Substitute this by your real mount path.
[*]Open a terminal and issue the following commands. They will prepare and start the chroot environment.
```
$ cd /media/sdcard
$ sudo mount -o bind /dev ./dev
$ sudo mount -o bind /proc ./proc
$ sudo mount -o bind /sys ./sys
$ sudo mount -o bind /tmp ./tmp
$ sudo chroot .
# 
```Now we are in the environment of the SD-card Linux as user root.
[*]Add the required modules to support the SD-card at the start of Linux (after GRUB 2 passes over the control)
Edit the file ```
/etc/initramfs-tools/modules
```by adding these module names:
(On other hardware/Linux the required modules might differ For my system with Ubuntu 12.04 these modules have done the job.)
```
mmc_block
sdmod
```
[*]Back on the command line execute the following command to repackage the "initrd"-file:
```
# update-initramfs -u
```
[*]To leave the "chroot" environment execute
```
# exit
```
[/LIST]
[/INDENT]***II.   Copy the Linux boot files to the bootable device***[INDENT]CD to the root directory of your bootable device.
In case of the internal hdd its "/", for an USB-Stick something like "/media/usb"
Typically you will find there the "boot" directory of the GRUB installed on your bootable device.
```
$ sudo mkdir boot.guest
$ ls -l /boot                                 # to find out the real kernel version
$ sudo cp /boot/*3.2.0-23* boot.guest/        # substitute the kernel version by yours.
```
**NOTE:**  After a kernel update of the SD-card's Linux this step has to be repeated.

[/INDENT]***III.   Add the menu entries to the GRUB 2 configuration on the bootable device***[INDENT]Depending  on your Linux distribution, there might be some differences of the GRUB  integration in the distribution. As the GRUB on the bootable device is  the code executing version, it is preferable to let that GRUB generate  some menu entries, but not just copy/paste the relevant entries from the  SD-card's GRUB:
[/INDENT]
[LIST=1]
[*]
[LIST=1]
[*]If not already up 'n running, start the OS that hosts and manages the GRUB 2 installation of the bootable device.
[*]Insert your SD-card with the not-booting Linux installation.
[*]Execute:
```
$ sudo update-grub
```This should generate probably 2 additional entries for your not booting SD-card installation. *These entries will not work,* but they are the base for our further patch.
[*]Might be that errors occure (something like "no device"). Then the script could not find any GRUB device entry for  your SD-card in the file ```
/boot/grub/device.map
```
[LIST]
[*]Check the device filename of your SD-card (This example: "/dev/sdc")
[*]Edit (with root priviledges) "device.map" manually and add a new entry for your SD-card. Example:
[/LIST]
```
(hd0) /dev/sda
(hd1) /dev/sdb
**(hd2) /dev/sdc**
```Then repeat step 3.
[/LIST]
 
[/LIST]
[INDENT]Typically the updated GRUB 2 configuration is stored in ```
/boot/grub/grub.cfg
```
[LIST]
[*]Open it for later copy/paste (read-only is enough)
[/LIST]
We  will add a custom script to provide our custom entries directly after  our linux distribution on the bootable device (Details her fit to  Ubuntu). The position is defined by the number the script-name will  start.

[LIST=1]
[*]```
$ cd /etc/grub.d
$ sudo cp 40_custom 15_custom_sdcard
```
[*]Open with root priviledges the new file "15_custom_sdcard" for further editing.
[*]Change to the previously opened "grub.cfg".
Search and copy the two menu entries for the SD-card Linux boot.
[*]Paste the copied text to the end of the "15_custom_sdcard".
[*]Find  the correct GRUB device name "(hd**?**,**?**)" for your boot device. You will  find it in the the already opened "grub.cfg" at the menu entry for the  Linux on your boot device.
Patch the following line in both menu entries of "15_custom_sdcard" to the values you've found.```
set root=(hd**?**,**?**)
```
[*]Now  we patch the "search" line of both menu entries. Typically a UUID is  set as search string. Substitute the given UUID (very log hex-number) by  the UUID of your boot device.
Besides many other ways you typically  can find it at the already opened "grub.cfg" within the menu entry for  your Linux on the boot device.
[*]As the next we correct the path  to kernel and initrd files. Currently they are stated to be in "/boot".  This we correct to the new path ```
/boot.guest/.....
```
[*]Optionally you can change the first line of the menu entries to get  a more conveniant description. (Watch out to edit only within the quotation marks.)
[*]Save and close "15_custom_sdcard".
Close "grub.cfg".
[*]Execute ```
$ sudo update-grub
```
[*]Everything done. - Verify the content of your newly generated "grub.cfg" for the presence of your new menu entries.
[/LIST]

**NOTE:**   After a kernel-update of the SD-card Linux, the statements "linux" and "initrd" have to be updated to the new filenames.




To  get a visual imagination of how the "15_custom_sdcard" should look like,  here an example. Note: The detailed values will not fit to your system.


```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.



menuentry 'Ubuntu 12.04 LTS (sd-card)' --class ubuntu --class gnu-linux --class gnu --class os {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set=root 12345678-222d-333e-444f-123456789abc
    linux    /boot.guest/vmlinuz-3.2.0-24-generic root=UUID=1abcdef1-a1a1-b2b2-c3c3-1abcdef12345 ro   quiet splash $vt_handoff
    initrd    /boot.guest/initrd.img-3.2.0-24-generic
}
menuentry 'Ubuntu 12.04 LTS (sd-card) (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set=root 12345678-222d-333e-444f-123456789abc
    echo    'Loading Linux 3.2.0-24-generic …'
    linux    /boot.guest/vmlinuz-3.2.0-24-generic root=UUID=1abcdef1-a1a1-b2b2-c3c3-1abcdef12345 ro recovery nomodeset 
    echo    'Loading initial ramdisk …'
    initrd    /boot.guest/initrd.img-3.2.0-24-generic
}
```To point out the essential trick:

[LIST]
[*]The "set root" statment points to the bootable disk, where the "outsourced" kernel and initrd reside.
[*]Also the "search" statment points to that bootable disk.
[*]But the "linux" statement has to point to the SD-card !!!
[/LIST]


[/INDENT]***IV.   Reboot your system and in the GRUB menu choose the SD-card Linux***


***V.    What's next to do?***

[LIST]
[*]To  get all this to production quality, some should extend the GRUB script  "15_custom_sdcard" to make an autodetect for the newest filenames of  linux and initrd in "/boot.guest/". Then replacing these names with  apropriate variables in the script will make editing obsolete.
(Should be a  5-minute job for a GRUB experienced coder.)
[*]Write  a script that automatically will copy new versions of the kernel files  to the outsourced directory. (dito effort as above.)
[/LIST]
***VI.   Alternative solution:***[INDENT]Surely it is possible to install GRUB 2 of the SD-card Linux to the bootable device directly by something like

```
$ sudo grub-install --boot-directory=/mnt/boot /dev/sdb
```A manual copy action after a kernel update would be obsolete.



This alternative might be especially usefull if "/dev/sdb" represents your bootable USB-device.
For  "/dev/sdb" being your internal harddrive with your primary OS, you  should first think about the consequences concerning your primary OS.


Mentioning  my personal taste, I prefer to have the complete OS on the SD-card and  make a copy to the outsourced boot folder. So the grade of portability  between other computers is higher. As a consequence, I would also keep  an up-to-date copy of the file "15_custom_sdcard" on the SD-card.

[/INDENT]So have some fun!
gecco

---

### Post by forlackofabettername on 2012-05-08
Thank you so much, gecco. I've just been looking for something like this.

---

