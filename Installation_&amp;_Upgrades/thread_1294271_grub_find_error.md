---
title: "grub find error"
date: 2009-10-18
forum: Installation &amp; Upgrades
---

### Post by ottosykora on 2009-10-18
I am unable to boot my ubuntu 9.04 any more.

Grub menu is displayed, win XP can be booted, the memtest too, but not ubuntu, it says file not found

Tried suppergrub disk, but each time it wants to boot or to change something, the pc does reboot.

Tried some ubuntu live CD.
in grub, find /boot/grub/stage1
returns
Floating point exeption (core dumped)

any idea how to restore the grub from here?

---

### Post by ottosykora on 2009-10-18
in addition to above, also there seems to be some kind of mess in the still existing grub menu.lst
I shoudl edit it, but how?
I tried from the grub at begining itself, going 'e' for edit, well I can edit, but how to save the changes?

---

### Post by bulldog on 2009-10-18
If you have a live cd which you can use to boot from,you can edit the menu.lst.
But I would ask what is the course of this behavior?
Did you make changes to your system or what?

The changes you make with the 'e' are just for one time and won't be saved.

---

### Post by ottosykora on 2009-10-18
>But I would ask what is the course of this behavior?
Did you make changes to your system or what?<

yes, that means I did install second linux, in next ext3 partiton, debian leny.
When it came to grub, I thought it should be this time stored in the actual root partition, but the debian installer said failed and wanted to install it to mbr. OK I let it go.
But from that on all beacme corrupt apparently.
The grub disk does not work any more, system reboots each time it arrives at selection of some partition.

>The changes you make with the 'e' are just for one time and won't be saved<
but how to use it then? I mean I want just make small change to one line so I can try booting with it. But this seems not to be possible.

---

### Post by bulldog on 2009-10-18
If you want to use the 'e' within GRUB edit the line to what you want it to be,and hit the 'b' for boot key.
If the parameters are set as they should be,linux should boot.
Than you can 'gedit' the menu.lst to what it should be,to make it more permanent.


Edit:
I'm not sure what the floating point exeption means,it could be that there's something wrong with the partitions.
I would suggest to boot from the live cd and copy the output of the ```
sudo fdisk -l
``` command performed in a terminal
to the forum.

---

### Post by ottosykora on 2009-10-18
>f you want to use the 'e' within GRUB edit the line to what you want it to be,and hit the 'b' for boot key.
If the parameters are set as they should be,linux should boot.<
Oh I see! This clear nw.

>Than you can 'gedit' the menu.lst to what it should be,to make it more permanent.<
actually I used the more crude method, booted from live cd, sudo chmod to max on the list , edited and restored the rights as they were. The system complained that it was not able to update the backup list, so edited this one as well.
Strange: the entries were with kernel ...-11 and I have now -15 and deinstalled the previous -11 before I did all other work. And the menuwas then correct. After playing with the debian, this went by some accedent back to -11 kernel.
After correcting the list, I was able to use the known find-root-setup procedure on the grub. The fail was apparently just because there was no entry for known kernel in the list.
Since all the automatic procedures on the grub supperdisk will ceratinly start with find.. , this was the crash and reboot probably from the grub disk.

---

### Post by bulldog on 2009-10-18
If I understand you correctly,it works again?
Just the wrong kernel in menu.lst?

---

### Post by ottosykora on 2009-10-18
> **bulldog said:**
> If I understand you correctly,it works again?
Just the wrong kernel in menu.lst?

yes correct.

what does exactly cause this scary problem I am not sure. But any attempts to run any of the grub recovery schemes known to me failed first. The list had previous kernel in it only but this one was deinstalled earlier and the grub did work in this configuration (was holding correct kernel name).

After install atempt of the debian this did probably pick some bak of the menu.lst or what, no idea, but entry was wrong. Having only one linux entry pointing to kernel not existig.

After edit of the list to the correct kernel name, all problems left, also the grubdisk and other things work.

It could be, that the find command looks for the stage1, but also checks somehow the plausibility of the finding and crashes when all points to kernel not present.

can this be so?

---

### Post by ottosykora on 2009-10-18
BTW:

when I try to install second linux version, I should selct to instal the grub into the root partition of that system righ?

Then run grub update from ubuntu and all is clean?

---

### Post by bulldog on 2009-10-18
I never used a SuperGrub disk so I can't tell you how it works.
It's most likely that your debian install has messed up things,you should keep in mind that every distro wants to install it's own bootloader and keep this in it's own file system.
It only should display the other OS's installed,but menu.lst which will be in use,should be on the latest installed distribution.

Edit:
I would suggest to install GRUB in the MBR of the hdd,so it overwrite the 'old' GRUB.
The new GRUB would be the one from the latest install and should display all other OS's,but as said,
it is in /boot/grub from the debian install,not the ubuntu install.although your menu.lst in ubuntu still exist
it will not be in use.

---

### Post by ottosykora on 2009-10-18
and now comes the worst:

after one boot to ubuntu and one boot to windows, stange things happen again.
again the find command gives floating point exeption and the brub disk crashes.

what as next? how to fix the grub when it is not possible to run its normal things to do?

is there some way to reinstall the grub completely?

from the grub menu the command root and setup work, the find one not.

---

### Post by bulldog on 2009-10-18
Look for a menu.lst in your debian install.
If not present,we can re-install GRUB from the live cd.

---

### Post by ottosykora on 2009-10-18
> **bulldog said:**
> Look for a menu.lst in your debian install.
If not present,we can re-install GRUB from the live cd.

the debian which did cause this all is not any more present, the partition formated.

The reinstall, or repair was done under live cd.

---

### Post by bulldog on 2009-10-18
I'm a little lost here :)
What is going wrong and how did you reinstall GRUB.
When reinstalling GRUB it should find the boot partition and it should not list non existing kernels or whatever.
To reinstall GRUB from the live cd:
```
sudo grub
```
This will return a location which you have to use in the next command.
```
find /boot/grub/stage1
```
Enter the location given by the previous command in the next command. 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr
```
setup (hd0)
```
Exit the grub shell
```
quit
```
Now Grub will be installed to the mbr.
If you have done this,no need to do it again of course.

---

### Post by ottosykora on 2009-10-18
>find /boot/grub/stage1<

does definitely not work, floating point error

there rest does work, but after one reboot again problem with grub.```
sudo update-grub
[sudo] password for otto: 
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... found: (hd0,12)/boot/grub/splashimages/menu-sta.xpm.gz

Found kernel: /boot/vmlinuz-2.6.28-15-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... Updating the default booting kernel
done

```


and now all starts behavong differently again:
```
grub> find /boot/grub/stage1

Error 15: File not found

grub> root (hd0,12)

Error 21: Selected disk does not exist

grub> setup (hd0)

Error 12: Invalid device requested

grub> 

```

---

### Post by ottosykora on 2009-10-18
now on next instance, same ubuntu :```
grub> root (hd0,12)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,12)/boot/grub/stage2
 /boot/grub/menu.lst"... succeeded
Done.

grub> 

```

but when I try again find:

```
grub> find /boot/grub/stage1Floating point exception
otto@laptopottos4:~$ 
```

---

### Post by bulldog on 2009-10-18
Hmm,I think that there's more wrong with your computer,and GRUB is innocent.
Maybe you'll have to check your hdd and/or  it's cable work and power.
If the hdd isn't found by GRUB,you definitely should have a look in the BIOS if the hdd is displayed on a correct manner.

Edit:
That floating point error is something I don't understand.
Maybe GOOGLE has more to say to it,I definitely have not.
All started after a debian install which should not be such a big problem.
It shouldn't mess with any existing install and only GRUB install failed at that point.
Just re-install GRUB and you should be fine,if not I have no answer to it.

---

### Post by ottosykora on 2009-10-18
well all is new, hd is new installation too. had no problems until the debian.

Tried again from the live cd ubuntu 8.10. Same.

```
grub> find /boot/grub/stage1Floating point exception (core dumped)
ubuntu@ubuntu:~$ 

```

The ubuntu itself does light up an icon reporting crash.

I just wonder, is there a way to reinstall the whole grub, not just its bit in mbr?

I mean the whole thing is still in that partition, all its parts are not replaced, only the small mbr part. Can all inside the grub folder be replaced smehow?

---

### Post by ottosykora on 2009-10-18
when doing setup from the live cd

```
grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,12)/boot/grub/stage2
 /boot/grub/menu.lst"... succeeded
Done.

grub> 

```

tells me ok, but it is not. so how can I reinstall and overwrite it all without having to reinstal ubuntu completely?

---

### Post by bulldog on 2009-10-18
Only the stage1 is someway corrupted,the rest is just fine.
You don't have a separate /home I presume?

But anyway I wouldn't know how to replace the stage1 or whole GRUB from an install cd,without re-installing,sorry for that.

The quickest way to resolve things is to re-install,but maybe you will wait till some one else comes by with new ideas.

If you do a new install,take some things in mind.
If you're gonna repartition anyway just think about somethings to do different.
Make two or three primary partitions 6-10GB each.
Make a swap partition 1-2GB
Make a /home partition
And if your hdd is big enough maybe a data partition can be handy too.

The first partitions you can use by installing different distro's without messing around with gparted all the time,only choose manual when the partition editor comes up when installing.
Mount the system partition as / and set it to format ext3
Mount swap as swap
Mount /home as /home and just format it once, when empty, to ext3 
You need just one swap file for all the distro's
Your /home will keep all your personal data and the hidden files for ubuntu.
You can copy all the data you'll need between two ubuntu's or what ever.
Only keep in mind to use different user-names and passwords for different distro's,so they get there own folder in your /home.

This makes a re-install or trying out some other distro so much easier.

>tells me ok, but it is not. so how can I reinstall and overwrite it all without having to reinstal ubuntu completely?<
It's only telling you it exist,not of it's corrupted.

---

### Post by ottosykora on 2009-10-19
hi bulldog

just FYI
I was abt to format all and start from zero. Then just run fsck from boot cd on the ubuntu partition and thereafter run the repair version of ubuntu (second line in grub) and from there update grub.
Now again all works fine, the find command of grub does  not crash any more, the stage1 seems to be fixed too, supperdisk works with all features too.

it was more the fsck reapiring something rather then the grub feature, but anyway.

OK will now make images of the partitions and see what will happen on next attempt to install debian....

---

