---
title: "Just ruined my computer...."
date: 2006-02-09
forum: Installation &amp; Upgrades
---

### Post by Pedestrian A on 2006-02-09
Help guys,

I think I just ruined my computer while trying to install Ubuntu... It happened when I was partitioning my hd. I think I made my Windows partition inacessible or worst, deleted it. I didn't touch the partition where I stored all my important files, though. Do you think my files are still there? I've installed Ubuntu but can't access the partition I stored my partition in. Maybe because it's NTFS? Now I want to re-install Windows but what will happen? Will GRUB boot loader be affected? If GRUB is ruined too how will I boot up Ubuntu or Windows?

Pedestrian A,
- I'm just confused and worried, very....

---

### Post by noeluylee on 2006-02-09
On Ubuntu, install Gparted or QTParted. open it, and look for your windows partition. If it wasnt there, you have accidently deleted it.  GParted or QTParter is just like PartitionMagic where you can browse your hard disk partition.

Good Luck!

---

### Post by Pedestrian A on 2006-02-09
Hopefully not. :(

How do I install software on Ubuntu?

---

### Post by noeluylee on 2006-02-09
just go to synaptics package manager, and select the program that you need. 

Repositories are needed for the installation. 

You can add repositories at:
edit /etc/apt/sources.list

for your reference.. my sources.list contains
==
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) breezy main restricted 
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) breezy main restricted 

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) breezy-updates main restricted 
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) breezy-updates main restricted 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) breezy universe multiverse 
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) breezy universe multiverse 

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team
## Official backports
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) breezy-backports main restricted universe multiverse 
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) breezy-backports main restricted universe multiverse 

deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras main restricted universe multiverse  

## Security Updates
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) breezy-security main restricted 
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) breezy-security main restricted 

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) breezy-security universe 
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) breezy-security universe 

#KDE 3.5 Upgrade (Breezy)
deb [http://kubuntu.org/packages/kde35/](http://kubuntu.org/packages/kde35/) breezy main 

## PLF - [http://wiki.ubuntu-fr.org/doc/plf](http://wiki.ubuntu-fr.org/doc/plf)
deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free 
deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free 

## Ubuntu China
deb [http://archive.ubuntu.org.cn/ubuntu-cn/](http://archive.ubuntu.org.cn/ubuntu-cn/) breezy main 
==

Hope this helps.

Good luck

---

### Post by niviche on 2006-02-09
[QUOTE=Pedestrian A]How do I install software on Ubuntu?[/QUOTE]

Click on the menu button on the top left hand of the screen (if you are on Ubuntu-Gnome) or bottom left (on Kubuntu-Gnome) and click on "add application" (gnome) or "Adept" (Kde). You can then look for the application you want to add (Qparted or Gparted). If you can't find it in the "Add application" dialog, click on "Advanced" somewhere (sorry, I am on KDE, not on Gnome), and make a search for it.

Good luck.

---

### Post by Pedestrian A on 2006-02-11
Thanks guys,

My files are safe (phew) but I had to reinstall Windows. I think I know the Ubuntu partitioner more now. I have a question on file systems that's gotta do with Ubuntu. Do I post it at the Ubuntu 5.10 forum or can I just post it here? Thanks.

Pedestrian A.

---

### Post by Lord Illidan on 2006-02-11
I guess you can post it here.

---

### Post by Pedestrian A on 2006-02-11
[QUOTE=Lord Illidan]I guess you can post it here.[/QUOTE]
Thanks, 

Ok, so now I've got both Win XP and Ubuntu on my desktop. So I'm wondering what file system can be both readable and writable on both operating systems? I moved all my files to one partition (I used to have four, now I have 7, one for Windows, three for Ubuntu and now I want to have the other 3 both readable and writable from both OSs) and formated the other two I want to use to FAT32. But I have one small partition I thought I could share with Windows and Ubuntu which is Ext3. I read it from [this guide]("http://users.bigpond.net.au/hermanzone/p14.htm") but I guess I misunderstood it because the Ext3 partition doesn't even show in Windows. Do you recommend this tweak I read from [this PDF]("http://ubuntu.xgn.com.br/ubuntu_user_guide.pdfhttp://ubuntu.xgn.com.br/ubuntu_user_guide.pdfhttp://ubuntu.xgn.com.br/ubuntu_user_guide.pdf") and just format that small partition to FAT32? And how do I set GRUB to boot Windows as default? I still new to Ubuntu (Linux) and have lots of things to learn so I still need Windows as my primary OS.

Pedestrian A.

---

### Post by infoseeker on 2006-02-11
Arrange your '/boot/grub/menu.lst' like this

> title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

title		Ubuntu, kernel 2.6.12-10-686 
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-10-686 root=/dev/hda3 ro quiet splash vga=0x317 video=vesafb:mtrr,ywrap
initrd		/boot/initrd.img-2.6.12-10-686
savedefault
boot


Modify to suit your partition structure tho !

---

### Post by FrankTM on 2006-02-11
[QUOTE=Pedestrian A]And how do I set GRUB to boot Windows as default? I still new to Ubuntu (Linux) and have lots of things to learn so I still need Windows as my primary OS.[/QUOTE]

sudo gedit /boot/grub/menu.list
you will find an option **default		0**

that is the first item in the list you see when you boot, or down below in the same file
change this number to wherever windows is in that same list and it will boot that as default...

however, when you change **0** to **saved** it will boot the OS you last used... which - i think - is pretty neat :)




about the filesystem to use for your shared partition(s)
windows can only read and write from fat, fat32 and ntfs

linux can read all of those, but it cannot write to ntfs
well... its possible, but still very experimental, browse the forums for captive if you're interested

a good choice would be fat32 then, as fat is _REALLY_ old
a limitation to fat32 is that you cannot store files larger then 4Gb, dvd iso's for example

the choice is yours ;)

---

