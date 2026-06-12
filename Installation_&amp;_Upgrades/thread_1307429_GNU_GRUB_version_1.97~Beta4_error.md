---
title: "GNU GRUB version 1.97~Beta4 error"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2009-10-31
I have used wubi to installed 10.9 as dual booting.
when the installation finished and i want to boot linux it just jupm into console, not the desktop.
I can see this message on the top of the console.
GNU GRUB version 1.97~Beta4
I didn't think that I was using the beta version.

---

### Post by James2k on 2009-10-31
It is the GRUB loader for Ubuntu 9.10.

---

### Post by hoboy on 2009-10-31
> **James2k said:**
> It is the GRUB loader for Ubuntu 9.10.

What shall I do to come out of it to go to the desktop ?

---

### Post by Killbot956 on 2009-10-31
Try typing the command:   startx 
This should start X Server.

---

### Post by JosephMarc on 2009-11-01
hoboy i had the same problem, this is the dvd's (or cd's) fault.
Try reburning ubuntu at low speed on quality support.

---

### Post by hezuo on 2009-11-02
I'm having the same issue. please, help, I have no idea how to solve this.

---

### Post by Alaa2 on 2009-11-07
am having the same problem,..i installed the updates from the update manger (the grub updates) and now am stuck in the console mode and i can't switch back to the desktop or GUI,anyone have any idea what should we do ? :?:

---

### Post by drs305 on 2009-11-07
For all of those having this problem: Which "console" are you talking about? A system prompt or a grub prompt? Did the system ever start or are you stuck at the grub or grub-rescue prompt?

If you are stuck at a grub prompt or grub-rescue prompt (Not just the word "GRUB" in the top left corner of the screen) you may still be able to boot to the system via the grub command line.

Here is a link to a guide to help you do that:
[https://help.ubuntu.com/community/Grub2#Rescue Mode]("https://help.ubuntu.com/community/Grub2#Rescue%20Mode")

---

### Post by Alaa2 on 2009-11-08
if what i see is "sh:grub>" then what does this indicate,and still how can i get out of this mode ?

---

### Post by drs305 on 2009-11-08
> **Alaa2 said:**
> if what i see is "sh:grub>" then what does this indicate,and still how can i get out of this mode ?

Same link as previous post. You will have to tell Grub 2 where the kernel is and where the "root" filesystem is. Follow the steps in the link and if you have questions ask on the IRC channels (#ubuntu) for live help or post back here.

---

### Post by Alaa2 on 2009-11-09
> **drs305 said:**
> Same link as previous post. You will have to tell Grub 2 where the kernel is and where the "root" filesystem is. Follow the steps in the link and if you have questions ask on the IRC channels (#ubuntu) for live help or post back here.

okies,will do thanks.

---

### Post by mittparadox on 2009-11-09
im bumping this tread as i have the same problem.
i have tried about everything >.<

i tried this guide: [https://help.ubuntu.com/community/Grub2#Rescue%20Mode](https://help.ubuntu.com/community/Grub2#Rescue%20Mode)

[[IMG]http://img43.imageshack.us/img43/2274/imag0023n.th.jpg[/IMG]](http://img43.imageshack.us/img43/2274/imag0023n.jpg)

that dident work.

i had this problem when i first installed ubuntu, then i got it working, i cant remember if i did somting to get it to work, i think i just booted and all the sudden it worked^^
that was a few weeks ago, been changing back and forth from win 7 to ubuntu with no problems, today when i tried to boot it was like this again :S

i have installed with wubi installer and ubuntu is in C:/ubuntu
so not sure with the sda1, sdb1 or whatever i should use but tried lots of them and all i get is errors.

i did: ls -l and found out that C: was hd1
so thats sdb1? xD (this is so confusing)

any idea what to do? :S

---

### Post by Alaa2 on 2009-11-10
> **mittparadox said:**
> im bumping this tread as i have the same problem.
i have tried about everything >.<

i tried this guide: [https://help.ubuntu.com/community/Grub2#Rescue%20Mode](https://help.ubuntu.com/community/Grub2#Rescue%20Mode)

[[IMG]http://img43.imageshack.us/img43/2274/imag0023n.th.jpg[/IMG]](http://img43.imageshack.us/img43/2274/imag0023n.jpg)

that dident work.

i had this problem when i first installed ubuntu, then i got it working, i cant remember if i did somting to get it to work, i think i just booted and all the sudden it worked^^
that was a few weeks ago, been changing back and forth from win 7 to ubuntu with no problems, today when i tried to boot it was like this again :S

i have installed with wubi installer and ubuntu is in C:/ubuntu
so not sure with the sda1, sdb1 or whatever i should use but tried lots of them and all i get is errors.

i did: ls -l and found out that C: was hd1
so thats sdb1? xD (this is so confusing)

any idea what to do? :S

same thing here,i installed the 9.10 version through windows 7 on an NTFS partition and when i try the commands in the guide for manual booting through the CLI,i get errors @ "2. linux
Type and continue." i get error couldnt find specified kernal,as for the other commands i just get errors.

---

### Post by drs305 on 2009-11-10
> **Alaa2 said:**
> same thing here,i installed the 9.10 version through windows 7 on an NTFS partition and when i try the commands in the guide for manual booting through the CLI,i get errors @ "2. linux
Type and continue." i get error couldnt find specified kernal,as for the other commands i just get errors.

Are you using wubi? I don't know if Grub 2 interacts differently with wubi installs. The main reason I'm posting is to ensure you are correctly interpreting step 2 of the guide you referenced. You are to enter Steps 2-5 *all on one line* before pressing ENTER. Is that what you are doing?

---

### Post by zodiacallight on 2009-11-12
Just wanted to chime in. I installed 9.10 with Wubi (from Vista) a few weeks ago and it worked beautifully (loving it as a new user) for three weeks or so. This morning, I think I got the same issue, effectively locking me out. After the selecting 'Ubuntu' at the dual boot screen I get the GRUB version 1.97~beta4 screen saying "minimal BASH-like line editing is supported..." etc. trying the command 'boot' gives me 'no loaded kernel.'

I checked out the above-mentioned help file but the first command "is" doesn't seem to be recognized. (I don't really know what I'm doing though..)

---

### Post by drs305 on 2009-11-12
> **zodiacallight said:**
> 
I checked out the above-mentioned help file but the first command "is" doesn't seem to be recognized. (I don't really know what I'm doing though..)

The command is lowercase "LS", not "IS". That should get you started.

---

### Post by mgrajeesh on 2009-11-12
> **drs305 said:**
> The command is lowercase "LS", not "IS". That should get you started.
i am also facing the same problem .i gone through all the procedures to boot.but its is not working.
I have installed Ubuntu 9.10 in a USB Hard disk which having two patitions.Please give me clear procedure to boot .Really i dont like the promt to boot Ubuntu.
Please help me i am a new guy to Ubuntu

---

### Post by drs305 on 2009-11-12
> **mgrajeesh said:**
> i am also facing the same problem .i gone through all the procedures to boot.but its is not working.
I have installed Ubuntu 9.10 in a USB Hard disk which having two patitions.Please give me clear procedure to boot .Really i dont like the promt to boot Ubuntu.
Please help me i am a new guy to Ubuntu

mgrajeesh,

You should probably start your own thread for this. Include the following information in your post:
Grub 2 (Karmic fresh install)?
What do you see when you try to boot - Grub menu, grub prompt, grub-rescue prompt, blank screen with word Grub?
If you try to boot, what happens?
Which device is GRUB 2 installed on?

Have you looked at [https://help.ubuntu.com/community/Grub2#GRUB%20Errors]("https://help.ubuntu.com/community/Grub2#GRUB%20Errors"), which is the Grub Problems section, and also the reinstalling GRUB 2 section.

---

### Post by mrebanza on 2009-11-13
SAME PROBLEM - 

WUBI INSTALL UBUNTU 9.10 DUAL BOOT WITH XP

On my Acer Aspire One Netbook

Got ubuntu up and running perfect . . . . then after about a week - After installing the automatic updates via the ubuntu update manager the system was running slow and not playing audio on youtube and other flash video so I rebooted 

Now when I boot and select ubuntu it brings me to "gnu grub v1.97 beta4 minimal bash-like " command prompt echoing

sh:grub>

wtf

comand boot 

echos something about kernel not being selected or something

my guess is that the auto update replace a file assuming that it was not a dual boot (again wtf) and now grub can find the kernel to load up gnome 

Now I know wubi isn't the recomeded way to install Ubuntu but should we take into consideration all the TONS of people who do have Ubuntu installed via Wubi when promting them to install automatic updates????

come on guys . . . I dont even use my Win XP install but so what Now I have not way to acess all my file on the ubuntu partition . . . at least not from XP

Solution (well not really) - Used a BOOT CD on another PC Desktop Computer (since netbooks have no CD drives aka reason I used WUBI in the first place) to create an official USB boot drive (fast & easy) - Press F12 on start up to select to boot from USB - Installed a FRESH copy of Ubuntu via USB (no more dual boot - no partitions No more WUBI no more windows whiped my netbook clean of all OS's and files :( ) 

Hopefully Ubuntu will be more stable this way (I hope) because I am actually pretty acustom to it already and windows just doesn't feel the same anymore . . . I am going to install the automatic updates again and see what happends . . . .oh well I was getting tired of selecting Ubuntu from the Windows XP Boot list anyway ;)

---

### Post by mittparadox on 2009-11-13
noting seems to work :S

[[IMG]http://img690.imageshack.us/img690/6689/imag0029.th.jpg[/IMG]](http://img690.imageshack.us/i/imag0029.jpg/)

[[IMG]http://img691.imageshack.us/img691/3778/imag0030a.th.jpg[/IMG]](http://img691.imageshack.us/i/imag0030a.jpg/)

im i doing this all wrong?

i looked in the ubuntu folder in win 7, 
"C:\ubuntu\disks\boot\grub" that folder is empty, is it suppose to be that?

---

### Post by mrebanza on 2009-11-13
> **mittparadox said:**
> noting seems to work :S
im i doing this all wrong?

i looked in the ubuntu folder in win 7, 
"C:\ubuntu\disks\boot\grub" that folder is empty, is it suppose to be that?

yes if I understand correctly C:\ drive isn't your hardrive its your windows harddrive partition (aka the section of your harddrive just for windows to use) but the are both ubuntu and windows sharing space on you ROOT hard drive 

so windows is REALLY installed in root/host/ but they dont give you accept to anything under the "C:/ drive"

Ubuntu's file are in root/home/

Sorry I was mad about Ubuntu and I deleted all my files from my laptop earlier with out thinking but that DOES NOT mean that that is what you guys have to do . . . 

. . . . In my frustration . . . and hast I forgot how easy it is to boot ubuntu before accually installing it . . . . 

SO HERE IS THE PROBLEM SOLVER

after you make the Boot USB . . . Boot Up ubuntu on it ! ! ! ! just select try it first option instead of install and BAM - your up and running in Ubuntu WITH OUT INSTALLING IT running it off the USB . . . . Save all your must have files from windows and the corrupted gnu grub bash-yourself-in-the-head-like WUBI x Ubuntu sh:grub> throw all your photos on your flash drive your upload em online and then when your done saving all your document and you got em in a safe place just click the install now icon on the desktop . . . what could be easier than that?

idk


( ps I am running a FRESH INSTALL of Ubuntu 9.10 NOW and even after runing the auto updated that caused this problem in the first place, everything is working perfectly fine and after rebooting it is running much fast than it was with the WUBI - DUAL BOOT gnu grub off windows so consider a fully upgrade to your whole hard drive  if your really interested in using ubuntu full time)

---

### Post by orangeworx on 2009-11-13
> **drs305 said:**
> Same link as previous post. You will have to tell Grub 2 where the kernel is and where the "root" filesystem is. Follow the steps in the link and if you have questions ask on the IRC channels (#ubuntu) for live help or post back here.

I'm in the command-line mode (by pressing c) and I'm trying to follow the GRUB2 rescue.
when I do ls, I get
(hd0) (hd0,1)
error: out of disk

what does that mean?

---

### Post by drs305 on 2009-11-13
> **orangeworx said:**
> I'm in the command-line mode (by pressing c) and I'm trying to follow the GRUB2 rescue.
when I do ls, I get
(hd0) (hd0,1)
error: out of disk

what does that mean?

Over on the grub IRC channel I was told it is often a corrupted partition table. 

If you can get into your system or boot to the LiveCD perhaps running "sudo fdisk -l" might tell you if ubuntu can read your partition table.

---

### Post by mittparadox on 2009-11-15
i gave up on wubi.
so i went into windows and shrink the partition down so i had 30gb free on C:
then i booted ubuntu live cd with usb stick and installed ubuntu.
everyting went fine but when i rebooted i just loaded into windows.
i dident get any option to boot ubuntu, any idea what to do?

it looks like im just not supose to have linux :(
i have tried for a few years now!
this version i have boot problems, [Hardy Heron]("http://forum.ubuntu.no/viewforum.php?f=22&sid=06c95d91e7c826caa69ed2cd40333047") dident like my gfx card and [Gutsy Gibbon]("http://forum.ubuntu.no/viewforum.php?f=21&sid=06c95d91e7c826caa69ed2cd40333047") dident have compatible drivers for my sound card etc.

---

### Post by drs305 on 2009-11-15
> **mittparadox said:**
> 
then i booted ubuntu live cd with usb stick and installed ubuntu.
everyting went fine but when i rebooted i just loaded into windows.
i dident get any option to boot ubuntu, any idea what to do?

The first thing to do would be to see if GRUB 2 is installed and is automatically sending you to Windows or if there is another problem. During the boot, hold down the SHIFT key and see if the GRUB 2 menu appears. If it does, you may see an Ubuntu option (although this is not how it should be acting). If holding down the SHIFT key does not produce a GRUB 2 menu, either the installation was not successful or there a more serious problems with the GRUB 2 setup.

---

### Post by mittparadox on 2009-11-15
yeah, this worked :D
got several options. choose the first one. and it booted in.

but i see i have lots of updates now. those updates is what messed up the grub when i had ubuntu installed with wubi. guess i just have to hope it doesent happens this time :S

Edit*
o..k, installing updates now and this popped up:

[IMG]http://img509.imageshack.us/img509/3904/skjermdumpdebconfpimpat.png[/IMG]

i dont want to mess up this time so havent done any thing yet :D
what is it and what do i choose? :D

If i click help it says: "A new version of configuration file /etc/default/grub is available, but the version installed currently has been locally modified."

---

### Post by drs305 on 2009-11-15
> **mittparadox said:**
> 
i dont want to mess up this time so havent done any thing yet :D
what is it and what do i choose? :D

If i click help it says: "A new version of configuration file /etc/default/grub is available, but the version installed currently has been locally modified."

What the message is telling you is that any tweaks you have made to /etc/default/grub will be lost. Usually this would be things like the default selection, menu timeout, and perhaps the splash image you've chosen (depending on what files will be updated). I believe it still offers you a chance to look at the changes if you can understand them.

I usually allow it to update to the new version, since the devs decided something needed updating. When I do this, I first make a backup copy of /etc/default/grub and the /etc/grub.d folder. You can do this even while it is waiting for you to decide what to do.
That way you have a copy of your old settings should you want to refer to them.

If you select to update, check /etc/default/grub to ensure the "DEFAULT=X" choice is still what you want, and also the GRUB_TIMEOUT. I usually make sure the menu will display, at least the first time after an update, just to make sure Grub takes me where I want to go.

Long answer, I know. Short answer: Yes, I let it upgrade, but take some precautions first.

---

### Post by mittparadox on 2009-11-15
finally everything seems to work :D
thanks a lot for help :)

---

### Post by Alaa2 on 2009-11-24
guys i would like to point out that the problem is still not solved,.. as everyone said most commands give errors,...am thinking of switching completely from windows to ubuntu/kubuntu but what i am basically doing right now is installing them with wubi on an empty partition with ~27-28 GB,but this GRUB loader/boot is really pissing me off,i had to uninstall kubuntu and install ubuntu AGAIN,.. just to get over this update but i have just installed ubuntu and this problem gets right out of the box now,now when u install ubuntu u will see that it already cant find the kernals or whatever it wants to boot from,...i dunno what am i supposed to do now,but looks like its long way ahead b4 i can think of a total switch to ubuntu,.. not to mention running steam,team fortress 2 and css is still veryyyy buggy :rolleyes:.

anyways i just want to fix this grub loader issue first.

---

### Post by gwatsmiles on 2009-11-27
> **drs305 said:**
> Same link as previous post. You will have to tell Grub 2 where the kernel is and where the "root" filesystem is. Follow the steps in the link and if you have questions ask on the IRC channels (#ubuntu) for live help or post back here.

i'm also stuck with GNU GRUB version 1.97~ beta4 console via wubi. i just did an update and then everytime i open my ubuntu it will open the console.
i tried the above given link but i find many commands different from what i'm using (ubuntu 9.10) can somebody help me please? coz i'm still a noob in ubuntu. just recently tried using this OS. thank you. i will really appreciate your help! :)

---

### Post by replikanxxl on 2009-12-07
ah . at least this problem got the forums so crowded right ???

anyway. i have same issue like you all . but perhaps wubi installs should be treated a little different . as i saw in this thread 
[http://ubuntuforums.org/showthread.php?t=1321107](http://ubuntuforums.org/showthread.php?t=1321107)

---

### Post by Wavvver334 on 2010-01-07
I tried using the following link posted above. I tried to follow the step by step instructions. I just would like to exit the Grub program. It automatically starts up every time i want to use Linux. Is there just an easy command to exit this program and just boot Ubuntu?

---

### Post by kansasnoob on 2010-01-07
> **Wavvver334 said:**
> I tried using the following link posted above. I tried to follow the step by step instructions. I just would like to exit the Grub program. It automatically starts up every time i want to use Linux. Is there just an easy command to exit this program and just boot Ubuntu?

If this is a Wubi install you might find this (and the links therein) helpful:

[http://ubuntuforums.org/showthread.php?t=1374248&page=3](http://ubuntuforums.org/showthread.php?t=1374248&page=3)

I don't use Wubi so I can't be of more help, sorry :(

---

### Post by grifan526 on 2010-01-11
I am also having this problem and when I followed the instructions on a links mentioned somewhere around the beginning of this forum,
[https://help.ubuntu.com/community/Grub2#Rescue%20Mode](https://help.ubuntu.com/community/Grub2#Rescue%20Mode)
It was all working until I got to step 6. It said that there is no such file but when I looked into the boot folder I see that the folder is there. What do I do now?

---

### Post by meierfra. on 2010-01-11
Boot into Windows and try these instruction from the author of Wubi:

[https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210]("https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210")

---

### Post by grifan526 on 2010-01-12
I can't boot to windows, as soon as i turn on my computer it goes straight to the grub recovery and I can't get past that. Any suggestions?

---

### Post by meierfra. on 2010-01-12
grifan526: Let's check out your setup:    Boot from an Ubuntu Live CD and follow these [instructions]("http://ubuntuforums.org/showthread.php?t=1291280").

---

### Post by grifan526 on 2010-01-12
When I type the command it just says 
bash: /home/ubuntu/Downloads/boot_info_script*.sh: No such file or directory
I have checked and my Firefox download folder is still Downloads

---

### Post by meierfra. on 2010-01-12
Strange.  
Did you had any problems downloading? 
Check you spelling.
Use the file browser to navigate to /home/ubuntu/Downloads and see whether you actually succeeded to download the script.

You might also try:

```
sudo bash ~/Downloads/boot_info_script048.sh
```

Or try downloading again, but tell firefox to download the script to the desktop and then use "sudo bash ~/Desktop/boot_info_script048.sh"

---

### Post by grifan526 on 2010-01-14
That worked apparently it didn't download the first time. Here are my results:
```

============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub.
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /etc/fstab

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda9: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /etc/fstab

sda10: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7f41eb71

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    13,858,815    13,856,768  27 Hidden HPFS/NTFS
/dev/sda2    *     13,858,816   166,837,564   152,978,749   7 HPFS/NTFS
/dev/sda3         166,851,090   234,436,544    67,585,455   5 Extended
/dev/sda5         186,386,193   219,030,209    32,644,017  83 Linux
/dev/sda6         232,348,158   234,436,544     2,088,387  82 Linux swap / Solaris
/dev/sda7         166,851,216   185,454,359    18,603,144  83 Linux
/dev/sda8         185,454,423   186,386,129       931,707  82 Linux swap / Solaris
/dev/sda9         219,030,273   231,673,364    12,643,092  83 Linux
/dev/sda10        231,673,428   232,348,094       674,667  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda10: UUID="cc2d3472-d98a-4930-b705-02ac898cb8f5" TYPE="swap" 
/dev/sda1: UUID="B4649E88649E4D4C" LABEL="Recovery" TYPE="ntfs" 
/dev/sda2: UUID="ECC0A094C0A06714" TYPE="ntfs" 
/dev/sda5: UUID="10aa4f5b-b30e-43f5-ab53-49d1450192d5" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="333aa3c0-b143-4e94-968f-f0233c6d4bed" TYPE="swap" 
/dev/sda7: UUID="6ca88b59-7786-4093-a659-9250d7833701" TYPE="ext4" 
/dev/sda8: UUID="6018f9f7-c388-431b-b46a-d01f025da58d" TYPE="swap" 
/dev/sda9: UUID="528fd453-2f7c-4374-b1fb-4ade94132ec5" TYPE="ext4" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)


=========================== sda5/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
#timeout        10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=10aa4f5b-b30e-43f5-ab53-49d1450192d5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=10aa4f5b-b30e-43f5-ab53-49d1450192d5

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 9.10, kernel 2.6.31-14-generic
uuid        10aa4f5b-b30e-43f5-ab53-49d1450192d5
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=10aa4f5b-b30e-43f5-ab53-49d1450192d5 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic
quiet

#title        Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
#uuid        10aa4f5b-b30e-43f5-ab53-49d1450192d5
#kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=10aa4f5b-b30e-43f5-ab53-49d1450192d5 ro  single
#initrd        /boot/initrd.img-2.6.31-14-generic

#title        Ubuntu 9.10, kernel 2.6.28-16-generic
#uuid        10aa4f5b-b30e-43f5-ab53-49d1450192d5
#kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=10aa4f5b-b30e-43f5-ab53-49d1450192d5 ro quiet splash 
#initrd        /boot/initrd.img-2.6.28-16-generic
#quiet

#title        Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode)
#uuid        10aa4f5b-b30e-43f5-ab53-49d1450192d5
#kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=10aa4f5b-b30e-43f5-ab53-49d1450192d5 ro  single
#initrd        /boot/initrd.img-2.6.28-16-generic

#title        Ubuntu 9.10, kernel 2.6.28-15-generic
#uuid        10aa4f5b-b30e-43f5-ab53-49d1450192d5
#kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=10aa4f5b-b30e-43f5-ab53-49d1450192d5 ro quiet splash 
#initrd        /boot/initrd.img-2.6.28-15-generic
#quiet

#title        Ubuntu 9.10, kernel 2.6.28-15-generic (recovery mode)
#uuid        10aa4f5b-b30e-43f5-ab53-49d1450192d5
#kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=10aa4f5b-b30e-43f5-ab53-49d1450192d5 ro  single
#initrd        /boot/initrd.img-2.6.28-15-generic

#title        Ubuntu 9.10, kernel 2.6.28-11-generic
#uuid        10aa4f5b-b30e-43f5-ab53-49d1450192d5
#kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=10aa4f5b-b30e-43f5-ab53-49d1450192d5 ro quiet splash 
#initrd        /boot/initrd.img-2.6.28-11-generic
#quiet

#title        Ubuntu 9.10, kernel 2.6.28-11-generic (recovery mode)
#uuid        10aa4f5b-b30e-43f5-ab53-49d1450192d5
#kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=10aa4f5b-b30e-43f5-ab53-49d1450192d5 ro  single
#initrd        /boot/initrd.img-2.6.28-11-generic

#title        Ubuntu 9.10, memtest86+
#uuid        10aa4f5b-b30e-43f5-ab53-49d1450192d5
#kernel        /boot/memtest86+.bin
#quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
#title        Windows Vista (loader)
#rootnoverify    (hd0,0)
#savedefault
#makeactive
#chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista (loader)
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader    +1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda5 :
UUID=10aa4f5b-b30e-43f5-ab53-49d1450192d5 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda6 :
UUID=333aa3c0-b143-4e94-968f-f0233c6d4bed none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sda2 /media/windows ntfs-3g defaults,locale=en_US.UTF-8 0 0

=================== sda5: Location of files loaded by Grub: ===================


  95.4GB: boot/grub/core.img
  95.4GB: boot/grub/menu.lst
  95.4GB: boot/grub/stage2
  95.4GB: boot/initrd.img-2.6.28-11-generic
  95.4GB: boot/initrd.img-2.6.28-15-generic
  95.4GB: boot/initrd.img-2.6.28-16-generic
  95.4GB: boot/initrd.img-2.6.31-14-generic
  95.4GB: boot/initrd.img-2.6.31-16-generic
  95.4GB: boot/vmlinuz-2.6.28-11-generic
  95.4GB: boot/vmlinuz-2.6.28-15-generic
  95.4GB: boot/vmlinuz-2.6.28-16-generic
  95.4GB: boot/vmlinuz-2.6.31-14-generic
  95.4GB: boot/vmlinuz-2.6.31-16-generic
  95.4GB: initrd.img
  95.4GB: initrd.img.old
  95.4GB: vmlinuz
  95.4GB: vmlinuz.old

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=6ca88b59-7786-4093-a659-9250d7833701 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=6018f9f7-c388-431b-b46a-d01f025da58d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=============================== sda9/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda9 during installation
UUID=528fd453-2f7c-4374-b1fb-4ade94132ec5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda10 during installation
UUID=cc2d3472-d98a-4930-b705-02ac898cb8f5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

---

### Post by drs305 on 2010-01-15
grifan526,

You don't have a grub.cfg file in sda5, which is where Grub 2 is looking for the configuration file.

You can follow the guide for booting from the rescue mode from the following link, or try these commands to boot to the Ubuntu 9.10 version found on sda5.
[https://help.ubuntu.com/community/Grub2#Using%20CLI%20to%20Boot]("https://help.ubuntu.com/community/Grub2#Using%20CLI%20to%20Boot")

From the rescue prompt:
```

set root=(hd0,5)
linux /boot/vmlinuz root=/dev/sda5 ro
initrd /boot/initrd 
boot

```

This should boot the Kamric 2.6.31-16-generic kernel.

Once you get to the Desktop, reinstall Grub 2 to create the grub.cfg file in the appropriate location. Although the first step may not be necessary, I'd reinstall Grub 2 since you still have the residual menu.lst and no grub.cfg.
```

sudo apt-get install --reinstall grub-pc grub-common
sudo grub-install /dev/sda
sudo update-grub
```

Once everything is fixed and  you can get into Ubuntu, if you still can't boot to windows, refer to this guide:
[How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)]("http://ubuntuforums.org/showthread.php?t=1014708")

Added: Note you can use the same swap partition for all your linux distros, a separate swap is not needed for each one.

---

### Post by grifan526 on 2010-01-15
Thank you so much that did it

---

### Post by RACazorla on 2010-01-15
I'm having a similar problem, I'm getting a message of

error: no such device: 86d32ee3-aec6-490b-8dab-e5cfff9c7af9
Press any key to continue

which takes me back to the Grub menu. At first thought that I had done something wrong when I installed the Ubuntu (Dual boot fresh install), so I erased my HD including XP just to be sure, and installed it by itself, but got the same message again. I killed it again and reinstalled XP and installed 9.10, and the error still there. Reading all you previous posts, I tried the some of the recommended none worked. Below is a copy of my grub.cfg please help
### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,6)
search --no-floppy --fs-uuid --set 86d32ee3-aec6-490b-8dab-e5cfff9c7af9
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 86d32ee3-aec6-490b-8dab-e5cfff9c7af9
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=86d32ee3-aec6-490b-8dab-e5cfff9c7af9 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 86d32ee3-aec6-490b-8dab-e5cfff9c7af9
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=86d32ee3-aec6-490b-8dab-e5cfff9c7af9 ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 1608e8fb08e8daaf
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###

---

### Post by drs305 on 2010-01-15
RACazorla

In your case, you can try to alter the entry in the Grub 2 menu.

Boot to the menu, highlight the first entry, then press "e" to enter the editing mode. Remove this line by holding down the DEL key at the start of the line:
> 
search --no-floppy --fs-uuid --set 86d32ee3-aec6-490b-8dab-e5cfff9c7af9

Next move to this line and change it to:
> 
linux /boot/vmlinuz-2.6.31-14-generic root=UUID=86d32ee3-aec6-490b-8dab-e5cfff9c7af9 ro quiet splash
*and change it to*
linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda6 ro quiet splash

Then CTRL-x and see if it boots.

If not, you can try running the commands I gave in post #41, but use *sda**6*** instead of *sda5*.

If you still can't get it to boot, provide the results of the boot info script.  (See #37).

---

### Post by RACazorla on 2010-01-15
That did it, how do I make this change permanent, I tried sudo gedit /boot/grub/grub.cfg and made the changes but when I try to save it said the drive is protected

---

### Post by drs305 on 2010-01-15
> **RACazorla said:**
> That did it, how do I make this change permanent, I tried sudo gedit /boot/grub/grub.cfg and made the changes but when I try to save it said the drive is protected

Grub 2 doesn't really want you to edit the grub.cfg file. It's read only and created by various scripts, especially those in the /etc/grub.d folder.

Since it appears that your UUIDs are a problem in the Grub 2 menu, run this command and note the UUID of the Ubuntu partition.

```
sudo blkid -c /dev/null
```

Next, run:
```

sudo update-grub

```
Then check the UUIDs in /boot/grub/grub.cfg to see if they match. Specifically, you are looking for the stanzas that begin with "menuentry". You can check with this command:
```

gksu gedit /boot/grub/grub.cfg

```

Hopefully the update-grub command found the correct UUIDs and changed the grub.cfg file to match.

There are links in my signature line that cover what is different in Grub 2. (GRUB2, G2 Basics)

---

### Post by RACazorla on 2010-01-16
I'll like to say problem fixed but still the problem is there, It seems to be the line 
search --no-floppy --fs-uuid --set 86d32ee3-aec6-490b-8dab-e5cfff9c7af9
after I erase it and do a Ctrl-X boot it works. Also I went ahead and ran update manage, to see if that would solve it, but no luck either. Any other suggestions?

---

### Post by meierfra. on 2010-01-19
RACazorla:
Try this:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search)

---

### Post by KEBDARGE on 2010-01-20
Same problem here:

Wubi on a Compaq 6720s with windows Vista installed…

I am a real newbie to all this and all the posts here just blow my mind. 
Is there someone who has a straight forward solution for this?

---

### Post by linsol on 2010-01-20
I finally got mine to boot. Here's what I did
what I used is:

sh:grub>set root=(loop0)
sh:grub>linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro
sh:grub>initrd /boot/initrd.img-2.6.31-14-generic
sh:grub>boot

Except I used 2.6.31-17-generic in place of -14
I found that the latest update installed -18-generic which broke my boot to ubuntu. After retyping the above in again it booted up then I used the package manager and removed all -18 installs. Then I ran sudo update grub, then rebooted. Works great.
Don't think I will install anymore -whatever-generic updates!!!!!

---

### Post by meierfra. on 2010-01-20
linsol: You have been hit by a bug in Grub2. To avoid this problem in the future follow these direction from the author of Wubi:

[http://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210](http://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210)

---

### Post by meierfra. on 2010-01-20
KEBDARGE:  You probably have been hit by a bug in Grub2.

 Follow these direction from the author of Wubi:

[http://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210](http://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210)

If that did  not cure your problem, start a new thread and describe exactly what is happening  during boot up.

---

### Post by KEBDARGE on 2010-01-20
it worked when I replaced the wubi file in windows. thnx anyway!

---

### Post by jim0watkins on 2010-01-21
> **meierfra. said:**
> grifan526: Let's check out your setup:    Boot from an Ubuntu Live CD and follow these [instructions]("http://ubuntuforums.org/showthread.php?t=1291280"). 

I have the "GNU GRUB version 1.97~Beta4... "minimal BASH-like line editing is supported..." problem... can anyone give me a hint about what to do?  I've already tried a bunch of solutions given in this thread, but still no solution.  Thanks for the help.

```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     BootPart in the file /NST/nst_grub.mbr is trying to 
                       chain load sector #202290543 on boot drive #1
    Operating System:  Windows Vista
    Boot files/dirs:   /NST/menu.lst /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda2/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub 1.97
    Boot sector info:  Grub 1.97 is installed in the boot sector of sda6 and 
                       looks at sector 217003471 of the same hard drive for 
                       core.img, core.img is at this location on /dev/sda and 
                       looks on partition #6 for /boot/grub.
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd45b9fb3

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048     3,074,047     3,072,000  27 Hidden HPFS/NTFS
/dev/sda2    *      3,074,048   198,386,547   195,312,500   7 HPFS/NTFS
/dev/sda3         220,516,352   234,440,703    13,924,352  17 Hidden HPFS/NTFS
/dev/sda4         198,386,685   220,508,189    22,121,505   5 Extended
/dev/sda5         198,386,748   202,290,479     3,903,732  82 Linux swap / Solaris
/dev/sda6         202,290,543   219,865,589    17,575,047  83 Linux
/dev/sda7         219,865,653   220,508,189       642,537  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/loop1: UUID="3ab8ba1b-a689-4791-9951-0e53f662d408" TYPE="ext4" 
/dev/sda1: UUID="CAF66A08F669F4DB" LABEL="TOSHIBA SYSTEM VOLUME" TYPE="ntfs" 
/dev/sda2: UUID="AEC07120C070F047" LABEL="S3A6134D002" TYPE="ntfs" 
/dev/sda3: UUID="B0E477B9E4778100" LABEL="HDDRECOVERY" TYPE="ntfs" 
/dev/sda5: UUID="dd20f1ad-0307-407b-8b0b-3787aa76ddcd" TYPE="swap" 
/dev/sda6: UUID="f53d071b-5cdf-4f9f-afcd-31399a38a0be" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: UUID="896a354a-f0fc-4dfd-962b-739b221b4246" SEC_TYPE="ext2" TYPE="ext3" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


============================== sda2/NST/menu.lst: ==============================

# NeoSmart NeoGrub Bootloader Configuration File
#
# This is the NeoGrub configuration file, and should be located at C:\NST\menu.lst
# Please see the EasyBCD Documentation for information on how to create/modify entries:
# [http://neosmart.net/wiki/display/EBCD](http://neosmart.net/wiki/display/EBCD)

=========================== sda6/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,6)
search --no-floppy --fs-uuid --set f53d071b-5cdf-4f9f-afcd-31399a38a0be
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set f53d071b-5cdf-4f9f-afcd-31399a38a0be
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=f53d071b-5cdf-4f9f-afcd-31399a38a0be ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set f53d071b-5cdf-4f9f-afcd-31399a38a0be
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=f53d071b-5cdf-4f9f-afcd-31399a38a0be ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda2)" {
	insmod ntfs
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set aec07120c070f047
	chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda3)" {
	insmod ntfs
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set b0e477b9e4778100
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=f53d071b-5cdf-4f9f-afcd-31399a38a0be /               ext3    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=896a354a-f0fc-4dfd-962b-739b221b4246 /home           ext3    defaults        0       2
# /windows was on /dev/sda2 during installation
UUID=AEC07120C070F047 /windows        ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
# swap was on /dev/sda5 during installation
UUID=dd20f1ad-0307-407b-8b0b-3787aa76ddcd none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 103.5GB: boot/grub/core.img
 103.5GB: boot/grub/grub.cfg
 103.5GB: boot/initrd.img-2.6.31-14-generic
 103.5GB: boot/vmlinuz-2.6.31-14-generic
 103.5GB: initrd.img
 103.5GB: vmlinuz
```

---

### Post by RACazorla on 2010-01-21
[http://sourceforge.net/apps/mediawik...roblems:search]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search")
that worked thank you

---

### Post by meierfra. on 2010-01-21
jim0watkins:  

>  I have the "GNU GRUB version 1.97~Beta4... "minimal BASH-like line editing is supported..." problem... 

Does this happen when you try to boot Wubi, or when trying to boot Ubuntu 9.10?

 The Wubi file system seems to be corrupted, at least the script was not able to mount it. So you should run a file system check. I can give you instructions for  that. But you also have Ubuntu 9.10 installed in /dev/sda6, so I am not  sure whether you are still using Wubi.

Are you able to boot Ubuntu 9.10?   It looks like you are booting Ubuntu 9.10 via EasyBCD. And as far as I can see, EasyBCD and Grub are configured correctly.

---

### Post by meierfra. on 2010-01-21
[QUOTE=RACazorla]that worked thank you[/QUOTE]
Great. Have fun with Wubi.

---

### Post by kenneth999 on 2010-03-08
Help needed! I got hit by the same problem, after installing some updates, now my ubuntu said: "gnu grub version 1.97 beta 4" blah... then stay with "sh:grub>". I have tried the grub2 rescue, but after typing "boot", it showed a bunch of commands, then, bom, restart the computer, and i was trapped to the "sh:grub>" again. 
 
here is my wubi configuration: 
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda2/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd0f4738c

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        96,389        96,327  de Dell Utility
/dev/sda2    *         96,390   156,232,124   156,135,735   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x104a2b27

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   625,137,344   625,137,282   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       c12d2bc0-325e-4f6d-8629-ad0f61fab133   ext4                                     
/dev/sda1        07D7-0916                              vfat       DellUtility                   
/dev/sda2        08E0A250E0A243B2                       ntfs                                     
/dev/sdb1        B8CC53A1CC535928                       ntfs       data                          

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


================================ sda2/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn 
C:\wubildr.mbr = "Ubuntu" 

======================== sda2/Wubi/boot/grub/grub.cfg: ========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 08e0a250e0a243b2
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-20-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 08e0a250e0a243b2
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-20-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 08e0a250e0a243b2
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-19-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 08e0a250e0a243b2
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-19-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 08e0a250e0a243b2
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 08e0a250e0a243b2
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Dell Utility Partition (on /dev/sda1)" {
    insmod fat
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 07d7-0916
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Microsoft Windows XP Professional (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 08e0a250e0a243b2
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

============================= sda2/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0

/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

================= sda2/Wubi: Location of files loaded by Grub: =================


   6.7GB: boot/grub/grub.cfg
   4.2GB: boot/initrd.img-2.6.31-14-generic
   4.5GB: boot/initrd.img-2.6.31-19-generic
   6.7GB: boot/initrd.img-2.6.31-20-generic
   2.1GB: boot/vmlinuz-2.6.31-14-generic
   1.2GB: boot/vmlinuz-2.6.31-19-generic
   3.8GB: boot/vmlinuz-2.6.31-20-generic
   6.7GB: initrd.img
   4.5GB: initrd.img.old
   3.8GB: vmlinuz
   1.2GB: vmlinuz.old
```

---

### Post by kenneth999 on 2010-03-08
problem solved at my last try with method posted before:
[http://bugs.launchpad.net/ubuntu/+so...9/comments/210]("http://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210")


> **kenneth999 said:**
> Help needed! I got hit by the same problem, after installing some updates, now my ubuntu said: "gnu grub version 1.97 beta 4" blah... then stay with "sh:grub>". I have tried the grub2 rescue, but after typing "boot", it showed a bunch of commands, then, bom, restart the computer, and i was trapped to the "sh:grub>" again. 
 
here is my wubi configuration: 
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda2/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd0f4738c

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        96,389        96,327  de Dell Utility
/dev/sda2    *         96,390   156,232,124   156,135,735   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x104a2b27

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   625,137,344   625,137,282   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       c12d2bc0-325e-4f6d-8629-ad0f61fab133   ext4                                     
/dev/sda1        07D7-0916                              vfat       DellUtility                   
/dev/sda2        08E0A250E0A243B2                       ntfs                                     
/dev/sdb1        B8CC53A1CC535928                       ntfs       data                          

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


================================ sda2/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn 
C:\wubildr.mbr = "Ubuntu" 

======================== sda2/Wubi/boot/grub/grub.cfg: ========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 08e0a250e0a243b2
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-20-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 08e0a250e0a243b2
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-20-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 08e0a250e0a243b2
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-19-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 08e0a250e0a243b2
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-19-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 08e0a250e0a243b2
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 08e0a250e0a243b2
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Dell Utility Partition (on /dev/sda1)" {
    insmod fat
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 07d7-0916
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Microsoft Windows XP Professional (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 08e0a250e0a243b2
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

============================= sda2/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0

/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

================= sda2/Wubi: Location of files loaded by Grub: =================


   6.7GB: boot/grub/grub.cfg
   4.2GB: boot/initrd.img-2.6.31-14-generic
   4.5GB: boot/initrd.img-2.6.31-19-generic
   6.7GB: boot/initrd.img-2.6.31-20-generic
   2.1GB: boot/vmlinuz-2.6.31-14-generic
   1.2GB: boot/vmlinuz-2.6.31-19-generic
   3.8GB: boot/vmlinuz-2.6.31-20-generic
   6.7GB: initrd.img
   4.5GB: initrd.img.old
   3.8GB: vmlinuz
   1.2GB: vmlinuz.old
```

---

### Post by Dr Droid on 2010-03-11
Thanks [meierfra.]("http://ubuntuforums.org/member.php?u=552151") for the solution! Thanks to your fix I was up and running in minutes. For the most part, I thought that I needed to use grub rescue. However I'm curious as if I will need to do it again or is this wubildr file going to keep me going for any future kernel updates?

edit- 

Originally I had found a bug report that initially posted the fix, so I never clicked on your link above. It sounds like you are unsure if the patch is stable and I would like to say that I used it after upgrading to 2.6.31-20-generic and it worked successfully

---

### Post by meierfra. on 2010-03-11
> However I'm curious as if I will need to do it again 
No, you don't. It's a permanent fix.

---

### Post by docpavi80 on 2010-03-11
I had a same problem with wubi ubuntu 9.10 installation through windows. After update, i was getting GRUB 1.97~Beta4 Error. I tried everyting and finally replacing wubildr in windows c:/ section worked for me. 
[https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210](https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210)
link for the solution

---

### Post by danadn on 2010-04-03
^^^
That worked!! thanks:D!!!

---

### Post by sam2650 on 2010-04-20
hey there ! 
i loved using ubuntu ! 
but i have a problem and when i restart it used to give me 2 choices boot into Vista and one into ubuntu but there was a problem for some reason it it goes into the system prompt gives me a message that says : GNU GRUB version 1.98-1ubuntu1
Minimal BASH-like line editing is supported. for the first word, TAB lists possible command completions.
Anywhere else TAB lists possible device or file completions.

grub> _ 
like that PLEEAASE HELP ! !

---

### Post by milkyway538 on 2010-04-20
I have a similar problem of seeing the GRUB prompt .... I have found a way around it but it is not a final solution as I would like to know how to avoid this in the first place.
Here is my problem with dual boot XP & Ubuntu.
My system: Dell portable Inspirons (1.6GHz, 1G RAM, 60GB HD) with Window XP and an external HD 500GB
I have recently installed Ubuntu v9.10 from live CD on the external drive (USB connected to PC). I use the menu driven installation (WUBI method, provided by the live CD) and I selected the external drive as the place for Ubuntu. I did not do any partitioning on this external drive before hand.

After installation, when power up the system (reboot) I see the option Ubuntu after the XP (as expected !), but after selecting Ubuntu, the system does not start up Ubuntu but it goes to grub> command screen.

Then by chance I have found out that if I type the commands:
grub> root ==> reply with (hd0,2) 
grub> reboot (hd0,2) then the system reboots and choosing Ubuntu option again will properly boot my PC into Ubuntu enviroment ... i.e. I can see different kernel versions (generic mode, recovery mode etc...) and then Ubuntu runs correctly 

Now my question is: 
1) how can I get rid of the intermmediate process of typing the command 'reboot (hd0,2)' when I expect the system should boot correctly from the first try ?
someone tells me the problem may lie with USB detection when first power up ??

2) After I experiment with changing the grub> command to 'reboot (hd1,1)' when I encounter the first boot issue (mentioned above) in order to see understand the issue.

However after rebooting with this command, the first Kernel option on the list (version .20 (generic) does not work anymore (error message of synchronisation to hard disk ??!!)

So I go back to reboot with command 'reboot (hd0,2)' and then choose the older kernel version (.14 generic)) and Ubunti works again.

So how can I correct the first Kernel version ?

---

