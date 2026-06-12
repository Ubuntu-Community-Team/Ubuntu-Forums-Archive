---
title: "moving from minimal 8.10 to full install"
date: 2009-03-26
forum: Installation &amp; Upgrades
---

### Post by cutting on 2009-03-26
Hi everyone, 

To make a long story short... I had to do a netboot install of 8.04 (8.10 froze at the install screen?) to a tablet with no other way to access and a corrupted WinXP. Apparently, the netboot install is only the minimal install. The install was successful, but when i boot it goes to the login with about 1/4 screen on the left and nothing else visible but vertical ubuntu colored lines. I assume the support for this computer is only in the full desktop install, because when i connect to an external monitor everything works great. The machine is a Motion Computing LE1600. 

Can anyone help me go from the netboot install to the full? 

Thanks! I'm really stuck on this one..

---

### Post by spcwingo on 2009-03-26
If you already have a Window Manager/Desktop Environment installed drop out to the command line (CTRL+ALT+F1) and type these commands:

```
sudo apt-get install ubuntu-desktop
```

followed by:

```
sudo apt-get clean && sudo reboot
```

This will clean your apt cache (the package ubuntu-desktop links to ALOT of packages) and boot into your new full Ubuntu Desktop.

---

### Post by cutting on 2009-03-27
perfect!! Thanks, Did the trick.

Now i just need to get back the right side of my screen...

---

### Post by forestwalkerjoe on 2009-05-02
I have been having trouble getting any real feed back for Tablet Pc's.. I am posting here because it was the closest i could find to HOW TO'S or HELP ME's on the system. 
Unless you have a better set of pages you can direct me to? 
I have a Motion Computing M1400. Standardly installed with WIN XP for Tablet. 
Ubuntu 904 just came out.. but i am nervy about installing 810 or 904.. i am told they are both issued with Tablet Wacom support. 
Some have had little to no trouble installing on this very model of Tablet.. In one set of posts.. but those are "NO REPLY" allowed posts now , with little real info.  
Any one have some stuff i can read up on.. to make my conversion or WUBI of the above mentioned MOTION COM M 1400 a bit easier? 
I would need all the APTS GETS  and APPS i can get.. ready and understood to make this a smooth.. very work able WUBI install. 
IF i can get it all working.. within expectations.. i will be a Hero at work. ANY TAKERS ? or SUGGESTIONS? thanks 
and please don't say.. buy a pre configed Tablet.. or get another.. its all i got to work with.. until i can personally afford a THINK Lonovo X60 or X 61. Some thing Newer in any rate. 
FWJ

---

### Post by Favux on 2009-05-02
Hi forestwalkerjoe,

It is very doable.  Installing a serial tablet pc in Hardy or Intrepid is well understood and usually pretty straightforward.  Occasionally you can run into a wrinkle.

Loic2's Wacom wiki (mainly for external graphic tablets) has useful info.:  [https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom)

The thing that would be helpful is if you knew the spec.s on various Motion Computing models.  How they differ or are the same, especially their Wacom serial tablets.  But it's not critical.
[http://ubuntuforums.org/showthread.php?p=4972622#post4972622](http://ubuntuforums.org/showthread.php?p=4972622#post4972622)
[http://ubuntuforums.org/showthread.php?t=1061660](http://ubuntuforums.org/showthread.php?t=1061660)
[http://ubuntuforums.org/showthread.php?t=830496](http://ubuntuforums.org/showthread.php?t=830496)

Things change with Jaunty because there is a new method of handling the tablet.  The HAL/.fdi method.  Theoretically it should offer more support out of the box.  But since it is new there are some teething pains.  We've found work arounds for most.

Theoretically WUBI should be the same as installing.  But I haven't worked with many on WUBI and I'm not sure if it makes a difference.

I hope this is helpful.

---

### Post by forestwalkerjoe on 2009-05-03
My Tablet arrives on Tuesday.. and the CD ROM not a writable one.. will be there day after. 
So.. for now.. i have a downloaded Guide book.. and this page. 

[http://www.ruggedpcreview.com/3_slates_motion_m1400.html]("http://www.ruggedpcreview.com/3_slates_motion_m1400.html")

the only Stats it shows are here. 
 ```

Type  	Tablet PC slate
Processor 	Intel Pentium M 733
OS 	Windows XP Tablet PC Edition 2005
Memory 	256MB to 2GB
Display 	12.1" XGA (1024 x 768) transflective wide angle TFT
Digitizer/Pens 	Wacom/1
Keyboard 	optional snap-on or USB keyboards
Storage 	20 to 60GB hard disk
Optical storage 	Optional external
Size 	11.65" x 9.45" x 0.87"
Weight 	3.4 pounds incl. battery pack
Power 	Replaceable 40 watt-hour Lithium-Ion ("over 4 hours")
Communication 	56k V.92 modem, LAN, 802.11b/g WiFi
Interface 	RJ11/45, audio, video, 2 USB 2.0, IEEE 1394, dock, fingerprint reader
```
the Keyboard is the USB one.. not the integrated stand one. So USB support will be a big deal. Without it I'll be stuck with only pen or exterior mouse. that would defeat the whole reason of having a Tablet Slate in the first place. 
I guess, i can use the disk i have for 8:10 and install from there. If i had a free USB Flash.. i would attempt to do a Flash install.. but .. for a later time. 
It must support the two settings.. land scape and standard view.. the pen must write both in apps and be used as a mouse for navigation. THE STANDARD XP tablet OS has a NOTE app and can work with Journal.. I hope that this will also work in a similar Linux program. 
It would be NICE of the battery has a good utility and life monitor and hope the FINGER PRINT READER is supported.. but i can deal with that either way. 
FWJ

---

### Post by Favux on 2009-05-03
Hi forestwalkerjoe,

Hopefully you'll have more than 256MB on the RAM and the larger hard disk.  I don't know why the OEM's are so shy on giving the Wacom digitizer spec.s.  But that seems to be a universal thing.

At a minimum you'll want CellWriter (virtual keyboard and character recognition) and Xournal.

I assume you'll be dual booting.  Some info on partitioning:
[https://help.ubuntu.com/8.04/installation-guide/powerpc/partitioning.html](https://help.ubuntu.com/8.04/installation-guide/powerpc/partitioning.html)
[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

Good luck!

---

### Post by forestwalkerjoe on 2009-05-03
it has ONE GIG RAM.. and 1.2 gighurtz Single chip. 
hard drive.. i cant recall if its 40 or 60 gigs. BUT should work for what i need it for. 
I found a really TECHIE over the top , set of pages for installing the Finger reader.. but .. " could they get any more geek technical on me?" waaaay above my head on " HOW TO". 
but apparently some one had my very model and was able to "get 'er done". 
that makes me feel a bit better.. NOW , if i can be sure to get the PC CARD D LINK running.. or the internal WIFI.. get the touch screen/wacom digi pen working.. i will feel like a success. I was only hoping to get 810 or 904 in.. so i could have the Compiz EFFECTS.. THAT  really does impress the masses. 
IMAGINE.. a converted Tablet from 05.. running modern Ubuntu.. with Finger reader active.. touch screen working.. DIGI PEN working.. Compiz bouncy screens and fire pages.. that tends to deal with both ram and power better than the others at work.. all i would need to finish my coo, is to get MS READER to work in WINE.. and "IM THE MAN". 
thanks for helping. 2 more days before my Tabby should show up. 

FWJ

---

### Post by Favux on 2009-05-03
Hi forestwalkerjoe,

One other thing you should be aware of.  Some Intel video chipsets aren't so well supported in Jaunty currently.  It's an issue with the Xorg video drivers.  They are working on it.  I'm guessing your tablet has an Intel motherboard video chipset.

---

### Post by paledread on 2009-05-13
Try my HOWTO for the M1400 at 

[http://ubuntuforums.org/showthread.php?t=1154085](http://ubuntuforums.org/showthread.php?t=1154085)

and shout if it gives problems.

Thanks.

---

### Post by forestwalkerjoe on 2009-05-17
l an om that tablet NOW- windows- Cant install via CD- and I'd prefer to install 810 not Jackalope .- 
This hardware has little issues  but is oK . 
Will there be much difference if l use 8:10?

---

### Post by Favux on 2009-05-18
Hi forestwalkerjoe,

No, not at all.  In fact you'll avoid the Intel video issues in Jaunty.

---

### Post by forestwalkerjoe on 2009-05-18
OK sorry for being the new guy but Isn't Jaunty the Newest one 9.04? 
I am worried about doing the newest one. 
I have 9:04 Upgrade- on my home pc still has some real sound issues- and little glitches. .. I do have both 8:10 and 9:04 on Disk. 
How do I install best on USB
Flash DRIVE.
I'll have to move all my stuff off my 4 gig to try that.

---

### Post by Favux on 2009-05-18
Hi forestwalkerjoe,

The releases are named after the year and month.

So Hardy LTS (long term support) 8.04 (2008/April)
Intrepid 8.10
Jaunty 9.04 (the latest)

Sorry, I don't know anything about a usb install.  There are several threads on that you could look at.  And you could start a new thread here in Installations & Upgrades explaining what you want to do.

This thread talks about one way to do things:  [http://ubuntuforums.org/showthread.php?t=1121058](http://ubuntuforums.org/showthread.php?t=1121058)  And I think he used:  [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

