---
title: "[SOLVED] GRUB error 17 with Ubuntu 8.04"
date: 2008-08-25
forum: General Help
---

### Post by jackhynes on 2008-08-25
Like [many others]("http://ubuntuforums.org/tags.php?tag=error+17"), I have the dreaded error 17 at the grub screen of Ubuntu 8.04. I recently increased my root partition size and reinstalled Ubuntu (and formatted the previous installation), which was obviously the problem but didn't occur last install.

I've tried nearly all of the suggestions on the forums to try and fix this, I've tried all of Herman's methods (including filesystem check: was fine, the details in my /boot/grub/menu.lst seem to be correct, reinstalled GRUB and I don't have any BIOS options to change the hard disk boot). Hope someone can help me because I even tried installing Intrepid alpha-4 but it gave me a 'Buffer I/O error' which I also couldn't manage to work around. Thanks in advance for any help!

/boot/grub/menu.lst
```
title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=2b9e6896-9919-4c1e-a77c-df9027d3ee66 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=2b9e6896-9919-4c1e-a77c-df9027d3ee66 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,1)
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
```

/boot/grub/device.map
```
(hd0)	/dev/sda
```

sudo fdisk -l
```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9a10d0a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3040    24414062+   7  HPFS/NTFS [Windows]
/dev/sda2           36961       38791    14707507+  83  Linux [root]
/dev/sda3            3041       36960   272462400   83  Linux [home]
/dev/sda4           38792       38913      979965   82  Linux swap / Solaris
```

---

### Post by unutbu on 2008-08-25
Have you tried using a SuperGRUB disk? [http://www.supergrubdisk.org/wiki/Multi_Distribution_Boot_Howto](http://www.supergrubdisk.org/wiki/Multi_Distribution_Boot_Howto)

If that's been tried, then this sounds like a real stumper.
Well, to help us with a little more information, perhaps try this:

Reboot.
Press ESC to get to the GRUB menu.
Press 'c' to get to the GRUB command line.
Type
```
find /boot/grub/stage1
```
Does it return something other than (hd0,1)?
Note what ever this command returns.
Then type
```
geometry (hd0,[TAB]
```
Write down whatever output you see.

Power down the computer.
Post the output.

---

### Post by jackhynes on 2008-08-25
> **unutbu said:**
> Have you tried using a SuperGRUB disk? [http://www.supergrubdisk.org/wiki/Multi_Distribution_Boot_Howto](http://www.supergrubdisk.org/wiki/Multi_Distribution_Boot_Howto)

Yeah, tried that but all the modes failed. I couldn't even seem to boot Windows. When I run the livecd all of the partitions are found, and like I said before the filesystem check was fine on /dev/sda2. I'm gonna reboot now and try those commands, thanks for the help!

---

### Post by jackhynes on 2008-08-25
> **unutbu said:**
> Well, to help us with a little more information, perhaps try this:

Reboot.
Press ESC to get to the GRUB menu.
Press 'c' to get to the GRUB command line.
Type
```
find /boot/grub/stage1
```
Does it return something other than (hd0,1)?
Note what ever this command returns.
Then type
```
geometry (hd0,[TAB]
```
Write down whatever output you see.

Power down the computer.
Post the output.

Just tried, can't get to the GRUB menu. It flicks straight to Error 17, no matter when I press Esc. Any other ideas? I've already tried reinstalling 8.04, cheers for the help so far.

---

### Post by unutbu on 2008-08-25
Hm. Do you have a USB key plugged into the machine? Any external drives?
If so, unplug them. 

I know you've probably done this before, but since I don't have any better idea, please humor me and try this once again:

Boot from the LiveCD, open a terminal and type
```

sudo grub
root (hd0,1)
setup (hd0)
```

The output should look like this:
```

 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,1)/boot/grub/stage2 /boot/grub/menu.lst".
.. succeeded
Done.

```
If your output is different, copy it down and post.

Type 'quit' to quit grub.

To help us gain more information about what's going on, please also run at the terminal:

```
sudo dd if=/dev/sda  bs=1 skip=1049 count=2 | hexdump
```

The output should say
```

    00000000 ff01           
    00000002
```

The "01" means that the bootloader will hand-off to (hd0,1).

If you get something different, make note of what you get.

Then type
```

sudo dd if=/dev/sda bs=512 count=1 | hexdump -C

```
You should see
```

1+0 records in
1+0 records out
512 bytes (512 B) copied, 0.000985481 seconds, 520 kB/s
00000000  eb 48 90 44 65 6c 6c 20  38 2e 30 00 02 08 26 10  |.H.Dell 8.0...&.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 47 b7 01 00  |........?...G...|
00000020  4d 12 a0 00 ed 27 00 00  00 00 00 00 02 00 00 00  |M....'..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 03 02  |................|
00000040  ff 00 00 80 d7 08 2b 00  00 08 fa 90 90 f6 c2 80  |......+.........|
00000050  75 02 b2 80 ea 59 7c 00  00 31 c0 8e d8 8e d0 bc  |u....Y|..1......|
00000060  00 20 fb a0 40 7c 3c ff  74 02 88 c2 52 be 7f 7d  |. ..@|<.t...R..}|
00000070  e8 34 01 f6 c2 80 74 54  b4 41 bb aa 55 cd 13 5a  |.4....tT.A..U..Z|
00000080  52 72 49 81 fb 55 aa 75  43 a0 41 7c 84 c0 75 05  |RrI..U.uC.A|..u.|
00000090  83 e1 01 74 37 66 8b 4c  10 be 05 7c c6 44 ff 01  |...t7f.L...|.D..|
000000a0  66 8b 1e 44 7c c7 04 10  00 c7 44 02 01 00 66 89  |f..D|.....D...f.|
000000b0  5c 08 c7 44 06 00 70 66  31 c0 89 44 04 66 89 44  |\..D..pf1..D.f.D|
000000c0  0c b4 42 cd 13 72 05 bb  00 70 eb 7d b4 08 cd 13  |..B..r...p.}....|
000000d0  73 0a f6 c2 80 0f 84 ea  00 e9 8d 00 be 05 7c c6  |s.............|.|
000000e0  44 ff 00 66 31 c0 88 f0  40 66 89 44 04 31 d2 88  |D..f1...@f.D.1..|
000000f0  ca c1 e2 02 88 e8 88 f4  40 89 44 08 31 c0 88 d0  |........@.D.1...|
00000100  c0 e8 02 66 89 04 66 a1  44 7c 66 31 d2 66 f7 34  |...f..f.D|f1.f.4|
00000110  88 54 0a 66 31 d2 66 f7  74 04 88 54 0b 89 44 0c  |.T.f1.f.t..T..D.|
00000120  3b 44 08 7d 3c 8a 54 0d  c0 e2 06 8a 4c 0a fe c1  |;D.}<.T.....L...|
00000130  08 d1 8a 6c 0c 5a 8a 74  0b bb 00 70 8e c3 31 db  |...l.Z.t...p..1.|
00000140  b8 01 02 cd 13 72 2a 8c  c3 8e 06 48 7c 60 1e b9  |.....r*....H|`..|
00000150  00 01 8e db 31 f6 31 ff  fc f3 a5 1f 61 ff 26 42  |....1.1.....a.&B|
00000160  7c be 85 7d e8 40 00 eb  0e be 8a 7d e8 38 00 eb  ||..}.@.....}.8..|
00000[COLOR="Red"]170[/COLOR]  06 be 94 7d e8 30 00 be  99 7d e8 2a 00 eb fe 47  |...}.0...}.*...[COLOR="Red"]G[/COLOR]|
00000[COLOR="Red"]180[/COLOR]  52 55 42 20 00 47 65 6f  6d 00 48 61 72 64 20 44  |[COLOR="Red"]RUB .Geom.Hard D[/COLOR]|
00000[COLOR="Red"]190[/COLOR]  69 73 6b 00 52 65 61 64  00 20 45 72 72 6f 72 00  |[COLOR="Red"]isk.Read. Error.[/COLOR]|
000001a0  bb 01 00 b4 0e cd 10 ac  3c 00 75 f4 c3 00 00 00  |........<.u.....|
000001b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```
This is your MBR. Yours may differ a bit at the beginning and at the end, but lines 17--19 should contain the string "GRUB .Geom.Hard Disk.Read. Error." This is supporting evidence that GRUB was successfully installed on the sda's MBR.

Finally, try rebooting.

---

### Post by ageilers on 2008-08-25
Might try checking the UUID of the partition in question against what is in your GRUB printout. I remember doing something similar with the same GRUB error.

---

### Post by jackhynes on 2008-08-26
> **unutbu said:**
> Hm. Do you have a USB key plugged into the machine? Any external drives?
If so, unplug them. 

I know you've probably done this before, but since I don't have any better idea, please humor me and try this once again:

Boot from the LiveCD, open a terminal and type
```

sudo grub
root (hd0,1)
setup (hd0)
```

The output should look like this:
```

 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,1)/boot/grub/stage2 /boot/grub/menu.lst".
.. succeeded
Done.

```
If your output is different, copy it down and post.

Type 'quit' to quit grub.

To help us gain more information about what's going on, please also run at the terminal:

```
sudo dd if=/dev/sda  bs=1 skip=1049 count=2 | hexdump
```

The output should say
```

    00000000 ff01           
    00000002
```

The "01" means that the bootloader will hand-off to (hd0,1).

If you get something different, make note of what you get.

Then type
```

sudo dd if=/dev/sda bs=512 count=1 | hexdump -C

```
You should see
```

1+0 records in
1+0 records out
512 bytes (512 B) copied, 0.000985481 seconds, 520 kB/s
00000000  eb 48 90 44 65 6c 6c 20  38 2e 30 00 02 08 26 10  |.H.Dell 8.0...&.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 47 b7 01 00  |........?...G...|
00000020  4d 12 a0 00 ed 27 00 00  00 00 00 00 02 00 00 00  |M....'..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 03 02  |................|
00000040  ff 00 00 80 d7 08 2b 00  00 08 fa 90 90 f6 c2 80  |......+.........|
00000050  75 02 b2 80 ea 59 7c 00  00 31 c0 8e d8 8e d0 bc  |u....Y|..1......|
00000060  00 20 fb a0 40 7c 3c ff  74 02 88 c2 52 be 7f 7d  |. ..@|<.t...R..}|
00000070  e8 34 01 f6 c2 80 74 54  b4 41 bb aa 55 cd 13 5a  |.4....tT.A..U..Z|
00000080  52 72 49 81 fb 55 aa 75  43 a0 41 7c 84 c0 75 05  |RrI..U.uC.A|..u.|
00000090  83 e1 01 74 37 66 8b 4c  10 be 05 7c c6 44 ff 01  |...t7f.L...|.D..|
000000a0  66 8b 1e 44 7c c7 04 10  00 c7 44 02 01 00 66 89  |f..D|.....D...f.|
000000b0  5c 08 c7 44 06 00 70 66  31 c0 89 44 04 66 89 44  |\..D..pf1..D.f.D|
000000c0  0c b4 42 cd 13 72 05 bb  00 70 eb 7d b4 08 cd 13  |..B..r...p.}....|
000000d0  73 0a f6 c2 80 0f 84 ea  00 e9 8d 00 be 05 7c c6  |s.............|.|
000000e0  44 ff 00 66 31 c0 88 f0  40 66 89 44 04 31 d2 88  |D..f1...@f.D.1..|
000000f0  ca c1 e2 02 88 e8 88 f4  40 89 44 08 31 c0 88 d0  |........@.D.1...|
00000100  c0 e8 02 66 89 04 66 a1  44 7c 66 31 d2 66 f7 34  |...f..f.D|f1.f.4|
00000110  88 54 0a 66 31 d2 66 f7  74 04 88 54 0b 89 44 0c  |.T.f1.f.t..T..D.|
00000120  3b 44 08 7d 3c 8a 54 0d  c0 e2 06 8a 4c 0a fe c1  |;D.}<.T.....L...|
00000130  08 d1 8a 6c 0c 5a 8a 74  0b bb 00 70 8e c3 31 db  |...l.Z.t...p..1.|
00000140  b8 01 02 cd 13 72 2a 8c  c3 8e 06 48 7c 60 1e b9  |.....r*....H|`..|
00000150  00 01 8e db 31 f6 31 ff  fc f3 a5 1f 61 ff 26 42  |....1.1.....a.&B|
00000160  7c be 85 7d e8 40 00 eb  0e be 8a 7d e8 38 00 eb  ||..}.@.....}.8..|
00000[COLOR="Red"]170[/COLOR]  06 be 94 7d e8 30 00 be  99 7d e8 2a 00 eb fe 47  |...}.0...}.*...[COLOR="Red"]G[/COLOR]|
00000[COLOR="Red"]180[/COLOR]  52 55 42 20 00 47 65 6f  6d 00 48 61 72 64 20 44  |[COLOR="Red"]RUB .Geom.Hard D[/COLOR]|
00000[COLOR="Red"]190[/COLOR]  69 73 6b 00 52 65 61 64  00 20 45 72 72 6f 72 00  |[COLOR="Red"]isk.Read. Error.[/COLOR]|
000001a0  bb 01 00 b4 0e cd 10 ac  3c 00 75 f4 c3 00 00 00  |........<.u.....|
000001b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```
This is your MBR. Yours may differ a bit at the beginning and at the end, but lines 17--19 should contain the string "GRUB .Geom.Hard Disk.Read. Error." This is supporting evidence that GRUB was successfully installed on the sda's MBR.

Finally, try rebooting.

All of those were the correct output (although I had 16 sectors embedded) and when I rebooted Error 17 wa still there waiting for me :(

I might try and install 7.10 to see if that makes any difference. Thanks for the help.

---

### Post by caljohnsmith on 2008-08-26
Jackhynes, I think your problem might be related to a limitation of your BIOS, where your BIOS can only see the first 137 GB of your HDD. From your fdisk output, it looks like your Ubuntu root partition starts at about 300 GB, which is well outside of the 137 GB range. How old is your BIOS? If your BIOS is truly the culprit, the best solution would be to upgrade it so it can handle a larger HDD. Or you could simply move your /boot/grub directory over to your Ubuntu /home partition sda3, since the sda3 partition starts at about 25 GB. Moving the Grub directory to a partition closer to the start of your HDD certainly couldn't hurt, and I think there's a strong possibility it will solve your problem.

---

### Post by jackhynes on 2008-08-26
> **caljohnsmith said:**
> Jackhynes, I think your problem might be related to a limitation of your BIOS, where your BIOS can only see the first 137 GB of your HDD. From your fdisk output, it looks like your Ubuntu root partition starts at about 300 GB, which is well outside of the 137 GB range. How old is your BIOS? If your BIOS is truly the culprit, the best solution would be to upgrade it so it can handle a larger HDD. Or you could simply move your /boot/grub directory over to your Ubuntu /home partition sda3, since the sda3 partition starts at about 25 GB. Moving the Grub directory to a partition closer to the start of your HDD certainly couldn't hurt, and I think there's a strong possibility it will solve your problem.

Okay I tried moving the /boot/grub directory to the home partition but it didn't work, I tried changing the menu.lst ubuntu partition entry to (hd0,2) and that didn't work either. Because I can't boot Windows either I can't update my BIOS, something which I don't think wine allows you to do. I think I'm back to square one, thanks anyway for the help but I think a full reinstallation is in order...

---

### Post by unutbu on 2008-08-26
caljohnsmith might still be right. The /home partition begins within the address range that your BIOS can map to, but it might be the case that it ends outside the range. If you copy /boot/grub to sda3, it might have landed at an address that is still too deep in the disk. If you are game for one more go at this,
use the LiveCD's gparted to resize /home so that /boot  can have its own partition close to the beginning of the disk. Then copy /boot/grub there.

If you are interested, post and I can write up more detailed instructions.

---

### Post by caljohnsmith on 2008-08-26
Wait guys, I think the only problem may be that after you move the /boot/grub directory over, you then have to reinstall Grub to the MBR and point it to that new partition. Jackhynes, your home partition is on sda3, so:```
sudo grub
grub> root (hd0,2)
grub> setup (hd0)

```
If that doesn't work, then I agree with you, Unutbu, that it could be because that directory is still out of range of the BIOS. That's a great insight. After all, his home directory ends at the 300 GB mark. :)

---

### Post by jackhynes on 2008-08-27
> **caljohnsmith said:**
> Wait guys, I think the only problem may be that after you move the /boot/grub directory over, you then have to reinstall Grub to the MBR and point it to that new partition. Jackhynes, your home partition is on sda3, so:```
sudo grub
grub> root (hd0,2)
grub> setup (hd0)

```
If that doesn't work, then I agree with you, Unutbu, that it could be because that directory is still out of range of the BIOS. That's a great insight. After all, his home directory ends at the 300 GB mark. :)

Wow, something happened! I've now go a new error, this is so exciting! It's now giving me Error 18, not to soon either, I was starting to bore of Error 17. Now to search the forums on what to do about Error 18.

---

### Post by jackhynes on 2008-08-27
Hopefully [this]("http://users.bigpond.net.au/hermanzone/p15.htm#18") will help me. I'll need to look over it when I've got some time.

---

### Post by unutbu on 2008-08-27
According to [http://www.gnu.org/software/grub/manual/grub.html#Troubleshooting](http://www.gnu.org/software/grub/manual/grub.html#Troubleshooting)
GRUB Error 18 means:
```

18 : Selected cylinder exceeds maximum supported by BIOS
    This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB in general). 


```
Here is your partition table with the cylinder start/end positions in order:
```
                    Cylinder numbers:
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3040    24414062+   7  HPFS/NTFS [Windows]
/dev/sda3            3041       36960   272462400   83  Linux [home] <-- has /boot
/dev/sda2           36961       38791    14707507+  83  Linux [root]
/dev/sda4           38792       38913      979965   82  Linux swap / Solaris
```

Error 18 is saying the /boot resides at a cylinder number that is too high.
To force /boot to reside on a lower cylinder, perhaps:

delete /dev/sda2, 
move /dev/sda3 to the right, into the space previously occupied by /dev/sda2
create a new /dev/sda2
reinstall Ubuntu on /dev/sda2

---

### Post by caljohnsmith on 2008-08-29
Just another thought, Jackhynes, in case you haven't all ready changed your entire partitioning scheme yet; another option is that you could make room for a really small 10 MB (not GB) partition right after sda1, and use that as your dedicated Grub partition. That's how I've done it on my HDD, because I like to have Grub independent of all the Linux distros I play with. It is really easy to set up if you are interested. That might be the easiest solution as it could save doing a reinstall, but if you don't mind doing a reinstall, then unutbu's idea would work great too I'm sure.

---

### Post by jackhynes on 2008-08-31
> **unutbu said:**
> Error 18 is saying the /boot resides at a cylinder number that is too high.
To force /boot to reside on a lower cylinder, perhaps:

delete /dev/sda2, 
move /dev/sda3 to the right, into the space previously occupied by /dev/sda2
create a new /dev/sda2
reinstall Ubuntu on /dev/sda2

Excellent work, I'm back up and running (...almost - an update to Intrepid has broken my keyboard at the login screen). I did what you said and just deleted sda2 and sda3 then installed ubuntu to the 'Beginning' of the free space and created my large partition at the 'End' of the free space. Thanks again and thanks also to caljohnsmith!

---

### Post by caljohnsmith on 2008-08-31
Thanks for following up and letting us know how you fixed the problem. We're glad you're up-and-running again. :)

---

### Post by smusevic on 2008-09-04
Ok, more grub related problems.

Installed Ubuntu 8.04 on partition 3 of disk 2. Got the Grub Error 17.
Booted with LiveCD, here is the status:

```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 10.0 GB, 10005037056 bytes
255 heads, 63 sectors/track, 1216 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xea1aa9c7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1215     9759456    7  HPFS/NTFS

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f298f29

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1044     8385898+   7  HPFS/NTFS
/dev/sdb2            1045        4325    26354632+   7  HPFS/NTFS
/dev/sdb3            4326        9235    39439575   83  Linux
/dev/sdb4            9236        9964     5855692+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ 

```

sbd1,sdb2 are old xp partitions, that I'd like to keep.
Here is what I do:
```

ubuntu@ubuntu:~$ sudo grub
grub> find /boot/grub/stage1
 (hd1,2)

grub> geometry (hd1,2)
drive 0x81: C/H/S = 9964/255/63, The number of sectors = 160086528, /dev/sdb
   Partition num: 0,  Filesystem type unknown, partition type 0x7
   Partition num: 1,  Filesystem type unknown, partition type 0x7
   Partition num: 2,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 3,  Filesystem type unknown, partition type 0x82
grub> root (hd1,2)

grub> setup (hd1)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd1)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd1) (hd1)1+16 p (hd1,2)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.
grub> quit
ubuntu@ubuntu:~$ sudo dd if=/dev/sdb  bs=1 skip=1049 count=2 | hexdump
2+0 records in
2+0 records out
0000000 ff02                                   
2 bytes (2 B) copied0000002
, 0.00951691 s, 0.2 kB/s
ubuntu@ubuntu:~$ sudo dd if=/dev/sdb bs=512 count=1 | hexdump -C
1+0 records in
1+0 records out
512 bytes (512 B) copied, 5.6057e-05 s, 9.1 MB/s
00000000  eb 48 90 d0 bc 00 7c fb  50 07 50 1f fc be 1b 7c  |.H....|.P.P....||
00000010  bf 1b 06 50 57 b9 e5 01  f3 a4 cb bd be 07 b1 04  |...PW...........|
00000020  38 6e 00 7c 09 75 13 83  c5 10 e2 f4 cd 18 8b f5  |8n.|.u..........|
00000030  83 c6 10 49 74 19 38 2c  74 f6 a0 b5 07 b4 03 02  |...It.8,t.......|
00000040  ff 00 00 20 01 00 00 00  00 02 fa 90 90 f6 c2 80  |... ............|
00000050  75 02 b2 80 ea 59 7c 00  00 31 c0 8e d8 8e d0 bc  |u....Y|..1......|
00000060  00 20 fb a0 40 7c 3c ff  74 02 88 c2 52 be 7f 7d  |. ..@|<.t...R..}|
00000070  e8 34 01 f6 c2 80 74 54  b4 41 bb aa 55 cd 13 5a  |.4....tT.A..U..Z|
00000080  52 72 49 81 fb 55 aa 75  43 a0 41 7c 84 c0 75 05  |RrI..U.uC.A|..u.|
00000090  83 e1 01 74 37 66 8b 4c  10 be 05 7c c6 44 ff 01  |...t7f.L...|.D..|
000000a0  66 8b 1e 44 7c c7 04 10  00 c7 44 02 01 00 66 89  |f..D|.....D...f.|
000000b0  5c 08 c7 44 06 00 70 66  31 c0 89 44 04 66 89 44  |\..D..pf1..D.f.D|
000000c0  0c b4 42 cd 13 72 05 bb  00 70 eb 7d b4 08 cd 13  |..B..r...p.}....|
000000d0  73 0a f6 c2 80 0f 84 ea  00 e9 8d 00 be 05 7c c6  |s.............|.|
000000e0  44 ff 00 66 31 c0 88 f0  40 66 89 44 04 31 d2 88  |D..f1...@f.D.1..|
000000f0  ca c1 e2 02 88 e8 88 f4  40 89 44 08 31 c0 88 d0  |........@.D.1...|
00000100  c0 e8 02 66 89 04 66 a1  44 7c 66 31 d2 66 f7 34  |...f..f.D|f1.f.4|
00000110  88 54 0a 66 31 d2 66 f7  74 04 88 54 0b 89 44 0c  |.T.f1.f.t..T..D.|
00000120  3b 44 08 7d 3c 8a 54 0d  c0 e2 06 8a 4c 0a fe c1  |;D.}<.T.....L...|
00000130  08 d1 8a 6c 0c 5a 8a 74  0b bb 00 70 8e c3 31 db  |...l.Z.t...p..1.|
00000140  b8 01 02 cd 13 72 2a 8c  c3 8e 06 48 7c 60 1e b9  |.....r*....H|`..|
00000150  00 01 8e db 31 f6 31 ff  fc f3 a5 1f 61 ff 26 42  |....1.1.....a.&B|
00000160  7c be 85 7d e8 40 00 eb  0e be 8a 7d e8 38 00 eb  ||..}.@.....}.8..|
00000170  06 be 94 7d e8 30 00 be  99 7d e8 2a 00 eb fe 47  |...}.0...}.*...G|
00000180  52 55 42 20 00 47 65 6f  6d 00 48 61 72 64 20 44  |RUB .Geom.Hard D|
00000190  69 73 6b 00 52 65 61 64  00 20 45 72 72 6f 72 00  |isk.Read. Error.|
000001a0  bb 01 00 b4 0e cd 10 ac  3c 00 75 f4 c3 00 00 00  |........<.u.....|
000001b0  00 00 00 00 00 00 00 00  29 8f 29 8f 00 00 80 01  |........).).....|
000001c0  01 00 07 fe ff ff 3f 00  00 00 d5 ea ff 00 00 00  |......?.........|
000001d0  c1 ff 07 fe ff ff 14 eb  ff 00 91 47 24 03 00 fe  |...........G$...|
000001e0  ff ff 83 fe ff ff a5 32  24 04 ae 99 b3 04 00 fe  |.......2$.......|
000001f0  ff ff 82 fe ff ff 53 cc  d7 08 99 b3 b2 00 55 aa  |......S.......U.|
00000200

```

PLEASE NOTE: the output of ```
sudo dd if=/dev/sdb  bs=1 skip=1049 count=2 | hexdump
``` returned ff02. If I understand this correctly, it should be ff12 (according to root (hd1,2) ).

BIOS is setup to boot from sdb.

sdb2/boot/grub/device.map
```

(hd0)	/dev/sda
(hd1)	/dev/sdb

```
relevant part of sdb2/boot/grub/menu.lst
```

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=b8a5c053-1fd6-4013-a75a-4d1e4fdd70ba ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=b8a5c053-1fd6-4013-a75a-4d1e4fdd70ba ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```

Reboot, GRUB ERROR 17.

Thanks in advance, 
   Sash!!!

---

### Post by unutbu on 2008-09-04
smusevic, thank you for the beautiful output. 

I agree with you that I would have expected the output of 
```

sudo dd if=/dev/sdb  bs=1 skip=1049 count=2 | hexdump
```

to be ff12. However, I am not entirely confident I understand what the output of this command should be in all cases. Also, the output from "setup (hd1)" looks perfect. For these two reasons, I am going to ignore this for now and assume it is correct.

How about try this:

Boot from the LiveCD, and in a terminal type```

sudo mount /dev/sdb3 /mnt
gksu gedit /mnt/boot/grub/menu.lst
```

Do a search and replace to change all occurrences of (hd1,2) to (hd0,2). Save and Exit.

See if that is enough to allow you to boot Linux. If it is, we may have to make some similar change to get Windows booting.

---

### Post by caljohnsmith on 2008-09-04
> **smusevic said:**
> 
ubuntu@ubuntu:~$ sudo dd if=/dev/sdb  bs=1 skip=1049 count=2 | hexdump
2+0 records in
2+0 records out
0000000 ff02                                   
2 bytes (2 B) copied0000002
, 0.00951691 s, 0.2 kB/s

PLEASE NOTE: the output of ```
sudo dd if=/dev/sdb  bs=1 skip=1049 count=2 | hexdump
``` returned ff02. If I understand this correctly, it should be ff12 (according to root (hd1,2) ).

Actually the "ff02" means that the Grub MBR points to the 3rd partition on the same HDD (which happens to be (hd1)), so "ff02" is exactly what you want.
> **smusevic said:**
> 
Reboot, GRUB ERROR 17.

Thanks in advance, 
   Sash!!!
So are you sure you have your BIOS set to boot the Ubuntu HDD first? And when you say you get Grub error 17, is that before you get a Grub menu on start up, or after you select Ubuntu/Windows? I would guess it is the latter case, because you need to change your Ubuntu/Windows entries in your menu.lst. The point of confusion I think is that Grub considers which HDD is first in the boot order to be (hd0). So if you boot your Ubuntu HDD first on start up, then your Ubuntu entries in menu.lst should be (hd0,2) and not (hd1,2). And then your Windows is considered to be on (hd1,0) instead of (hd0,0). So bottom line, try changing your menu.lst as follows, and I think you should be all set:
```
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		[COLOR="Blue"](hd0,2)[/COLOR]
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=b8a5c053-1fd6-4013-a75a-4d1e4fdd70ba ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		[COLOR="Blue"](hd0,2)[/COLOR]
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=b8a5c053-1fd6-4013-a75a-4d1e4fdd70ba ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		[COLOR="Blue"](hd0,2)[/COLOR]
kernel		/boot/memtest86+.bin
quiet
```
Let me know how it goes.

---

### Post by unutbu on 2008-09-04
caljohnsmith, thanks for the information regarding ff02. I have one further question:
If a person had 3 hard drives, and did
```

root (hd2,2)
setup (hd1)
```

and 
```

sudo dd if=/dev/sdb  bs=1 skip=1049 count=2 | hexdump
```

would it return "ff12" because the third drive is the next one after sdb or would it return "ff22" because "ff12" refers to the first drive? 

This certainly adds another element of complexity -- each drive has its own numbering system for the other drives!? Yuck!

Edit: On further reflection, there is no "added element of complexity". The drives have no idea about numbering. They are just drives :). The meaning of the numbering is simply the numbering used by the BIOS.

So "ff12" for example, would direct the stage1.5 bootloader to hand-off to (hd1,2), and the meaning of (hd1,2) is determined by whatever the BIOS thinks (hd1) means. The meaning can change depending on how many USB flash drives you have plugged in at the time, for example.

---

### Post by caljohnsmith on 2008-09-04
> **unutbu said:**
> caljohnsmith, thanks for the information regarding ff02. I have one further question:
If a person had 3 hard drives, and did
```

root (hd2,2)
setup (hd1)
```

and 
```

sudo dd if=/dev/sdb  bs=1 skip=1049 count=2 | hexdump
```

would it return "ff12" because the third drive is the next one after sdb or would it return "ff22" because "ff12" refers to the first drive? 

This certainly adds another element of complexity -- each drive has its own numbering system for the other drives!? Yuck!
Yes, it's confusing, but here is the way I believe it works (note the XX stands for a number):
[LIST]
[*]ffXX means that the Grub MBR points to a partition that is on the same HDD, and it is partition (hd0,XX). Thus ff04 means Grub points to (hd0,4) or the 5th partition of that same HDD. "ff12" would simply mean (hd0,12).
[*]If the "ff" is anything else, such as "80" or "82" for example, that means Grub in the MBR will look at some other HDD for its files. The problem is, because I have only experimented with one extra HDD in addition to the Grub MBR HDD, I don't know how the numbers correspond with more than one extra HDD; and also I've gotten what seems to be conflicting results from others. Thus "8005" would mean look at some HDD other than the one the Grub MBR is on, and look in partition (hdY,5) or the 6th partition (where Y is not zero, but 1, 2, etc). So the problem is I don't know Y, but if you have several HDDs to experiment with and you figure it out, let me know please. :)
[/LIST]
And really all the credit goes to Ubuntu forum member "meierfra." who figured out where the (hdX,Y) variables were stored in the MBR in the first place. He's the one who originally came up with that clever "dd" trick to find where the Grub MBR was looking for its files.

---

### Post by unutbu on 2008-09-04
Yes, meierfra.'s post ([http://ubuntuforums.org/showpost.php?p=5242287&postcount=4](http://ubuntuforums.org/showpost.php?p=5242287&postcount=4)) was very interesting!

Your post has spurred me on to do a little experiment. I'm not sure what to make of the results however.

I took two empty USB flash drives, and did "root (hd0,2)", "setup (hdX)" on both. 
The dd output I was expecting to see was
```

    00000000 2002
    00000002     
```

but instead each drive gave me something different!

```

darkm@ter:~% mount
...
/dev/sda3 on / type ext3 (rw,errors=remount-ro)
/dev/sdb1 on /media/disk type ext2 (rw,nosuid,nodev)
/dev/sdc1 on /media/disk-1 type ext3 (rw,nosuid,nodev)
darkm@ter:~% sudo fdisk -l
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x48000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2               8         660     5245222+   b  W95 FAT32
/dev/sda3   *         661       38536   304238970   83  Linux
/dev/sda4           38537       38913     3028252+   5  Extended
/dev/sda5           38537       38913     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 2004 MB, 2004877312 bytes
191 heads, 11 sectors/track, 1863 cylinders
Units = cylinders of 2101 * 512 = 1075712 bytes
Disk identifier: 0x000961c3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1864     1957887+  83  Linux

Disk /dev/sdc: 2048 MB, 2048728064 bytes
255 heads, 63 sectors/track, 249 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000af11

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         249     2000061   83  Linux

```
```
darkm@ter:~% sudo grub
Probing devices to guess BIOS drives. This may take a long time.

grub> root (hd0,2)

grub> setup (hd1)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd1)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,2)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 d (hd1) /boot/grub/stage2 p /boot/grub/menu.lst "...
succeeded
Done.

grub> root (hd0,2)

grub> setup (hd2)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd2)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 d (hd2) (hd2)1+17 p (hd0,2)/boot/grub/stage2 /boot/gr
ub/menu.lst"... succeeded
Done.
```
```

darkm@ter:~% sudo dd if=/dev/sdb bs=1 skip=1049 count=2 | hexdump
2+0 records in
2+0 records out
2 bytes (2 B) copied, 0.00330255 seconds, 0.6 kB/s
0000000 0000                                   
0000002
darkm@ter:~% sudo dd if=/dev/sdc bs=1 skip=1049 count=2 | hexdump
2+0 records in
2+0 records out
0000000 8002                                   
0000002
2 bytes (2 B) copied, 0.00489244 seconds, 0.4 kB/s

```
```
darkm@ter:~% sudo dd if=/dev/sdb bs=512 count=1 | hexdump -C
1+0 records in
1+0 records out
512 bytes (512 B) copied, 3.0196e-05 seconds, 17.0 MB/s
00000000  eb 48 90 d0 bc 00 7c fb  50 07 50 1f fc be 1b 7c  |.H....|.P.P....||
00000010  bf 1b 06 50 57 b9 e5 01  f3 a4 cb be be 07 b1 04  |...PW...........|
00000020  38 2c 7c 09 75 15 83 c6  10 e2 f5 cd 18 8b 14 8b  |8,|.u...........|
00000030  ee 83 c6 10 49 74 16 38  2c 74 f6 be 10 07 03 02  |....It.8,t......|
00000040  80 00 00 80 14 43 e6 08  00 08 fa 90 90 f6 c2 80  |.....C..........|
00000050  75 02 b2 80 ea 59 7c 00  00 31 c0 8e d8 8e d0 bc  |u....Y|..1......|
00000060  00 20 fb a0 40 7c 3c ff  74 02 88 c2 52 be 7f 7d  |. ..@|<.t...R..}|
00000070  e8 34 01 f6 c2 80 74 54  b4 41 bb aa 55 cd 13 5a  |.4....tT.A..U..Z|
00000080  52 72 49 81 fb 55 aa 75  43 a0 41 7c 84 c0 75 05  |RrI..U.uC.A|..u.|
00000090  83 e1 01 74 37 66 8b 4c  10 be 05 7c c6 44 ff 01  |...t7f.L...|.D..|
000000a0  66 8b 1e 44 7c c7 04 10  00 c7 44 02 01 00 66 89  |f..D|.....D...f.|
000000b0  5c 08 c7 44 06 00 70 66  31 c0 89 44 04 66 89 44  |\..D..pf1..D.f.D|
000000c0  0c b4 42 cd 13 72 05 bb  00 70 eb 7d b4 08 cd 13  |..B..r...p.}....|
000000d0  73 0a f6 c2 80 0f 84 ea  00 e9 8d 00 be 05 7c c6  |s.............|.|
000000e0  44 ff 00 66 31 c0 88 f0  40 66 89 44 04 31 d2 88  |D..f1...@f.D.1..|
000000f0  ca c1 e2 02 88 e8 88 f4  40 89 44 08 31 c0 88 d0  |........@.D.1...|
00000100  c0 e8 02 66 89 04 66 a1  44 7c 66 31 d2 66 f7 34  |...f..f.D|f1.f.4|
00000110  88 54 0a 66 31 d2 66 f7  74 04 88 54 0b 89 44 0c  |.T.f1.f.t..T..D.|
00000120  3b 44 08 7d 3c 8a 54 0d  c0 e2 06 8a 4c 0a fe c1  |;D.}<.T.....L...|
00000130  08 d1 8a 6c 0c 5a 8a 74  0b bb 00 70 8e c3 31 db  |...l.Z.t...p..1.|
00000140  b8 01 02 cd 13 72 2a 8c  c3 8e 06 48 7c 60 1e b9  |.....r*....H|`..|
00000150  00 01 8e db 31 f6 31 ff  fc f3 a5 1f 61 ff 26 42  |....1.1.....a.&B|
00000160  7c be 85 7d e8 40 00 eb  0e be 8a 7d e8 38 00 eb  ||..}.@.....}.8..|
00000170  06 be 94 7d e8 30 00 be  99 7d e8 2a 00 eb fe 47  |...}.0...}.*...G|
00000180  52 55 42 20 00 47 65 6f  6d 00 48 61 72 64 20 44  |RUB .Geom.Hard D|
00000190  69 73 6b 00 52 65 61 64  00 20 45 72 72 6f 72 00  |isk.Read. Error.|
000001a0  bb 01 00 b4 0e cd 10 ac  3c 00 75 f4 c3 00 00 00  |........<.u.....|
000001b0  00 00 00 00 00 00 00 00  c3 61 09 00 00 00 00 00  |.........a......|
000001c0  02 00 83 be 0b f3 01 00  00 00 ff bf 3b 00 00 00  |............;...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
darkm@ter:~% sudo dd if=/dev/sdc bs=512 count=1 | hexdump -C
1+0 records in
1+0 records out
512 bytes (512 B) copied, 3.3755e-05 seconds, 15.2 MB/s
00000000  eb 48 90 8e d0 bc 00 7c  8b f4 50 07 50 1f fb fc  |.H.....|..P.P...|
00000010  bf 00 06 b9 00 01 f2 a5  ea 1d 06 00 00 be be 07  |................|
00000020  b3 04 80 3c 80 74 0e 80  3c 00 75 1c 83 c6 10 fe  |...<.t..<.u.....|
00000030  cb 75 ef cd 18 8b 14 8b  4c 02 8b ee 83 c6 03 02  |.u......L.......|
00000040  82 00 00 20 01 00 00 00  00 02 fa 90 90 f6 c2 80  |... ............|
00000050  75 02 b2 80 ea 59 7c 00  00 31 c0 8e d8 8e d0 bc  |u....Y|..1......|
00000060  00 20 fb a0 40 7c 3c ff  74 02 88 c2 52 be 7f 7d  |. ..@|<.t...R..}|
00000070  e8 34 01 f6 c2 80 74 54  b4 41 bb aa 55 cd 13 5a  |.4....tT.A..U..Z|
00000080  52 72 49 81 fb 55 aa 75  43 a0 41 7c 84 c0 75 05  |RrI..U.uC.A|..u.|
00000090  83 e1 01 74 37 66 8b 4c  10 be 05 7c c6 44 ff 01  |...t7f.L...|.D..|
000000a0  66 8b 1e 44 7c c7 04 10  00 c7 44 02 01 00 66 89  |f..D|.....D...f.|
000000b0  5c 08 c7 44 06 00 70 66  31 c0 89 44 04 66 89 44  |\..D..pf1..D.f.D|
000000c0  0c b4 42 cd 13 72 05 bb  00 70 eb 7d b4 08 cd 13  |..B..r...p.}....|
000000d0  73 0a f6 c2 80 0f 84 ea  00 e9 8d 00 be 05 7c c6  |s.............|.|
000000e0  44 ff 00 66 31 c0 88 f0  40 66 89 44 04 31 d2 88  |D..f1...@f.D.1..|
000000f0  ca c1 e2 02 88 e8 88 f4  40 89 44 08 31 c0 88 d0  |........@.D.1...|
00000100  c0 e8 02 66 89 04 66 a1  44 7c 66 31 d2 66 f7 34  |...f..f.D|f1.f.4|
00000110  88 54 0a 66 31 d2 66 f7  74 04 88 54 0b 89 44 0c  |.T.f1.f.t..T..D.|
00000120  3b 44 08 7d 3c 8a 54 0d  c0 e2 06 8a 4c 0a fe c1  |;D.}<.T.....L...|
00000130  08 d1 8a 6c 0c 5a 8a 74  0b bb 00 70 8e c3 31 db  |...l.Z.t...p..1.|
00000140  b8 01 02 cd 13 72 2a 8c  c3 8e 06 48 7c 60 1e b9  |.....r*....H|`..|
00000150  00 01 8e db 31 f6 31 ff  fc f3 a5 1f 61 ff 26 42  |....1.1.....a.&B|
00000160  7c be 85 7d e8 40 00 eb  0e be 8a 7d e8 38 00 eb  ||..}.@.....}.8..|
00000170  06 be 94 7d e8 30 00 be  99 7d e8 2a 00 eb fe 47  |...}.0...}.*...G|
00000180  52 55 42 20 00 47 65 6f  6d 00 48 61 72 64 20 44  |RUB .Geom.Hard D|
00000190  69 73 6b 00 52 65 61 64  00 20 45 72 72 6f 72 00  |isk.Read. Error.|
000001a0  bb 01 00 b4 0e cd 10 ac  3c 00 75 f4 c3 00 00 00  |........<.u.....|
000001b0  00 00 00 00 00 00 00 00  11 af 00 00 00 00 00 01  |................|
000001c0  01 00 83 fe 3f f8 3f 00  00 00 7a 09 3d 00 00 00  |....?.?...z.=...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```
I thought maybe fsck'ing /dev/sdb1 might make it behave, but it made no difference:

```
darkm@ter:~% sudo /etc/init.d/hal stop
 * Stopping Hardware abstraction layer hald
   ...done.
darkm@ter:~% sudo umount /dev/sdb1
darkm@ter:~% sudo umount /dev/sdc1
darkm@ter:~% sudo e2fsck -fvy /dev/sdb1
e2fsck 1.40.2 (12-Jul-2007)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
/lost+found not found.  Create? yes

Pass 4: Checking reference counts
Pass 5: Checking group summary information

/dev/sdb1: ***** FILE SYSTEM WAS MODIFIED *****

      11 inodes used (0.01%)
       1 non-contiguous inode (9.1%)
         # of inodes with ind/dind/tind blocks: 0/0/0
    4584 blocks used (0.94%)
       0 bad blocks
       1 large file

       0 regular files
       1 directory
       0 character device files
       0 block device files
       0 fifos
       0 links
       0 symbolic links (0 fast symbolic links)
       0 sockets
--------
       1 file
darkm@ter:~% sudo e2fsck -fvy /dev/sdc1
e2fsck 1.40.2 (12-Jul-2007)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

      11 inodes used (0.00%)
       1 non-contiguous inode (9.1%)
         # of inodes with ind/dind/tind blocks: 0/0/0
   16808 blocks used (3.36%)
       0 bad blocks
       1 large file

       0 regular files
       2 directories
       0 character device files
       0 block device files
       0 fifos
       0 links
       0 symbolic links (0 fast symbolic links)
       0 sockets
--------
       2 files
darkm@ter:~% 
```
```

grub> root (hd0,2)

grub> setup (hd1)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd1)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,2)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 d (hd1) /boot/grub/stage2 p /boot/grub/menu.lst "...
succeeded
Done.

grub> 
```
```

darkm@ter:~% sudo dd if=/dev/sdb bs=1 skip=1049 count=2 | hexdump
2+0 records in
2+0 records out
2 bytes (2 B) copied, 7.0136e-05 seconds, 28.5 kB/s
0000000 0000                                   
0000002
```

No change.

---

### Post by caljohnsmith on 2008-09-04
> **unutbu said:**
> 
[/CODE]
```
darkm@ter:~% sudo grub
Probing devices to guess BIOS drives. This may take a long time.

grub> root (hd0,2)

grub> setup (hd1)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
[COLOR="Red"] Running "embed /boot/grub/e2fs_stage1_5 (hd1)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,2)"... failed (this is not fatal)[/COLOR]
 Running "install /boot/grub/stage1 d (hd1) /boot/grub/stage2 p /boot/grub/menu.lst "...
succeeded
Done.

grub> root (hd0,2)

grub> setup (hd2)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 [COLOR="Red"]Running "embed /boot/grub/e2fs_stage1_5 (hd2)"...  17 sectors are embedded.
succeeded[/COLOR]
Running "install /boot/grub/stage1 d (hd2) (hd2)1+17 p (hd0,2)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.
```
```

darkm@ter:~% sudo dd if=/dev/sdb bs=1 skip=1049 count=2 | hexdump
2+0 records in
2+0 records out
2 bytes (2 B) copied, 0.00330255 seconds, 0.6 kB/s
0000000 [COLOR="Red"]0000[/COLOR]                                   
0000002
darkm@ter:~% sudo dd if=/dev/sdc bs=1 skip=1049 count=2 | hexdump
2+0 records in
2+0 records out
0000000 [COLOR="Red"]8002[/COLOR]                                   
0000002
2 bytes (2 B) copied, 0.00489244 seconds, 0.4 kB/s

```

What you got actually makes perfect sense I think. First of all, note that the command:
```
sudo dd if=/dev/sdb bs=1 skip=1049 count=2 | hexdump
```
Is not really looking in the MBR per se (the first sector of a HDD, or the first 512 bytes), but actually it is looking near the beginning inside the 3rd sector; i.e. the third sector begins at 1024, and we have dd looking at bytes 1050 and 1051 (dd starts at 1049+1). So we are actually reading inside the stage1_5 file that usually gets embedded into the sectors immediately after the MBR. 

But for some reason, your sdb drive didn't allow Grub to embed its stage1_5 (see the error you got above), so Grub instead just had the MBR point to its stage2 file in the same partition where its menu.lst and stage2 files are. In fact, that is always what happens when you install Grub to a PBR (partition boot record) rather than the MBR; Grub installs only to the boot sector of the partition and points to its stage2 file in the partition that you specified with "root (hdX,Y)". So I'm not sure why Grub didn't install its Grub stage1_5 file while you installed Grub to the MBR of sdb. 

Bottom line though, is that "dd" command gave bogus information for sdb because the stage1_5 was not in the sectors immediately following the MBR. Yet for sdc, where the stage1_5 file installed correctly, the dd output was exactly what I would expect: 8002, or HD(Y,2). 

How about trying this experiment: you can try to force Grub to install its stage1_5 file for sdb with:
```
grub> root (hd0,2)
grub> install /boot/grub/stage1 d (hd1) (hd1)1+17 p /boot/grub/stage2 /boot/grub/menu.lst
```
Give that a try and let me know what you come up with. :)

---

### Post by smusevic on 2008-09-04
> **caljohnsmith said:**
> Actually the "ff02" means that the Grub MBR points to the 3rd partition on the same HDD (which happens to be (hd1)), so "ff02" is exactly what you want.

Thanks for clarifying this. It opens further question, though (already discussed here).
> **caljohnsmith said:**
> 
So are you sure you have your BIOS set to boot the Ubuntu HDD first?
Yes, I'm sure. If I change boot order (eg: sda, sdb instead of sdb, sda), than XP boots normally from first disk.
> **caljohnsmith said:**
> And when you say you get Grub error 17, is that before you get a Grub menu on start up, or after you select Ubuntu/Windows?
Sorry, not the case. ERROR 17 appears immediately after boot, the list does not appear yet.
> **caljohnsmith said:**
> I would guess it is the latter case, because you need to change your Ubuntu/Windows entries in your menu.lst. The point of confusion I think is that Grub considers which HDD is first in the boot order to be (hd0). So if you boot your Ubuntu HDD first on start up, then your Ubuntu entries in menu.lst should be (hd0,2) and not (hd1,2). And then your Windows is considered to be on (hd1,0) instead of (hd0,0). So bottom line, try changing your menu.lst as follows, and I think you should be all set:
```
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		[COLOR="Blue"](hd0,2)[/COLOR]
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=b8a5c053-1fd6-4013-a75a-4d1e4fdd70ba ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		[COLOR="Blue"](hd0,2)[/COLOR]
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=b8a5c053-1fd6-4013-a75a-4d1e4fdd70ba ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		[COLOR="Blue"](hd0,2)[/COLOR]
kernel		/boot/memtest86+.bin
quiet
```
Let me know how it goes.

Changed menu.lst as described, invoked grub ( root(hd1,2), setup (hd1) ), did the 'dd' thing (returned "ff02"), had a bad feeling that nothing would change, restarted, nothing changed :mad: ...
Still ERROR 17 before list (FYI list does not appear). I even commented out all entries, pointing to XP partitions, so only the 3 ubuntu entries were left. I have this feeling, that whatever I do has no effect.

Thoughts:
When I run grub from LiveCD and I invoke setup(hd1) it responds:
```

.
.
.
Running "install /boot/grub/stage1 (hd1) (hd1)1+16 p (hd1,2)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
.
.
.

```
But when the I mount the hd1,2 partition, it is accessible at /media/disk/, so the file /boot/grub/menu.lst is actually wrong, it should be /media/disk/boot/grub/menu.lst, right? Note that first line contains (hd1,2)/boot/grub/stage2 which seems reasonable (probably translates to /media/disk/boot/grub/stage2) so the second should read: (hd1,2)/boot/grub/menu.lst...succeeded
Right?  :confused:

I once accidentally interrupted the grub loader with ESC or DEL or something and some mysterious console appeared...Cannot repeat it though...Maybe I could fix it from there?

I'm just wondering: is it really SO hard to write a reasonable boot utility that would just fix all this problems!?!

---

### Post by meierfra. on 2008-09-04
> I don't know how the numbers correspond with more than one extra HDD; and also I've gotten what seems to be conflicting results from others. Thus "8005" would mean look at some HDD other than the one the Grub MBR is on, and look in partition (hdY,5) or the 6th partition (where Y is not zero, but 1, 2, etc). So the problem is I don't know Y, but if you have several HDDs to experiment with and you figure it out, let me know please

I just did an experiment with 4 hard drives and six different linux OS's.  According to my experiment

root (hdx,y)
setup (hdz)

gives 

8x0y  if  x and z are different.

and

ff0y   if x=z

(but  for a couple of my linux OS's I'm using the stage files from the supergrub disk. For these OS's I  always got "312e". So it seems the supergrub stage  files store the partition information in a different location)

---

### Post by caljohnsmith on 2008-09-04
> **meierfra. said:**
> I just did an experiment with 4 hard drives and six different linux OS's.  According to my experiment

root (hdx,y)
setup (hdz)

gives 

8x0y  if  x and z are different.

and

ff0y   if x=z

(but  for a couple of my linux OS's I'm using the stage files from the supergrub disk. For these OS's I  always got "312e". So it seems the supergrub stage 2 files stores the partition information in a different location)
Thanks so much for sharing those results, meierfra; that clears up all my confusion regarding the results of that dd command for multiple HDDs. :) But unfortunately we're still stuck not knowing what Z is when Z does not equal X. 

I'm curious about the results with the Super Grub Disk; have you looked at the stage1_5 file that Super Grub embeds after the MBR in a Hex editor? For a stage1_5 file that's not embedded using Super Grub, that "skip=1049" in the dd command puts you right at a point in the stage1_5 file where it says "/boot/grub/stage2 /boot/grub/menu.lst" in ascii. So have you by chance looked in the same place (preceding that ascii string) in a Super Grub embedded stage1_5 file? It may not exactly be byte 1050 and 1051, like your dd command assumes.

---

### Post by caljohnsmith on 2008-09-04
> **smusevic said:**
> 
But when the I mount the hd1,2 partition, it is accessible at /media/disk/, so the file /boot/grub/menu.lst is actually wrong, it should be /media/disk/boot/grub/menu.lst, right? Note that first line contains (hd1,2)/boot/grub/stage2 which seems reasonable (probably translates to /media/disk/boot/grub/stage2) so the second should read: (hd1,2)/boot/grub/menu.lst...succeeded
Right?  :confused:

No, I think the /boot/grub/menu.lst is correct; Grub works in its own world regardless of whether you have that partition mounted or not, and regardless of the mount point. :) In other words, Grub is dealing directly with the partition, and does not care whether it is mounted or not.

Since it seems like Grub is installed to your Ubuntu HDD exactly the way it should be, I suspect you may have a problem with your partition table. Try booting a Live CD and doing the following:
```
sudo apt-get install testdisk
sudo testdisk
```
In the testdisk screen, choose "create log", select HDD and "proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give. If it returns any errors, you can use testdisk to fix your partition table. Let me know if it returns any errors.

---

### Post by meierfra. on 2008-09-04
> **caljohnsmith said:**
> But unfortunately we're still stuck not knowing what Z is when Z does not equal X. 

sudo dd if=/dev/device_name_of_hdz  bs=1 skip=64 count=1 | hexdump

will return

008z         if x and z are different and  the stage1.5 files are used;

008x        if x and z are different and  the stage1.5 files are not used;

and

00ff         if x=z


> I'm curious about the results with the Super Grub Disk

I had a short look at the embedded stage1.5 Super Grub files, but was not able to figure out what was going on.


Edit: Figured it out:

Just before the partition information, comes the version string for grub: "0.97". Supergrub uses "0.97-os.1" instead.  This pushes back the partition information by 5 bytes, So one needs to use

```
 sudo dd if=/dev/sdb bs=1 skip=1054 count=2 | hexdump
```
for supergrub.

---

### Post by unutbu on 2008-09-04
Here is a script which attempts to determine the "controlling partition" -- that is, the partition containing the stage2 file (and menu.lst) that stage1.5 hands-off to during the boot process.

Credit goes to [meierfra.]("http://ubuntuforums.org/member.php?u=552151") for crafting the tests implemented in the script and which he describes here:

[http://ubuntuforums.org/showpost.php?p=5242287&postcount=4](http://ubuntuforums.org/showpost.php?p=5242287&postcount=4)
[http://ubuntuforums.org/showpost.php?p=5727176&postcount=26](http://ubuntuforums.org/showpost.php?p=5727176&postcount=26)
[http://ubuntuforums.org/showpost.php?p=5727778&postcount=29](http://ubuntuforums.org/showpost.php?p=5727778&postcount=29)

Save the script as meierfra.py
```

#!/usr/bin/env python

"""
Credit goes to meierfra. (http://ubuntuforums.org/member.php?u=552151)
for crafting the tests implemented in the script and which he describes here:

http://ubuntuforums.org/showpost.php?p=5242287&postcount=4
http://ubuntuforums.org/showpost.php?p=5727176&postcount=26
http://ubuntuforums.org/showpost.php?p=5727778&postcount=29
"""

import subprocess
import sys

try:
    device_name=sys.argv[1]
    device_name=device_name[0:3]
except IndexError,err:
    print "Usage: meierfra.py sdX"
    exit()

proc = subprocess.Popen(\
    'sudo dd if=/dev/%(device_name)s bs=1 skip=1049 count=2 2>/dev/null| hexdump'%locals(), 
    shell=True, stdout=subprocess.PIPE, )
try:
    magic = proc.communicate()[0].split()[1]
except IndexError:
    print "Unrecognized bootloader"
    exit(1)

proc = subprocess.Popen(\
    'sudo dd if=/dev/%(device_name)s bs=1 skip=64 count=1 2>/dev/null| hexdump'%locals(), 
    shell=True, stdout=subprocess.PIPE, )
try:
    moremagic = proc.communicate()[0].split()[1]
except IndexError:
    print "Unrecognized bootloader"
    exit(1)

def decipher(magic,moremagic):
    data={}
    data['z']=ord(device_name[2])-97
    data['y']=int(magic[3],base=16)
    if moremagic.startswith('00ff'):
        data['x']=data['z']
    elif moremagic.startswith('008'):
        data['x']=int(magic[1],base=16)
    return data

data=decipher(magic,moremagic)
print "root (hd%s,%s)"%(data.get('x','?'),data.get('y','?'))
print "setup (hd%s)"%data.get('z','?')

```

Make it executable:
```

chmod 755 meierfra.py
```
Run it like this:
```

./meierfra.py sda
```
The output are the grub commands that would have produced the bootloader found on /dev/sda:
```

root (hd0,2)
setup (hd0)

```

Please test and notify me if there are any errors.

CHANGELOG
2008-09-04: converted hexadecimals to decimals in the output

---

### Post by caljohnsmith on 2008-09-04
That's awesome Unutbu that you put all of these crude Grub hacks into a script that does all the work for us! It worked perfectly on my computer, although at the moment I couldn't test it for the case of having the MBR point to a partition on another disk. I'm sure it works though for that case. Thanks for the great script! :)

---

### Post by meierfra. on 2008-09-04
> **unutbu said:**
> 
Please test and notify me if there are any errors.

I tested it and it worked just fine. Couple of comments:

I)  I had to run the script via  "./meierfra.py sda" (rather than "meierfra.py sda")

II)  After 

root (hd1,13)
setup (hd0)

the output of the script was 

root (hd1,d)
setup (hd0)

Note here that "d" is the hexadecimal for "13".

---

### Post by smusevic on 2008-09-05
> **caljohnsmith said:**
> 
```
sudo apt-get install testdisk
sudo testdisk
```

Hm...this didn't work from LiveCD, package not found.Anyway, found it somewhere, downloaded checked all partitions, no errors.

Then I noticed, that my Linux installation has 2 partitions: ext3 and swap. The ext3 seemed suspicious (should be ext2 right?), so I reinstalled ubuntu again, formatting the partition to ext2. Well, needles to say it came out worse than before: grub installed itself onto hd0, successfully overwriting the XP MBR, but failed with error 17 when booted, so I had nothing working at this point.

Had to run XP from CD, ran the Recovery Console, then FIXMBR, FIXBOOT...That overwrote the grub MBR with XP MBR, so now at least XP is working.

Played around with bios settings (after viewing [a post from AmericanYellow]("http://ubuntuforums.org/showthread.php?t=442945")), here is something weird:
Checking properties of hd1 (sdb) this is what I see:
...
Size: 33.000 MB
...
Now remember a part of fdisk -l printout, referring to hd1 (sdb):
```

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1044     8385898+   7  HPFS/NTFS
/dev/sdb2            1045        4325    26354632+   7  HPFS/NTFS
/dev/sdb3            4326        9235    39439575   83  Linux
/dev/sdb4            9236        9964     5855692+  82  Linux swap / Solaris

```
Summing up sizes of first two partitions and subtracting the little (always present) magic difference, we come down to roughly 33.000MB, which is what BIOS shows. To confirm that, I booted (now working) XP instance and checked capacities:

D: 8,00 GB
E: 25,13 GB

So, my BIOS cannot see the other 2 paritions of sdb: sdb3,sdb4 (ext2, linux swap, respectively)!!!
OK, the motherboard is old (date 8/19/2005 appears on boot), but I had Ubuntu working in this setup already!!!
To clarify: I had 3 HDDs in comp and Ubuntu working on one of them (not sure which disk, but grub handled XP,Linux multiboot perfectly). I unmounted 1 of then (to put it in USB box and use it on laptop) and while I was at it, I rearranged the order of remaining 2 disks (there was some mess with cables in case), which caused the situation I'm in. The 2 remaining HDDs are on secondary IDE, if that helps.

Thanx all!

---

### Post by smusevic on 2008-09-05
OK, this was a nasty one.
For the record: GRUB installed itself 100% OK: the menu.lst was correct from the start, no HDD order confusion. HDDs were all error free, partition table was also OK.

I have an old motherboard, so when BIOS was set up to autodetect HDD geometry, for some reason it detected only 33GB...The key moment was this info:
```

ubuntu@ubuntu:~$ sudo fdisk /dev/sdb

The number of cylinders for this disk is set to 9964.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

```
So, BIOS HDD size autodetect was way off, but somehow it was exactly the same as first two partitions combined :confused:
Anyway, disabled the autodetect, I overwrote the size and everything was fine.

THANKS A MILLION....
This is almost like having PRO support...:)
Cheers, Sash

---

### Post by unutbu on 2008-09-05
smusevic, I'm really glad to hear you've solved the problem! And thanks very much for taking the time to post the solution. At every step of the way you've given very clear and detailed information about what you tried and the result. Hopefully, that will help us recognize this problem quicker in the future.

---

