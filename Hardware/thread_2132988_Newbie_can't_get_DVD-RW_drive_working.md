---
title: "Newbie can't get DVD-RW drive working"
date: 2013-04-06
forum: Hardware
---

### Post by tizzidale on 2013-04-06
OK. I feel so lost in Linux, but I'm determined to learn. Fresh install of Ubuntu 12.04 and I can't use my DVD-RW, either to read or write. Should this be simpler?  :)  It probably is, but I'm not seeing it. Any help would be appreciated.

---

### Post by carl4926 on 2013-04-06
Does it physically open and close?
If Yes, When you put in a music CD, what happens?
Define - Not working?!

---

### Post by glln0v on 2013-04-06
Hi, tizzidale. I felt lost in ubuntu at first too cause all i knew was windows. you'll be glad you stick with it cause its much better than windows once you get familiar.

Can you provide some more info? It could be that you are missing a driver.

When you put a cd/dvd into the tray, does an entry appear in Nautilus under the "Devices" heading?

What computer are you using? Desktop? Laptop w/ built-in? Laptop w/ external optical drive?

---

### Post by tizzidale on 2013-04-06
The drive works normally outside of Ubuntu. It opens and closes, and it's what I loaded Linux using. When I insert a disk, nothing appears in the file browser (I'm assuming this is Nautilus?) I'm using a Lenovo 3000 N200 laptop.  The drive is a DVD-RW.

---

### Post by carl4926 on 2013-04-06
I take it you didn't install using that drive then?

---

### Post by tizzidale on 2013-04-06
Yes, I did install using the drive.

---

### Post by carl4926 on 2013-04-06
> **tizzidale said:**
> Yes, I did install using the drive.

That seems odd then?

Are you sure you are not missing something? I'm not in a position to just test this myself ATM, people are asleep close to me (I seldom use the optical drive myself) - But I will check this later. 

So the drive does open and close in Ubuntu but you don't see anything that suggests it's working (for Eg when you put a Video DVD in there)?

---

### Post by tizzidale on 2013-04-07
I'm absolutely sure I'm missing something. I just don't know enough to know what exactly. I know I used this drive to install Linux. I know that it works mechanically. I know that I can place a music CD, data CD, or DVD - doesn't matter- nothing occurs.

---

### Post by carl4926 on 2013-04-07
If insert Eg the Ubuntu DVD - Nautilus opens auto and I see
[[img]http://s20.postimg.org/ueaw7ab1l/Screenshot_from_2013_04_07_05_13_37.jpg[/img]](http://postimg.org/image/ueaw7ab1l/)

---

### Post by gechxx on 2013-04-07
Hi !

Im also new to linux/ubunto, and have problem with getting the DVD/CD drive, possibly I should make new thread ?

Anyways; I have booted from USB-stick. I have a tower/desktop PC (dell dimemsion 5000) that has no good OS on HDrive. 

Now that I have successfully booted from USB/Ubunto, the "activities" does not give any clue about the DVD-drive

In the "help" there is a reference that "activities" should include some choice "disk drives" (or so, I dont have access to screen just now, since it is used for this current PC);  however that choice is nonexistent !! , under that there would be some reference to volumes, but failing to find any such.

Thanks for any advice on how to assess status of DVD/CD. Is there a possibility that the Motherboard is faulty for the buss connecting the drive ? or something 

BR georg

---

### Post by BartlettMagic on 2013-04-07
i am having the exact same problem.  everything works perfectly EXCEPT DVD's.  i started a question at Launchpad that didn't get much for responses. it's here: [https://answers.launchpad.net/ubuntu/+question/226035](https://answers.launchpad.net/ubuntu/+question/226035)

here's a copy/paste of the gist of my prob: 

ubuntu 12.04 lts
mem: 748.2MiB
processor: Intel Pentium(R) 4 CPU 2.66GHz
graphics: unknown
OS type: 32-bit
 HP Media Center PC 864n
 
medibuntu repositories have been added, as well as libdvdcss2.

 
i am not able to read DVD's, commercial or written.  the following  examples are from VLC media player; keep in mind, NO other  player/software (system movie player, WinFF, Arista Transcoder, AcidRip)  can read the drive.  this has been tested with many different DVD's.

 
when i insert a DVD, no prompts appear. my settings say that i should be asked what to do with the DVD.

 i open VLC, navigate Open Media>Disc>Play, and get the following error:
 
Playback failure:
DVDRead could not open the disc "/dev/dvd".
Your input can't be opened:
VLC is unable to open the MRL 'dvd:///dev/dvd'. Check the log for details.

 
most solutions i found in my searches described changing the device  path (from /dev/dvd to /dev/sr0, /dev/sg1, etc).  NONE of the options  present work.

 
when i use [sudo lshw -C disk; sudo lshw -C drive], i get:

 
*-disk
       description: ATA Disk
       product: WDC WD1600BB-55R
       vendor: Western Digital
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 20.0
       serial: WD-WCANMH588953
       size: 149GiB (160GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=000934c3
  *-cdrom:0
       description: DVD reader
       product: DVD Writer 200j
       vendor: HP
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/sr0
       version: 1.36
       serial: E
       capabilities: removable audio cd-r cd-rw dvd
       configuration: ansiversion=5 status=nodisc
  *-cdrom:1
       description: CD-R/CD-RW writer
       product: CD-RW SOHR-5238S
       vendor: LITE-ON
       physical id: 0.1.0
       bus info: scsi@1:0.1.0
       logical name: /dev/cdrom1
       logical name: /dev/cdrw1
       logical name: /dev/sr1
       version: 4S09
       capabilities: removable audio cd-r cd-rw
       configuration: ansiversion=5 status=nodisc

 
(sidenote:  when the above command was entered, a regular commercial DVD, US-region1? was in the drive.)

 
you now know as much as i do.  my google-fu is apparently weak, as  nothing i have found in any of my searches solves this problem.  my  ultimate goal is to backup my DVD collection to my newly purchased  external drive.

 
FYI- i am a copy/paste terminal user.  i don't know command line language.

 
i will be happy to enter commands and post results.

also, the drive labelled 'CD-R/CD-RW writer - CD-RW SOHR-5238S' works  perfectly fine with audio CD's, both commercial and written.

tested the (DVD) drive with written and commercial CD's.  they worked  perfectly, all of the appropriate prompts appeared and they played  successfully.

---

