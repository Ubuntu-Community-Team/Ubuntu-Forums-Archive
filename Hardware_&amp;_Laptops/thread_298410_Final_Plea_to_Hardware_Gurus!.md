---
title: "Final Plea to Hardware Gurus!"
date: 2006-11-12
forum: Hardware &amp; Laptops
---

### Post by lovloss on 2006-11-12
I have some very annoying problems involving my USBHDD and a new Motherboard. Linux is installed on the USB. I really don't know what else to do or where else to turn, so Im going to list my issues. Thank you for looking :KS 
 
The problems started when i changed motherboards. The new motherhood is newer, better, faster and uses the same Bios, WinFast. I dont see why this is happening :/

I have two issues:

1. Start up Issues
 I cant log into Windows XP on my internal HD. From the computer's Bios it refuses to locate a C:\ like it used to, and grub simply sits there and says its loading when I select WINXP. I also have to change the devices now in Grub. It keeps wanting to boot Linux from (2,0) when now its (0,0), and Im not actually entirely sure what the coordinates are for the internal, but it wants to boot that from (1,0), which fails. 

2. The USB isnt Mounting!
 When I log into windows, linux begins to run and everything from the USB HDD, then suddenly it says that the drive isnt accepting a number of addresses, and it freezes. I turn off the drive and turn it back on, and then it resumes. I don't get it.


Can anyone help me at all? :-k

---

### Post by deepwave on 2006-11-12
Well not sure exactly how to help.  But if you want to find out the location of the drives just look at the device names.

In Grub, hd?? (IDE) and sd?? (SCSI) drives map to hd(?,?)
Now hda would be the first drive or hd(0,?) in grub.  Note it starts with zero and not 1.
Further hda2 would be the second partition on the first drive, or in GRUB-speak hd(0,1)
USB devices get labeled (sd*) like SCSI devices in /dev.

Back to your question, is one drive is only Windows and the other Linux?  Or both partitioned?  Also which hard drive is configured to boot first?

If you can tell the boot order of your drives, and the partitioning that would be great.  You can use parted or fdisk under Linux for finding your partitions.

---

### Post by lovloss on 2006-11-12
The order is external, then internal. The computer is set to check CDs, then boot from hard disks in that order. The external contains the only linux partitions, while the internal is all windows. The grub exists on the external so wlel that I can boot my ubuntu up on other people's computers simply by reconfiguring the x-server.
 But the internal cannot boot alone because I never restored the mbr. It is meant to be loaded from the grub console. Im curious now, however - your device explanation interests me. Could it be that the windows disk i need to boot from is hd(0,1)? I havent tried that.

 But why do i need to change the device number every time i use grub? any way to save changes?

---

### Post by deepwave on 2006-11-12
You can edit /boot/grub/menu.lst for permanent changes.  Interesting setup though, never would of though of demonstrating Linux that way.

---

### Post by lovloss on 2006-11-12
Well its gotta wait till i get home. In the meantime, any idea why i have to flick the external off and on? A little odd, that. Something tells me its looking for the wrong device. :/

---

### Post by lovloss on 2006-11-13
Alright I have new data. I really appreciate help guys, even if I am making a nuisance of myself.

The drive names on my internals appear to be "hda1" and "hdb1". The external is referred to only as "sda" and there are 3 partitions inside that. Sda is considered to be my first device, which may be a cause of other problems because it used to be my very last device. Anyway, the boot partition for Linux is, naturally, sd0,0. That makes sense to me.

However, I attempted to boot from hd0,1, where Windows should be. It still didnt find the device. I used a grub boot disk to restore the mbr and got into windows, but before the splash screen I got our good friend, the blue screen of death, telling me to chkdsk /f, which I did to no avail. I dont think the BIOS thinks of the internal as a c:/ anymore and that's confusing Windows. I used to put my boot order: "boot from cd, c:/, d:/" and now its just "boot from hard disk"

I really wish this made more sense.

I may re-install ubuntu so that the grub will work right, and to fix a number of other kinks as well... but Windows XP is a retard when you install it (and remains so). I wouldnt even bother if I could emulate all my games, but some just wont do it. 

(BTW, I should be able to just reformat the partition of Linux itself and reinstall there iwthout touching the data partition, right? ) :)

---

### Post by deepwave on 2006-11-13
> **lovloss said:**
> 
(BTW, I should be able to just reformat the partition of Linux itself and reinstall there iwthout touching the data partition, right? ) :)

Absolutely.  Keeping separate data partitions is the way to go.  Glad to hear things are starting to work out.

---

