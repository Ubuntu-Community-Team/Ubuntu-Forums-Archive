---
title: "How can I update TO 9.10rc from within 9.04 via the CD?"
date: 2009-10-24
forum: Installation &amp; Upgrades
---

### Post by TBerk on 2009-10-24
Right now I have -

A) a burned .iso of 9.10 release candidate on CD  & 

B) an Update Manager that wants to update my Ubuntu Studio 9.04 to Karmic Koala via the Internet.

Trouble is, I went to all the trouble (and time) to download the BootCD and I'd like it to be the source of my newer files.

So, Can I reconfig Synaptics and/or Update manager, and/or a command from within Terminal to accomplish this?

I can't seem to find this (seemingly easy) answer via the archives yet, so although I face ridicule for noobish behavior, I'm asking anyway.



berk

---

### Post by motsteve on 2009-10-24
Before you do:  Please! Please! Please! backup your work.  Keep in mind also your evolution settings and installed package info as well as noting what apps you may have installed manually.  If you have backup, go to a terminal and enter on the command line "update-manager -d".  It'll bring up a update manager window, but there should be a box on the top window that shows that there's a new distro.  Push that and away you go.  Good luck and I hope you're 32 bit, my 64 bit is kicking my butt.

---

### Post by prshah on 2009-10-24
> **TBerk said:**
> Trouble is, I went to all the trouble (and time) to download the BootCD and I'd like it to be the source of my newer files.

For this, you need to download the "alternate" cd; sorry you cannot use the "desktop" (aka live) CD for this. 

You can download the "alternate" CD image for Ubuntu Karmic from [this page]("http://releases.ubuntu.com/karmic/") scroll down a bit to find the "alternate" section, and download the relevant CD image (amd64 / i386)

Once you have downloaded and burnt the iso, insert it into your CD drive, and you will be prompted to upgrade automatically. At a later point, you will be asked whether you want to use the CDROMs packages or download the latest packages; choose what you like. Be aware, that if you choose the CDROM as the source, you will probably have to download another 400~700MB of updates. However, if you are working with multiple machines, CDROM probably a good option.

You can also directly use the "alternate" ISO without burning it to CD; post back if you want more information on this.

---

### Post by TBerk on 2009-10-24
> **motsteve said:**
> Before you do:  Please! Please! Please! backup your work.  Keep in mind also your evolution settings and installed package info as well as noting what apps you may have installed manually.  If you have backup, go to a terminal and enter on the command line "update-manager -d".  It'll bring up a update manager window, but there should be a box on the top window that shows that there's a new distro.  Push that and away you go.  Good luck and I hope you're 32 bit, my 64 bit is kicking my butt.

OK, 

1) I am running 32bit versions.

2) "update-manager -d" is what got me into this mess in the 1st place. It defaults to using the Internet Connection, which is causing me trouble as it wants to do an hour and a half download when I think I have what I need locally already.

(read my next reply for cont...)


berk

---

### Post by TBerk on 2009-10-24
> **prshah said:**
> For this, you need to download the "alternate" cd; sorry you cannot use the "desktop" (aka live) CD for this. 


OK, Thx for that. 


You can download the "alternate" CD image for Ubuntu Karmic from [this page]("http://releases.ubuntu.com/karmic/") scroll down a bit to find the "alternate" section, and download the relevant CD image (amd64 / i386)

Once you have downloaded and burnt the iso, insert it into your CD drive, and you will be prompted to upgrade automatically. At a later point, you will be asked whether you want to use the CDROMs packages or download the latest packages; choose what you like. Be aware, that if you choose the CDROM as the source, you will probably have to download another 400~700MB of updates. However, if you are working with multiple machines, CDROM probably a good option.

You can also directly use the "alternate" ISO without burning it to CD; post back if you want more information on this.[/QUOTE]

Thx, I think i can handle poking around with Karmic in the current install I did:

by using the standard RC cd to boot from it moved over the current OS filesystem and installed on a 'new' partition all it's own.

Once I get some bugs worked out (wicd instead of Network Manager, etc) I'll purge the separate partition and reclaim the space.


Thx, both you guys.

berk

Follow up: I ended up farflugeling my 9.04 to 9.10 upgrade in place so  ended up deleting the partition that was BOOT (since my /Home folder resided on another partition I didn't loose too much in doing so...)

I booted from the Alt CD and ran the Partition Tool in manual mode (so as to not reformat the whole, multi-partitioned hard drive) and reinstalled (the NEW ver of) Ubuntu back on the drive.

A few patches with Synaptics and all is well. 
<end>

---

