---
title: "&quot;NTLDR is missing&quot; - Vista/8.10 64 Bit Error"
date: 2008-12-08
forum: Installation &amp; Upgrades
---

### Post by outerspacerace on 2008-12-08
Hi all,

I feel like a huge fool right now as I've had a very similar problem before on XP:

[http://ubuntuforums.org/showthread.php?t=979623](http://ubuntuforums.org/showthread.php?t=979623)

Though now I have the same error when I try to load Vista from GRUB. 

However the info from that thread wasn't quite enough to help me solve it again - so here I go!

I had a perfect Vista install and dual booted 8.10 64 Bit tonight.

I can't say if that was what caused it alone (doubt it), or the fact that I left another IDE HDD plugged in at boot by accident (most likley).

The HDD still had my old XP/Ubuntu install documented in the thread linked above, so I'm guessing it screwed things up. 

Either way, I need to fix it so below I'll paste what I can to help you guys out.

---

### Post by outerspacerace on 2008-12-08
sudo fdisk -l:

> 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc0e94950

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       27529   221120512    7  HPFS/NTFS
/dev/sda2           27530       60801   267257340    5  Extended
/dev/sda5           57155       60801    29294527+  83  Linux
/dev/sda6           27830       57153   235544998+  83  Linux
/dev/sda7           27530       27828     2401654+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdf: 500.1 GB, 500107862016 bytes
16 heads, 63 sectors/track, 969021 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0xb971dd6f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1      969018   488385040+   7  HPFS/NTFS

Disk /dev/sdg: 8011 MB, 8011120640 bytes
16 heads, 32 sectors/track, 30560 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x000ac36f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1   *           1       30560     7823344    c  W95 FAT32 (LBA)

---

### Post by outerspacerace on 2008-12-08
GRUB menu.lst:

> # menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=f6a62373-5c4c-45e7-a5c5-786a2bbb6214 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f6a62373-5c4c-45e7-a5c5-786a2bbb6214

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		f6a62373-5c4c-45e7-a5c5-786a2bbb6214
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=f6a62373-5c4c-45e7-a5c5-786a2bbb6214 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		f6a62373-5c4c-45e7-a5c5-786a2bbb6214
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=f6a62373-5c4c-45e7-a5c5-786a2bbb6214 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		f6a62373-5c4c-45e7-a5c5-786a2bbb6214
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


---

### Post by caljohnsmith on 2008-12-08
So which partition is Vista on? Is is sda1 or sdf1? I've attached a bash script to this post that will greatly clarify your setup, and help determine how you should be booting Vista. Please download it to your desktop and do:
```
sudo sh ~/Desktop/boot_info.sh.txt
```
And please post the output. 

P.S. Many thanks to forum member meierfra who is the author of the script.

---

### Post by outerspacerace on 2008-12-08
Hi and cheers for the reply - you were the one who saved me last time mate!

Here's the results of the bash script you gave me:

> sda1 :ntfs:Vista: /Boot /bootmgr 
sda2 ::None: 
sda5 :ext3:None: /boot/grub/menu.lst /boot 
sda6 :ext3:None: 
sda7 :swap:None: 
sdb1 :ntfs:XP: 

I've also posted this screen grab.

Weird that there's so many little partitions. I did manually partition but usually get all that stuff correct.

If it helps to know I created two partitions from the Vista installer initially which may have created the 8MB or so lots of unallocated space... isn't that a Windows/RAID thing?

Or maybe I miscounted when creating the ubuntu partitions - my screen was flickering from a lack of nVidia drivers during setup lol :(

Either way that's getting off track.

Any advice getting VIsta to boot again would be magic!

Thanks in advance.

---

### Post by caljohnsmith on 2008-12-08
In that previous thread where I helped you get XP booting, you had XP in sda1; according to that script you ran, you now have Vista's boot files there. Which drive did you install Vista to? It looks like your device names might be changing. Also, when you try and boot Vista from the Grub menu using the entry you all ready have:
```
title Windows Vista/Longhorn (loader)
root (hd0,0)
savedefault
makeactive
chainloader +1
```
Is that when you get the "NTLDR is missing" error? Please post the output of all the following commands:
```
sudo xxd -l 2 -p /dev/sda
sudo xxd -s 1049 -l 2 -p /dev/sda
sudo xxd -l 2 -p /dev/sdb
sudo xxd -s 1049 -l 2 -p /dev/sdb
sudo mkdir /mnt/sda1 /mnt/sdb1
sudo mount /dev/sda1 /mnt/sda1
sudo mount /dev/sdb1 /mnt/sdb1
ls -l /mnt/sda1 /mnt/sdb1

```
Note "-l" is a lowercase L, not a one. We can work from there. :)

---

### Post by outerspacerace on 2008-12-08
Thanks again mate...

I neglected to mention earlier that this is an entirely fresh, brand new HDD (SATA this time around). Though you probably guessed from the size readouts ;)

Vista is in the same spot XP was on the old drive as they were both installed first.

Basically I installed Windows, then 8.10 64 bit. 

It could be my device names are changing as you mentioned OR the fact I accidentally put the old drive back in whilst I booted. That drive is the exact one from my previous thread in which you helped me out (so it would still contain GRUB info ETC).

I stupidly did that as I wanted to get some files from it, which I should have backed up first but forgot to as I was in such a hurry :( The correct thing would have been to seek out an external USB case and grab the files that way but it was getting late...

Interestingly, both times I've had to ask for help is when I've dual booted with the 64 bit 8.10. I had used 8.04 32 bit many times, with manual partitioning, and it worked fine on various PC's.

When I return home tonight I'll be sure to run the commands you posted and get back to you here.

---

### Post by outerspacerace on 2008-12-08
P.S. Yes, that's when I get the "NTLDR" error, in that configuration above. 

I haven't changed options in the GRUB menu.lst or anything else since installing 8.10

---

### Post by outerspacerace on 2008-12-09
Hiya,

Just fixed things by myself - pretty easily too :)

After the GRUB menu is displayed I noticed ubuntu was booting from hd1,4 so I modified my menu.lst to read:

> title Windows Vista/Longhorn (loader)
root (hd1,0)
savedefault
makeactive
chainloader +1

and voila!

Things are fine for both OS's, I'm typing from Vista now.

Cheers again for your observation about the devices possible changing, that gave me a big clue.

Out of curiosity, should I bother resizing partitions to eat up those small blocks of unallocated space? I like to keep things neat & tidy is all...

Also, is it ok for me to rename Vista in the menu.lst file? I'd rather it didn't read as Longhorn, that really bugs me.

BTW I can still log back into ubuntu to run the commands you gave above if you think it's need.

Cheers again!

---

### Post by caljohnsmith on 2008-12-09
> **outerspacerace said:**
> 
Out of curiosity, should I bother resizing partitions to eat up those small blocks of unallocated space? I like to keep things neat & tidy is all...

You could, but I definitely think it is more trouble and risk than it is worth considering that the few unused portions are only 1-7 MB apiece. Also, I just want to warn you that please don't be tempted to resize your Windows sda1 partition at the beginning to use the 1 MB of free space at the beginning of your sda drive, because moving the starting point of a Windows partition breaks Windows in a way that only lots of hacking can fix. The other problem is if you resize your Linux partitions to use the other tiny chunks of free space, the UUIDs of the Linux partitions will change; you would have to fix that afterwards. So it's up to you of course if you want to do it, but I don't think the benefits of gaining the extra ~20 MB of unused space is worth the trouble or the risk of repartitioning. :)
> **outerspacerace said:**
> 
Also, is it ok for me to rename Vista in the menu.lst file? I'd rather it didn't read as Longhorn, that really bugs me.

BTW I can still log back into ubuntu to run the commands you gave above if you think it's need.

Cheers again!
Sure, you can call Vista anything you want in your menu.lst. And as long as you have all your OSes booting OK, no need to run those commands I gave; the commands would have clarified what you all ready figured out on your own. Anyway, cheers and have fun with all your OSes. :)

---

### Post by outerspacerace on 2008-12-09
Cheers mate, sound advice.

As for having fun, I was almost Microsoft free until I decided to do a short course in Flash CS4. 

Hence I had to install Windoze, though went the Vista route this time.

It's hardly fun but I gotta say it's nowhere near as bad as I'd heard... on my hardware at least it's much better than XP.

---

### Post by outerspacerace on 2008-12-10
This is somewhat unrelated, though I figured I'd continue the saga on here, it's just one of those weeks it seems :(

I ended up putting another 320GB IDE drive back into the PC to copy some files over from.

Can hardly believe it myself - but I left the jumper on/IDE channel as master by mistake. I know, I know - after all this!!!

Now Vista won't boot, even when I remove that drive. I'm really learning that having old IDE drives set as master on a dual boot machine is a bad thing the hard way.

It's the only IDE drive left I need working in my sytem.

Now I've set it as a slave, so ubuntu boots fine and I was able to grab the files I needed. I'll leave it in as is from now on, along with all the current drives.

Question is, can I fix Vista this time?

After I select Vista from the GRUB bootloader menu it says "Starting Up" but only ever displays a flashing cursor and nothing more.

This doesn't sound good I realise :(

Cheers in advance.

---

### Post by caljohnsmith on 2008-12-10
Sorry to hear you're having problems with Vista again; how about first trying the following entry in your Grub's menu.lst for Vista and see if it works:
```
title Windows Vista
root       (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1 
```
If it doesn't work, please let me know exactly what happens when you try it from the Grub menu, and we can work from there. :)

---

### Post by outerspacerace on 2008-12-10
Thanks again!

When I try that I get the old "NTLDR Is Missing" error, though at least we may be getting somewhat closer now...

---

### Post by caljohnsmith on 2008-12-10
OK, how about trying:
```
title Windows Vista
root (hd0,0)
chainloader +1
```
And if for some reason that doesn't work, let me know exactly what happens when you try it from the Grub menu. Also, on start up, press "c" at the Grub menu to get the command line, and then do:
```
grub> geometry (hd0)
grub> geometry (hd1)
```
And please let me know the output.

---

### Post by outerspacerace on 2008-12-10
Thanks a bunch again Caljohn!

Your first suggestion worked.

Mate I'm so grateful for that, I really need Vista to be learning Flash so you helped out more than you realise!

Is there anywhere you can suggest that is a good place to learn about GRUB/Bootloaders etc?

I can't always be picking your brain buddy!

Cheers again!

---

### Post by caljohnsmith on 2008-12-10
> **outerspacerace said:**
> Thanks a bunch again Caljohn!

Your first suggestion worked.

Mate I'm so grateful for that, I really need Vista to be learning Flash so you helped out more than you realise!

Is there anywhere you can suggest that is a good place to learn about GRUB/Bootloaders etc?

I can't always be picking your brain buddy!

Cheers again!
You're welcome, glad to hear that worked. If you want to learn more about Grub, you could start with these two resources:

[http://www.users.bigpond.net.au/hermanzone/p15.htm](http://www.users.bigpond.net.au/hermanzone/p15.htm)
[http://www.gnu.org/software/grub/manual/](http://www.gnu.org/software/grub/manual/)

But don't feel like you need to learn all the intracacies and nuances of Grub just to troubleshoot your booting problems if it doesn't really interest you; feel free to come back and ask if you have any more booting problems. Anyway, cheers and have fun learning Flash. :)

---

