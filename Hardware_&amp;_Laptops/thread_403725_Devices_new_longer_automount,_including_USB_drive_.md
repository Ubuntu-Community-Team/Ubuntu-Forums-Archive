---
title: "Devices new longer automount, including USB drive and mmcdisk"
date: 2007-04-07
forum: Hardware &amp; Laptops
---

### Post by ajkessel on 2007-04-07
At some point recently automounting just stopped working for me. udevmonitor sees devices appear and disappear, and pmount/pumount work fine manually, but devices are not appearing on their own. I have no idea what might have changed or why it's not working. Following advice in another thread, I purged and reinstalled the following packages, but still no luck:

hal hal-device-manager hwdb-client update-notifier hwdb-client-common ivman gnome-volume-manager hwdb-client-gnome gnome-power-manager

It used to be inserting an SD card mounted /media/mmcdisk automatically; now it doesn't. Similarly, the external USB drive used to startup at /media/usbdisk, now it doesn't.

Any ideas on how to troubleshoot? I am using almost all Edgy packages except the kernel (2.6.20-13-lowlatency), but I don't think the kernel is the problem since the devices are all appearing fine and being detected by udevmonitor. I have not changed any udev or hal config settings. The devices are set to automount/run in the Gnome settings for "removable drives and media."

---

### Post by uranus0206 on 2007-04-07
I have same problem after upgrading my fesity recently....

but i have another problem that i do not know how to mount manually....

i don't know which device in /dev    i have to choose

---

### Post by joehill on 2007-04-08
I have the same problem--external usb drives no longer mount automatically after upgrading to Feisty.  I'd be glad if someone could tell me how to get it up and working again!  It's a pain to have to manually mount usb devices every time.

---

### Post by Bloch on 2007-04-19
I've just updated to Feisty (final version) and automounting doesn't work now, neither for my external vfat hard drive nor for memory sticks.

---

### Post by mogwai on 2007-04-20
I am having some automount problems as well.
I started with Feisty Beta. It didn't automount my DVD drive.
If I go to Places -> Computer and double-click on DVD/CD-ROM drive, it says there is no disc in the drive.
If I go to a terminal and type "sudo mount /media/cdrom0", it successfully mounts the drive.
If I go back through Places -> Computer and double-click on CD-ROM drive, it still says there is no disc. Also, I do not get an icon on my desktop.
I have updated less than an hour ago and I still have this problem.

So, i am have to navigate through the filesystem (Computer->Filesystem->media->cdrom0) to read the content of my CD. Also, I need to keep a terminal window open so I can mount/umount the drive.

I don't know if USB is working as I dont have a USB Drive to test.

Any ideas?  :confused:

---

### Post by monkeytech on 2007-04-21
Hi all,
         I am having the same issues after upgrade to 7.04, USB key, USB external, SDcard no longer automount.
i've looked around and cant seem to find a fix for this problem, looks like its a bug in gnome-volume-manager maybe?

if anyone knows of a fix please let us know! 
[this fix i get errors]("http://ubuntuforums.org/showthread.php?t=398073&highlight=feisty+automount")

---

### Post by Arcade81 on 2007-04-21
I am having the same problem as well since upgrading to 7.04. My USB drive, memory stick and SD card will not automount., but I can manually mount the fine. I have never had this problem with previous versions of Ubuntu.

---

### Post by Hashi on 2007-04-21
I hate to sound like an echo, but I have the same problem (won't automount usb drive, ipod) using kubuntu feisty. Works fine in another computer running edgy.

---

### Post by Wight_Rhino on 2007-04-22
I wonder if problems people are having mounting different devices are related to this bug;

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/94119](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/94119)

---

### Post by amalzal on 2007-04-22
I think I have the same problem too. When I used my external hard disk (USB 2.0) in the previous Edgy version, an icon appeared in the desktop and it was perfect. But now in the Feisty version, no icon appears and I can't find the external hard disk anywhere. 

The SD card never worked, not in the Edgy version, not in the Feisty one.
I'm quite a newbie so any help would be appreciated.

---

### Post by rivera151 on 2007-04-22
Yep.  Another echo.  I can't get USB drives working.  I'll add something to this thread for the debuggers out there.  

Without anything connected, I type lsusb and I get:

```

ricardo@chupalaptop:~$ lsusb
Bus 003 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000

```

I plug in a USB drive and it doesn't get automounted.  However, the lsusb command now gives:

```

Bus 003 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 003: ID 0930:653d Toshiba Corp. 
Bus 002 Device 001: ID 0000:0000

```

The USB drive is a PNY Attaché, so I guess PNY = Toshiba.

I think this type of thread is about to become quite popular; something's definitely broken on the USB.

---

### Post by staticsage on 2007-04-22
Echo.

Maxtor external drive does not mount on boot, but if I unplug/plug-in or power cycle the drive it gets mounted.

Running Feisty on a Dell Precision M60.

---

### Post by bsc on 2007-04-22
Same problem after upgrading to 7.04.  lsusb sees devices, no auto mounting takes place.  :confused:

---

### Post by bsc on 2007-04-22
I just did a sudo aptitude reinstall of the packages the OP listed and now my automount works and all expected actions take place when I plug in my usb drive.

---

### Post by rivera151 on 2007-04-23
bsc:  Please specify which packages and what you mean by "what the OP listed" so I can try.

---

### Post by Despot on 2007-04-23
He means the packages listed in the original post, i.e:

[INDENT]hal hal-device-manager hwdb-client update-notifier hwdb-client-common ivman gnome-volume-manager hwdb-client-gnome gnome-power-manager
[/INDENT]

So the full system command would be:
[INDENT]sudo aptitude reinstall hal hal-device-manager hwdb-client update-notifier hwdb-client-common ivman gnome-volume-manager hwdb-client-gnome gnome-power-manager[/INDENT]

Doesn't work for me, unfortunately. :( USB flash drive isn't automounted, but CDs and cameras are automounting perfectly. My Palm synchronization seems to have stopped working as well, which is odd because it didn't have any problems when I first installed Feisty. :confused: 

The log files tell me that Udev is detected the drive quite nicely, so it'd seem that somehow the events are either not reaching gnome-volume-manager, or they're being ignored once they arrive. Any logging facilities available for g-v-m?

---

### Post by rivera151 on 2007-04-23
Despot: Well, I tried your command and it didn't work.  I don't know if my CD's were auto-mounting, but they do now.  But USB drives still do not hot plug.  I'm beginning to think the kernel's broken, since the silence from the higher up community is deafening.

---

### Post by fang2415 on 2007-04-23
Yep, something very strange is going on here.  I've tried doing some digging, but haven't found much.

First of all, I am running a beefed-up server installation of Feisty (sort of like Ubuntu Lite) and recently upgraded from Edgy, which had no automount problems.  The only packages I have installed from the list mentioned above are hal and ivman.  This makes me think that the problem is in hal, ivman, or the kernel.

Second, my usb drives *usually* aren't automounting.  I would describe the behaviour as erratic, though.  Sometimes, it works perfectly, sometimes imperfectly, usually not at all.

Here are the only patterns I've found, after a lot of testing:

1) Automount usually works only the first time after *either* the ivman daemon or the hald daemon is restarted.
2) It hardly ever works with my 250G Maxtor OneTouch usb drive, but usually works on the first try after a daemon restart with my 2G SanDisk Cruzer Micro usb drive.  If I restart the daemon, plug in the Maxtor, unplug it, and then plug in the SanDisk, the Maxtor usually doesn't work and the SanDisk does.
3) The usb device sometimes gets assigned to /dev/sda1 and sometimes to /dev/sdb1.  This doesn't seem to affect whether the automount works, but it does affect where it mounts.  /dev/sdb1 will mount to /media/usbdisk with my user id as the uid (same as it always did in Edgy), but /dev/sda1 will mount to /media/sda1 with uid=0 (root).

The dmesg output looks the same whether automount succeeds or fails -- the only difference is that on success I get a warning about mounting FAT drives with utf8.  Also, purging and reinstalling ivman and hal don't help.

At first I thought this was an ivman or hal bug, but 1) and 3) make me think this might be kernel-related.  If it was a hal-only or ivman-only problem, why would restarting *either* daemon help?  Granted, I don't know either why the kernel would care that a daemon had restarted and behave differently for only one mount afterwards...

I think a bug report should be filed for this on Launchpad, but I'm not sure which of these packages to file it under.  Anybody got any ideas?

Anyway, I hope that somebody who knows what they're doing better than I do will find this useful.  I can post my dmesg, ivman debug, or 1,000,000 pages of hal debug if you want, but I figured I'd keep the thread readable for now.

<disillusionedrant>
This is not very good.  This is two troublesome upgrades in a row.  I've still got bugs left from the Edgy upgrade that I haven't sorted out yet, plus a bunch of ACPI stuff that's never worked, and now this.  FSM help the Windows switchers who don't like to spend their time Googling bug reports...
</rant>

Here's hoping we can find a patch for this soon!

F2

---

### Post by rivera151 on 2007-04-23
Added to launchpad [here]("https://bugs.launchpad.net/ubuntu/+source/hal/+bug/86292") under **hal**.  Feel free to add some information to the thread.

---

### Post by staticsage on 2007-04-24
> **fang2415 said:**
> Second, my usb drives *usually* aren't automounting.  I would describe the behaviour as erratic, though.  Sometimes, it works perfectly, sometimes imperfectly, usually not at all.


That is the best way I would describe my problem. It is also with a Maxtor One Touch II 200GB. Sometimes it mounts right on boot. Other times I have to mount it manually, or unplug/plug in.

---

### Post by jimmah6786 on 2007-04-24
Just to add to this mess of no automounting.

I tried Ubuntu 6.06LTS and 6.10, versions of which automounting seems to work perfectly, and upgrading to 7.04 from either of them you lose the ability to automount USB devices. 

In regards to the CD automount. I had no trouble with any of the Ubuntu release in question.

Hope there is a fix to this soon, I wanna listen to my music on my HD without having to mount the drive myself LOL. 

-Jimmah

---

### Post by rivera151 on 2007-04-24
I have to post back that **my** problem with outomounting has been resolved; however it was auto inflicted to begin with.  I'll explain what happened in case someone goes through the same (doubtful).

I'm working Ubuntu amd64 Feisty on an HP laptop.  Those with one know how pleasant it is getting the embedded ATI accelerator and Broadcom wireless card working.  

Well, I got a vanilla kernel b/c ndiswrapper wouldn't work on Edgy 64 bit without one, and installing ndiswrapper the first time in Feisty didn't work.  So I got 2.6.20.7 (so it's close to Feisty's (2.6.20-15-generic), recompiled using [The Master Kernel Thread]("http://ubuntuforums.org/showthread.php?t=311158") and got ndiswrapper working.  I then got fglrx working too.

It was a couple of days later that I tried using the USB drive and noticed it wasn't mounting.  Thus my posts.  

I uninstalled fglrx AND ndiswrapper, and reverted back to the 2.6.20-15-generic kernel and guess what?  Automounting.  But if that's not enough, ndiswrapper was working too!  So I still can use my wireless!  :confused: 

Can somebody tell me if I did something wrong in my uninstall script?

```

sudo ndiswrapper -e bcmwl5
sudo modprobe -r ndiswrapper
sudo cd ~/wireless/ndiswrapper*
sudo make uninstall
sudo shutdown -r now

```

About the USB issue: I must have omitted something in recompiling my kernel.  Otherwise, there is a bug in the 2.6.20.7 kernel that hinders USB mounting (unlikely, but feel free to say so if that's your experience).  I hope this info is helpful to someone.

---

### Post by tonywhelan on 2007-04-25
> **ajkessel said:**
> At some point recently automounting just stopped working for me. udevmonitor sees devices appear and disappear, and pmount/pumount work fine manually, but devices are not appearing on their own. I have no idea what might have changed or why it's not working. Following advice in another thread, I purged and reinstalled the following packages, but still no luck:

hal hal-device-manager hwdb-client update-notifier hwdb-client-common ivman gnome-volume-manager hwdb-client-gnome gnome-power-manager

It used to be inserting an SD card mounted /media/mmcdisk automatically; now it doesn't. Similarly, the external USB drive used to startup at /media/usbdisk, now it doesn't.

Any ideas on how to troubleshoot? I am using almost all Edgy packages except the kernel (2.6.20-13-lowlatency), but I don't think the kernel is the problem since the devices are all appearing fine and being detected by udevmonitor. I have not changed any udev or hal config settings. The devices are set to automount/run in the Gnome settings for "removable drives and media."

I fixed this on my laptop with Edgy using the following:
```
sudo modprobe tifm_core
sudo modprobe tifm_sd

```
then inserted the card, got a dialog asking what to do with card.

Then added tifm_core and tifm_sd to file /etc/modules so they loaded at startup.

Sadly, having just upgraded to Feisty, this fix doesn't work for me now.

---

### Post by billyjoebob on 2007-04-27
Add me to the list of sorry suckers who "upgraded" to Feisty from Edgy.  My drives used to work, now they don't.  I have an external USB drive (sbf) that no longer automounts.  It is essentially an ATA drive connected via USB conversion.  I have not changed any jumper settings.

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10199    81923436    7  HPFS/NTFS
/dev/sda2           10200       19075    71296470   83  Linux
/dev/sda3           19076       19452     3028252+   5  Extended
/dev/sda5           19076       19452     3028221   82  Linux swap / Solaris

Disk /dev/sdf: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               2       24321   195350400    f  W95 Ext'd (LBA)
/dev/sdf5               2       24321   195350368+   7  HPFS/NTFS

I *see* sdf, it is a damn shame I can't get to the data on it.  When I try to mount it manually using:

sudo mount -t ntfs-3g /dev/sdf5 /media/usb -o defaults.umask=0  (I created a /media/usb directory)

I get:

NTFS signature is missing.
Failed to startup volume: Invalid argument
Failed to mount '/dev/sdf5': Invalid argument
The device '/dev/sdf5' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

I am definitely an uber-n00b at this.. does anyone know of a mount command that will work?  So far, substituting sdf for sdf5 has not worked either.  I know this is a valid (non-corrupt) NTFS partition.

I feel like this upgrade was definitely a downgrade.  If I ever get my drive mounted, I get to spend another night fixing the Beryl/XGL that broke as a result of my "upgrade".

-BJB

---

### Post by theferretguy on 2007-04-28
Yar the generic internal multi reader i had working 100% in edgy doesnt seem to work at all in feisty. In fact alot of stuff that worked in edgy i cant get to work in feisty :(

---

### Post by aristachus on 2007-04-29
I have moderate skill in terms of using Linux (about 4 months straight) and just upgraded to 7.04 on a new computer (I would like to thank the development team for the excellent job they have done, as everything worked out of the box).  Interestingly, earlier today I was able to read, mount, eject, browse the contents of and burn cds and dvds, although it seems immediately after burning a cd, I was no longer able to automount anything, and when I do mount a disk in su, I cannot open, or browse the contents, of this disk.  I am wondering if anyone knows either a fix to this problem, or which config files relate to cdrom drive so I can try to find one for my issue.  I realize that this isn't identical to the problems in this thread, but it is similar and perhaps a fix for one issue will be a fix for us all.

---

### Post by megamik79 on 2007-04-30
Add me to the no usb-automount list. It even does not appear in the lsusb nor lshw lists after plugging it (it works OK under Dapper in the same machine) and **no devs are created**.

The dongle is a common Kingston DTI/512 pendrive, and the mainboard is an Asus 7N8X-X (nVidia nForce2 chipset).

---

### Post by Tom Tiger on 2007-05-01
Same problem here, but only with my external USB 2.0 harddisk (which is ext3 and worked perfectly under 6.10),  mounting is no problem, but unmounting is impossible,  I can only unmount through the terminal and sudo umount /media/disk....

And on another of my systems, the cdrom seems to have disappeard, it still mounts automaticly but can not be unmounted through any gui, the drive applet doesn't see it.... but I can still unmount it manually.

---

### Post by leodp on 2007-05-01
I have similar problems here, on kubuntu feisty, kernel 2.6.20-12-generic #2 SMP
Only a bit more complex situation, due to my HDD partitioning.

I have an external USB disk with four partitions on it, that almost every time are mounted correctly as:
/dev/sda7            244598656 233698224  10900432  96% /media/disk
/dev/sda5            7052464     32812          6661408    1%   /media/disk-1
/dev/sda6            25197220   23341036    576208      98% /media/disk-2
/dev/sda1            15243312   12584064    1884920    87% /media/disk-3

But sometimes only one or two of them are automounted. 
If then I unmount it with the "safely remove" option on the desktop icon, then the other partitions are automounted, or if I unplug/replug the USB cable.

That's quite annoying, because on those disks I have audacity and cinelerra projects, that have references to absolute paths. As the drives are mounted from time to time in different /media/disk-x directories I have to manually edit every time the scripts. Moreover when I connect a second drive it's not so easy to distinguish what is what, as was with the /media/sdax,  /media/sdbx, ...   naming convention.
Does anybody know why disks are not mounted anymore on the /media/sdax directories, or how to do it?

I will report on [https://bugs.launchpad.net/ubuntu/+source/hal/+bug/86292](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/86292)

Ciao, Leo

---

### Post by wireless on 2007-05-01
Hey ppl
Same usb automounting issue here.. Im using 7.04 under Thinkpad x60.. same problems as mentioned above except for the sd card which is being mount automatically (still:)) 
besides that my external usb hdd and my sansa e250 player is not being auto mount.. tried to sort it out but no luck..

---

### Post by aseem on 2007-05-01
Automount  WORKS  for USB Sticks and USB hd's but not for SD card.  SD card automount did't work for Edgy either, so I'm interested in a solution.  My computer is an HP nc4010.

Not much help from me, sorry....

---

### Post by doabean on 2007-05-01
I had the same issue with my external 2.5" USB disk drive.  

Newly Installed Ubuntu did not automount.  However, I was able to get it to work by manually mounting the ntfs file system that was on it.

I confirmed that Ubuntu did "recognize" the usb drive as device /dev/sdb.  Using parted, i confirmed that my ntfs partiton was on /dev/sdb2.  i did the following to mount the drive:

sudo mkdir /media/usb_storage1
sudo mount /dev/sdb2 /media/usb_storage1/ -t ntfs -o nls=utf8,umask=0222

I hope the above helps.

---

### Post by clueless dave on 2007-05-01
It doesn't look all that simple to me (a relative newbie) but I ran across this in one of the other forums, for whatever it's worth - 

[http://ubuntuforums.org/showthread.php?goto=newpost&t=315497](http://ubuntuforums.org/showthread.php?goto=newpost&t=315497) (for Edgy)
 
[http://ubuntuforums.org/showthread.php?t=420721](http://ubuntuforums.org/showthread.php?t=420721) (Feisty)

There are some other posts focusing on TI internal card readers, including
[http://ubuntuforums.org/showthread.php?t=404521&highlight=TI+Reader+Feisty+HOW+TO%3A](http://ubuntuforums.org/showthread.php?t=404521&highlight=TI+Reader+Feisty+HOW+TO%3A)

I haven't tried any of the remedies offered, and can't vouch for them.   Based on the posts, they seem to have checkered success, but suspicion seems to lean towards a problem with the new kernal.

---

### Post by SamChameleon on 2007-05-03
Hi all. I have the same problem. My external usb storages (HDD or stick) are found only temporary. Look [here]("http://ubuntuforums.org/showpost.php?p=2580033&postcount=27") for my solution. If anybody has a better (enduring) solution, I would be glad to hear about it.

---

### Post by Lord Yupa on 2007-05-03
> **SamChameleon said:**
> Hi all. I have the same problem. My external usb storages (HDD or stick) are found only temporary. Look [here]("http://ubuntuforums.org/showpost.php?p=2580033&postcount=27") for my solution. If anybody has a better (enduring) solution, I would be glad to hear about it.

Same problem and same solution (sudo rmmod ehci_hcd)... Is this a kernel bug? (I'm using precompiled 2.6.20-15-generic kernel)

---

### Post by SamChameleon on 2007-05-03
Disabling USB 2.0 is not satisfying at all. After another hour googling around the web, I found this [ Ubuntu wiki]("http://ubuntuguide.org/wiki/Ubuntu:Feisty"). Search for "ehci" and you will find:

> 
Random disconnection is a kernel bug that is not fixed yet. Some users report randomly disconnecting USB devices, especially external hard drives. One solution is to start the system with the option "irqpoll" in grub, but this doesn't work for everybody, and is believed to make the whole system slower. The other solution is to disable USB 2.0. This will result in way slower read/write, but the connection remains stable.


I fear removing USB 2.0 support is the only option so far :( Let`s hope they`ll fix it soon, cause in my opinion it`s a **major(!)** bug.

---

### Post by tenoaks on 2007-05-04
hi guys,

i had the same problem, system: ubuntu 7.04 + kde. Western Digital 120g works fine from the font usb, Seagate 320g doesn't from the back, which was ok in edgy.

problem solved by installing 'ntfs mounter' & 'nautilus' from automatix2. (i don't know which one actually did that job:) ).

hope this helps.

btw, do you guys know how to solve this? [http://bugs.launchpad.net/ubuntu/+source/kubuntu-meta/+bug/50471]("http://bugs.launchpad.net/ubuntu/+source/kubuntu-meta/+bug/50471")

modified 11am 04/05:

Sorry, after disconnecting the one from the back, it's not recognized again. 
seems to me the above solution only works if you power on the drive before the system.

---

### Post by SamChameleon on 2007-05-04
no, sorry. Never used kde and always worked with gdm (since first installation of Debian Woody).

---

### Post by jdpipe on 2007-05-05
My USB situation is a bit different. I run Ubuntu of a USB external HDD. My hard drive contains a main ext3fs partition that mounts as /. There is a swap partition, and then a vfat partition containing my music and other stuff that I like to be able to access when I'm in windoze.

In edgy,  I had the vfat partition mounted with read/write privileges as /media/USB.

Since the upgrade to Feisty, /media/USB now mounts read-only. Additionally, a new mount, /media/USB_ has appeared, which *does* have the necessary read-write privileges.

Can anyone unravel how it is that I now have two mounts? I think this is related to changes in UUID handling of file systems, possibly.

Cheers
JP

---

### Post by clueless dave on 2007-05-06
This won't help on the USB devices (mine will automount but must be manually umounted), but may help someone on the card reader issue. 

 I am using a TI card reader in a System76 laptop with SD cards used in a Palm T/X and a Canon digital camera.  I had no problem under Edgy with cards that I had cleaned and reformatted in the Palm.  However, after the upgrade to Feisty things stopped working.  Syslogs showed that the system recognized that a card had been inserted, but wouldn't automount it.

It turned out that brand new "unformatted" cards automounted.  After digging around to see how I could reformat the card in Linux and having no luck with the commands to do so, I decided to try reformatting the cards in my digital camera.  Bingo!  The cards automount, no problem transferring audio files, and I'm good to go.

I know this isn't a purist solution, but is a no-hassle workaround that might be useful to someone with an otherwise recognized device and access to a digital camera.  I can only conclude that Feisty is fussier with regard to the file formats on the SD card.

---

### Post by crmccreary on 2007-05-06
Same story. Found a post, [http://ubuntuforums.org/showpost.php?p=2580033&postcount=27]("http://ubuntuforums.org/showpost.php?p=2580033&postcount=27"),
 that fixed it right up. In short:

sudo modprobe -r ehci_hcd

Don't know what happened nor how long the fix will last.

On further research, it appears that this problem is a kernel bug. I found that adding irqpoll as a boot option is a more permanent fix. I also read that this may slow the system (true?)
Relevant section of menu.lst:
## ## End Default Options ##

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=cf89718b-0b16-4131-a8d1-4932be9aef95 ro quiet splash irqpoll
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

---

### Post by gsimone on 2007-05-06
It did not work for me... :-k 

Could someone bring some light pleeease?! [-o<

---

### Post by SamChameleon on 2007-05-07
The post mentioned above was originally from me. And the irqpoll solution does not work for me either. I found out recently that I can use USB 2 if I have an USB-Stick mounted, too. I don`t know why this works, but it WORKS.

---

### Post by styven on 2007-05-07
Oh well, here is my two penneth...............

Fresh Fiesty intsall.

1gb Verbatim pen drive will automount and eject.
Generic card reader will automount and eject.
Maxtor 80gb exthdd will automount,  I try eject but it won't in that it immediately automounts again, during which time a window pops up saying it can't eject media!
If I pull out the usb lead I get told off for doing so, and because it has not ejected properly when I plug the lead back in it won't get mounted again because the drive is still running!

Hope that all makes sense.



Steve.

---

### Post by styven on 2007-05-07
Following on from my previous post in respect to the external drive problem, this means that if I attempt to save data to this disk, I can't then get the info to "write to disk" upon ejecting.

Unless anyone knows different:) 

Steve.

---

### Post by kthijs on 2007-05-09
Same problem with no automounting usb devices here. Modprobe -r ehci_hcd didn't work either. 
Will try irqpoll now, even if it slows down my system. Hope a solution is found someday soon.:-|

edit: ok, irqpoll doesn't work. When I mount and unmount manually everything works perfect so I'll just stick to that for now.

---

### Post by kthijs on 2007-05-09
Okay I found a partial solution, I added this line:

/dev/sdb1 /media/sdb1 ntfs auto,uid=1000,gid=1000,users,exec,rw 0 0

to /etc/fstab
Now my drive will automount when I power it after kubuntu has loaded, unmounting also works. It will not mount when the drive is already on when kubuntu loads, I cannot write to the disk and as soon as I try anything with ntfs-config it messes up completely, after which it is not able to unmount unless manually through a console, and after which it will not remount anymore because ntfs-config changes the /etc/fstab file. 

It's not much but at least I can read from my drive and it will automount and unmount (almost) correctly.

---

### Post by wireless on 2007-05-12
Very wierd I had the same issue as i posted here before.. + i had issue with nautilus opening up instead of just konqueror when automount occours , so updating hal fix the nautilus issue (dont ask me why i have no idea:)) and yesterday i thought i should see what happens if i plug the usb drives through an extenral usb hub and tadaa.. IT WORKS... again have no idea why. would love to hear an explenation.. anyway it sounds like a temporary solution for me, but its better than nothing.. so i hope it helps to others with same issue!
LOVE UBUNTU! :)
CHEERS!

---

### Post by ben s on 2007-05-13
Hey, cool, the reinstall command "sudo aptitude reinstall hal hal-device-manager hwdb-client update-notifier hwdb-client-common ivman gnome-volume-manager hwdb-client-gnome gnome-power-manager" worked for me.  Guess I'm one of the lucky ones...

---

### Post by mh114 on 2007-05-13
Same problem here, I can't use my USB sticks anymore.. :( They worked fine in Edgy.

---

### Post by xe1ufo on 2007-05-14
After trying a dozen other things, what brought my automounting of my external hard drives back to normal was removing the Automatox read/write NTFS and FAT32 Mounter. Now my external USB drives automount without a problem!!!

:popcorn:

---

### Post by Tulsapoke on 2007-05-29
> **xe1ufo said:**
> After trying a dozen other things, what brought my automounting of my external hard drives back to normal was removing the Automatox read/write NTFS and FAT32 Mounter. Now my external USB drives automount without a problem!!!

:popcorn:

Thank you!! This fixed my problem.  All my usb keys quit working this weekend after I installed that NTFS Automatix tool.  Now all is right again.  I was blaming the kernel upgrade pushed out over the weekend, however that was coincidence evidently.  Once again thanks.

---

### Post by charliejamesuk on 2007-05-31
Thanks for who ever suggested the following command

"sudo aptitude reinstall hal hal-device-manager hwdb-client update-notifier hwdb-client-common ivman gnome-volume-manager hwdb-client-gnome gnome-power-manage"

Mounting USB Drive works a treat now ;)

---

### Post by BonBlaise on 2007-05-31
Not to be another echo but i have the same problem (No automount of USB external drive)  and i dont know how to mount it manually.  This problem started only after my last system update.

i did find a temporary soution.  My laptop has three USB ports, one of which is occupied by the mouse.  I have two USB Drives so when i insert them both, whichever one i insert second opens up.  But if i mount them one at a time, no luck.  

So in short all three of my USB ports have to be in use and only the third one will automount.  Hope this helps someone, and i hope the fix for this bug is in the next update.

---

### Post by flotoonie on 2007-06-07
> **Tulsapoke said:**
> Thank you!! This fixed my problem.  All my usb keys quit working this weekend after I installed that NTFS Automatix tool.  Now all is right again.  I was blaming the kernel upgrade pushed out over the weekend, however that was coincidence evidently.  Once again thanks.

This fixed my problem too!  I am a linux noob and without this forum I may have just jumped ship.  thanks

---

### Post by arno77 on 2007-06-07
Hello.

I am using feisty and have posted this problem also under "general help" but since it seems this is the thread where (auto)mount problems of external drives (usb sticks) are discussed I post it here too. Sorry for any inconvenience but this automount problems are really annoying.
The problem appears since the latest kernel upgrade.
 
After plugging in my usb stick I receive the following message:

"Cannot mount volume. You are not privileged to mount the volume <name>."

I can mount it manually with "sudo mount -t vfat /dev/sda1 /mnt" but then I cannot write do it. It is also not a great solution if you try to convince people using linux instead of windows. A quick solution would be greatly appreciated.

arno77

---

### Post by twrock on 2007-06-10
Just adding my name to the list of people who can't get USB drives (flash drives, card readers, hard drives) to mount under Feisty. I've tried the fixes suggested above. USB drive mounting worked under Edgy.
System: Dell Inspiron 700m

---

### Post by Freaky_Llama on 2007-06-10
Mounting seems to be intermittent on my Toshiba laptop with SD cards. My External WD Hard Drive has no iddues whatsoever, but certain SD cards give me the problem. I tried the pmount fix I found while googling, but that only seemed to enhance the issue of non-mount with SD cards.

---

### Post by mh114 on 2007-06-10
What solved this for me:
I created a new launcher to the deskop called USB Fix, with this command: ```
gksu "modprobe -r ehci_hcd"
``` (make sure that the quotes are normal, with no formatting). Granted, I still have to do this every time (after a reboot/shutdown) I need to use USB sticks, but it's still much better than they not working at all. :)

---

### Post by Bluecircle on 2007-06-10
This happened to me when I upgraded to 7.10. I wrote a script to manually do it, but when I restarted it just started auto working again? Hmmm.

try:

```

sudo apt-get install usbmount

```

---

### Post by twrock on 2007-06-10
Just some points of curiosity. 
How many of the people who are having these problems installed the "Automatix read/write NTFS and Fat32 Mounter"?
Any possible relation between the latest kernel upgrade and this problem? (I actually can't quite remember when the last time I tried to use a USB memory card was.)

If I could figure out a fast way to backup all of my data, I'd try a fresh install of Feisty to see if anything would be solved. But I can't mount any of my external hard drives to do a quick backup. :(

---

### Post by twrock on 2007-06-11
Well, I went ahead and did it. I backed up my data to CD and just did a clean install of Feisty (reformatting the partitions). After the fresh install, all of my USB storage devices are recognized and automounted. So my problems are resolved.

I'm still very interested to know how much of my problem might be related to the "Automatix read/write NTFS and Fat32 Mounter". But not interested enough to install it again to find out! Since it never seemed to work right for me anyway, I won't be taking the chance.

---

### Post by abburdlen on 2007-06-15
Is there where the USB mounting problem line forms?

New fiesty user here.  At first had no problems with my external Maxtor HDD automounting.  A few weeks ago it would only show up if it was plugged in when I booted up the laptop then it stopped showing up altogether.

I tried the  ```
sudo aptitude reinstall hal hal-device-manager hwdb-client update-notifier hwdb-client-common ivman gnome-volume-manager hwdb-client-gnome gnome-power-manager
``` but no change with that.
I had removed the automatix ntfs bit and now when I plug in the drive I get an error **Unable to mount the volume 'Maxtor'.**
I suppose that's progress;)

---

### Post by jinschoi on 2007-06-17
I experienced the same problem of non-automounting of an external USB drive. I took a look at the drive with fdisk and noticed that its partition type was set to W95 FAT32, even though it was an ext3 partition. Just on the off chance, I set it to type 83 (Linux) and removed and re-loaded the usb_storage kernel module. I had tried reloading the usb_storage module before, and it had successfully detected the drive and assigned it to /dev/sdb, but didn't automount it. After setting the partition type and reloading, it automounted it and put the icon on my desktop.

For what it's worth, other people having problems mounting external storage drives might want to try the above.

---

### Post by Mozork on 2007-07-08
>  How many of the people who are having these problems installed the "Automatix read/write NTFS and Fat32 Mounter"?
Interesting. ;)
I just encountered the same problem, the automounter didn't work and i had to mount manually, after doing so I had no write privileges on my usb devices. After I uninstalled "Automatix read/write NTFS and Fat32 Mounter" everything worked seamlessly again (at least my FAT32 device).
I'm now going to install ntfs read/write support the old fashioned way: [http://news.softpedia.com/news/Installing-NTFS-Write-Support-on-Fedora-Ubuntu-41390.shtml](http://news.softpedia.com/news/Installing-NTFS-Write-Support-on-Fedora-Ubuntu-41390.shtml)

---

### Post by tom blum on 2007-07-20
Imagine my joy, when, after weeks of piddling, I found a line to “cut and paste” that claimed to mount  my external hard drive correctly and it actually worked.

Here is that line
 186  sudo mount -t ntfs-3g /dev/sda1 /media/sda1 

Imagine my despair, when, upon shutting down and rebooting, the drive was no longer mounted.

What is the terminal command that mounts it forever??

This O/S is a tricky SOB for anything not in the default.

I migrated here to eliminate the long boot process of Windows XP because of antivirus and firewall system load times. I'm wondering if I shouldn't just improve my tolerance levels a bit??

I hope we get a permanent fix soon.

Tom

---

### Post by nfoti on 2007-07-22
I've had similar problems with usb and power issues. if you're having issues with connected usb drives not mounting period - run dmesg | grep usb - if you see output like this:

usb 1-1.3: rejected 2 configurations due to insufficient available bus power
[   44.777628] usb 1-1.3: no configuration chosen from 2 choices

- you might be having a power issue, I've had to force usb devices to connect at low speed inorder to mount. At any rate, dmesg output is your friend.
(btw - the output above is from a g4 powerpc - I was trying to attach usb pendrive to the keyboard, connecting to a powered usb port solved the issue.)

---

### Post by kubobbu on 2007-07-23
I am having the same problems, except that I am still running Dapper Drake... 6.06LTS. This problem only started in the last 24-36 hours, after updating some packages as suggested by the automatic update signal on my window tray.

I am also having trouble with Picassa2 and Gwenview. Sometimes they will not start at all, and if I try to read from a usb flashdrive, the program locks up and I have to reboot. This is brand new, on an install that has been running for many months with no problems.

Help!!!!!

Thanks....
Bob

---

### Post by GlennW on 2007-07-25
I think that I have a similar problem. Although I don't have any USB drives/devices to be mounted, I have two partitions that have disappeared or is that, have unmounted? 

I have a dual boot with XP Pro. On one of the partitions, resides my entire music library that now has disappeared. I can locate the directory but open attempting to open it, it displays as empty. How can this be? 

I could live without the first partition but the second one (where my music lives) is crucial.

Can anyone tell me how to find/uncover this partition?

Frustrated newb............

---

### Post by El_Hobo on 2007-07-27
I can just add in to this, having similar problems.
Just a week ago my cd/dvdrom stoped working totaly.
I went in to disk manager and found it pointing to /dev/sdb.
I used terminal to mount it, but it didnt work, so i tried to mount /dev/cdrom instead, and it worked fine.
went in to disk manager again, and changed /dev/sdb to /dev/cdrom, and now i can manualy activate it, but automount doesnt work..
(and also, vlc refuses to accept dvd movies from it..but thats another question :) )

---

### Post by NZ-Wanderer on 2007-07-27
Well I seem to have managed to get both my external Hard Drives working perfectly now :) :)

After reading all the threads and not really seeing an answer, I decided to try to edit my fstab on my own..

First I created folders in /media that I wanted my partitions to be eg:
CD-Backups
Backup-Apps
Backup-Games etc

then I edited fstab with the following lines added to the end of it:

# /dev/sdc1
/dev/sdc1 /media/CD-Backups ntfs defaults,nls=utf8,umask=007,uid=0,gid=46,auto,rw,nouser 0 1
# /dev/sdd1
/dev/sdd1 /media/Backup-Apps ntfs defaults,nls=utf8,umask=007,uid=0,gid=46,auto,rw,nouser 0 1
# /dev/sdd5
/dev/sdd5 /media/Backup-Games ntfs defaults,nls=utf8,umask=007,uid=0,gid=46,auto,rw,nouser 0 1
# /dev/sdd6
/dev/sdd6 /media/Backup-HDD ntfs defaults,nls=utf8,umask=007,uid=0,gid=46,auto,rw,nouser 0 1

Note 1: I would have used the UUID for each drive, but couldn't figure out how to get a list of UUID's, so just used the /dev/sdc and /dev/sdd instead

After I put them into fstab, I rebooted the computer and imagine my suprise when my partitions on my external drives actually showed up..

Now all I gots to do is find someone mentioning their fstab that has a ext3 line in it, as I still got one more partition to do

/dev/sdd7 /media/Home-Kubuntu-BU ext3 ????????????????????????

, but can't as I dunno what the stuff is that goes in the line where I put the ??????? above... (cause I pretty sure it isn't the same stuff as in the ntfs lines.

I know it not going to solve the problems for those who are trying to get their usb sticks etc to work, but it may help those that have external HDDs plugged in all the time. :)

UPDATE: Seems something has gone wrong, and I can no longer see 4 of my partitions on one of my removeable drive, could be maybe cause I turned it off I'm not sure.. - Does anyone know the command that will show me the UUID for the drives please??

---

### Post by slack42 on 2007-07-28
Hi, I was having the same problem and I found a way to fix it. What I did was I edited the /etc/fstab and added the following line at the end. ( sudo gedit /etc/fstab )

/dev/sda         /media          auto           defaults       0    0

For me when I plugged in my usb drive it would show up as /dev/sda1 . I found this out with this command.

sudo fdisk -l

When it used to work it would get mounted as /media/disk so that's why I used /media in the fstab. And the auto part tells it to automatically detect the file system type.  Here is a good web site that explains what all the options are and how they work.

[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

I don't know if the same problem everyone is having is the same as mine but I had this happen after I did a fresh install. Hope this is able to help someone.

---

### Post by tom blum on 2007-07-30
I have continued to "scratch at this itch" since my last post.

I resigned myself to booting the external hard drive when I needed it. 

Today, I stumbled into Storage Device Manager. After a few failures, because I didn't "erase" previous eroneous mount attempts, I set parameters, with Storage Device Manager, to mount at boot and to allow any user to write to the disc. 

Voila!! it seems to have worked.

Share my joy!!!

Tom

---

### Post by nasov on 2007-07-30
OP way of reinstalling packages worked fine for me.

cheers :)

---

### Post by tom blum on 2007-07-31
Whoops!!!

The auto mount at boot enabled by "Storage Device Manager"is without write privileges.

A quick search of "write priveliges" reveals nothing but overly complex instructions capable of doing everything a Swiss Arme Knife can do and more..

Sigh!!

The acolyte rules.

NASOV: What does "OP" mean?

Tom
still scratching the itch

---

### Post by twrock on 2007-07-31
Tom is still scratching the itch. I guess I am too.

I saw that this thread had some new activity and I thought I'd reply with a follow-up.

I have had success ever since my complete reinstall of Feisty. I did have a problem with two of my 2 gb SD card not being recognized at all, but since it was only those two, I simply reformatted them to fat32 on a Windows machine (vs. formatting them in my Palm handheld as originally) and they started being recognized and automounted like everything else. I do have one external hard drive that is recognized but returns an error message that it can't be mounted, but then it is mounted anyway. I also can't eject it properly. It gives me an error message that it can't be ejected and then immediately remounts it (and again gives me the same error message that it can't be mounted). It is a bit weird, but at least I can read and write to it as normal even though it would seem I shouldn't be able to. I simply yank out the cord when I'm done with it and close the warning messages about it not be ejected properly (it has two partitions).

Here are the details:
```
Cannot mount volume.
Unable to mount the volume.
Details
mount:/dev/sdb2: can't read superblock
```

Note: I have not reinstalled Automatix since this last system reinstall. I still am wondering about that and about the NTFS automount utility.

---

### Post by tom blum on 2007-08-03
it just keeps getting worse.

Yesterday I tried to use my memory stick and it wouldn't mount

So, I thought I would reupload my camera directly to this computer. NOW the camera, which used to work automatically doesn't mount.

If I try the new installation, I run into my own personal bug-a boos in migrating email records.

This whole practice began when I tried to back up my system. That still isn't done, because of the external hard drive problems.

And yet---Life goes on.

Tom

---

### Post by tom blum on 2007-08-04
By the way:

Would the person who edited fstab please tell me how?

I was going to try that approach, but after editing, I wasn't allowed to save the changes. Seems I didn't have the necessary permissions.

I'm noticing a pattern here.

<G>

Tom

---

### Post by simbot on 2007-08-05
I seem to have the same issue, with USB devices not auto mounting in Debian Etch. This started happening when I upgraded from Gnome 2.16 to 2.18. My resolution to this problem was found [here]("http://wiki.archlinux.org/index.php/HAL") under"Automount only removable devices". I ran gnome-volume-manager in the foreground and found that some "ignore" flag was being set:

```
manager.c/2358: volume.ignore set to true on /org/freedesktop/Hal/devices/volume_uuid_737B_BA73, not mounting
```

So the resolution was to add a hal policy with the following, to hint GVM to mount the device.

```

<?xml version="1.0" encoding="UTF-8"?> 
<deviceinfo version="0.2">
  <device>
    <match key="volume.fsusage" string="filesystem">
      <merge key="volume.ignore" type="bool">true</merge>
      <match key="@block.storage_device:storage.removable" bool="true">
        <merge key="volume.ignore" type="bool">false</merge>
        <merge key="storage.policy.should_mount" type="bool">true</merge>
      </match>
    </match>
  </device>
</deviceinfo>
```

---

### Post by NZ-Wanderer on 2007-08-05
> **tom blum said:**
> By the way:
Would the person who edited fstab please tell me how?
I was going to try that approach, but after editing, I wasn't allowed to save the changes. Seems I didn't have the necessary permissions.
I'm noticing a pattern here.
<G>
Tom


Hi there, to edit the fstab just put the following into a terminal window

If using Kubuntu
>  sudo kate /etc/fstab

If using Ubuntu (I think)
>  sudo gedit /etc/fstab

---

### Post by MrMilti on 2007-08-21
I am having Problems with automount/"Disk Mounter Applet" in Feisty.
I am using an external usb-harddrive, containig two partitions (vfat and ext3) and want them to be mounted on the proper mountpoints. Thats why my fstab looks like this:

```

UUID=46C4-02ED                              /media/ANGELICA   vfat   rw,users,nodev,shortname=mixed,gid=100,uid=1000,umask=000 0 0
UUID=bb919f20-4eed-40cc-936d-94b1c7704486   /media/PETRA      ext3   rw,users 0 0

```

automount works perfect, but when i try to unmount it (either as a user from console, or by using Disk Mounter Applet from Gnome) i get the errormessage, that the mount disagrees with the fstab. Okay, i can understand that, because only the devicenames (/dev/sdb1..) are stored in the mounttable and when i edit my fstab to use the devicename instead of the uuid, it works fine. But thats exactly, what i dont want to do, because if i would plug a different usb-stick before my harddisk, the devicename would be different, and therefore mounted in a different location.

at the moment, i can only unmount them as root from the console. both "sudo umount /dev/sdb1" and "sudo umount /media/ANGELICA" works correct, but thats a bit complicated...

is there any possible way, to teach umount UUIDs?

---

### Post by trepid666 on 2007-09-21
Hey from Alberta, Canada.

Initially, thanks to these forums, I set up my 64bit 6.10 to read my SD cards, USB drives, cameras, and mp3 players. Must say that Ubuntu is the greatest flavor/distro to happen to my computer. Linux is King and Ubuntu is Jester. Fun, amusing and flexible.

My problem is:

Sept 20th my various mounted drives are not showing up iconified on my Desktop. Now this is not a major problem to me because they are all accessible through filesystems and places. They still auto-load and my options are still customized in System-> Preferences -> Removable drives and media.

So I haven't tried to restart my laptop yet which I'm thinking may resolve my issue. Yet I'm curious as to why this would happen. There have been no crashes except an error concerning Npiviewer. 

Cheers.         :guitar:

---

### Post by ender42 on 2007-09-25
Echo.

Running Dapper long-term support.  Only figured out how to get dapper to recognize my USB hardware recently (Warty liveCD & my Warty install did so automagically).  I did upgrade from warty instead of doing a clean install (which appears to be more than half of the problem).



Automount currently isn't working (and hasn't worked since the liveCD/warty install).

udevmontior shows the kernel getting mount/unmount messages.  
fdisk -l (now) shows the drive.

What other diagnostics would help?


Fix attempts:

Not sure what this "Automatix read/write NTFS and Fat32 Mounter" thing is, but unless it's installed by default, I don't recall installing it.  What's the package name?

modprobe -r ehci_hcd - doesn't help. ehci_hcd was one of the things which had been on the Warty liveCD, which wasn't in Dapper, that I'd added to be able to get access to my USB ports, but apparently it is not necessary - as I removed it and was still able to mount my camera-card reader, and automount still didn't start.

I'd added irqpoll earlier, in an attempt to get my USB ports back:

gedit /boot/grub/menu.lst
# defoptions=quiet splash noapic irqpoll
update-grub

So that's already been set, and doesn't help with the automount problem.

Other ideas for possible fix solutions/workarounds?

---

### Post by suchawato on 2007-11-03
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/gnome-volume-manager/+bug/132349](https://bugs.launchpad.net/ubuntu/+source/gnome-volume-manager/+bug/132349) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Bug link

---

### Post by suchawato on 2007-11-03
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/134712](https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/134712) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Second bug link

---

### Post by suchawato on 2007-11-03
If anyone has any information on the status of when we can expect a fix update, please post.

---

### Post by suchawato on 2007-11-03
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/159711](https://bugs.launchpad.net/ubuntu/+bug/159711) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				And a third.

---

### Post by suchawato on 2007-11-03
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/154775](https://bugs.launchpad.net/ubuntu/+bug/154775) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				and a fourth.
This one mentions  iPods.

---

