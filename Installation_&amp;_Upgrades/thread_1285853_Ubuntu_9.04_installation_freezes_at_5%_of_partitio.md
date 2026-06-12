---
title: "Ubuntu 9.04 installation freezes at 5% of partitions formatting"
date: 2009-10-08
forum: Installation &amp; Upgrades
---

### Post by ivgelder on 2009-10-08
Hi,

I'm trying to install Ubuntu on an old desktop computer. But everytime I try to install, it freezes at 5% of the partition formatting. 

As I said, it's an old computer with 256MB RAM en 40GB HD.

Hope one of you can help me.

Inneke

---

### Post by ivgelder on 2009-10-08
Some additional information:

the cd works fine as live cd and i tested the cd with the tool in the option list of the ubuntu installer

---

### Post by pmlxuser on 2009-10-08
1. did you check that the disk is OK (check disk for defects)
2. what parttion system have you selected. try the manual parttioning instead of lert ubuntu choose for you

---

### Post by ivgelder on 2009-10-08
the first time i chose to remove windows and use the whole disk

---

### Post by pmlxuser on 2009-10-08
try manual partitioning (i think its the last option on the disk partitioner) don't be scared by the message it displays since you have chosen to completely remove windows there is nothing to loose

---

### Post by ivgelder on 2009-10-08
It still freezes, now at formatting swap space in partition #5 of SCSI1


What's the best partition I should use?

---

### Post by pmlxuser on 2009-10-08
try formating using ext3 not ext4 for file system

don't know if am correct

but i would suggest that for swap you assign 512 MB

swap 512Mb
/ 5Gb
/home 14.5Gb

---

### Post by ivgelder on 2009-10-08
i used 
swap 512MB
/ 5 GB
/home all the left free space

seems like it is working now, it's around 22% and still busy

---

### Post by ivgelder on 2009-10-08
it seems i had too much hope :)
now it feezes at 25% of installing system - copying files

could it be that 256 MB RAM isn't enough?

---

### Post by raymondh on 2009-10-08
> **ivgelder said:**
> it seems i had too much hope :)
now it feezes at 25% of installing system - copying files

could it be that 256 MB RAM isn't enough?

yes ... though it may be listed as minimum requirements, remember that some of it will be taken by the graphic card.  Some options :

-Try an [alternate install CD]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate").  It is text based instead of GUI
-Try a [server edition]("http://www.ubuntu.com/products/whatIsubuntu/serveredition") and then build-up (add programs you only need) from there as well as use a lighter desktop manager like [openbox]("http://icculus.org/openbox/index.php/Main_Page") or [lxde]("http://wiki.lxde.org/en/Ubuntu")
-Try [crunchbang linux]("http://crunchbanglinux.org/") (I prefer the ubuntu flavor)

Happy ubuntu-ing.

---

### Post by ivgelder on 2009-10-08
> **raymondhenson said:**
> yes ... though it may be listed as minimum requirements, remember that some of it will be taken by the graphic card.  Some options :

-Try an [alternate install CD]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate").  It is text based instead of GUI
-Try a [server edition]("http://www.ubuntu.com/products/whatIsubuntu/serveredition") and then build-up (add programs you only need) from there as well as use a lighter desktop manager like [openbox]("http://icculus.org/openbox/index.php/Main_Page") or [lxde]("http://wiki.lxde.org/en/Ubuntu")
-Try [crunchbang linux]("http://crunchbanglinux.org/") (I prefer the ubuntu flavor)

Happy ubuntu-ing.


I'll try and let you know if it works

---

### Post by ivgelder on 2009-10-08
i have problems with burning the alternate cd
give me some time to solve this

---

### Post by ivgelder on 2009-10-08
There was something wrong with the alternate install iso.
Then I realized I may be better to install Xubuntu, but I have the same behaviour. It freezes at 15%.

---

### Post by ivgelder on 2009-10-08
I cannot burn both Ubuntu alternate cd and Xubuntu alternate cd.
I'll try crunchbang linux tomorrow. 
I hope it works because now I deleted a working Windows version...

---

### Post by raymondh on 2009-10-08
> **ivgelder said:**
> I cannot burn both Ubuntu alternate cd and Xubuntu alternate cd.
I'll try crunchbang linux tomorrow. 
I hope it works because now I deleted a working Windows version...

On an ubuntu install CD (which you said the live (try without changing) was working .... when you boot up into the liveCD, you can press F4 and select safe graphics mode. See if that helps.

I am running crunchbang on a '98 pentium3 system with 256mb RAM.  

Regards,

---

### Post by ivgelder on 2009-10-09
> **raymondhenson said:**
> On an ubuntu install CD (which you said the live (try without changing) was working .... when you boot up into the liveCD, you can press F4 and select safe graphics mode. See if that helps.

Regards,

I already tried that and it isn't working... 

I tried crunchbang and didn't find where to install (i'm new to linux, i only know ubuntu)

thank you for your help

---

### Post by ivgelder on 2009-10-09
i finally managed to burn the xubuntu alternate cd. now the installation freezes at "select and install software" 24%. i'm getting really desperate...

---

### Post by ivgelder on 2009-10-09
i managed to install xubuntu with the alternate cd, but i had to skip the "select and install software"part. now i can boot my computer, but xubuntu seems to be only command line. Why? How can i heal this?


i'm trying 
sudo apt-get update
sudo apt-get install xubuntu-desktop

but i'm unsure if this will help

---

### Post by ivgelder on 2009-10-09
i got a bit further typing
sudo apt-get install xserver-xorg

now the system boots in the GUI, but before logging in i get an error
"Can't open file /usr/share/gdm/themes/Human/Human.xml"

i can click "ok" and then i get a log-in screen, but it is not the screen from xubuntu 
I do can choose a session and i can log in, but then i get a blank screen**

---

### Post by ivgelder on 2009-10-09
i can log in into a safe terminal session

i tried again
sudo apt-get install xubuntu-desktop
but then the computer freezes when "Adding diversion of /usr/share/vim/vim72/doc/tags to usr/share/vim/vim72/doc/tags.vim-tiny by vim-runtime"

---

### Post by ivgelder on 2009-10-09
It worked!!!!!

I installed Xubuntu in text mode (server)
then 

sudo apt-get update
sudo apt-get install xubuntu-desktop
sudo apt-get install gdm

and it is working now!!!

thank you for your help

---

### Post by cameronwp on 2009-10-11
I'm having the same problem, but I'm installing on new hardware.  It keeps freezing at 5% ext3 partition formatting.

EP45-UD3P
Sapphire Radeon HD4870
Core 2 Quad 2.833Ghz
Western Digital 1TB

Could it be a harddrive problem?  What's a good way of testing a hard drive's integrity on a system without an operating system?  Thanks.

---

### Post by hajons on 2010-03-16
I have the same problem on both 9.04 and 9.10. Trying to install Ubuntu on a Dell Precision 380, which has been running 9.10 before without any problem until HDD crashed. Have now tried to install both 9.04 and 9.10 on three different HDDs with both ext3 and ext4. Nothing works. At 5% nothing ever happens. It just looks like it is going on forever without getting anywhere. No indication of progress. Nothing.

---

### Post by Freze on 2010-03-17
i have the exact same problem.
 
Freezes at 5% and my mouse won't work..

---

