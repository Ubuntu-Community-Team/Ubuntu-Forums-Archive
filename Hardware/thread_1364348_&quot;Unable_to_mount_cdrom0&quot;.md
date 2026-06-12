---
title: "&quot;Unable to mount cdrom0&quot;"
date: 2009-12-25
forum: Hardware
---

### Post by BaroqueBloke on 2009-12-25
I dusted off my first 1,1 macbook a few weeks ago and decided to install ubuntu 9.10 o it.  Im new to Linux so this has been one huge learning experience for me.  But, ever since I installed I have run into a few problems.  

1.  Least of the trouble is my suspend/hibernate doesnt work.  I have chosen to ignore this for the time being as it would seem it is a common problem.  

2.  (And the real issue)   My CDRom no longer works.  I have posted on othr threads here for this issue but have yet to recieve an answer.  Every time I try to do anything with a CD or a DVD I get the error "Unable to mount cdrom0"   
     this would be no issue If I were running a Netbook (which I hope to soon be)  But alas, I am not.  I burned the install disc I used when upgrading, on this computer.  The optical drive is functioning.  I have spent hours tring to find any drivers I may still be missing but have been unsuccessful.  

ANY help or tips will be thoroughly appreciated.  I cannot read, burn CD's nor play/rip DVD's.  

I love Ubuntu so far but this is turning into a Deal breaker fo me!!!  :(

---

### Post by willgb54 on 2009-12-25
I have the same problem and have also posted other places. Apparently there is no answer available, other than you just don't know what you are doing. It is perfectly reasonable in UBUNTU SPEAK to spend hours trying to get a CD to open and work properly. How can Microsoft ever catch up to these geniuses?

---

### Post by Raymond Petit on 2010-01-06
Good news, guys, the code to force the cdrom to mount is: sudo mount /dev/hdc /media/cdrom -t udf

First make certain of what your system has designated your cdrom as, mine in the example above is /dev/hdc. To find yours in the terminal type:
cat /etc/fstab, then press the enter key. You should find it in the last line.

When you are certain of what your cdrom is called place a dvd in the drive, then type sudo mount /dev/"your cdrom name" /media/cdrom -t udf, then the enter key.

The cdrom should appear on the desktop. From there you can left click it to select either to play the dvd with movieplayer or vlc. Mine played flawlessly on an old ibook g4, 1GHz processor with Ubuntu 9.10.

To eject the dvd I have to use the terminal also, right clicking to select "eject" doesn't work. So after watching movie, in a terminal type:
sudo eject /cdrom/

Interestingly enough, after I did this the first time vlc was somehow able to detect and open a dvd without me having to use the code to force the cdrom to mount, but movieplayer still can't see it so you'll have to use the code first if you want to watch a disk with movieplayer.

Kudos go to DrDevice who gave it to aramumayo in response to 'Unable to mount location, no Media in drive
9.04-Ubuntu Forums July 2009

---

### Post by Pieuga on 2010-11-17
I tried this but still I have problem:
The fstab says:
[FONT=Courier New]#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=088e4c28-0d84-4e6c-8acd-b5dde9f3a06e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=1286252e-c56a-4872-83c4-5459399b4845 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
[FONT=Verdana]And the mount command return:
[FONT=Courier New]peter@peter-laptop:/dev$ sudo mount /dev/scd0 /media/cdrom -t udf
[sudo] password for peter: 
mount: il device speciale /dev/scd0 non esiste[/FONT]

if I try to mount CDROM0 from the resource menu the result is the same.
This problem is active sice I have upgreded to Maverick Meerkat.
Please, can someone help me?
Regards, Peter.
[/FONT][/FONT]

---

### Post by sridharpandu on 2010-11-18
I have the same issue. The DVD RW drive is not detected. Someone I spoke to told me that this is due to [COLOR=#808080]*usb_modeswitch*[/COLOR]. Can someone throw some light on how to mount the DVD ROM drive.

Best regards

Sridhar [COLOR=#808080][/COLOR]

---

