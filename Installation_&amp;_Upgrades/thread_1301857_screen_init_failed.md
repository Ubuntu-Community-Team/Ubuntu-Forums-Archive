---
title: "screen init failed"
date: 2009-10-26
forum: Installation &amp; Upgrades
---

### Post by TemuxUser on 2009-10-26
Hello!
I am trying to set up a computer lab in my village in Guatemala (I am a Peace Corps volunteer) and I have a pile of somewhat dated computers that came from a business in the US. They are all identical (thank god) but I am having trouble getting past a few issues with the install. Computer stats:

Pentium II processor
512 MB RAM
5, 40 or 120GB HDs
Diamond Fire GL Pro 1000 video card

This seems to fit with the system requirements for Intrepid, which is what I am trying to install (live CD install, original disk received by mail and checks as error-free)

I get through most of the install checks, then it gets to this:

Loading, please wait...
usplash: Setting mode 640x480 failed
screen init failed

then it gives about a paragraph describing the unix build, then gives me a command prompt
ubuntu@ubuntu:~$

at which point it is just waiting. Anyone have any thoughts on where to go from here?

---

### Post by nerdzero on 2009-10-26
I think if you hit F6 at the install menu when you have "Install Ubuntu" selected, you can modify the boot parameters to remove 'quiet splash'.  This may let you get further in the install process.

---

### Post by TemuxUser on 2009-10-27
F6 doesn't do anything. :P  All the help documentation online assumes that I am getting to the spiffy Ubuntu installation options screen like they show here:
[https://help.ubuntu.com/community/BootParameters](https://help.ubuntu.com/community/BootParameters)
But I am getting a blue  ASCII text-only box for my installation options. It looks like this (attached file) and F6 doesn't do anything from there. My linux-geek buddy (using "geek" in the most respectful way, of course!) says he's never seen anything like that before. 

I also tried installing Ubuntu as a dual-boot on top of WinXP, as a possible workaround, and that is failure as well. In this case, is says something about X server failing to startup after 60 seconds (second attached file).

---

### Post by nerdzero on 2009-10-28
Whoa...that does look different.  I was thinking "Oh, he has alternate install CDs" until I saw your picture.  You got these CDs in the mail?

The error message about X seems related to the usplash error.  It sounds like your video card may not be supported.  What is available under the Advanced options menu?

---

### Post by bribera on 2009-10-28
Weird - that doesn't look like any menu I've seen.

I wonder if it's a text-only fallback since the default installer can't figure out how to use his graphics card. That card *should* be supported in general, but perhaps it's not built into the installer system.

Have you tried both of the first two options? Do you hit the same error with both?

Removing "quiet splash" from the boot parameters seems like a good route to try, so do check the Advanced Options for some path that would let you try that.

---

### Post by TemuxUser on 2009-10-28
@nerdzero: yeah, they are the original 8.10 install CDs that ship in the mail. I ran the CD check utility, too, and it says they are OK. Under the Advanced Options menu, all it gives me is the option to return to the main menu (a bit disappointing!).  I feel like your hunch that it has to do with the video card might be right... I am trying to install TinyXP on a sister machine, same specs, and I am having a hell of a time getting XP to place nice with the video card, too. it's SO annoying to work on a Windows machine as it is, but in 16 color 640x480?  Yuk!

@bribera: both of the first two options give the same error. Advanced doesn't do anything (see above) and the normal boot parameter line isn't available. I can get to a 
boot:
command prompt, but I am not sure that's where I can modify boot parameters. I will try it tomorrow, and see.

So now the question might be, what does one do if they want to install Ubuntu on a machine with an unsupported video card?

---

### Post by nerdzero on 2009-10-28
Google did not provide much more info.  Seems you are not alone in having problems with this video card though.

[http://www.linuxcompatible.org/Diamond_Fire_GL_1000_Pro_c10281.html](http://www.linuxcompatible.org/Diamond_Fire_GL_1000_Pro_c10281.html) (from 2005)

[http://features.linuxtoday.com/news_story.php3?ltsn=1999-01-26-015-05-NW-SM&reply=0084&quote=1](http://features.linuxtoday.com/news_story.php3?ltsn=1999-01-26-015-05-NW-SM&reply=0084&quote=1) (this one is from 99!)


If you can, I'm not sure what your connection is like, try the Ubuntu alternate installation CD or another distribution.  I've had success with installing Damn Small Linux on older hardware when Ubuntu wouldn't work.  It's Debian-based too.

[http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

Or, since you can boot into Windows, perhaps installing Ubuntu via Wubi is an option.  I have never tried it.


I'd also considering filing a bug report in launchpad.

[https://help.ubuntu.com/community/ReportingBugs#Filing%20bugs%20at%20Launchpad.net](https://help.ubuntu.com/community/ReportingBugs#Filing%20bugs%20at%20Launchpad.net)

[https://bugs.launchpad.net/ubuntu/+filebug/?no-redirect](https://bugs.launchpad.net/ubuntu/+filebug/?no-redirect)


Let us know how it goes.  Good luck!

---

### Post by nerdzero on 2009-10-28
> **TemuxUser said:**
> I also tried installing Ubuntu as a dual-boot on top of WinXP, as a possible workaround, and that is failure as well. In this case, is says something about X server failing to startup after 60 seconds (second attached file).

Wait a sec, does this mean you were able to install but just can't boot into the desktop environment?

---

### Post by bribera on 2009-10-29
> **TemuxUser said:**
> what does one do if they want to install Ubuntu on a machine with an unsupported video card?

If possible, download the alternate install CD as nerdzero suggested. Your graphics card may actually be supported, but wasn't supported by the installer for some reason. The alternate CD should just let you do a text-only install without needing to load up the X server.

---

### Post by TemuxUser on 2009-11-03
> **nerdzero said:**
> Wait a sec, does this mean you were able to install but just can't boot into the desktop environment?

It will install (i think?) but I don't know for sure because it won't run. 

Following an earlier idea, I finally got DSL downloaded and tried installing that. It will actually run (yay!) but it has huge problems with the graphics. Check out the three attached screenshots. The first is the DSL splash screen, which seems to be at a reasonable resolution and bit depth, though it's hard to tell since it isn't a really colorful image.  Then, during install, it gives me a really narrow range of options for screen selection. (second image).  I pick the highest one, 80x60, and can get a functioning desktop environment with DSL.... but it's a pretty bad resolution (third image). How can that be, after the splash screen looked so good?. 

I know this isn't a DSL forum, but this all leads me to believe that the whole thing is video card related, which brings me back to Ubuntu. Is there a way I can get at least this far with Ubuntu? And if I do that, is there a driver I need to get & install for my oddball graphics card? Does Ubuntu even use drivers? I know nothing about Unix (what better way to learn?) 

I will be back in the US in a few weeks for a visit, and will (hopefully) pick up the disk for the latest Ubuntu release, and can try that. Should I also be spending the week or whatever to bittorrent an alternate install CD? If so, can someone point me in the right direction?

---

### Post by nerdzero on 2009-11-04
Oooo, man.  You are really testing my troubleshooting abilities.  I will have to do some more research.  Reminds me of when I first started using Linux ;)

Hopefully this will get you a usable desktop in DSL:  Right-click on the background and from the menu that appears select Setup > Xvesa.  This should open another window with a list of resolutions and color depths.  Pick one.  Does it look any better?

I would say it's definitely due to the older video card.  I checked AMD's website and the Linux drivers for your card are very old and not usable in Ubuntu.

[http://support.amd.com/us/gpudownload/Pages/firegllegacy-linux.aspx](http://support.amd.com/us/gpudownload/Pages/firegllegacy-linux.aspx)

XP drivers are available though.

[http://support.amd.com/us/gpudownload/Pages/firegllegacy-xp.aspx](http://support.amd.com/us/gpudownload/Pages/firegllegacy-xp.aspx)

I'll be back after I read some more...Hey!  Any X experts feel free to chime in with suggestions!

---

### Post by jaime256 on 2009-11-04
You should try downloading previous version which is Ubuntu 9.04.  I think it's one of the better versions and you just need one cd. The latest version (9.10) has been nothing but a headache for me. That previous one installs in almost anything for me. I just scaned through your thread but even with just a slow line, you can use the bittorrent to download it from the Ubuntu site so you can try it now instead of after you come back to the US, and also do try the alternative version if this one doesn't work. If you have access to a faster line, just download the iso and burn that one cd. Make sure you do a disk check before you install though, it will save you a bit of time if there is a problem with the download. But if that cards are really that old, then who knows since video was one of the problems with linux before with the earlier versions.

---

### Post by nerdzero on 2009-11-04
Well, to use Ubuntu, I think your best bet is using the alternate install CD and then generate a custom /etc/X11/xorg.conf file to tell your system to use the standard vesa driver (the fglrx driver may work though).  Performance may suffer but at least you should have a usable desktop.

Here's a link to the torrent for the alternate install of 9.10:

[http://releases.ubuntu.com/9.10/ubuntu-9.10-alternate-i386.iso.torrent](http://releases.ubuntu.com/9.10/ubuntu-9.10-alternate-i386.iso.torrent)

If you want a different version, just change 9.10 everywhere in the link to the version you want.

Since, this is older hardware, you may also want to consider using Xubuntu since it's a little lighter-weight vs. a standard Ubuntu installation.

[http://www.xubuntu.org/](http://www.xubuntu.org/)

[http://mirror.anl.gov/pub/ubuntu-iso/CDs-Xubuntu/9.10/release/xubuntu-9.10-alternate-i386.iso.torrent](http://mirror.anl.gov/pub/ubuntu-iso/CDs-Xubuntu/9.10/release/xubuntu-9.10-alternate-i386.iso.torrent)

---

### Post by TemuxUser on 2009-11-05
@nerdzero: in DSL i tried your Setup > Xvesa and it gave me an empty window with an OK button. I guess that there aren't any video options available?  I will try the alternate install disks too, i guess.

@jaime256: I am bittorrenting 9.04, when it's done in a few days I'll give it a try. If it doesn't go, i will try 9.10 when i get the disks.

---

### Post by TemuxUser on 2009-11-09
OK guys, I got 9.04 and tried both live install and regular, and it gives me the same errors. I checked the disk, and it's good. I have this OTHER idea... maybe I should go to Ebay and get a handful of old-ish video cards that are cheap and confirmed to work with Ubuntu. Sooo....  any recommendations?  They should be old enough to be cheap, so I can get a half dozen of them using the VERY SMALL budget I have (I am a Peace Corps volunteer, remember!), but new enough to still be available and work with Ubuntu. 

thoughts?

---

### Post by jaime256 on 2009-11-10
Well, sorry to hear that. I was just re-reading the beginning of your post and I think I also had problems with the same brand cards. Here's an idea. Do you have access to other older computers, any computer that you can borrow their card from? If so try that first as long as they are not diamond just to make sure they work. Then that may give you a better idea of what you may be able to use with those older computers instead of spending money and finding something wrong, again. Might save you time and a headache this way.

---

### Post by nerdzero on 2009-11-10
Sorry and surprised to hear that.  I was sure the alternate install CD would work and at least get you to the prompt of a fully installed system.  Ack...oh well.

I've always had good luck with NVIDIA GeForce cards. I'm not sure what kind of systems you have but make sure you get the right kind (AGP, PCI, etc) and one that will physically fit in your case.

I think I have an old AGP GeForce or Radeon somewhere around here in my pile o' parts.  PM me if it will fit one of your motherboards and I'll see if I can find it.

---

