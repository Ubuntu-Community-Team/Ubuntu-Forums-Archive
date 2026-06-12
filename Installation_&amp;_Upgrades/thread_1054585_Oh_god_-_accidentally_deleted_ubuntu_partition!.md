---
title: "Oh god - accidentally deleted ubuntu partition!"
date: 2009-01-29
forum: Installation &amp; Upgrades
---

### Post by NEUR0M4NCER on 2009-01-29
I know this is probably futile, but i've jus made a big boo-boo. I was trying to set up a dual boot, Ubuntu first, then XP... there's three HDs in the PC, and I deleted the wrong partition - stupid, I know.

Is there any way of getting it back, or the files that were on it? Any way at all?





**********************************************************************************************************************************************

********* SOLVED! DO NOT DESPAIR IF YOU FIND THIS AND HAVE THE SAME PROBLEM! THANKS TO caljohnsmith FOR SAVING ME FROM MY G/F'S WRATH! ********

**********************************************************************************************************************************************

---

### Post by taurus on 2009-01-29
Hope this works for you, [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk).

---

### Post by NEUR0M4NCER on 2009-01-29
Well it looks like most of the data's still there - that's an amazing start! Thanks taurus. Next Q...

As it appears to be relatively intact, can I just copy the whole /home folder (or more even?) to one of the other disks, and then re-install - when that's done, just copy back the /home ?

Thanks again!

---

### Post by konungursvia on 2009-01-29
You can do that.

---

### Post by NEUR0M4NCER on 2009-01-29
Excellent!! Should I get *more* than just /home, or should I just stick with that?

---

### Post by NEUR0M4NCER on 2009-01-29
Also - I don't seem to be able to modify/copy/paste any of the files in GUI - do I need to use the terminal, and if so, how might I go about doing that?

---

### Post by caljohnsmith on 2009-01-29
You might not even have to copy your files, you might be able to recover the full partition. How about posting the results of the "deep scan" with testdisk, and let me know exactly which partitions listed are the ones you want to recover. We can work from there if you want.

---

### Post by NEUR0M4NCER on 2009-01-29
I'll get testdisk back up and running, but while I do that - when I ran testdisk previously, should that not have restored the partition, because I tried to boot from it, and got some OS error on boot. Might the deep scan get around that?

**oh, and thank-you so much for your offer of help - I wouldn't refer to myself as a new Linux user, but this is just a bit too scary to be flying by the seat of my pants, if you know what I mean**

---

### Post by caljohnsmith on 2009-01-29
Definitely the deep scan gives the most accurate results in my experience. How about running testdisk, but follow these directions: choose "No Log", select HDD and "Proceed", "Intel", "Analyze", "Quick search", Y/N depending on if you have any Vista partitions, hit enter to continue, and select "Deeper Search" so it does a deeper search, which could take a while. Please post the output of the screen that has the deep search results. Also, use your up/down arrow keys to select each partition listed in the deep search results, and press "p" to get a directory listing; please let me know exactly which partitions give you a directory listing, and of those partitions that give a directory listing, also let me know which partitions you want to recover. We can work from there if you want.

---

### Post by NEUR0M4NCER on 2009-01-29
I'm afraid I already chose "Log", but it's going through the "Deeper Search" now. There's actually only the main ext3 and the old swap partition on this drive, if that makes things any easier. All of my media is safe on a physically seperate disk (thank god, I don't know what i'd do if I lost *that*). The search is 45% done - i'll post the results when they're ready.


**oh, wait - I see. It detects older partitions as-well. Hm. I'll just have to have a look through the results.**

---

### Post by NEUR0M4NCER on 2009-01-29
Okay. So the first screen when scan is finished gives this:```

Disk /dev/sdb - 160 GB / 149 GiB - CHS 19457 255 63
     Partition               Start        End    Size in sectors
D HPFS - NTFS              0   1  1  8817 254 63  141661107
D Linux                    0   1  1 18706 254 63  300527892
D Linux                 8818   1  1 16406 254 63  121917222
D HPFS - NTFS          11624   0  9 19456 254 63  125837137
D Linux                16407   1  1 19017 254 63   41945652
D Linux Swap           18707   1  1 19456 254 63   12048687
D Linux Swap           19018   1  1 19456 254 63    7052472

```
Paritions that give a directory listing are: I was going to post the results, but if I just say that all of the partitions beginning with```

D Linux

```
give directories. The one I want is the first in the list,```

D Linux                    0   1  1 18706 254 63  300527892

```
It appears to have everything there, with the most recent dates.

---

### Post by caljohnsmith on 2009-01-29
OK, how about selecting the first Linux partition in the list (the one you want to recover), and using the right/left arrow keys, mark it with "*". Also select the second-to-last swap partition and mark it with "P" (might as well recover it as long as we're at it). Then select each of the other partitions and mark them all with "D". Press enter to get the next screen, and then write the new partition table. Once you are done, please post:
```
sudo fdisk -lu
sudo mount /dev/sda1 /mnt && ls -l /mnt
```
And change sda1 to be your linux partition if necessary, but most likely it will be sda1.

---

### Post by NEUR0M4NCER on 2009-01-29
Thanks for all this. Do I need to re-boot the LiveCD to get to the changes, or can I go ahead and issue the terminal commands now?

---

### Post by caljohnsmith on 2009-01-29
Try them now, and if fdisk or mounting the partition doesn't work, go ahead and reboot.

---

### Post by NEUR0M4NCER on 2009-01-29
Well without re-booting, I get:
```

ubuntu@ubuntu:~/testdisk-6.10/linux$ sudo fdisk -lu

Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders, total 240121728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6c136ec4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   240091424   120045681    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   300527954   150263946   83  Linux
/dev/sdb2       300528018   312576704     6024343+  82  Linux swap / Solaris

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00073bed

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63  2930272064  1465136001   83  Linux

```
and...
```

ubuntu@ubuntu:~/testdisk-6.10/linux$ sudo mount /dev/sda1 /mnt && ls -l /mnt
total 0

```

---

### Post by caljohnsmith on 2009-01-29
My mistake, please do:
```
sudo umount /mnt
sudo mount /dev/sdb1 /mnt && ls -l /mnt
```

---

### Post by NEUR0M4NCER on 2009-01-29
Cool.
```

ubuntu@ubuntu:~/testdisk-6.10/linux$ sudo umount /mnt
ubuntu@ubuntu:~/testdisk-6.10/linux$ sudo mount /dev/sdb1 /mnt && ls -l /mnt
total 116
drwxr-xr-x   2 root root  4096 2009-01-08 02:47 bin
drwxr-xr-x   3 root root  4096 2009-01-28 21:37 boot
lrwxrwxrwx   1 root root    11 2009-01-07 23:21 cdrom -> media/cdrom
drwxr-xr-x   4 root root  4096 2008-10-29 21:18 dev
drwxr-xr-x 141 root root 12288 2009-01-30 01:45 etc
drwxr-xr-x   3 root root  4096 2009-01-07 23:26 home
lrwxrwxrwx   1 root root    33 2009-01-08 02:52 initrd.img -> boot/initrd.img-2.6.27-11-generic
lrwxrwxrwx   1 root root    32 2009-01-07 23:33 initrd.img.old -> boot/initrd.img-2.6.27-7-generic
drwxr-xr-x  15 root root 12288 2009-01-29 09:59 lib
drwxr-xr-x   4 root root  4096 2009-01-09 17:22 lib32
lrwxrwxrwx   1 root root     4 2009-01-07 23:21 lib64 -> /lib
drwx------   2 root root 16384 2009-01-07 23:20 lost+found
drwxr-xr-x   3 root root  4096 2009-01-29 17:15 media
drwxr-xr-x   2 root root  4096 2008-10-20 12:27 mnt
drwxr-xr-x   2 root root  4096 2008-10-29 21:04 opt
drwxr-xr-x   2 root root  4096 2008-10-20 12:27 proc
drwxr-xr-x  14 root root  4096 2009-01-30 01:37 root
drwxr-xr-x   2 root root  4096 2009-01-09 17:22 sbin
drwxr-xr-x   2 root root  4096 2008-10-29 21:04 srv
drwxr-xr-x   2 root root  4096 2009-01-08 12:17 storage-0
drwxr-xr-x   2 root root  4096 2009-01-08 12:17 storage-1
drwxr-xr-x   2 root root  4096 2008-10-14 13:02 sys
drwxrwxrwt  14 root root  4096 2009-01-30 01:45 tmp
drwxr-xr-x  12 root root  4096 2009-01-08 02:29 usr
drwxr-xr-x  15 root root  4096 2008-10-29 21:28 var
lrwxrwxrwx   1 root root    30 2009-01-08 02:52 vmlinuz -> boot/vmlinuz-2.6.27-11-generic
lrwxrwxrwx   1 root root    29 2009-01-07 23:33 vmlinuz.old -> boot/vmlinuz-2.6.27-7-generic
-rw-r--r--   1 root root  2668 2009-01-08 02:09 xorg.conf.new

```

---

### Post by caljohnsmith on 2009-01-29
Looks like you're in business. :) How about doing:
```
sudo grub
grub> root (hd1,0)
grub> setup (hd1)
grub> quit
```
Then reboot, set your BIOS to boot your Ubuntu sdb drive, and let me know how far you get.

---

### Post by NEUR0M4NCER on 2009-01-29
Thanks for your help so far. re-installing grub seemed to go fine, so i'll re-boot, and have a muck around in the Bios. I'll post back a.s.a.p.

---

### Post by NEUR0M4NCER on 2009-01-29
OMFG i'm in!!!!
It all appears to be working fine!

You, sir, are a saviour. I'm a big guy, but i'm actually close to tears right now - seriously. Thank-you so much.

Last one: Is there any way of checking whether everything's *actually* all still there (is it FSCK or something?) or should I just count my lucky stars?

Thank-you again!

---

### Post by caljohnsmith on 2009-01-29
That's great news you booted into Ubuntu OK. :) Most likely everything is just fine, but if you want to do a file system check just to make sure, how about either booting your Live CD again or boot into recovery mode, and then do:
```
[ "$(mount | grep sdb1)" ] || sudo fsck -yCM /dev/sdb1
```
Anyway, I have to run now, but cheers and I'm really glad your Ubuntu partition turned out to be OK. :)

---

### Post by NEUR0M4NCER on 2009-01-29
Will do. Thanks *again*! Where the hell's the 'Thanks' button gone????

---

