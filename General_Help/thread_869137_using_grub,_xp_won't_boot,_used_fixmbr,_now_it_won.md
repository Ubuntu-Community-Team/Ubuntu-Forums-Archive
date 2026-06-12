---
title: "using grub, xp won't boot, used fixmbr, now it won't boot anything!!!"
date: 2008-07-24
forum: General Help
---

### Post by Joseph Banea on 2008-07-24
Hello, this is my first time on this forum. I am having a major problem with my computer not booting. I am new to linux (actually using Puppy, but needed additional help), as you can see. To help you out, what I've done is create new partitions, installed it, and added grub. However, when grub appears and I select xp, it doesn't boot. Rather, it appears (from what I remember) it did not find xp and came back to grub. Puppy worked, so I used that to find help.
After looking for help, I saw several sites saying fixmbr will help me boot xp no matter what, b/c I didn't think it was worth using puppy if I couldn't use xp. I used the recovery system in my xp setup disc to use "fixmbr" and exited. Now, it won't boot anything, saying fatal errors.
I apologize for my lack of knowledge, but I sure hope I can boot back xp again. (my brother will have a fit when he sees this.) Thank you for your help!

---John

---

### Post by Archimedes0212 on 2008-07-24
you need to edit the grub menu file.  The line that is "pointing" to your windows partition is incorrect.  It may be pointing to the wrong partition or something along those lines.

It depends on the order that you have your drive partitioned.

EX:  My partiions go Windows, Swap space, Ubuntu

in my grub:
   Windows: 0 
   Ubuntu:  2

i don't remember the whole line off the top of my head, im not at my system right now.  but the basic understanding is there.

your windows partition in the grub menu is probably pointint to the swap space or to empty space.  Once you find out which order your computer is in, modify the line for windows to point to the correct partition and it should work fine.

Hope this helps.  If not, private message me and I'll give you a more detailed snippet of the grub menu when I'm back on my linux system.

---

### Post by Joseph Banea on 2008-07-24
I would do this, but what I've done has grub disappeared. fixmbr has gotten rid of grub, now all I get is several errors not accessing the drive. I'll try again.

---

### Post by Potatoj316 on 2008-07-24
You could reinstall grub (that is my sugestion) search the forum or google for how to do this with a live CD

---

### Post by WRDN on 2008-07-24
Boot into the XP disk again, and run 2 commands:

```

fixmbr
fixboot

```

You could also use [Super Grub Disk]("http://www.supergrubdisk.org/") to restore the GRUB bootloader.

Alternatively, boot from the LiveCD and reinstall GRUB using [this]("http://ubuntuforums.org/showthread.php?t=224351") guide. If it is reinstalled, it should automatically add the ubuntu and windows entries, so you do not need to manually edit the menu.lst file (/boot/grub/menu.lst)

---

### Post by Joseph Banea on 2008-07-24
Ok, thank you for your help right now. I've got grub back on, exactly where things gone haywire. I still cannot boot xp right now, but it shows puppy linux (which I've installed). Any ideas on what I may need to fix? I will try fixboot in a few minutes, but what does it do? I don't want to fall into a deeper hole with my computer.

---John

---

### Post by caljohnsmith on 2008-07-24
Don't use "fixboot" if you have Grub working, because "fixmbr" and "fixboot" will revert you back to a Windows only boot. :) Are you able to boot into puppy linux OK now? You didn't say specifically.

If you can get into Puppy Linux, how about posting the output of "sudo fdisk -l"? Then we can help you set up your grub's menu.lst so you can boot Windows too.

---

### Post by Joseph Banea on 2008-07-24
Actually, I've used fixboot after fixmbr, yet I can't boot into xp after resetting. Puppy Linux did work properly at grub before using the recovery console. I feel like grub can be installed again. I will do this, then post the output of "sudo fdisk -|". What does this do? I am using the live-cd currently. WIll that work, or do I need to use the installed linux thru grub instead? Thank you!

---John

---

### Post by caljohnsmith on 2008-07-24
Yes, I would definitely reinstall Grub so you can have both Puppy Linux and Windows. And yes, you can run "sudo fdisk -l" from your Live CD (please note -l is lowercase L); that will just give your HDD's partition table.

---

### Post by Joseph Banea on 2008-07-24
Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot     Start          End     Blocks    Id  System
/dev/hda1              1        28395  228082806     7  HPDS/NTFS
/dev/hda2          28396        28656    2096482+   83  Linux
/dev/hda3          28657        28819    1309297+   82  Linux swap/Solaris
/dev/hda4   *      28820        30401   12707415     b  W95 FAT32

The rest of the data seems to go to my usb drive that I used as a settings file for puppy. Will this help?

---John

---

### Post by Joseph Banea on 2008-07-24
ick, this time it'll be a screenshot.

---

### Post by Joseph Banea on 2008-07-24
here it is.

---

### Post by hal8000 on 2008-07-24
From your fdisk -l (which you posted from Puppy hda2 is your linux partition and hda3 your swap file)

Boot with the Hardy Live Cd
type sudo grub

gives you a grub shell
grub>

type the following

grub> find /boot/grub/stage1

this will return thr grub partition (almost certain to be hd0,1)

then tell grub where your root partition is

grub> root (hd0,1)

then install grub into the mbr

grub> setup (hd0)

quit.
Reboot and Ubuntu should be back. You may then need to edit menu.lst to restore XP, (or it may find XP and just work).

Post back and let everyone know please, hope that helps.

---

### Post by Joseph Banea on 2008-07-24
I hope this helps. I can't use Ubuntu b/c it keeps going into Busybox. That's why I opted for Puppy. I posted here b/c there should be similar problems like mine, I hope.

This is my post from the Puppy forums:

Thank you for the help.

My computer:
AMD Athlon XP 1600+
250 GB IDE HD
1.25 GB DDR233 RAM
abit motherboard
cd/dvd drive
ATI 9450 (9550?) AGP Graphics Card (or along the lines of that)
Installed: Windows XP SP2, Puppy Linux, linux swap, fat32 partition for storage

I can't remember much else unless I use PCWizard2008 on my Windows XP setup. Which I can't...

I looked up GParted. No, the nfts partition which holds XP is not flagged as "boot". My fat32 partition (which I made according to the manual from the Puppy site) is flagged, instead. Is this a problem?

I have Windows XP installed previously. First, I've separated my existing partition so there are three extra: ext2 for puppy, linux swap, and fat32 for sharing files b/w puppy and xp. This is according to the manual in the main puppy site.
After, I installed puppy in the first partition (hda2). Then, following the example of the manual, I added GRUB in the same partition(hda2). It also mentioned of editing the menu.lst for GRUB. I did that. When I restarted, it gave me the options for GRUB. I could boot from Windows XP, and from Puppy frugal. However, it would not boot XP. Then, after initial looking of internet help. I used my setup CD to access the recovery console. As I did, it showed the directory E:\WINDOWS. Why E:, I'm not too sure. It should be C:. I then used fixmbr and fixboot. Fixboot told me that it would fix the D: drive. Unusual, too. After exiting, I resetted. Then, GRUB disappeared, and the computer asked to bood from a disk. I assume it could not read any of my partitions after fixmbr. The last thing I've done was to install GRUB again, the same way, through my live-cd.
There. I hope this is enough initial information to start with. Give me 5 minutes to write exactly what I see when booting GRUB. It appears the same as when I used GRUB the first time, with the same errors. Please respond to me what you interpret from this, I appreciate the help.

---John

---

### Post by rip_it on 2008-07-24
Hey if you have both your windows xp installation cd and Ubuntu installation cd, and you have no luck with what the above author says...
What I've found with mbr's is that, once you screw them up, its easier to just erase and create over.  Windows tends to be "pushy" with other operating systems, if you have both installation cds, I would highly recommend popping in the windows cd first, doing a full install, tell windows partition program to erase all existing partitions and create new, and then 
install ubuntu afterwords. The partition program in ubuntu works really good, i've had to do this in other linux operating systems such as Slackware for instance, its quicker in most cases.  I always run into problems installing linux before windows, and its always the boot loader
with the mbr that goes bad first.  Goodluck

ahh crap, wrote all that and forgot your using puppy.  Oh well, dam u lol
This could still help for puppy too I guess.

---

### Post by caljohnsmith on 2008-07-24
> **Joseph Banea said:**
> When I restarted, it gave me the options for GRUB. I could boot from Windows XP, and from Puppy frugal. However, it would not boot XP.
I don't think I understand--first you say it would boot Windows XP, and then you say it would not? Please clarify.

It would help us if you would at this point post the output of your /boot/grub/menu.lst from your Puppy partition. I'm not familiar with Puppy linux, so it might use grub.conf instead of menu.lst. Anyway, to do this, boot your Live CD, mount the Puppy partition, and output the menu.lst file:
```
sudo mount /dev/hda2 /mnt
cat /mnt/boot/grub/menu.lst

```
Then copy and paste your results here.

---

### Post by Joseph Banea on 2008-07-24
See, I'm not about to destroy my computer with a format; I still want XP to work. Doesn't matter if Linux works after, I'll use the live-cd. Right now, I need a solution that will allow me to boot into XP again.

---

### Post by Joseph Banea on 2008-07-24
What I meant to say was that GRUB lists the options for Windows and Linux. However, none will boot.

Ok, this is what I got:

GNU GRUB version 0.97 640k lower/ 1309632k upper memory

Windows (on /dev/sda1)
Linux (on /dev/hda2)
Windows (on /dev/hda4)
Install Grub floppy (on /dev/fd0)
Install Grub Linux partition (on /dev/hda2)

When I select the first windows:

Booting 'Windows (on /dev/sda1)'
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)
makeactive

Error 21: Selected disk does not exist
Press any key to continue...

When I select Linux:

Booting 'Linux (on /dev/hda2)'
root (hd0,1)
Filesystem type is ext2fs, partitiontype 0x83
Kernel /boot/vmlinuz root=dev/hda2 ro vga=normal

Error 15: File not found

When I select the second Windows:

Booting 'Windows (on /dev/hda4)'
map (hd0,0) (hd0,3)
map (hd0,3) (hd0,0)
rootnoverify (hd0,3)
makeactive
chainloader +1

This is not a bootable disk. Please insert a bootable floppy and press any key to try again...

DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER...

This message above appears just like the one when GRUB was gone after using fixmbr. 

Here is the GRUB file.

# GRUB configuration file '/boot/grub/menu.lst'.
# generated by 'grubconfig'.  Thu Jul 24 16:11:02 2008
#
# The backup copy of the MBR for drive '/dev/hda' is
# here '/boot/grub/mbr.hda.6008'.  You can restore it like this.
# dd if=/boot/grub/mbr.hda.6008 of=/dev/hda bs=512 count=1
#
# Start GRUB global section
#timeout 30
color light-gray/blue black/light-gray
# End GRUB global section
# Other bootable partition config begins
  title Windows (on /dev/sda1)
  map (hd0) (hd1)
  map (hd1) (hd0)
  rootnoverify (hd1,0)
  makeactive
  chainloader +1
# Other bootable partition config ends
# Linux bootable partition config begins
  title Linux (on /dev/hda2)
  root (hd0,1)
  kernel /boot/vmlinuz root=/dev/hda2 ro vga=normal
# Linux bootable partition config ends
# Other bootable partition config begins
  title Windows (on /dev/hda4)
  map (hd0,0) (hd0,3)
  map (hd0,3) (hd0,0)
  rootnoverify (hd0,3)
  makeactive
  chainloader +1
# Other bootable partition config ends
title Install GRUB to floppy disk (on /dev/fd0)
pause Insert a formatted floppy disk and press enter.
root (hd0,1)
setup (fd0)
pause Press enter to continue.
title Install GRUB to Linux partition (on /dev/hda2)
root (hd0,1)
setup (hd0,1)
pause Press enter to continue.
title -     For help press 'c', then type: 'help'
root (hd0)
title -     For usage examples, type: 'cat /boot/grub/usage.txt'
root (hd0)

---

### Post by caljohnsmith on 2008-07-24
John, previously you posted that:
> 
Device Boot Start End Blocks Id System
/dev/hda1 1 28395 228082806 7 HPDS/NTFS
/dev/hda2 28396 28656 2096482+ 83 Linux
/dev/hda3 28657 28819 1309297+ 82 Linux swap/Solaris
/dev/hda4 * 28820 30401 12707415 b W95 FAT32

which means everything is on one HDD, correct? In other words, you don't have two HDDs, true? If that is the case, then change your menu.lst Windows entry like the following:
```
title		Windows XP
root		(hd0,0)
makeactive
chainloader	+1
```
In other words, you shouldn't need to do any drive remapping. Let me know if that works, and then we can work on booting up puppy. (Yikes, that sounds rather sadistic, we're not trying to hurt any puppies here). :)

---

### Post by Joseph Banea on 2008-07-24
Lord Almighty, bless his soul. You are a brilliant man, John. I had a hunch there was something wrong with the menu.lst, but I figured my computer had got corrupt. Ok, after I copied and pasted your code into menu.lst, I rebooted into GRUB, and selected Windows XP. It worked! First, Windows XP booted. Then it went into chkdsk, then rebooted. After that, I entered GRUB again, and selected Windows XP. It booted, and finally I could see my desktop, in all its shining glory! Woo! Am I glad to see it! ..... not that Linux is any bad. So, I'm happy. I will work with Puppy to boot, but I may need a day to recuperate from near-disaster from my brother, who luckily works in the office now. If I can, I'll try to reinstall Puppy in such partitions, and keep menu.lst the same. Puppy seems to be broken (see above post). Any advice? Thank you again!

---John

---

### Post by Joseph Banea on 2008-07-24
umm... p.s., we're both John, by coincidence. I hope I don't look narcissistic?

---

### Post by caljohnsmith on 2008-07-25
> **Joseph Banea said:**
> Lord Almighty, bless his soul. You are a brilliant man, John. I had a hunch there was something wrong with the menu.lst, but I figured my computer had got corrupt. Ok, after I copied and pasted your code into menu.lst, I rebooted into GRUB, and selected Windows XP. It worked! First, Windows XP booted. Then it went into chkdsk, then rebooted. After that, I entered GRUB again, and selected Windows XP. It booted, and finally I could see my desktop, in all its shining glory! Woo! Am I glad to see it! ..... not that Linux is any bad. So, I'm happy. I will work with Puppy to boot, but I may need a day to recuperate from near-disaster from my brother, who luckily works in the office now. If I can, I'll try to reinstall Puppy in such partitions, and keep menu.lst the same. Puppy seems to be broken (see above post). Any advice? Thank you again!

---John
So glad to hear you got Windows XP to boot OK and won't have to worry about getting in hot water with your brother after all. :) About your Puppy partition, it's probably OK and we could get it to boot without reinstalling. But if you prefer to reinstall it, just be *really* careful that you install it to the correct partition (hda2) so you don't overwrite Windows. But there's a good chance you might have to modify the menu.lst again to get Windows booting OK, but you know the correct entry for Windows to put in your menu.lst now. 

If you want to try modifying your menu.lst to boot puppy instead of reinstalling, please post your complete menu.lst and put "code tags" around it so it is more readable. (To do that, highlight the text, and then hit the # sign at the top of the forum text entry dialog in your web browser).

---

