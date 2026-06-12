---
title: "Ubuntu wont detect my Harddrive..at all"
date: 2008-08-16
forum: General Help
---

### Post by Drood on 2008-08-16
HI, I just installed Ubuntu yesterday and so far I like it alot.My problem begins when tryingt o recover stuff that was on my second hard drive.Ubuntu wont detect the ahrd drive at all, i talked to several ppl in the #ubuntu mirc channel but none of them could help me solve this (despite trying ALOT of solutions).

I have a ECS KA3 MVP MOtherboard
1 IDE 80gb hard drive (where ubuntu is installed working fine)
1 SATA 120gb Hard drive that ubuntu wont detect, it shows up in the BIOS and windows was reading it perfectly fine.
The Sata hard drive is a WD Caviar 1200js.

I am not familiar at all with linux/ubuntu so please try to be overly clear when suggesting solutions or asking questions. Thanks

ALso one of the guys in the mirc channel told me to show this on the forum:
[http://paste.ubuntu.com/37920/](http://paste.ubuntu.com/37920/)

Please help, i dont want to go back to Windows.

---

### Post by coffeecat on 2008-08-16
Your attachment is showing the contents of your /etc/fstab file, which is used by Ubuntu to mount HD partitions and other devices on bootup. There are two (presumed) NTFS partitions which it's very unhappy with. I've never seen such a comment in a fstab file before.

My guess is that the fstab file needs editing for those partitions. We need some more information. Open a terminal and post the output of:

```
sudo fdisk -l
```(That's a lower-case L, not one.) That will show us the HD partitions that the system can see whether or not they are mounted.

And post the output of:

```
sudo blkid -c /dev/null
```That will give us the UUIDs (unique identifiers) for each partition so we can see whether the UUIDs in fstab are correct or not.

**Edit:** Just had another thought. We need to see if the mountpoints for the NTFS partitions have been created. Post the output of:

```
ls /media
```

---

### Post by Drood on 2008-08-16
[http://paste.ubuntu.com/37976/](http://paste.ubuntu.com/37976/)

Theres the outcome of all 3 commands you asked for.
Yeah thats what everyone ive showed it to say, ppl keep telling me this is a weird problem..

---

### Post by TenPlus1 on 2008-08-16
Go into System -> Administration -> Synaptic Package Manager

Click on Search (look in name) and type NTFS in the search box <enter>

Select to install:

  - NTFS-3G
  - NTFSPROGS
  - NTFS-CONFIG and press APPLY

Go into Applications -> System -> NTFS Configuration Tool

Tick both boxes (one may be greyed), now you can read/write NTFS partitions/drives...

Go here for any mounting problems:

[http://ubuntuforums.org/showthread.php?t=142481](http://ubuntuforums.org/showthread.php?t=142481)

---

### Post by Drood on 2008-08-16
I already ahd all thsoe tools except for NTFSPROGS, coing into the NTFS configuration tool was suggested to me in the irc channel yesterday, when i click enable or ok or whatever nothing happens. Ill follow the instructions on the link you provided. Thanks

---

### Post by Drood on 2008-08-16
Diidnt change anything.

---

### Post by vivichrist on 2008-08-16
this program saved me from nervous breakdown, in gparted program I managed to delete my partition table by using the disklabel function, I've done some stupid things in my time but by alibaba I just about gave myself a heartattack. but without farther a due [http://www.cgsecurity.org/wiki/TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") but this only works if the hardrive is accessable... in which case I'd say its a bios problem or you have the jumpers set wrong.

---

### Post by Drood on 2008-08-16
Ill try it, although ubuntu completely negletcs my hard drive, ill double check jumper settings.

---

### Post by Drood on 2008-08-16
Please help, i dont know what else to do.

---

### Post by coffeecat on 2008-08-16
Sorry I wasn't able to respond earlier. The outputs of fdisk and blkid show that the SATA drive is not being detected at all, not that it isn't being mounted.

Since it is being detected in the BIOS, but not in Ubuntu, I wonder if this is a SATA controller driver problem. A quick google shows that your motherboard came out a couple of years ago and has the ATI Radeon Xpress 3200 chipset. I have no experience of ATI chipsets, but I would have thought that there would be kernel drivers for them by now.

Try googling and/or searching this forum for your particular motherboard. If it's a chipset/driver issue this would be relevant and you might come up with something. It would be useful to know the name of the actual SATA controller for you to google/search that, so post the output of:

```
sudo lspci
```For instance, lspci in my machine with an nvidia chipset contains these two lines:

> 00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)

Look for something similar (obviously ATI, not nVidia) and that might give us a lead.

---

### Post by revolutio on 2008-08-16
I'm not sure if this will be of help to you but the NTFS hard drives I use in Linux do occasionally disappear entirely, despite being recognized by the BIOS.  This happens if Windows crashes on me or I just lose power while in Windows.  The drives won't appear again until I boot into Windows and restart properly.

Also to test whether it is a problem with just Ubuntu, you could try the live-CD of another Linux distribution such as openSUSE or Fedora.

---

### Post by Drood on 2008-08-16
Hey, thanks for taking your time in trying to help me.
here is the output of the code you gave me.

[http://paste.ubuntu.com/38074/](http://paste.ubuntu.com/38074/)

Ill try doing some research on my chipset, i too thought it might be a driver issue. WOuld i be looking for a driver for the sata hdd itself, the chipset in my mobo, or for what exactly. Also where can i check if its being detected at all, i need to be able to tell if when i change someting the hdd is bveing recognized or not.
THanks

---

### Post by Drood on 2008-08-16
THats a good suggestion. Ill try that.ALso i might try reinstalling windows, i need to backup all that stuff anyways, thanks.

---

### Post by Drood on 2008-08-16
OK i got this program called disk space analyzer it says i have 140gb free, so does that mean it is recognizing the 120gb hdd, cause otherwize why would it show that much? 
[IMG]http://img397.imageshack.us/img397/3259/screenshotdiskusageanalbl5.png[/IMG] 

Note: This is after i made some changes in the BIOS.

---

### Post by coffeecat on 2008-08-17
> **Drood said:**
> Note: This is after i made some changes in the BIOS.

Progress, I think. Ubuntu must be detecting the SATA now if you're getting that output. By the way, in response to your earlier post, I was thinking of the SATA controller specifically - have a look on your output of lspci - but it seems as if the BIOS change has half-solved the problem.

If you haven't already, install the application Gparted from Synaptic. After it's installed, you'll find it in System > Administration > Partition Editor. It will show you your partition layout for both drives and we can see why there's a discrepancy between the 120 and 145GB. Your SATA will probably show up as sdb - there's a button top-right with drop-down menu to choose whichever drive to show in the main window. Post a screenshot of the Gparted window if you want.

---

### Post by Garratt on 2008-08-17
basicaly when you open your home folder, or <your name> folder

eg goto Places ---> home folder -or whatever it opens up file browser
... , there will only be one other HDD listed under
<home>
<Desktop>
<File System>
<other Hdd>
<Network services>
<Rubish bin> 

or something to that effect, i to run 2 hdd's but only one show's up there that is because the way linux file system works, the disk space analyzer does count both hdd's as one... its dumb BUT

if you click EDIT ---> PREFERENCES

it will actually list the 2 hdd's in your computer.

you just need to get your head around the fact that this is not micro-soft windows, and the file systems are a lot different, 

eg: when you install a program, normally in MS windows, it would goto program files, and 1 or 2 files would goto win>system and registery.

on linux its a bit different, you got executables in 1 folder, system files in another, and objects all over the place... i'm not the best to explain this i'm new to linux to but back to the point.

yea.. you don't see the hdd that linux is on in the file browser... but it is there!
<File System> is the HDD... its just not C: like windows, or recognisable as a hdd, it should still have a media icon tho.

---

### Post by Garratt on 2008-08-17
i uploaded the full jpg f you need to see it larger...

notice the file browser as well as my 80gb HDD + 600gb HDD

[IMG]http://img209.imageshack.us/img209/4208/screenshotju1.jpg[/IMG]

---

