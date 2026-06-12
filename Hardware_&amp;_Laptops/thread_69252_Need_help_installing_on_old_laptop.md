---
title: "Need help installing on old laptop"
date: 2005-09-26
forum: Hardware &amp; Laptops
---

### Post by Tony Goodwin on 2005-09-26
So I just bought an old laptop. It is a Compaq LTE 5300

I don't know how to install Ubuntu onto it. I have Ubuntu 5.04 on a bootable CD. It will not boot from the CD (or any CD for that matter). It can boot from a floppy. I have successfully booted both a Win98 boot disk, and Hal91 (Linux on a floppy). Unfortunately, the floppy and cd-rom share a bay, and you can't use both at the same time. They may be warm-swappable, but I have been unable to verify that.

It is not networkable. It does have a pcmcia 56k modem card. However it goes to a regular phone line, not an ethernet port. Any ideas?

-Tony

---

### Post by karuptdata on 2005-09-26
This may sound retarded but in your machiines bios is it set to boot from cd first??It sounds like your machine is set to boot from floppy....

---

### Post by Tony Goodwin on 2005-09-26
[QUOTE=karuptdata]This may sound retarded but in your machiines bios is it set to boot from cd first??It sounds like your machine is set to boot from floppy....[/QUOTE]


Yeah, its too old to boot from cd. Its not an option in the bios to boot from it.

---

### Post by d1337 on 2005-09-26
Just did a quick google on that machine, and the one thing that I saw is that it came loaded with 48megs of Ram.  This may bring you to a screaching halt even if we can get past the boot from CD issue.  You may check your bios date and see if there is a bios update available which may allow you to set it to boot from CD.  I also read a post that claims the drives are warm swappable.

You may try [hp.com]("http://h18007.www1.hp.com/support/files/LTE/us/download/8058.html") and give the bios upgrade a whirl

---

### Post by Tony Goodwin on 2005-09-26
This one actually has 32mb RAM. I couldn't find any minimum harware requirements for Ubuntu, so is this a problem?

---

### Post by d1337 on 2005-09-26
I have run Ubuntu on machines with 128mb RAM and have become rather frustrated while waiting for apps to load.  Most modern distros in which a full blown X environment is desired, 32mb is probably not going to cut it.  Likewise, though, for any MS operating system since probably Win95.  I don't know how much you have invested in the machine, or how much ram you can add to it (or find), but if you want a desktop environment, I don't think you can do it with 32.  There are a few distros out there that strip down services pretty tight and you can use something lighter weight than gnome or kde.  You may check out distrowatch or even linux.org for some links to some of these other distros.  To name a few, DamnSmall Linux, Peanut Linux, Tiny Linux..., and I have heard of folks running some of these with 32-64megs of Ram.  I had an old laptop that I was going to try these on, but in the end I opted to spend my time on bigger hardware.  If you wanted to add a pcmcia network card, they can be had for about $20 which would get you on the net...at least via lynx.

Another thing to keep in mind, if you have the stock 1.3G harddrive, you're going to be slim on what you can install.

IMO, if you did manage to get Ubuntu installed, the experience would be disappointing which is not what I'd like to have happen to someone showing some interest.

---

### Post by Limulus on 2005-09-26
[QUOTE=karuptdata]This may sound retarded but in your machiines bios is it set to boot from cd first??It sounds like your machine is set to boot from floppy....[/QUOTE]

Apparently one can boot a very simple version of Debian from floppy, change the repositories and turn it into ubuntu; see:

[http://www.ubuntuforums.org/showpost.php?p=120024&postcount=3](http://www.ubuntuforums.org/showpost.php?p=120024&postcount=3)
[http://www.ubuntu.com/support/documentation/faq/upgrade-sarge/talkback/1113587843/](http://www.ubuntu.com/support/documentation/faq/upgrade-sarge/talkback/1113587843/)

---

### Post by PaganHippie on 2005-09-26
Much as I love Ubuntu, I'm inclined to agree.  Wiith so little RAM & no way to boot from CD, I'd start looking at Slackware instead of Ubuntu.

---

### Post by d1337 on 2005-09-27
I guess you got me thinking...and I couldn't stop.  I have come across two items in the wiki that **may** be of assistance.

[Smart Boot Manager HowTo]("https://wiki.ubuntu.com/SmartBootManagerHowto?highlight=%28CategoryDocumentation%29")
and
[Low Memory System Install]("https://wiki.ubuntu.com/Installation/LowMemorySystems?highlight=%28CategoryDocumentation%29")
But, of course, no guarantees.  I haven't used smart boot manager and don't know if it would work during a warm swap of drives.  If you knew someone with a USB cdrom, I think SBM will recognize, but again I have no experience.
If it's a toy for learning, this may be a great opportunity.  I have read posts about folks cross cabling with a desktop machine and playing other tricks to work around the cdrom issue.  The low memory install only makes sense as Linux has/is used by many on machines that may otherwise be useless.

Edit:I guess this machine doesn't have USB ports, so a usb cdrom would be worthless...my bad.

---

### Post by Tony Goodwin on 2005-09-27
This laptop had windows 98SE on it, running fairly well. It has a 2.1GB HD

---

### Post by Tony Goodwin on 2005-09-27
Slackware or Debian would be better than Ubuntu?

I suppose I'll try one of those.

---

### Post by d1337 on 2005-09-27
I've used (and still do on a production server and a workstation) Debian and have had great luck.  But the low memory install in the wiki that I linked in my last post looks pretty promising.  There are also 4 links at the bottom of that page, including [this one]("http://www.ubuntuforums.org/showthread.php?t=42873") that have sparked my desire to try my old laptop again.

As Limulus has posted and included a link, it is possible to load a minimal debian and change repos.  That would be where I'd start.  There are instructions on [debian.org]("http://www.debian.org/distrib/") to make install diskettes for this express purpose.  It's probably time consuming, though.  When you started this thread, you said that you had Hal91 running on it.  Is that a Debian based distro?  If it is, that may be just as good a starting place as any if it uses apt-get and has a /etc/apt/sources.list to play with.

d1337

---

### Post by Tony Goodwin on 2005-09-27
Here's the deal. I just basically want something portable I can type screenplays on. I don't need  a whole lot of extra stuff. A GUI would be prefered.

 I also don't have it networked, so any apt-get wouldn't be helpful I don't think.

Hal91 is just a very very small distro. It fits on one floppy. Its somewhat of a rescue disk type distro, I believe.

---

### Post by d1337 on 2005-09-27
Okay...forgot it wasn't newtorked, but again a pcmcia ethernet card could be had for $20, maybe less.  Use the link in my last post to hit Debian.org and follow their instructions to install a base system from floppy disks.  Once you have a base system installed, if you are able to then remove the floppy drive, install the cdrom drive, you may be able to edit your apt-sources list to add the Ubuntu CD rom as a repository...mine is removed, so I don't know it verbatim, but I'm sure someone could help (possibly in the repo forum).  You'd likely have to comment out anything in the sources.list that referred to a web address.  I think that you'd be able to use the cdrom to get a minimal desktop going with a text editor if that would serve your purpose.  If not, you could always burn other packages (and dependencies) to another cdrom and install them that way.  I'd shy away from OO (too heavy) and I think that Abiword has some libs that may overload your machine as well.  Sorry if I wasn't as helpful as you'd like.

d1337

---

### Post by Tony Goodwin on 2005-09-27
Hmmm, I dl'd the Debian floppy images, now it won't boot from the floppy. It says

SYSLINUX 2.11 2004-08-16 Boot failed

---

### Post by d1337 on 2005-09-27
Well, I'm guessing that it is at least reading something from the floppy.  Which images did you write to floppy using what OS (ie. dd for linux or rawrite from ms).  Was your disk new?  Did you format?

The reason I'm asking is that I have had new floppy disks that would not take a format.  I can't recall what I used to check the integrity, but I pitched literally half of a 30 pack of floppy disks that were brand new and sealed.  You may try another floppy (or two).

---

### Post by Tony Goodwin on 2005-09-27
I used rawrite

I reformated the disk and re wrote it, and it gets to a Debian boot screen that says: press f1 for help or press enter to boot


so I hit enter
 and nothing happens

---

### Post by d1337 on 2005-09-27
[Debian.org Floppy Trouble]("http://www.debian.org/releases/stable/i386/ch05s03.html.en#unreliable-floppies")

[The page conatining what I believe to be the correct images]("http://http.us.debian.org/debian/dists/sarge/main/installer-i386/current//images/floppy/")
Is this where you got the images from?

---

### Post by Tony Goodwin on 2005-09-28
Actually, no I was getting the images elsewhere. Those seemed to have done the trick though, thanks.

However it gets stuck about half-way through. Since there is no cd-rom drive at the same time as a floppy is isnt detecting it, and thus not finishing the install


I'm going to try a few times more in different ways.

---

### Post by Tony Goodwin on 2005-10-03
[QUOTE=Tony Goodwin]Actually, no I was getting the images elsewhere. Those seemed to have done the trick though, thanks.
However it gets stuck about half-way through. Since there is no cd-rom drive at the same time as a floppy is isnt detecting it, and thus not finishing the install
I'm going to try a few times more in different ways.[/QUOTE]


Mmkay, just bought a PCMCIA ethernet card in order to do a network install...

---

### Post by Tony Goodwin on 2005-10-07
...And I should be getting it from UPS today.


Hopefully this goes well. Does anyone have a link to any kind of minimum hardware requirements page for either Ubuntu or any other distros? Like one site that has a lot of them would be best.

---

### Post by John.Michael.Kane on 2005-10-07
take your pick from here [https://wiki.ubuntu.com/?action=fullsearch&context=180&value=hardware&titlesearch=Titles](https://wiki.ubuntu.com/?action=fullsearch&context=180&value=hardware&titlesearch=Titles)
[https://wiki.ubuntu.com/?action=fullsearch&context=180&value=install&titlesearch=Titles](https://wiki.ubuntu.com/?action=fullsearch&context=180&value=install&titlesearch=Titles)

hope it helps

---

### Post by Tony Goodwin on 2005-10-10
Thanks for the links and help everyone.

I have a **Netgear FA411** pcmcia network card now. I am installing debian sarge, via floppy, which i then plan to change to Ubuntu when it gets to that point.

I am to the point where I can install drivers for the installation. My network card came with a cd with drivers, but I need to have the necessary ones on a floppy, so debian will install them from there. It has Linux drivers (for Red Hat) but I have no clue how to make a driver floppy. I just copied all the files I thought I may need to a floppy, but that didn't work.

Any ideas?

---

