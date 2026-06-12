---
title: "Installing Ubuntu 10.04 to external hd from Toshiba Laptop"
date: 2012-01-15
forum: Hardware
---

### Post by Calcrest on 2012-01-15
Good day everyone;

I'm new to this forum and I'm hoping that someone can help.  Here is my issue:
I have a Toshiba Satellite A200 TJ6; 2gb RAM; Intel Core2 Duo 1.5ghz; 32 bit OS 7 Pro.
I've downloaded Ubuntu 10.04 to CD. I checked the CD contents and it would seem, to the best of my knowledge, all the files are there.

What I want to do is install 10.04 on an external 160gb usb hd which has been formatted NTFS using the window 7 Pro.

The process used:
With Windows up and running, I installed the CD in the CD drive; I went to the boot record and changed the boot sequence, to boot from CD.    I exited saving the settings. I shut the computer down; turned it over and removed the drive from the laptop and rebooted.  I removed the drive because I was apprehensive that Ubuntu could corrupt os 7.  The CD spins in the drive and runs for few minutes; I'm assuming the CD is being read.  The boot screen appears and the screen reads out the directory specifications and stops at Grub with a flashing cursor.  I cannot type or use any external functions on the screen and I've left it at that position for up to 10 min. and nothing is happening.  

I also have a copy of Hardy Heron LTS 8.04, acquired from the purchase of a book "Beginning Ubuntu Linux". I tried the same with this as I did with 10.04 with the same results.  

I'm somewhat baffled because I've done this successfully in the past, with Hardy Heron; however, those installs where on a tower, using os XP service Pk 3, to an internal drive.  

Could someone please help me to resolve this issue.

Thank you :D

---

### Post by oldfred on 2012-01-15
My older Toshiba has always booted without issue, butmy Desktop needs nomodeset as it have video issues. What video does your system have? Sometimes other options may be required or you may have some setting in BIOS that needs changing (but portables often have few BIOS settings).

As CD starts you can press any key and then f6 to choose options. 

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)


When you get to the install to the external, version not critical as screens vary only slightly in the installer. But you need to use manual install to get the option to install grub2 boot loader to the external drive:

Install to external drive 11.04.
[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

---

### Post by Calcrest on 2012-04-04
Good morning OldFred;

Sorry for the late reply to your post; and thanks for the promptness to my questions.  I spent some time trying to figure out what the issue was; I went through your links and after considerable thought I figured it out; it turned out to be very simple in the end.  So now that I've solved the boot up sequence and can boot from the cd; use Ubuntu live and understand how to go to install and sequence everything seems to be working until I get to the section on setting up the partitions.  I get to the section on whether I should go with automatic or manual.  I went automatic and it present a pop up window that read: ROOT FILE System not defined.  So I went back to manual  and the partition editor opens up asking how much I want to partition,  type (Fat32, Fat16, ext3, etc), where I want to mount (??).

So since you were so nice in giving me such great advice on the boot up issue, I thought maybe you may have some suggestions on how to partition the 160 gig external drive.  I've done some reading and it is suggested that I  set  /, /swap, /home partitions.  If this is the correct partition sequence; what would be the correct amounts to use in each.  I'm sure if I just venture forth and establish say /10 /50 /100 it can be changed after if things don't seem to work out? 

If you have a favourite site you could point me to that will give this newbie instructions, that would be greatly appreciated.

Thanks

---

### Post by oldfred on 2012-04-04
Sequence on drive does not really matter. With MBR (not newer gpt) partitioning you can only have 4 primary partitions. Windows will only boot from a primary but that is only for internal drives. If you want to share some data with Windows you may want to have another partition formated to NTFS just for data. I still have my Firefox & Thunderbird profiles in my shared NTFS partition even though I rarely boot XP, now.

Partitioning is very personal, and after some time even an optimal partitioning scheme is not so optimal. I buy a new drive every few years, just because I know they fail and want more space and find I repartition differently. I like to use only 1 or 2 primary partitions and put the rest in logical partitions. Windows will read the logical also, so NTFS in logical is ok for data. 

A suggestion, others may have other opinions which are just as good.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

If you store some data into a shared NTFS then /home does not have to be as large. I now have all data in other partition and /home became so small that I now do not have it as a separate partition, but I consider that more advanced.

More info on shared NTFS.
Shared /data (NTFS)-see post #3 oldfred
[http://ubuntuforums.org/showthread.php?t=1772620](http://ubuntuforums.org/showthread.php?t=1772620)
Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)
Mount NTFS partition:
[http://ubuntuforums.org/showthread.php?t=1927504](http://ubuntuforums.org/showthread.php?t=1927504)
Share Windows partition older:
[http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)

---

### Post by Calcrest on 2012-04-17
Problems solved with your help and advice.
Took some problem solving skills, but then isn't that what it's all about.  

Thanks again really appreciate it.

---

### Post by oldfred on 2012-04-17
Your are welcome, glad you got it working.

---

