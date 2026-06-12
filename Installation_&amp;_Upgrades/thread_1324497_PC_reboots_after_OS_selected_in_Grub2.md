---
title: "PC reboots after OS selected in Grub2"
date: 2009-11-12
forum: Installation &amp; Upgrades
---

### Post by nik. on 2009-11-12
Hi,

I've done a fresh install of mythbuntu 9.10 (64) on a second partition, to run alongside my mythbuntu 9.04 (32) install.

During the 9.10 install, Grub2 was installed on sda, and has picked up the existing and new versions of mythbuntu (sda5 and sda7 respectively).

Selecting 9.04 boots just fine, but selecting 9.10 reboots the PC almost instantly.

Both sda5 and sda7 are logical partitions inside an extended partition (sda3).  Also within sda3 is sda6, a swap partition.

I've tried upgrade-grub, but exactly the same thing happens.  I've checked the grub settings and they look correct (correct file locations and partitions).

Any idea what could cause the rebooting?
Is there anything else I need to do to the sda7 partition to make it bootable?

For info, the (recovery mode) menu option does exactly the same.

Any help would be appreciated!

Nik

---

### Post by darkod on 2009-11-12
I installed ubuntu 9.10 and it was rebooting just before the login screen. After really long search it turned out it's the video driver, I guess the one coming with ubuntu didn't like my card. I have integrated Radeon HD3200.

What worked for me:
1. Select recovery mode from grub menu (in your case for 9.10 too)
2. In the first following screen select "root with networking" to have internet
3. Install video driver package EnvyNG with:
sudo apt-get install envyng-core envyng-qt
4. Run in text mode with:
envyng -t
5. It will give you a menu offering installtion of Nvidia or ATI driver (also entries for removing drivers but I didn't do that).
6. Select the driver and it will download it itself.

You'll figure it out from there. :)
After the driver installation and the reboot I just selected Ubuntu (normal mode) and worked straight away.

---

### Post by nik. on 2009-11-12
> **darkod said:**
> I installed ubuntu 9.10 and it was rebooting just before the login screen. After really long search it turned out it's the video driver, I guess the one coming with ubuntu didn't like my card. I have integrated Radeon HD3200.

What worked for me:
1. Select recovery mode from grub menu (in your case for 9.10 too)
2. In the first following screen select "root with networking" to have internet
3. Install video driver package EnvyNG with:
sudo apt-get install envyng-core envyng-qt
4. Run in text mode with:
envyng -t
5. It will give you a menu offering installtion of Nvidia or ATI driver (also entries for removing drivers but I didn't do that).
6. Select the driver and it will download it itself.

You'll figure it out from there. :)
After the driver installation and the reboot I just selected Ubuntu (normal mode) and worked straight away.
That's interesting, I have the same integrated graphics chips, but I don't think it's the same problem. The reason being that my reboot happens almost immediately after I select 9.10.  The same happens when I select the recovery option, so I fail at step 1 of your instructions!

I can boot using the live CD (with no problems with the gfx drivers btw), but don't want to start messing about with graphics drivers if there's another reason - I spent long enough doing that with 9.04!

---

### Post by darkod on 2009-11-12
It seems you have another problem. Live CD was rebooting my PC too. Sorry.

---

### Post by jo-hannes on 2009-11-13
> **nik. said:**
> That's interesting, I have the same integrated graphics chips, but I don't think it's the same problem. The reason being that my reboot happens almost immediately after I select 9.10.  The same happens when I select the recovery option, so I fail at step 1 of your instructions!

I can boot using the live CD (with no problems with the gfx drivers btw), but don't want to start messing about with graphics drivers if there's another reason - I spent long enough doing that with 9.04!I have the same problem..

---

### Post by nik. on 2009-11-24
> **jo-hannes said:**
> I have the same problem..
Glad I'm not alone!

I wondered if my disk setup was confusing matters, so I restructured my drive to make my original Mythbuntu 9.04 install and swap partitions primary.  I then created a new primary partition sda1 (16GB) to install Mythbuntu 9.10 on.

I then reinstalled 9.10 and rebooted.  Grub2 shows the new install as well as the old 9.04 one, but the same problem exists - if I select Mythbuntu 9.10, the PC almost instantly reboots - if I select 9.04 it boots just fine. Seems like the problem could be in install rather than Grub itself?

 Just in case it helps, my motherboard is Gigabyte GA-MA78GM-S2H rev 1.1.

---

### Post by nik. on 2009-11-24
Some more info in case anyone can help:

On the off chance, I reinstalled Mythbuntu 9.10 again, this time with a separate /boot partition using ext3 instead of the now default ext4.  This made no difference ;-(

fdisk -l now shows this:

Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6f63e436

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          62      497983+  83  Linux
/dev/sda2            4178        6159    15920415   83  Linux
/dev/sda3            6160        6408     2000092+  82  Linux swap / Solaris
/dev/sda4              63        2054    16000740   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6d005db9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux


sda1 is the new /boot partition
sda2 is my existing Mythbuntu 9.04 install
sda3 is obvious
sda4 is my new Mythbuntu 9.10 install
sdb1 is for recordings

One other thing I tried earlier was to do a full apt-get upgrade, this made no difference other than wiping the 9.04 entry from my grub loader.

Any ideas what else is worth a try????

---

### Post by darkod on 2009-11-24
I'll go on a huntch, but according to some problems I've seen here on the forum usually dual booting with windows and one OS was not starting from grub.

You see that sentence, "Partition table entries are not in order"? That is suspicious.

Notice the start/end sectors. Your /dev/sda4 is actually second in order on the disk (starting from 63). I have seen problems like this with people having recovery/utility partition on their drive. The partition is usually at the back of the disk but labeled /dev/sda2. In those situations they have problems booting one OS from the menu. Maybe just coincidence but I think that message "not in order" is important.

That's why I always try to create partitions sequentially on the disk. Did you shrink your 9.04 to make room for 9.10? And that's why your latest partition, /dev/sda4 is actually before /dev/sda2?

---

### Post by nik. on 2009-11-26
Thanks for your continued help!

The drive has a long history of OS's so the layout had developed over time.  After your message I did some further reorganising and now have the following layout:

Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6f63e436

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          62      497983+  83  Linux
/dev/sda2              63        2044    15920415   83  Linux
/dev/sda3            2045        2293     2000092+  82  Linux swap / Solaris
/dev/sda4            2294        4285    16000740    5  Extended
/dev/sda5            2294        4285    16000708+  83  Linux

sda1 is my /boot partition
sda2 is my existing Mythbuntu 9.04 partition
sda3 is swap
sda5 is my new Mythbuntu 9.10 partition.

Everything is now nicely ordered on the disk, however the same problem persists.

Jo-hannes - what is your disk layout like, are there any parallels with mine?

Does grub write any logs I can look at?  Are there any other logs worth looking at?  dmesg looks like this:
$ more dmesg 
(Nothing has been logged yet.)

I've searched through the /boot and / drives and nothing has an update timestamp relating to the last boot attempt.

Any other suggestions???

---

### Post by darkod on 2009-11-26
After the reorganizing did you run sudo update-grub or tried to reinstall grub2?

In fact, using mythbuntu 9.04 your grub might still be grub1. In that case you need to take a look in /boot/grub/menu.lst because most probably partiton numbers won't match now. Unless you already did that.

And if you are running grub2 and update-grub doesn't help reinstalling grub2 to give it a chance to "understand" the new layout wouldn't hurt.

---

### Post by nik. on 2009-11-26
Yeah, sorry forgot to mention, as part of the re-org I had to delete the 9.10 partition, so I reinstalled it from scratch, which re-installed Grub2.  The 9.04 partition still boots ok via Grub2.

---

### Post by darkod on 2009-11-26
And I guess if you check /boot/grub/grub.cfg it will show correct menu entry for 9.10 too? Look around in the file and compare the entries for 9.04 and 9.10.
I really have no idea what would reboot it.

---

### Post by nik. on 2009-11-26
Hi darkod,

The 9.10 entry looks like this:

[FONT=Courier New]menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 52c43454-4cd2-474d-b354-12974951cff2
    linux    /vmlinuz-2.6.31-14-generic root=UUID=38c86689-52e5-43d4-99e9-9251f5abcf1b ro   quiet splash
    initrd    /initrd.img-2.6.31-14-generic
}[/FONT]


while the 9.04 looks like this:

[FONT=Courier New]menuentry "Ubuntu 9.04, kernel 2.6.28-16-generic (on /dev/sda2)" {
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 9250ddae-d22e-498d-953c-9a613358806e
    linux /boot/vmlinuz-2.6.28-16-generic root=UUID=9250ddae-d22e-498d-953c-9a613358806e ro quiet splash
    initrd /boot/initrd.img-2.6.28-16-generic
}[/FONT]

I'm guessing the different UUID in the search line (compared to the linux line) of the 9.10 entry is caused by me having a separate /boot partition?

If I remove the set quiet=1 line, I actually get this displayed momentarily before the reboot:
[FONT=Courier New]Booting a command list

[Linux-bzImage, setup=0x3400, size=0x3bef40]
[Initrd, addr=0x3786f000, size=0x780673][/FONT] 

Booting into 9.04 produces this as it starts up:
[FONT=Courier New]Booting a command list

[Linux-bzImage, setup=0x3**0**00, size=0x3**51570**]
[Initrd, addr=0x378**ae**000, size=0x7**41ec6**][/FONT] 

I'm guessing the differences are purely because it's using a different kernel?

I've also tried removing everything else different, but that has no noticeable effect.

---

### Post by darkod on 2009-11-26
How about if you comment out the following

```
#recordfail=1
        #if [ -n ${have_grubenv} ]; then save_env recordfail; fi
```

Those lines are different than compared with the 9.04 entry. You don't have to delete them I believe if you comment them out with # at the start of the line it ignores the rest. For a quick test. If it doesn't help just remove the # after.

---

### Post by nik. on 2009-11-27
I've deleted them and it makes no difference - they only get deleted for that session if you press 'e' in Grub.

Any other ideas?  I might try installing the 32 bit version and see if that works....

---

### Post by darkod on 2009-11-27
It all looks fine. Sorry, no ideas. :(

---

