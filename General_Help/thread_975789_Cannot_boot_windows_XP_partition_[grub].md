---
title: "Cannot boot windows XP partition [grub]"
date: 2008-11-08
forum: General Help
---

### Post by alexgamerz on 2008-11-08
I just formatted my pc and decided to try ubuntu. After installing Windows XP Home Media Edition I installed the latest ubuntu (8.10 i think) and gave it just over half of my disk space. After failing to be able to get my wireless card to work, i wanted to boot windows for the time being. I booted and grub loaded, i saw ubuntu, memtest, windows xp and the windows recovery partition. After trying the windows partition and nothing happened, i tried the recovery partition. it worked. I tried the regular windows partition and for the last 20 mins it has only been saying "Starting up ...", i think this is still part of grub. help please!

my pc is made by hp

---

### Post by caljohnsmith on 2008-11-08
It sounds like you might need to repair the Windows boot sector, because that is often the cause of having Windows hang on "Starting up..." From Ubuntu. First make sure the Universe repository is enabled in Ubuntu under System > Admin > Software Sources, then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk, choose "no log", choose the correct HDD and "proceed", choose "intel", choose "advanced", select the Windows XP partition, choose "boot", then choose "Rebuild BS"; if testdisk gives you an error about boot sectors not matching, then choose "write". After you are done doing the "rebuild BS" in testdisk, reboot and let me know what happens. If that doesn't work, then please post the output of:
```
sudo fdisk -l
cat /boot/grub/menu.lst
```
Otherwise let me know how it goes.

---

### Post by TeXtonyx on 2008-11-08
duplicate

---

### Post by alexgamerz on 2008-11-08
your walkthrough was very nice but i don't know much about ubuntu and i don't have an internet access on that computer. I can use the command line in windows so am comfortable with the terminal. I can move files to that computer using my flash drive but the site that told me how to compile files was very complecated as the file you told me to download was .tar.bz2. if you help me i would be so greatfull tyvm

---

### Post by caljohnsmith on 2008-11-08
OK, how about downloading the [Ultimate Boot CD]("http://www.ultimatebootcd.com"), boot that, and go to Disk Tools > Partition > Testdisk, and you can follow the instructions from my previous post to use testdisk to repair the Windows boot sector.

---

### Post by froy02 on 2008-11-08
> **alexgamerz said:**
> I just formatted my pc and decided to try ubuntu. After installing Windows XP Home Media Edition I installed the latest ubuntu (8.10 i think) and gave it just over half of my disk space. After failing to be able to get my wireless card to work, i wanted to boot windows for the time being. I booted and grub loaded, i saw ubuntu, memtest, windows xp and the windows recovery partition. After trying the windows partition and nothing happened, i tried the recovery partition. it worked. I tried the regular windows partition and for the last 20 mins it has only been saying "Starting up ...", i think this is still part of grub. help please!

my pc is made by hp

Before you do anything else boot into windows and let windows repair the partition that Ubuntu resized during during installation.  It normal for windows to re-arrange the files and re-index them after Ubuntu installation.  It takes a while, almost as long as defragging the drive.

---

### Post by TeXtonyx on 2008-11-08
Before you do anything else boot into windows and let windows repair the 
partition that Ubuntu resized during during installation. It normal for 
windows to re-arrange the files and re-index them after Ubuntu 
installation. It takes a while, almost as long as defragging the drive. 
froy02 is offline   	Reply With Quote

TeX: I deleted my post and marked it duplicate because I was going to post
nearly the same information that caljohnsmith provided, 

[http://ubuntuforums.org/showthread.php?t=920862&highlight=ulbhudda&page=4](http://ubuntuforums.org/showthread.php?t=920862&highlight=ulbhudda&page=4) #32
meierfra is very competent. I wasn't very familiar with Testdisk at the time
but it has a very good success rate with fixing the error which says
"Starting up"
Repairing the installation should be tried after Testdisk, fixmbr and fixboot.

[http://www.mopedia.co.uk/2008/01/installing-software-from-source-in.html](http://www.mopedia.co.uk/2008/01/installing-software-from-source-in.html)
This explains how to install tar.bz2 in case you (OP) want to learn how.
You may need to satisfy some dependencies to have the build process work.

Why not download the .deb file which is easier to install?
sudo dpkg -i testdisk_6.10-1_i386.deb

[http://ftp.debian.org/debian/pool/main/t/testdisk/](http://ftp.debian.org/debian/pool/main/t/testdisk/)
and choose 	testdisk_6.10-1_i386.deb	17-Aug-2008 13:02 	1.5M
which is next to the last file towards the bottom. 
testdisk_6.10-1_i386.deb 

I used Firefox to download the file. Transfer the file to your usb stick.
Then put it on the desktop of your Ubuntu install which has  no internet 
connection. Under System->Preferences->Main Menu_>System Tools I added 
the Gdebi package installer so that it shows up under Applications ->
System Tools. Then I doubleclicked on the Desktop file below.
testdisk_6.10-1_i386.deb 
maybe there is going to be another dependency file to add.
from the terminal command line type: sudo testdisk
follow steps by caljohnsmith until you reach

Disk /dev/sda - 82 GB / 76 GiB - CHS 10011 255 63
     Partition                  Start        End    Size in sectors
 1 * HPFS - NTFS              0   1  1  8139 254 63  130769037

Boot sector
Status: OK

Backup boot sector
Status: OK

Sectors are identical.

A valid NTFS Boot sector must be present in order to access
any data; even if the partition is not bootable.


[  Quit  ]  [  List  ]  [Rebuild BS]  [Repair MFT]  [  Dump  ]
                            Return to Advanced menu
-----------------------------------------------------

If the sectors are identical it probably won't help to rebuild BS.
But if the sectors are reported as different, it will probably fix 
the problem to Rebuild BS.
(btw, I used the Gdebi package installer to open the testdisk*.deb
located on the Desktop and installed it. Then, sudo testdisk  )

---

### Post by alexgamerz on 2008-11-08
thank you everyone:)

---

