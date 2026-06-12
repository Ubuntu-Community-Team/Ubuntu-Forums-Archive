---
title: "What is the latest with &quot;Grub error 17&quot;?"
date: 2008-11-10
forum: General Help
---

### Post by vinoloco on 2008-11-10
Hi all,

Is there any help for us poor Ubuntu users who suffer from the dreaded "GRUB error 17" on attempted bootup?

I've had two installations fall victim to this malady in the past six months and really don't enjoy/need/want to suffer the requisite "well, just re-install the whole OS" suggestions.  There has got to be a way out of this.  My latest install just gave me the error and I'm wondering if there is anything I can do to revive it.  Any help would be appreciated...

---

### Post by TeXtonyx on 2008-11-10
There are quite a few grub error 17 threads that were fixed without
reinstalling. One way to find them is to put grub error 17 into the
Ubuntu forum Search window at the top right of the page. One result:

[url]http://ubuntuforums.org/ [copy and paste into one line in browser]
showthread.php?t=970275&highlight=grub+error+17

The above thread had several pages of discussion.

---

### Post by caljohnsmith on 2008-11-10
Are you getting the Grub error 17 before you see a Grub menu, or before you see "Press ESC to see menu", or do you get the error after selecting Ubuntu from the Grub menu? 

If you can boot your Live CD, how about opening a terminal (applications > accessories > terminal), and post the output of:
```
sudo fdisk -lu
```
Also, for each of the drives fdisk lists, like sda, sdb, etc, please post the output of:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
```
So replace "sda" above with each of your drives. And finally, for each command above that returns "GRUB", please post:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] bs=1 skip=1049 count=2 2>/dev/null | hexdump
```
And replace sda with the drives that previously returned "GRUB". That will greatly clarify what your setup is like.

---

### Post by giuce on 2008-11-24
i have an error 17 message after selecting ubuntu (sda4 on my fdisk). here is what 'sudo fdisk -lu' put out in terminal off of a live-cd: 

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1ab4ee97

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    14893055     7445504   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *    14893056   112435183    48771064    7  HPFS/NTFS
/dev/sda3       112437247   467893124   177727939    f  W95 Ext'd (LBA)
/dev/sda4       467893125   488392064    10249470   83  Linux
/dev/sda5       112437248   426032256   156797504+   7  HPFS/NTFS
/dev/sda6       426043863   467893124    20924631   83  Linux
ubuntu@ubuntu:~$ 

help me

---

### Post by Herman on 2008-12-06
From the [GNU/GRUB manual]("http://www.gnu.org/software/grub/manual/grub.html")
> 17 : Cannot mount selected partitionThis error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB. **:) Hello **giuce, 
You have only one hard disk, and you are getting GRUB Error 17 when you are trying to boot Ubuntu, so probably you need to boot your live CD and run file system check.
You can use Gnome Partition Editor (GParted) in your Ubuntu Live CD or you can use a special live CD like [GParted -- LiveCD]("http://gparted.sourceforge.net/livecd.php"). 
Always leave your file systems unmounted until after the file system check, never try to run a file system check in a file system while it's mounted.

[LIST=1]
[*]Just boot your Live CD, open Gnome Partition Editor and right-click on the partition you want checked. In Hardy Heron it is 'System-->'Administration'-->'Partition Editor'.
[*]Select 'check' from the right-click menu. If 'check' is greyed out you might need to select 'unmount first, then click 'check'.
[*]Click the 'Apply'  check mark button up on the toolbar.
[*]Click the 'Apply' button in the confirmation pop-up window
[*]Watch the reciprocating bar for a few minutes, a very large file system may take a while
[*]Click on the 'Details' triangle to expand the window
[*]Click on the triangle in front of 'Check and repair filesystem (ext3_ on ....)' for details
[*]Be sure to fully expand all details and read what has been done. If it's the Ext3 file system, GParted will have calibrated your file system and run e2fsck -f -y -v on it for you, and has run resize2fs for you to make sure your file system is the right size to fill your partition.
[/LIST]
A file system check would be the first thing to try, but if that doesn't fix it then please click on the link: [When trying to boot Linux]("http://users.bigpond.net.au/hermanzone/p15.htm#When_trying_to_boot_Linux")                                         (in a computer with only one hard disk) to see what other thing you could try.

There are three categories of GRUB Error 17,

[LIST]
[*][When trying to boot Linux]("http://users.bigpond.net.au/hermanzone/p15.htm#When_trying_to_boot_Linux")                                         (in a computer with only one hard disk)
[*][When trying to boot Linux or Windows]("http://users.bigpond.net.au/hermanzone/p15.htm#In_a_computer_with_more_then_one_hard") (in a computer with more than one hard disk)
[*][When booting Windows]("http://users.bigpond.net.au/hermanzone/p15.htm#When_trying_to_boot_Windows") (if you only have one hard disk)
[/LIST]
 I think the new uuid command in Intrepid Ibex's GRUB will reduce the number of GRUB Error 17 problems when it is caused by having multiple hard disks of different types in the same computer.

---

