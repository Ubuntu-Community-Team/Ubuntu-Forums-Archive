---
title: "Error: wrong fs type when trying to mount external HD"
date: 2011-12-31
forum: Hardware
---

### Post by LauraSol79 on 2011-12-31
My external hard drive works perfect with a windows machine, but I can not mount it on ubuntu 11.10.

I get the following error message:

[COLOR=DarkRed]"Error mounting: mount exited with exit code 1: helper failed with:
mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so"
[/COLOR]
dmesg | tail returns the following:

[COLOR=DarkRed][   89.817894] FAT-fs (sdc1): bogus number of reserved sectors
[   89.817910] FAT-fs (sdc1): Can't find a valid FAT filesystem
[  166.765576] FAT-fs (sdc1): bogus number of reserved sectors
[  166.765582] FAT-fs (sdc1): Can't find a valid FAT filesystem
[  271.436097] FAT-fs (sdc1): bogus number of reserved sectors
[  271.436103] FAT-fs (sdc1): Can't find a valid FAT filesystem
[  324.772352] FAT-fs (sdc1): bogus number of reserved sectors
[  324.772360] FAT-fs (sdc1): Can't find a valid FAT filesystem
[ 1228.799077] FAT-fs (sdc1): bogus number of reserved sectors
[ 1228.799089] FAT-fs (sdc1): Can't find a valid FAT filesystem
[/COLOR]
fdisc -l returns this:

[COLOR=DarkRed]Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x41ffc810

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   625121279   312560608+   7  HPFS/NTFS/exFAT

[COLOR=Black]What to do :confused:

Happy new year to you all
Laura
[/COLOR][/COLOR]

---

### Post by LauraSol79 on 2012-01-07
Okay, I got that it might be the exFUSE that is causing me trouble, but...

from [COLOR=#800000][http://ubuntuforums.org/showthread.php?p=10484125#post10484125](http://ubuntuforums.org/showthread.php?p=10484125#post10484125)
[/COLOR][COLOR=#800000][FONT=Verdana][COLOR=Black]I got the following:[/COLOR][/FONT][/COLOR]
[COLOR=#800000]
[/COLOR][COLOR=#800000]sudo apt-get install subversion[/COLOR]
[COLOR=#800000]sudo apt-get install scons[/COLOR] [COLOR=#800000]sudo apt-get install libfuse-dev[/COLOR] [COLOR=#800000]sudo apt-get install gcc[/COLOR] [COLOR=#800000]cd ~[/COLOR] [COLOR=#800000]svn co [http://exfat.googlecode.com/svn/trunk/](http://exfat.googlecode.com/svn/trunk/) exfat-read-only[/COLOR] [COLOR=#800000]cd exfat-read-only[/COLOR] [COLOR=#800000]scons[/COLOR] [COLOR=#800000]sudo scons install[/COLOR] [COLOR=#800000]cd ..[/COLOR] [COLOR=#800000]rm –rf exfat-read-only[/COLOR] [COLOR=#800000]sudo mkdir [mountpoint][/COLOR] [COLOR=#800000]sudo mount –t exfat-fuse [device_path] [mountpoint][/COLOR] 
[FONT=Verdana]no errors till rm , same error when trying to mount afterwards.

from [/FONT]
[http://genjusz.wordpress.com/2011/11/25/exfat-in-ubuntu-11-10/](http://genjusz.wordpress.com/2011/11/25/exfat-in-ubuntu-11-10/)
I got:

[COLOR=DarkRed]sudo su - add-apt-repository ppa:relan/exfat apt-get update apt-get install fuse-exfat
apt-get install build-essential apt-get install ncurses-dev apt-get install util-linux
[/COLOR]
And hey - I got through without errors! But It doesn't seem to be making any difference when trying to mount (or simply plug in) the HD.

I will continue to search and look for solutions myself, but any help will be much appreciated!

/Laura

---

### Post by upchucky on 2012-01-07
this could be a long shot, perhaps try Knoppix live cd, see if it chokes on the drive.
Another posibility would be to try forensic drive investigative software on the drive.
forensicswiki.org/wiki/Tools#Forensics_Live_CDs

---

