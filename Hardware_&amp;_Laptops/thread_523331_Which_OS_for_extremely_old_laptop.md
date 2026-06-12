---
title: "Which OS for extremely old laptop?"
date: 2007-08-11
forum: Hardware &amp; Laptops
---

### Post by Red Moose on 2007-08-11
I have an old Jetbook laptop that has 16mb ram and a 1gig hard drive.  As you can see it needs to be pretty small.  If possible I would like at least a simple GUI.  The only thing I want to use it for is to play old games.  Would puppy be small enough?
It currently has windows 95, but I don't intend to keep it.
Thanks for your help!

---

### Post by buzzmandt on 2007-08-11
[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

---

### Post by Red Moose on 2007-08-11
I forgot to mention the CPU is a Pentium 100mhz

---

### Post by Red Moose on 2007-08-11
I've thought about DSL, but I have something against the name...

---

### Post by buzzmandt on 2007-08-11
> **Red Moose said:**
> I've thought about DSL, but I have something against the name...

"what's in a name, A rose by any other name would smell as sweet"....

---

### Post by EXCiD3 on 2007-08-11
xubuntu is a good flavour of ubuntu for older laptops.

---

### Post by Red Moose on 2007-08-11
> **EXCiD3 said:**
> xubuntu is a good flavour of ubuntu for older laptops.
on 16mb ram?

---

### Post by merlinus on 2007-08-11
No way!

**xubuntu minimum system requirements**

 To run the Desktop CD (LiveCD + Install CD), you need 128 [MB]("http://en.wikipedia.org/wiki/Megabyte") [RAM]("http://en.wikipedia.org/wiki/RAM") to run or 192 [MB]("http://en.wikipedia.org/wiki/Megabyte") [RAM]("http://en.wikipedia.org/wiki/RAM") to install. The Alternate Install CD only required you to have 64 [MB]("http://en.wikipedia.org/wiki/Megabyte") [RAM]("http://en.wikipedia.org/wiki/RAM").
 To install Xubuntu, you need 1.5 [GB]("http://en.wikipedia.org/wiki/Gigabyte") of free space on your hard disk.
 Once installed, Xubuntu can run with 64 MB RAM, but it is strongly recommended to use at least 128 MB RAM.

-merlin

 

---

### Post by Red Moose on 2007-08-11
That's what I thought.  I saw something called DeLi Linux.  It looked small enough, but I didn't see where I could download packages to install.  I'm not very good a compiling source.

---

### Post by SeanHodges on 2007-08-11
Damn Small Linux and Puppy are both good choices, but I missed Ubuntu too much in the end :)

There is an excellent article here: [https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

There are a number of window managers you can use with Ubuntu that make it work perfectly on old hardware. My old P333 laptop with 64MB ram is installed with Ubuntu and the FVWM-Crystal window manager. [https://help.ubuntu.com/community/FVWM-Crystal](https://help.ubuntu.com/community/FVWM-Crystal). This set-up is brilliant for my hardware, but at 16MB ram you'll probably need to try the even more lightweight ones. I would suggest looking at:

[https://help.ubuntu.com/community/IceWM](https://help.ubuntu.com/community/IceWM)

and

[https://help.ubuntu.com/community/Fluxbox](https://help.ubuntu.com/community/Fluxbox)

You can install as many window managers as your disk space allows, and select between them in the login prompt (look for "Sessions" button) until you find one that suits you. Remember to use the Ubuntu SERVER install CD so that it only installs the bare essentials. You will also need to look at alternative lightweight applications. Forget about OpenOffice and Firefox, they will just be too slow, period. Instead, install the following:

```
sudo apt-get install dillo epiphany leafpad abiword vlc gaim
```

Those applications should get you started. Use the Dillo browser for the Web, and if you hit a site that does not play well in Dillo, copy and paste the address into Epiphany (which will be much slower but is based on the same engine as Firefox so should handle the site properly) 

This approach should also leave you with a good amount of disk space.

EDIT: I just read that you need at least 32MB memory for the Ubuntu text installer, so I guess that rules this out for your laptop...  but if you decide to try it anyway please post back on how you got on, I'd be interested to see if it's possible on such a low-spec machine.

---

### Post by ubuntu27 on 2007-08-11
Small Distros for old computers:

[Absolute Linux]("http://www.pcbypaul.com/absolute/")

[Core GNU/Linux]("http://www.coredistro.org/")

[Feather Linux]("http://featherlinux.berlios.de/")

[Fluxbuntu Linux]("http://fluxbuntu.org/")

Puppy Linux:  [http://www.puppylinux.org/](http://www.puppylinux.org/)       and  [http://www.puppylinux.com/](http://www.puppylinux.com/)

[URL="http://www.damnsmalllinux.org/"]
Damn Small Linux (DSL) [/URL]

[URL="http://www.vectorlinux.com/"]
VectorLinux[/URL]

---

### Post by RedSquirrel on 2007-08-11
Here's the link for DeLi Linux:

[http://www.delilinux.org](http://www.delilinux.org)

(it used to be on a less-obvious domain name; nice to see it's now where one might expect ;))

---

### Post by johnny4north on 2007-08-11
here is a very nice spin off from puppylinux.  i would recommend a 128mb swap partition w this one - [http://www.icepup.info/](http://www.icepup.info/) good luck and have fun - [http://www.icepup.info/](http://www.icepup.info/)  :)

---

### Post by louieb on 2007-08-11
:guitar:If you get Linux up and running with a GUI all in 16MB ram then you belong in the installers hall of fame.

---

### Post by Red Moose on 2007-08-11
Good -I can't wait to be there.:)

---

### Post by RedSquirrel on 2007-08-12
Here's a quotation from the DeLi Linux homepage:

>  The test computer is a 486 laptop with 16 MB RAM, and all apps which comes with DeLi Linux are running smoothly.

Now I feel like digging up a 486 to verify that claim... :)

---

### Post by notwen on 2007-08-12
Wowzers, please be sure to post back and let us know which distros you've tried and what all works for you on your machine. =]

---

### Post by Red Moose on 2007-08-12
Does anyone know if DeLi has any type of package managment, or would I have to install everything from source?

---

### Post by Red Moose on 2007-08-13
Okay, I downloaded DeLi but I can't install it.  You see, my computer won't boot from the cd so I installed the Smart Boot Master that was on the DeLi cd to a floppy.  The problem is, my laptop has both a floppy and a cd drive, but I can only have one in at a time.  (There's a slot in which you can put whichever drive in.)  I have to have the floppy in to run the boot master, but I have to have the cd in to install DeLi.  Is there any way that I can set it up so the boot master runs from the hard drive?

---

### Post by louieb on 2007-08-13
Probably not going to help in your situation but I have SBM on the hard drive of an old PC and use it when I need to boot to a CD. [GRUB/Chainloaded CD-ROM - Gentoo Linux Wiki]("http://gentoo-wiki.com/TIP_Chainloading_a_bootable_CD-ROM_from_GRUB") shows what i did.  
Wonder if you  can boot to the SBM floppy then swap the floppy for CD drive and get it to boot that way.

---

### Post by Red Moose on 2007-08-13
I tried that.  I started the SBM, took the floppy out and put the cd in.  The SMB screen was still there, but the cd wouldn't show up on it.
I don't think I'll be able to use that link you gave me, because it looks like I need linux already installed, right?
I think I need to install SBM on the Hard drive so that when it boots from the hard drive, it loads the SBM.  Then I can boot up with the cd in, and forget about the floppy.  

Oops, it looks like I reffered to the Smart Boot Manager as the Smart Boot Master in my last post.

---

### Post by Red Moose on 2007-08-13
I'm going to start a new topic in general help.  I'll let y'all know when(if) I get DeLi installed.

---

### Post by louieb on 2007-08-13
Actually all you need is GRUB installed on the hard drive to load SBM.  Wonder if there is anything out there that could format your drive with the ext3 file system  and install GRUB from a floppy?

---

### Post by kerry_s on 2007-08-13
> **Red Moose said:**
> I have an old Jetbook laptop that has 16mb ram and a 1gig hard drive.  As you can see it needs to be pretty small.  If possible I would like at least a simple GUI.  The only thing I want to use it for is to play old games.  Would puppy be small enough?
It currently has windows 95, but I don't intend to keep it.
Thanks for your help!

100mhz 16mb 1gig

[http://forums.debian.net/viewtopic.php?t=15077](http://forums.debian.net/viewtopic.php?t=15077)

---

### Post by Red Moose on 2007-08-14
Thanks that look interesting.

I think I may have found a floppy that can format to ext3, however I can't seem to find if there's any way to install GRUB on a formatted hard drive.

---

### Post by toupeiro on 2007-08-14
RedHat Linux 5.2 /sarcasm

(Hey, its what I ran on my 486 DX-4 100)

---

### Post by K.Mandla on 2007-08-14
> **louieb said:**
> :guitar:If you get Linux up and running with a GUI all in 16MB ram then you belong in the installers hall of fame.
Heck, if you can get through the Ubuntu installer on only 16Mb RAM you'll be in the Ubuntu installer hall of fame. I couldn't ever do it on less than 36Mb. The installer goes wacky.

Of course, if you veer clear of Ubuntu, you might get something working. Don't forget [Lowarch]("http://www.lowarch.org/"), although it might be a little more intense than is necessary.

---

### Post by Red Moose on 2007-08-14
Ok, I finally managed to get SBM to boot the CD!  After about six re-installs, I finally managed to get to the Window manager.  There are still a few problems such as:
I have to have the SBM floppy in, otherwise I get some SBKM error.  (I think it's SBKM, it may be some other combination.)
Also, it doesn't automatically start X.  I have to type "startx".
Other than that, it runs pretty good.  I couldn't get the screen resolution any higher than 640x480 and still keep it 16bit color.
Loading programs is about as fast as it was in windows 95.
I guess I belong in the installer hall of fame now!
Thanks all for your help.

---

