---
title: "Getting my iPod working"
date: 2004-11-13
forum: Hardware &amp; Laptops
---

### Post by princemackenzie on 2004-11-13
I have an older 3rd-Generation iPod that connects via FireWire.  When I plug it in under Ubuntu, it doesnt automatically mount (or I can't find it).

How do I get it to work?

---

### Post by xetoo00 on 2004-11-13
I have had the same problem (and still do). When I boot my box and everything is loading, if the ipod doesn't respond at hotplug support it just is not going to work. So I just reboot, and in about 4-6 reboots my ipod starts flashing the "Do not disconnect" .  Then just use a su root and mount the ipod.  In a Ubuntu thread I read that it is do to the module not loading correctly ( I really don't know).  If there is a better way then this I would also like to know.

---

### Post by scoon on 2004-11-15
[QUOTE=xetoo00]I have had the same problem (and still do). When I boot my box and everything is loading, if the ipod doesn't respond at hotplug support it just is not going to work. So I just reboot, and in about 4-6 reboots my ipod starts flashing the "Do not disconnect" .  Then just use a su root and mount the ipod.  In a Ubuntu thread I read that it is do to the module not loading correctly ( I really don't know).  If there is a better way then this I would also like to know.[/QUOTE]

Hey there, 

I have a 3rd gen as well.  This has been an ongoing problem with ANY linux distro for me.  In order for it to work, you need these modules: ohci1394, ieee1394 and then to get the "Do Not Disconnect" you need sbp2.  Then to get it to do a "Ok to Disconnect" you need to remove the sbp2 module.  

scoon

---

### Post by princemackenzie on 2004-11-15
I actually went to the [gtkpod](http://gtkpod.sourceforge.net/)  website today and used that to set it up, and it works very smoothly now.  I'm acutally considering writing a HOWTO for setting it up... took me about 45 mins, but hopefully I can simplify it so people can do it in under 10.  
 :grin:

---

### Post by DoubleDangerClub on 2004-11-18
A how-to on the set up would be awesome!

---

### Post by Rincewind on 2004-11-24
[QUOTE=xetoo00]I have had the same problem (and still do). When I boot my box and everything is loading, if the ipod doesn't respond at hotplug support it just is not going to work. So I just reboot, and in about 4-6 reboots my ipod starts flashing the "Do not disconnect" .  Then just use a su root and mount the ipod.  In a Ubuntu thread I read that it is do to the module not loading correctly ( I really don't know).  If there is a better way then this I would also like to know.[/QUOTE]

If you plug the ipod in and it doesn't automount, do the following (leaving the ipod plugged in):

sudo rmmod sbp2
sudo rmmod ohci1394
sudo rmmod ieee1394
sudo modprobe ieee1394
sudo modprobe ohci1394
sudo modprobe sbp2


Works every time for me, maybe should put it in an .sh file and call it mountipod or something.

Chris.

---

### Post by pistooli on 2004-11-24
gtkpod also works for me... but I am using an usb cable.... :-)

cheers - peter

---

### Post by dishkuvek on 2004-12-09
How did it take you 45 minutes to set up gtkpod?  Or are you talking about customizing and configuring it to your liking?

---

### Post by kayaker on 2005-01-13
I still have not been able to get gtkpod istalled, so I was jealous about 45 minutes. GtkPod needs gtk+ that needs glib, which won't talk with my install. What am I doing wrong?

[http://www.ubuntuforums.org/showpost.php?p=45823&postcount=9](http://www.ubuntuforums.org/showpost.php?p=45823&postcount=9)
[http://www.ubuntuforums.org/showpost.php?p=46023&postcount=10](http://www.ubuntuforums.org/showpost.php?p=46023&postcount=10)

Would switch to Ubuntu if Palm, Pod and Printer will work! Now I'm dual booting with w2k.

---

### Post by jamin_l on 2005-01-20
I'm working on getting my iPod fully functional with Ubuntu as well. I'm running Warty Ubuntu & 3rd Gen iPod 15G version 2.2 originally formatted with Windows.

I finally have working iPod mount & dismount scripts, feel free to use these if you want them:

Mounting iPod script:
```
#!/bin/sh
modprobe sbp2
mount /dev/sda2 /mnt/ipod
```

Unmounting iPod script:
```
#!/bin/sh
umount /mnt/ipod
rmmod sbp2
```

Now that I can sucessfully mount & unmount my iPod, I connect to GTKPod and the program gives me the following error:
> Could not open"/mnt/ipod/iPod_Control/iTunes/iTunesDB.ext" for reading.
Could not open iTunes DB "/mnt/ipod/iPod_Control/iTunes/iTunesDB" for reading.

Has anyone come across this error? If so, have you managed to fix it & what did you do to fix it?

---

### Post by ubuntu-nerd on 2005-01-20
I came across that error too, and still do.  But I am able to use my ipod with GTKpod without any problems so I chose to ignore that message.  Are you able to use your ipod with GTKpod?  

apt-get install gtkpod          will install version .70

---

### Post by jamin_l on 2005-01-20
GTKPod is 0.85, didn't try ignoring the message. Thought it was a fatal error.

As GTKPod is dependent on GNUPod... I looked at the documentation for it the other day. One thing that struck me as curious and might possibly be affecting this is this:

[quote=http://www.gnu.org/software/gnupod/gnupod.html]Well, you can find the iTunesDB on your iPod at iPod_Control/iTunes/iTunesDB . This file is read by the iPod when you 'boot' the device. The iTunesDB is a small Database and stores information about all MP3s on the iPod (Title, Artist, Path, Bitrate...) and all Playlists: everything the iPod needs to know.

The iTunesDB is a proprietary file format created by Apple.

The GNUtunesDB (iPod_Control/.gnupod/GNUtunesDB) holds the same information like the iTunesDB, but it's a simple XML file: easy to understand by humans and easy to edit by hand.

Everytime you run tunes2pod.pl, the iTunesDB will get parsed and converted into an XML File (the GNUtunesDB). mktunes.pl does the opposite: it parses the XML file and creates an iTunesDB (for the iPod and iTunes)

Only mktunes.pl and tunes2pod.pl have to worry about the iTunesDB format: all other tools (gnupod_addsong.pl for example) only have to deal with the XML file called GNUtunesDB.

It's important to keep the iTunesDB and GNUtunesDB 'in sync', so everytime you changed the GNUtunesDB (by hand or using gnupod_something.pl) you'll have to run mktunes.pl. [/quote]

I'm just a little scared to play beyond this right now until I understand more. Anyone more programming geekish that can understand this?

---

### Post by ubuntu-nerd on 2005-01-20
I think you're OK.  Are you hooking your ipod up with USB?

Is the device /dev/sda2 set up in yout /etc/fstab file? 

Mine is set up and automounts so i don't need scripts.

---

### Post by jamin_l on 2005-01-21
[QUOTE=ubuntu-nerd] Are you hooking your ipod up with USB? Is the device /dev/sda2 set up in yout /etc/fstab file? Mine is set up and automounts so i don't need scripts.[/QUOTE]

I connect with Firewire. Haven't checked fstab .. will get hubby to try and look at that.

---

### Post by ubuntu-nerd on 2005-01-21
I tried with firewire briefly and gave up.  My Linux knowledge only runs so deep.  Anyway I found by hooking it up with USB that ubuntu auto-mounted the ipod at /media/sda2 (after I edited the /ect/fstab)

However I was never able to unmount the ipod whether it be in command line or gui.  This is the first distro I have run into that problem.  Besides that, I am guessing 100% of your probelm is permissions on either the device or mounted folder.  So unless you are worried about comprimising security on your ipod I would just chmod the mount folder and device 777.  I did this and everything has worked just fine ever since.  

Hope this helps.

---

### Post by jamin_l on 2005-01-21
[QUOTE=ubuntu-nerd]Besides that, I am guessing 100% of your probelm is permissions on either the device or mounted folder.  So unless you are worried about comprimising security on your ipod I would just chmod the mount folder and device 777.[/QUOTE]

Been there. iPod ownership is set to myself, permissions on the iPod folder are at 777.

---

### Post by Mike Nasvadi on 2005-01-23
So the device is set to 777?

The mount point is also 777?

And you are still getting the error?  What happens if you run GTKpod as root.  At least we can narrow this down to a possible permissions problem which I suspect it is.

---

### Post by mediumcool on 2005-02-23
add to the options for sda2 in fstab: umask=0

---

### Post by yoha on 2005-02-27
Ubuntu-Nerd,
   I, too, am having problem disconnecting the ipod. I was able to eject and then umount the ipod of course, but the display on the ipod instead of changing to "Ok to disconnect", it stayed "Do not disconnect". /etc/mtab does not list the device as mounted anymore. issuing 'rmmod usb-storage', does not help either. have you found a solution? in my case, i have to let it connect until i shut it down.

y0ha

---

### Post by John McClane on 2005-02-27
[QUOTE=yoha]Ubuntu-Nerd,
   I, too, am having problem disconnecting the ipod. I was able to eject and then umount the ipod of course, but the display on the ipod instead of changing to "Ok to disconnect", it stayed "Do not disconnect". /etc/mtab does not list the device as mounted anymore. issuing 'rmmod usb-storage', does not help either. have you found a solution? in my case, i have to let it connect until i shut it down.

y0ha[/QUOTE]
 for disconnect ipod i use

```
eject sda2
```

it work perfectly

---

### Post by yoha on 2005-02-27
[QUOTE=John McClane]for disconnect ipod i use

```
eject sda2
```

it work perfectly[/QUOTE]
 John McClane,
    There are 2 scenarios here for issuing the command you shared. 
1) using my own account, i got this error and ipod does not eject: "eject: unable to eject, last error: Invalid argument"

2) using sudo account, i got the same error BUT the ipod does eject.

     i am not sure what argument they r looking for. i issued "eject /dev/sda2". i am confused to as to why i am not able to eject the ipod but the sudo can. this is what i added on my /etc/fstab: "/dev/sda2       /media/iPod     vfat        rw,user,noauto  0       0"
and this is what /etc/mtab shows when the ipod is connected: "/dev/sda2 /media/iPod vfat rw,noexec,nosuid,nodev,user=yohannes 0 0"
     any thoughts / suggestions?

ps: did you guys use usb2.0 to connect your ipod? i, although, have a usb2.0 add-on card, it seems that the card does not play well SPECIFICALLY on ipod. other storage devices are fine w/ the add-on card. Hence, i m using the old but goody built-in usb1.0

y0ha

---

### Post by jamin_l on 2005-02-28
Well I emailed Jorg Schuler who was the contact person on the GTKPod page. Here's the series of emails I exchanged with him. Even though it's still not working.  ](*,) 

> On Tue, Feb 01, 2005 at 01:21:23PM -0800, Carissa wrote:

>> Ok, I seem to be having a recurring problem with GTKPod and syncing my 
>> iPod. I tell it the songs I want it to sync up and add to my iPod. I 
>> Sync the directories... disconnect the iPod... and it's back to the old 
>> configuration. No new files have been added. What am I doing wrong?
>> 
>> Running Ubuntu Linux - Warty version (based off Debian)
>> Have a Firewire connected 3G 15GB iPod.

Simple: don't synchronize the directories, synchronize the iTunesDB -- it's
a different menu item. And of course, you cannot be offline when syncing.

Cheers,
JCS.

> >Ok, I get that, but when I try to add a Dir to the iPod, it doesn't add. 
>> I sync the iPod & update the iTunes DB and it's not there. I've even 
>> tried adding it song by song. Still nothing appears. Prior to connecting 
>> the iPod today: 517 songs. After connecting the iPod, using the Update 
>> iTunes DB: 517 songs.
>> 
>> I'm not offline while doing this, checked that already.
>> 
>> It gets the command to add files... but files aren't added. I don't get 
>> it.... and it frustrates me.

What files are you adding? Maybe they are not supported.
JCS.

I figured out at this point that I was a moron and some of the files were xx.mp3.OK - created a script to fix this and ran through the directory recursively to make sure all files were *not* "read-only."

> Did you check whether your iPod is writable -- it shouldn't just flash, it's
not that fast.

You can check by
touch /mnt/ipod/testfile
(replace /mnt/ipod if necessary)

At this point I've just temporarily given up and am listening to what songs are on my iPod right now.

And from pics like these - looks like rhythmbox is adding support for ipod

---

### Post by xbruceyx on 2005-03-03
Running Warty here. I have two firewire devices. A Maxtor 200 GB external hard drive and a third gen (3G) firewire ipod. The maxtor is detect and mounted on /dev/sda but the ipod is nowhere to be found. Extremely frustrating to get this thing detect and mounted.   Hoping the devs will fix this soon...

-A sad Ubuntu 'Warty Warthog' user-

---

### Post by yoha on 2005-03-03
[QUOTE=xbruceyx]Running Warty here. I have two firewire devices. A Maxtor 200 GB external hard drive and a third gen (3G) firewire ipod. The maxtor is detect and mounted on /dev/sda but the ipod is nowhere to be found. Extremely frustrating to get this thing detect and mounted.   Hoping the devs will fix this soon...

-A sad Ubuntu 'Warty Warthog' user-[/QUOTE]
 xbruceyx, try using usb cable instead. i heard somehwere ipod does not work nice w/ firewire on kernel 2.6x

---

### Post by Jet2k5 on 2005-03-03
I have an iPod Mini, lol don't know what generation just says version 1.2.  I have sucessfully got mine working with Linux, I'm able to transfer songs and stuff.  But the only thing that I can't seem to ever get is the " do no disconnect " sign to go away.  I've tried multiple of scripts and commands, but nothing seems to give the O.K to disconnect.  

The answer might be well withing this thread, I just skimed around ... didn't really look for anything in specific.  But it will be just easier if you can share your ideas on how to fix this.

Right now I'm dual-booting with windows just to use iTunes with my iPod.  Has the idea even crossed Apple's mind to port it to Linux?

Just curious .....

-Luis

---

### Post by Jesus Franco on 2005-03-03
[QUOTE=yoha]xbruceyx, try using usb cable instead. i heard somehwere ipod does not work nice w/ firewire on kernel 2.6x[/QUOTE]

I got my iPod 3rd gen working perfectly with FireWire in linux

It was automatically mounted and I only had to unmount it and mount it under /media/ipod/ because thats were gtkPod checks for the iPod by defualt. And by defualt linux will mount it under /media/IPOD NAME not /media/ipod I was however able to unmount it with ease as long as I didnt use gtkPod, once i used it to read or write files I had the same problem as stated above. All i did was shut down my pc and disconnect the iPod then turn the pc back on.  :D

---

### Post by yoha on 2005-03-03
[QUOTE=Jet2k5]I have an iPod Mini, lol don't know what generation just says version 1.2.  I have sucessfully got mine working with Linux, I'm able to transfer songs and stuff.  But the only thing that I can't seem to ever get is the " do no disconnect " sign to go away.  I've tried multiple of scripts and commands, but nothing seems to give the O.K to disconnect.  

The answer might be well withing this thread, I just skimed around ... didn't really look for anything in specific.  But it will be just easier if you can share your ideas on how to fix this.

Right now I'm dual-booting with windows just to use iTunes with my iPod.  Has the idea even crossed Apple's mind to port it to Linux?

Just curious .....

-Luis[/QUOTE]
 jet2k5, try eject /media/ipodnamehere or wherever you mount it. if it gives you an error and the ipod's display persisently displays "do not disconnect", then add sudo to the front of eject. this in my case still produces the error, but ipod was successfully ejected. the error is ""eject: unable to eject, last error: Invalid argument"

---

### Post by yoha on 2005-03-03
[QUOTE=Jesus Franco]I got my iPod 3rd gen working perfectly with FireWire in linux

It was automatically mounted and I only had to unmount it and mount it under /media/ipod/ because thats were gtkPod checks for the iPod by defualt. And by defualt linux will mount it under /media/IPOD NAME not /media/ipod I was however able to unmount it with ease as long as I didnt use gtkPod, once i used it to read or write files I had the same problem as stated above. All i did was shut down my pc and disconnect the iPod then turn the pc back on.  :D[/QUOTE]
 did you add ipod to your fstab file? /etc/fstab? if you dont list it in there, then the kernel will assign random-generated name for the ipod device and mount in within /media. try use sudo eject /media/ipodnamehere. you might/might not get an error, but your ipod will be umounted.

---

### Post by Jesus Franco on 2005-03-03
No I didnt add it. Thanks for the info  :grin: 

I always assumed that adding devices to the fstab is only for devices you want to be mounted on startup. I was wrong  :-# 

Thanks agian Yoha  :grin:

---

### Post by yoha on 2005-03-04
[QUOTE=Jesus Franco]No I didnt add it. Thanks for the info  :grin: 

I always assumed that adding devices to the fstab is only for devices you want to be mounted on startup. I was wrong  :-# 

Thanks agian Yoha  :grin:[/QUOTE]
 well if you dont want it to be automatically mounted when the ipod is inserted, you can do that too, but the kernel will assign ugly-looking number/characters every time the ipod is inserted. My only problem is the error i got everytime i want to eject it. Hence, Jesus, if you could not emulate the problem i had /*refer to the previous posts*/, then i will be inclined to hear what command you issue to eject the ipod.

---

### Post by PLZ_HELP_ME on 2005-07-22
HIHO!!

I'm using an ibook G3 900 MHz with 40 GB harddisk and 384 MB RAM i have mac os 10.4 running.

I have an iPod mini and want to install ubuntu 5.04 on it. i have the boot disk.

But it doesnt work. i havent any expirience with scripts or other commands in linux, but i want to play windows games via wine on it. it is like an extern harddisk.

can any body send me a step by step "workshop" or at least some help or tips for newbies like me.

this would be nice.

---

### Post by flyride13 on 2005-07-31
can someone help me to get my ipod working, i have the 3.1 and when i start it up all i get is the apple and then it goes to a folder with a triangle, then it turns off. anyone have any suggestions

---

### Post by pvphaneuf on 2005-08-07
My dad's company gave him a shuffle 512mb ipod, which he then gave me because he has no clue how to work anything electronic and I've followed a HOWTO on the Wiki 
page to get the thing working:

[https://wiki.ubuntu.com/IPodHowto?highlight=%28iPodHowto%29](https://wiki.ubuntu.com/IPodHowto?highlight=%28iPodHowto%29)

yet whenever I try to read the ipod it tells me:

*Could not open "iTunesDB.ext" for reading extended info.
Extended info will not be used.*

Now, the thing mounts properly in /mnt/ipod and the preferences for gtkpod are set for there, I've fstab it and followed the HOWTO to the point, except for the sda2 location, where my is listed as sda1. I'm thinking it might be a simple permission problem and I've seen some people on this thread speak of "chmod" and "777" but I'm not too sure how to do that or what it means. If I could get any advice on this problem, thnx  :)

---

### Post by SKLP on 2005-08-07
My 3rd gen firewire-connected iPod automounts *sometimes* in hoary. In breezy it seems to work 100% of the time.

As for which tool to use for transferring files, i can recommend the muine-ipod plugin.

---

### Post by macewan on 2005-08-10
can the ipod be switched to vfat?

originally started with the ipod formatted under an imac but hfsplus doesn't allow writing, only reading

---

### Post by crunch_ca on 2006-05-04
[QUOTE=pvphaneuf]My dad's company gave him a shuffle 512mb ipod, which he then gave me because he has no clue how to work anything electronic and I've followed a HOWTO on the Wiki 
page to get the thing working:

[https://wiki.ubuntu.com/IPodHowto?highlight=%28iPodHowto%29](https://wiki.ubuntu.com/IPodHowto?highlight=%28iPodHowto%29)

yet whenever I try to read the ipod it tells me:

*Could not open "iTunesDB.ext" for reading extended info.
Extended info will not be used.*
[/QUOTE]

I just bought a shuffle and have found that on occasion, gtkpod will corrupt the FAT file system on the USB drive.


From the syslog

```
localhost kernel: usb 4-1: new high speed USB device using ehci_hcd and address 2
localhost kernel: usb 4-1: configuration #1 chosen from 2 choices
localhost kernel: SCSI subsystem initialized
localhost kernel: Initializing USB Mass Storage driver...
localhost kernel: scsi0 : SCSI emulation for USB Mass Storage devices
localhost kernel: usb-storage: device found at 2
localhost kernel: usb-storage: waiting for device to settle before scanning
localhost kernel: usbcore: registered new driver usb-storage
localhost kernel: USB Mass Storage support registered.
localhost kernel:   Vendor: Apple     Model: iPod Rev: 2.70
localhost kernel:   Type:   Direct-Access ANSI SCSI revision: 04
localhost kernel: usb-storage: device scan complete
localhost kernel: SCSI device sda: 1015040 512-byte hdwr sectors (520 MB)
localhost kernel: sda: Write Protect is off
localhost kernel: sda: Mode Sense: 64 00 00 08
localhost kernel: sda: assuming drive cache: write through
localhost kernel: SCSI device sda: 1015040 512-byte hdwr sectors (520 MB)
localhost kernel: sda: Write Protect is off
localhost kernel: sda: Mode Sense: 64 00 00 08
localhost kernel: sda: assuming drive cache: write through
localhost kernel:  /dev/scsi/host0/bus0/target0/lun0: p1
localhost kernel: Attached scsi removable disk sda at scsi0, channel 0, id 0, lun 0
localhost kernel: FAT: Filesystem panic (dev sda1)
localhost kernel:     fat_get_cluster: invalid cluster chain (i_pos 2689815)
localhost kernel:     File system has been set read-only
localhost kernel: FAT: Filesystem panic (dev sda1)
localhost kernel:     fat_get_cluster: invalid cluster chain (i_pos 2689815)
localhost kernel: FAT: Filesystem panic (dev sda1)
localhost kernel:     fat_get_cluster: invalid cluster chain (i_pos 2689815)

```
This is taking all the precautions of unmounting the drive after modifications etc.

I'm not sure what exactly triggers the errors, but I've had to re-format the shuffle several times.

I finally found that once it's set up properly, you can use

[http://shuffle-db.sourceforge.net/]("http://shuffle-db.sourceforge.net/")

and deal with the ipod as a general USB mass storage device.  This allows you to just copy the music you want to any place on the iPod and simply re-build the shuffle's database of tracks.

---

