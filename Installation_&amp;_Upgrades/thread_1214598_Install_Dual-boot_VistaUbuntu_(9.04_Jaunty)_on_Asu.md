---
title: "Install Dual-boot Vista/Ubuntu (9.04 Jaunty) on Asus notebook/laptop"
date: 2009-07-16
forum: Installation &amp; Upgrades
---

### Post by beesblaas on 2009-07-16
I managed to successfully install Ubuntu as a dual boot so I'm posting this so that others can learn from my mistakes.

My laptop is Asus pro50 series, PRO50Z, AMD Athlon X2 Dual-Core QL-62, 2Gb mem, 250Gb disk,Comes with Vista pre-installed. 
(it is an obscure new model nr, bought jul 2009, maybe similar to F5Z or X50Z F50Z ?) 

a)
First of all I burnt an Ubuntu disk and booted from it without installation to see if the laptop could run Ubuntu, it was OK.

b)
I then used the Vista tool to defragment its disk.

Note: The laptop comes shipped with 3 partitions: Recovery (11Gb), C: Vista (116Gb), D: data (104Gb)

This site has all the info for a full manual defrag using Vista:
[http://www.howtohaven.com/system/vistadefragmentation.shtml](http://www.howtohaven.com/system/vistadefragmentation.shtml)
The command is:defrag c: -v -w

c)
I then used the Vista tool to shrink the Vista partition.
(because I wanted to have Ubuntu on part of the C: drive, not on the D: drive)
Right click on Computer > manage > disk management > click on partition, shrink volume

total size before shrink (119Gb)
size of available shrink space (34Gb)
enter the amount of space to shrink in Mb (34Gb - the maximum I could get)
total size after shrink (85Gb)

After the shrinking, I booted the laptop to make shure it was OK with new partition.

d) 
Ubuntu Installation First Try: (not good!):confused:
I then booted from Ubuntu install disk 9.04 the 64b version and did an install,
Note: for some reason the screen is dark during installation, due to install driver issues?.
I think I selected "use the largest continuous free space". I cant remember where it did the installation,
I think it used D although I wanted it to use the free space on C.
The PC booted fine into the new Ubuntu, then I tried booting it into Vista,
but here I ran into trouble. When the boot menu comes up, you have two options for Vista boot,
which represents the Vista recovery partition, and the Vista partition.
Both are labelled: "Windows Vista (loader)", refer /boot/grub/menu.lst
I selected the 1st, the recovery partition, which is wrong!
On boot, I got a full screen "ERROR", see [http://www.flickr.com/photos/world_eggplant/2892072661/](http://www.flickr.com/photos/world_eggplant/2892072661/)  
and thereafter the laptop could not boot into Ubuntu or Vista,
" can not open file c:\RECOVERY.DAT " and " grub error 22 "

Solution was as follows: I downloaded and burnt a bootable "super grub disk" below
[http://www.supergrubdisk.org/index.php](http://www.supergrubdisk.org/index.php)

and I booted from the supergrubdisk. It has many options. One of them allowed me to choose to boot into Vista, successfully, but I could not work out to make the boot fix permanent,
so eventually I chose an option to restore my MBR. So I now was back with Vista.

e)
2nd Try: Successfull installation:D
I booted from the Ubuntu installation disk
I decided to do a manual partition allocation of the free shrinked space on C for Ubuntu.
click on free space, new partition (logical), size 10000M, from beginning, ext3,  mount point = /
click on free space, new partition (logical), size 1000M, from beginning, swap area
click on free space, new partition (logical), size remain M, from beginning, ext3,  mount point = home

I completed the installation and booted into Ubuntu.
I then edited the /boot/grub/menu.lst file and commented out the 1st Vista boot option,
the one that boots into Vista recovery. (I dont want this to happen again!),
That left only the proper Vista boot option to be displayed.
I can now boot into both Vista & Ubuntu successfully.
I'm not sure what to do if I do need to recover Vista one day, but the laptop comes with a CD to do a complete re-install of Vista anyway.
The Vista boot options now looks as below in menu.lst:

===============================================================================
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
# title        Windows Vista (loader)
# rootnoverify    (hd0,0)
# savedefault
# makeactive
# chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista (loader)
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader    +1
=================================================================================

I'm very happy with Ubuntu, much faster than my Vista, I use it all the time.:P

---

### Post by ramnarayan on 2009-07-16
> **beesblaas said:**
> 
I completed the installation and booted into Ubuntu.
I then edited the /boot/grub/menu.lst file and commented out the 1st Vista boot option,
the one that boots into Vista recovery. (I dont want this to happen again!),
I'm not sure what to do if I do need to recover Vista one day, but the laptop comes with a CD to do a complete re-install of Vista anyway.
The Vista boot options now looks as below in menu.lst:


You can always boot into Linux re-edit the grub and un # the recovery option. In fact you can write you own text alongside the option so that no mistake is made

like "# title        Windows Vista (loader)"
could become
title        RECOVERY ONLY Windows Vista (loader)

or what ever you want.
```

===============================================================================
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
# title        Windows Vista (loader)
# rootnoverify    (hd0,0)
# savedefault
# makeactive
# chainloader    +1

```

check out this place for more help on grub 

[http://www.dedoimedo.com/computers/grub.html](http://www.dedoimedo.com/computers/grub.html)

> I'm very happy with Ubuntu, much faster than my Vista, I use it all the time.:P


nice

---

### Post by lisati on 2009-07-16
If you shrink a partition, the space freed up won't actually be associated with C: or D: (or whatever) until you define a new partition.

Have a look here: [http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)

---

