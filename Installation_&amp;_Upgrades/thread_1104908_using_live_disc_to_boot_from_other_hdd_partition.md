---
title: "using live disc to boot from other hdd partition"
date: 2009-03-24
forum: Installation &amp; Upgrades
---

### Post by michael.f on 2009-03-24
Hi,

I'm new(ish) to ubuntu and linux as a whole, and I was wondering if it would be possible to use a Ubuntu 7.10 Live disc to force my laptop to boot from a specific partition.. (this partition is a Windows recovery partition, yes I know you probably think its EViiiiiiiL lol)

It has the option to "boot from 1st harddrive" (or something along those lines) in its main menu.. but only from the first partition.


I am very unfamiliar with any command lines, etc.. but any help will be greatly appreciated..

Thank you for your time :)

---

### Post by MaindotC on 2009-03-24
You need to install grub (or any other bootloader) and create an entry to tell grub where to find the windows partition.  Do you only have a windows recovery partition on the drive?

---

### Post by michael.f on 2009-03-24
No, I have both a Windows partition I wish to rescue plus the recovery partition, leaving no space to install grub. Hence my problem. It is also a laptop so it isn't going to be very easy to use another hdd as well.

---

### Post by MaindotC on 2009-03-24
No need for another hdd.  The live cd has a tool that will resize the windows partition and then you can install grub.  I think it only requires 8 MB and there should be a master boot record (MBR) on your drive already.  Are you sure you can't tell the bios to boot into your recovery partition or press like f1 or f12 or something like that at start to start the recovery partition?

---

### Post by michael.f on 2009-03-24
I tried looking in the BIOS for that.. but it sadly is lacking in that feature.. I'm supposed to be able to press F11 after POST to boot into that partition without even using the BIOS setup, but it doesn't work either..

How stable is the NTFS partition resizing? I **really** don't want to lose any data.

It may be worth noting that I have USB boot support. Could I install grub onto a flash drive, and redirect it to boot from a hdd?

---

### Post by MaindotC on 2009-03-24
Resizing the partition won't harm your data.  You know if this is windows with which you are concerned, you could boot from a DOS floppy and type "fixmbr" and that will restore the MBR on your partition.  I doubt you have a floppy drive or floppy disks on the laptop so can you boot into the recovery console?

---

### Post by lisati on 2009-03-24
I found [this]("http://sourceforge.net/projects/btmgr/") recently when trying to figure out how to boot an older computer from CD, don't know how much it will help.

---

### Post by michael.f on 2009-03-24
Oh okay, that's good to hear about the resizing.

No, sadly I don't have a floppy drive, and I doubt that would work anyway (It's Vista not XP)

Anyway, is it possible to install grub on a flash drive as I said above? Or is the resizing my only option?

---

### Post by MaindotC on 2009-03-24
Forget about grub - unless you want to install a linux partition I don't see why grub is even an option.  Use the following directions using the Win XP cd:
> 
   1. Restart your computer with the Windows XP Setup disk in the CDROM drive.
   2. If you are prompted to press a key to start the computer from CDROM, do so quickly. Otherwise it may try to boot from the hard drive.
   3. After a few minutes, you'll see a prompt to press the R key to start the Recovery Console.
   4. When Recovery Console starts, it will prompt you to enter a number corresponding to the Windows XP installation that you need to repair. In most cases, you'll enter "1" (which will be the only choice). If you press ENTER without typing a number, Recovery Console will quit and restart your computer.
   5. Enter your Administrator password. If you don't enter the correct password, you cannot continue.
   6. At the Recovery Console command prompt, type fixmbr and then verify that you want to proceed. 


---

### Post by michael.f on 2009-03-24
But I don't have the disc, HP thought it was a great idea to give me a partition that is basically that disc instead. :)

---

### Post by MaindotC on 2009-03-24
Type in google "fixmbr usb" and use one of those options.

---

### Post by lisati on 2009-03-24
A couple more thoughts:
I have a COMPAQ desktop (made by HP): When I installed Ubuntu on it today (trying to get as much of my gear as possible loaded with *nix), the installer was able to detect both the recovery partition and the XP partition and placed entries for both in the menu.lst file
I also saw something on the HP website recently about being able to order recovery disks, but they're not made available to everybody.

---

### Post by michael.f on 2009-03-24
The (main) issue is not with the MBR. I **need** to use the recovery partition to solve the problem.

---

### Post by MaindotC on 2009-03-24
You can't get to the recovery partition until you fix the MBR.

---

### Post by michael.f on 2009-03-24
But there is nothing wrong with it?

---

### Post by MaindotC on 2009-03-24
There is if it's not finding your XP partition.

---

### Post by michael.f on 2009-03-24
Oh, sorry if I didn't make it clear.

It can find my Vista partition (not XP), and it begins to boot from it. Vista fails while loading drivers and goes into an infinite loop (including in safe mode)..

The BIOS is supposed to let me boot into my recovery partition when I press F11 after POST. This doesn't work (for some seemingly unrelated reason).

Both partitions are fine from a file system point of view, I can see them and mount them from within Ubuntu.

---

### Post by MaindotC on 2009-03-24
If you can boot into safe mode in Vista then just type "fixmbr" and it should reset the MBR so it finds the recovery partition.

---

### Post by michael.f on 2009-03-24
I can't boot into safe mode though, and it is not an issue with the MBR because Ubuntu can see the recovery partition fine.

---

### Post by MaindotC on 2009-03-24
Yes, Ubuntu can SEE it, but you can't boot into it until the MBR is fixed and it knows where the recovery partition is so you can boot into it.

---

### Post by michael.f on 2009-03-24
oooooh.. wait maybe this might help?

Cannot mount volume.

Unable to mount the volume 'HP_RECOVERY'.

Details

$LogFile indicates unclean shutdown (0,0) Failed to mount '/dev/sda2': Operation not supported Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by clicking on the 'Safely Remove Hardware' icon in the Windows taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for your own responsibility. For example type on the command line: mount -t ntfs-3g /dev/sda2 /media/HP_RECOVERY -o force
Or add the option to the relevant row in the /etc/fstab file:
dev/sda2 /media/HP_RECOVERY ntfs-3g defaults,force 0 0

---

### Post by MaindotC on 2009-03-24
I think you better contact your customer support.

---

### Post by michael.f on 2009-03-24
Oh okay.

Thanks for your time anyway.. I really appreciated it. :D

---

### Post by aikiwolfie on 2009-03-24
You can force mount the NTFS partitions. You can also use any Windows XP CD to fix this problem. You can even use the Windows 7 beta disc to fix this problem.

If you get hold of a Windows XP CD, boot from that and run chkdsk once you get to the recovery console.

If you want to use Ubuntu to force mount the partitions, ***which isn't entirely risk free***, you need to run the following command. Substitute **sda1** for the location of your Windows partition. The "**sda**" points to the first physical hard drive and the "**1**" is the first partition.

If you have an old IDE hard drive in your laptop swap **sda1** for **hda1**.

```
sudo mkdir /media/windows
sudo mount -t ntfs-3g /dev/**sda1** /media/windows -o force
```

If you reboot into Windows it should now work.

---

### Post by michael.f on 2009-03-24
I tried the force mounting, and now I can mount both partitions in Ubuntu and access the files, although I still have the other problems with booting from them.

After a couple of hours of googling and experimenting I've managed to get GRUB to work on one of my USB flash drives, although I haven't the faintest idea how to use it.

Could anyone point me to the GRUB command I should use to chainload from GRUB to the 1st hard drive, 2nd partition?

---

### Post by MaindotC on 2009-03-24
From [http://www.linuxselfhelp.com/gnu/grub/html_chapter/grub_4.html](http://www.linuxselfhelp.com/gnu/grub/html_chapter/grub_4.html)
> 
If you want to boot an unsupported operating system (e.g. Windows 95), chain-load a boot loader for the operating system. Normally, the boot loader is embedded in the boot sector of the partition on which the operating system is installed.

   1. Set GRUB's root device to the partition by the command @command{rootnoverify} (see section rootnoverify):

      grub> rootnoverify (hd0,0)

   2. Set the active flag in the partition by the command @command{makeactive}(5) (see section makeactive):

      grub> makeactive

   3. Load the boot loader by the command @command{chainloader} (see section chainloader):

      grub> chainloader +1

      `+1' indicates that GRUB should read one sector from the start of the partition. The complete description about this syntax can be found in section How to specify block lists.
   4. Run the command @command{boot} (see section boot). 

However, DOS and Windows have some deficiencies, so you might have to use more complicated instructions. See section DOS/Windows, for more information.


---

### Post by aikiwolfie on 2009-03-25
This is the entry from my menu.lst file for Windows 7 beta. All the important bits are the same for XP or 95 etc. Hope it helps.

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows 7 Ultimate Beta 1
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

How big is your flash drive? You can put a full Ubuntu installation on to an 8GB drive and the live CD version will fit into smaller drives. If you get an upto date version there's even a tool that helps you make a bootable USB stick.

---

