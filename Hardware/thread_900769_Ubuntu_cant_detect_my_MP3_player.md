---
title: "Ubuntu cant detect my MP3 player"
date: 2008-08-25
forum: Hardware
---

### Post by IDK312 on 2008-08-25
Hey! 

I need your guys help again!

Ubuntu cant seem to detect my MP3 player (Creative Zen 8GB). But yet it can detect my external hard drive (freegate agent 80gb)? I plug them into the same USB port but it doesnt detect my mp3 why it detects my external hard drive? You guys got any clue?

---

### Post by Crafty Kisses on 2008-08-25
Post the results of > lsusb

---

### Post by IDK312 on 2008-08-25
Bus 003 Device 005: ID 041e:4157 Creative Technology, Ltd 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 045e:00f0 Microsoft Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 001 Device 003: ID 046d:08f0 Logitech, Inc. QuickCam Messenger
Bus 001 Device 001: ID 0000:0000

---

### Post by wpiter on 2008-08-25
Good luck, your zen is recognized (creative technology, Ltd)

to mount your zen install mtpfs, libmtp and mtptools (sudo apt-get install)

then type
```
$ sudo mkdir /media/MyZen
$ sudo chmod 775 /media/MyZen
```

to create a mount point for your zen, you can the mount point in your /root/media

Now connect your zen and type ```
$ sudo mtpfs -o allow_other /media/MyZen
``` this will mount your zen at the /root/media location

now you can acces your files with drag and drop functionality

to unmount simply type ```
$ sudo umount /media/MyZen
```

---

### Post by IDK312 on 2008-08-25
It cant find mtptools and libmtp?

james@james-desktop:~$ sudo apt-get install mtpfs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mtpfs is already the newest version.
The following packages were automatically installed and are no longer required:
  python-opengl ttf-sil-andika ttf-mgopen netpanzer-data python-pygame
  python-pyogg libsdl-net1.2 python-pyvorbis libsdl-ttf2.0-0 wesnoth-data
  libboost-iostreams1.34.1 libphysfs-1.0-0 criticalmass-data libsdl-mixer1.2
  python-pkg-resources libsmpeg0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
james@james-desktop:~$ sudo apt-get install libmtp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libmtp
james@james-desktop:~$ sudo apt-get install mtptools
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package mtptools

It cant find mtptools and libmtp?

SOrry even this is probably simple task im just not that great with computer (linux) :( But im trying! :)

I also downloaded (.tar.gz file) libmtp i just dont know where to download the mtptools?

[IMG]http://i498.photobucket.com/albums/rr345/IDK312/Screenshot-1.png[/IMG]

The file is in the top middle

---

### Post by Jasethemuss on 2008-09-05
>  Re: Ubuntu cant detect my MP3 player
Good luck, your zen is recognized (creative technology, Ltd)

to mount your zen install mtpfs, libmtp and mtptools (sudo apt-get install)

then type
Code:

$ sudo mkdir /media/MyZen
$ sudo chmod 775 /media/MyZen

to create a mount point for your zen, you can the mount point in your /root/media

Now connect your zen and type
Code:

$ sudo mtpfs -o allow_other /media/MyZen

this will mount your zen at the /root/media location

now you can acces your files with drag and drop functionality

to unmount simply type
Code:

$ sudo umount /media/MyZen

That did the trick for my Zen Vision:M - thanks! Is there any way I can automate this though so the player gets mounted when I plug it in?

---

### Post by kspncr on 2008-09-05
> **IDK312 said:**
> Hey! 

I need your guys help again!

Ubuntu cant seem to detect my MP3 player (Creative Zen 8GB). But yet it can detect my external hard drive (freegate agent 80gb)? I plug them into the same USB port but it doesnt detect my mp3 why it detects my external hard drive? You guys got any clue?

Try Gnomad. It worked for my Zen Sleek Photo, and it's supposed to work for all Creatives.

[PHP]sudo apt-get install gnomad2[/PHP]

---

### Post by bryncoles on 2008-10-15
hey folks - ive been looking for a way to add my creative as a mountable drive for ages! but im having a little trouble with the solution as presented here. 

```
$ lsusb
Bus 007 Device 003: ID 041e:411b Creative Technology, Ltd Zen Touch
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 003: ID 1241:1111 Belkin Mouse
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
```

shows me im getting the player acknowledged (yay!) but i followed wpiter's posts and it created the directory for my zen player, but the directory seems not to be a link to my player. 

i might need to add something to the fstab perhaps?

anyway - heres to hoping someone can help! cheers guys!

---

### Post by chrono144 on 2008-11-18
I am having a similar, although somewhat different problem...
I have a Creative Zen Touch mp3 player, and it is just plain not recognized my my computer (HP tx2500z) 
the device just doesn't show up on my lsusb... it works fine on my other linuxboxes, usually listed as "Creative Technology, Ltd Zen Touch"
but here is the output of my lsusb 

Bus 006 Device 005: ID 04f2:b103 Chicony Electronics Co., Ltd 
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 056a:0093 Wacom Co., Ltd 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

none of which are Creative mp3 players...
the usb bus works, it detects my cellphone and external hard drive without problem.. just not the mp3 player

any ideas? :confused:

---

### Post by Jordanwb on 2008-12-28
> **IDK312 said:**
> It cant find mtptools and libmtp?


Libmtp is called libtmp8 in Ubuntu. I don't know about mtptools. I'm having the same problem.

[Edit]

You don't need mtptools (or it may be included in mtpfs). Follow wpiter's instructions and it works.

Does anyone know how I could have it mounted automatically and so that I don't have to be root to unmount? I seem to be having a problem with making folders. I make a folder and try to put a song into that folder but I get an error saying the folder doesn't exist even though I can see it.

---

### Post by zero244 on 2008-12-28
I have a Panasonic Flash Drive Mp3 player. I created a launcher to run this in a terminal window to mount the player.
This is the only way I have found to mount this paticular player.

You can run this in Terminal to see if it works.
sudo rmmod ehci_hcd
Password

---

### Post by bryncoles on 2009-01-04
i have a creative zen touch, and i followed all the instructions here. got as far as ```
sudo mtpfs -o allow_other /media/MyZen
``` and no dice! it doesnt seem to link to my creative zen player. also: if i click unmount instead of using the terminal command, i get the message > umount: /media/MyZen is not in the fstab (and you are not root) perhaps this is significant? 

unmounting with the terminal commend leaves the zen icon on the desktop, and clicking it gets the emssage > Sorry, could not display all the contents of "MyZen": Transport endpoint is not connected

anyone got any ideas? i mostly manage the player through kzenexplorer, as this has a very high functionality. id just like to mount it as an external drive from time to time. 

cheers guys!

---

### Post by brunolabs on 2009-01-04
> **kspncr said:**
> Try Gnomad. It worked for my Zen Sleek Photo, and it's supposed to work for all Creatives.

[PHP]sudo apt-get install gnomad2[/PHP]


It also works with Zen 8GB.

---

### Post by laitorn on 2009-01-05
I've installed gnomad and that's my lsusb result:

```
Bus 003 Device 002: ID 064e:a101 Suyin Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 004: ID 046d:c01e Logitech, Inc. MX518 Optical Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```


I'm using Ibrid and my zen is a X-Fi 8gb

---

### Post by NoBugs! on 2010-05-11
I think Creative players all use [njb]("http://libnjb.sourceforge.net/") protocol, and although you can view them in the file browser, you can't successfully add to it...

Rhythmbox and Gnomad should be able to transfer to a Creative device, though there is currently a [bug]("https://bugs.launchpad.net/ubuntu/+source/gnomad2/+bug/548967/") in 10.04's libmtp, you need to install the [libmtp package from 9.10]("http://packages.ubuntu.com/karmic/libmtp8") to get it to work.

---

### Post by bezolaam on 2010-05-17
> **NoBugs! said:**
> I think Creative players all use [njb]("http://libnjb.sourceforge.net/") protocol, and although you can view them in the file browser, you can't successfully add to it...

Rhythmbox and Gnomad should be able to transfer to a Creative device, though there is currently a [bug]("https://bugs.launchpad.net/ubuntu/+source/gnomad2/+bug/548967/") in 10.04's libmtp, you need to install the [libmtp package from 9.10]("http://packages.ubuntu.com/karmic/libmtp8") to get it to work.


Thank you, I had same problem with sony walkman nwz-a728b in ubuntu 10.04 and libmtp replacement helped me. Only somethink wrong with rhymhmbox now  - there is no radio option :D

upd: if I uninstal rhythmbox-pugins package,  I am able to mount my walkman easily, if I install rhythmbox-pugins package back, then there is no possibility to mount my walkman.
Any IDEAS?

---

### Post by pt123 on 2010-05-18
I was about to buy this sony mp3 player, luckily I am on Karmic.
[http://www.sony.com.au/product/nwz-b143f/sku/nwz-b143f_bce](http://www.sony.com.au/product/nwz-b143f/sku/nwz-b143f_bce)

bezolaam is the MTP support good on the sony mp3 player, i.e. drag and drop , and playlist support?

---

### Post by bezolaam on 2010-05-18
> **pt123 said:**
> 

bezolaam is the MTP support good on the sony mp3 player, i.e. drag and drop , and playlist support?


yes, I use it like a flash drive and works perfect, except on lucid I can't mount player if rhythmbox-plugins package is instaled. Btw I have very old nwz series walkman, newest walkmans should work out of the box in ubuntu

---

### Post by pt123 on 2010-05-18
> **bezolaam said:**
> yes, I use it like a flash drive and works perfect,  what about playlists are they easy to create on Ubuntu for the mp3 player?


I used to have an older Sony mp3 player the ones without MTP, and you had to use a java program called Jsympony, but they never had playlist support.

---

