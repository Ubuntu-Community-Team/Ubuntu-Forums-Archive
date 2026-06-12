---
title: "Ubuntu 12.04 on SSD.  partitioning,TRIM support help"
date: 2012-07-18
forum: Hardware
---

### Post by deepclutch on 2012-07-18
Hi,

I bought a 180GB Intel 330 series SSD. want to install Ubuntu 12.04 in SSD.
 I have a hard drive already. 
so, can SSD users help Me with SSD partitions? 

what to do with new SSD partition table? 
which partition table is to be used? MSDOS or GPT?
BTW, I've a DH67CL board with standard BIOS(not efi) and will install Windows 7 later. since Mine motherboard doesn't have a EFI BIOS, will it be a option to  use GPT partition table? Can I dual boot with Windows 7 with GPT?

regarding disk partitioning, I think a separate / partition of 15GB and /home of 40-50GB enough?

Will I place Swap partition on SSD or HDD? 

and lastly, You have to enable TRIM support for SSDs right? Please explain what to do.

Thanks in Advance,
dc

---

### Post by papibe on 2012-07-18
Hi deepclutch.

> **deepclutch said:**
> 
what to do with new SSD partition table? 
which partition table is to be used? MSDOS or GPT?
I would recommend MBR (MSDOS).

> **deepclutch said:**
> 
BTW, I've a DH67CL board with standard BIOS(not efi) and will install Windows 7 later.
If you can, I suggest partition the disk first with Live CD/Gparted, then install Windwows7 and lastly install Ubuntu. It is a little more easy that way.


> **deepclutch said:**
> 
regarding disk partitioning, I think a separate / partition of 15GB and /home of 40-50GB enough?
Sounds reasonable.

> **deepclutch said:**
> 
Will I place Swap partition on SSD or HDD? 
This is more debatable. Read this [guide]("https://help.ubuntu.com/community/SwapFaq/"). If you have enough RAM and you are not concern with hibernation, you can even go without swap just fine.


> **deepclutch said:**
> 
You have to enable TRIM support for SSDs right? Please explain what to do.
Yes, AFAIK it as post installation step. You basically add a mount option to the mount table. Read about it [here]("http://askubuntu.com/questions/18903/how-to-enable-trim").

I hope that helps, and let us know how it goes.
Regards.

---

### Post by deepclutch on 2012-07-18
Thank You @papibe for the answers. 
Another doubt, I read SSDs required proper partition alignment? Is there any resources available on this.

Thanks Again,
DC

---

### Post by oldfred on 2012-07-18
New partitioning tools in the last year or two align correctly. I normally download newest gparted or use gparted from newest Ubuntu liveCD. Windows defaults to 2048 as first sector or 1MiB boundry.

srs5694's to show 8 sector alignment post #9
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)

First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment - post 8
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)

I do not install Windows on SSD, so I use gpt with BIOS. But Windows only boots from gpt with UEFI. So if you want Windows you have to use MBR(msdos) partitioning as papibe states.
Do SSD need customization?
[http://ubuntuforums.org/showthread.php?t=1981478](http://ubuntuforums.org/showthread.php?t=1981478)
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)

You still need discard for trim and noatime to reduce writes. You can also use ext4 but turn journal off. I think that was about all I actually did. If using any newer version of gparted you should have alignment or first partition starts at sector 2048 and all partition starts are divisible by 8.

---

### Post by deepclutch on 2012-07-19
I am slowly figuring out all these info about partition alignment.

So, "Erase Block Size" needs to be known for  partition/file system alignment?

I searched for Intel 330 SSDs(Mine is 180GB) and there is no information available.

330 SSD specs shows:
> 
— Intel® 25nm NAND Flash Memory
— Multi-Level Cell (MLC)


---

### Post by oldfred on 2012-07-19
I think if you just use the new default with gdisk or gparted of 2048 as the start and 1MiB then you have no issues.

[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
> If choosing to start on a sector before the 2048th gdisk will  automatically shift the partition start to the 2048th disk sector. This  is to ensure a 2048-sectors alignment (as a sector is 512B, this is a  1024KiB alignment which should fit any SSD NAND erase block). 

---

