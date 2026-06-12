---
title: "Why does Ubuntu 10.04 hate newer Nvidia drivers?"
date: 2010-10-22
forum: Hardware
---

### Post by Objekt on 2010-10-22
Why is Ubuntu 10.04 incompatible with recent versions of the proprietary Nvidia graphics card drivers?  So far, the newest version of Nvidia drivers that will work is the one that jockey-gtk (aka "Hardware Drivers") calls "current," which is version 195.36.24, released this April.

I have an XFX GeForce 9800 GTX+ video card.  Both of the recent versions I've tried with Ubuntu 10.04, Nvidia drivers 256.53 and the latest, 260.19.12, result in an error message when I would normally see the Ubuntu login screen.  I then have to operate in Low Graphics Mode or else just do a command-line session.

That definitely isn't normal behavior.  It never happened with Ubuntu 9.10.  What's the deal?

Having the latest Nvidia drivers isn't absolutely necessary, but it would be nice.  Occasionally, new driver releases improve card performance or add features, and I'd like to have those advantages.

FWIW, I am using the 32-bit version of Ubuntu 10.04, and so the 32-bit version of the Nvidia drivers.  I was using the 64-bit version of Ubuntu 9.10, not that it should make any difference to this problem.

---

### Post by Objekt on 2011-03-10
It baffles me that no one has had a word to say about this for nearly 4 months.  Was I the only one who was previously unable to upgrade the Nvidia drivers?

Anyway, whatever it was has been fixed, I think.  I just successfully installed the Nvidia 260.19.44 drivers, released on 3/7/2011.  At least it's pretending to work so far.  Not marking this "solved" until I reboot and still get a GUI.

update:
Yep, not solved.  I got the old "ack, low graphics mode!" errors and garbage once I rebooted.

I uninstalled the 260.19.44 drivers, rebooted, and ran the "Hardware Drivers" thingy.  I chose "Current drivers," but it installed quite old ones, 195.36.24.

Why do I have to be stuck with really old Nvidia drivers?

---

### Post by Objekt on 2011-03-11
I found the solution.

Here's the thing: If you download and install the Nvidia drivers package yourself, it won't work.

You have to use the PPA method.  Here's one explanation that worked for me:

[http://www.ubuntugeek.com/how-to-install-nvidia-260-19-12-drivers-in-ubuntu-10-1010-04-using-ppa.html]("http://www.ubuntugeek.com/how-to-install-nvidia-260-19-12-drivers-in-ubuntu-10-1010-04-using-ppa.html")

The article deals with the Nvidia 260.19.12 drivers, but if you use that method you should get something newer.  I got the 270.29 drivers.

---

### Post by cascade9 on 2011-03-11
> **Objekt said:**
> Why do I have to be stuck with really old Nvidia drivers?

I wonder, do you think that you will see any difference comparing the 195.xx divers to newer versions? Was there a problem with the 195.xx drivers at all? 

> **Objekt said:**
> The article deals with the Nvidia 260.19.12 drivers, but if you use that method you should get something newer.  I got the 270.29 drivers.

I'd advise against gettting beta (270.xx currently) drivers. 

Sure, if you are one of those people that think that the newest, beta drivers from 2011 will make any real difference at all (compared to drivers of similar age and actually tested), for a chip from 2007, go ahead.

---

### Post by wojox on 2011-03-11
> **Objekt said:**
> I found the solution.

Here's the thing: If you download and install the Nvidia drivers package yourself, it won't work.

It does work and there are lot's of threads on how to do it and what to blacklist. :P

---

### Post by Objekt on 2011-03-12
> **cascade9 said:**
> I wonder, do you think that you will see any difference comparing the 195.xx divers to newer versions? Was there a problem with the 195.xx drivers at all? 

Yes and yes.  BIG difference.

Video performance of virtual machines under Virtualbox was terrible with the 195.xx drivers.  I saw a huge performance boost with the 260.xx and 270.xx drivers.  Strange but true.

Mainly I wanted to do it so I could watch Netflix streaming through a Windows XP virtual machine.

I don't know why I got the beta (270.xx) drivers with the ppa method.  Nowhere in the instructions was there anything about them being beta drivers.  I do seem to be getting hardcore X lockups though, so it's time to try the 260.xx drivers.

---

### Post by cascade9 on 2011-03-12
OK Objekt, that one I will believe. ;) 

Mostly when I see people trying to get much newer or the newest possible drivers from nvidia its in the hope that it will help the framerate on some game. Virtualbox is something that the newer drivers could make a big difference with. 

As for the beta thing, I've heard that said before (no warning that there would be beta drivers). Good luck with the 260.xx drivers. BTW, I was using the 270.xx dirvers for a short while, I didnt have any problems. But I wasnt using virtualbox, and I may have been using a different version anyway (I cant recall for sure, I thought I had 270.26)

---

### Post by Objekt on 2011-03-13
Sadly, the performance improvement with Virtualbox wasn't quite enough.  It worked fine when I had the VM running at 1280x1024 in a window, but as soon as I fullscreened it on my secondary monitor at 1920x1080, the Netflix streaming show turned into an ugly slideshow.

Anyway, I think I finally have my drivers straightened out.  I'm missing the icon for the Nvidia X Server Settings applet (under System->Administration), but that's all.

I also noticed the gtk-jockey app no longer detects my hardware or offers the possibility of installing the proprietary Nvidia drivers.  I think that's because of the blacklist entries I had to add to /etc/modprobe.d/blacklist.conf:
```
blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv
```
Those entries are necessary to be able to manually install the 260.19.44 drivers.  But if I'm not mistaken, they also make it impossible for gtk-jockey to "see" my Nvidia card.

As for the complete freeze-ups, that may not have been due to use of the beta (270.xx) drivers.  Random, hard-core system freeze-ups have plagued an unlucky few Ubuntu users since version 9.10.  I've only had it happen perhaps 4 times in the last year, and haven't the least clue why it really happened.  It just seemed suspicious that 2 of those 4 times were after installing the 270.xx drivers.  I've been running with 260.xx since yesterday, and no freeze-ups so far.

---

### Post by paziu on 2011-03-15
hi Objekt,

I just moved to KDE 4.6.1 - had nvidia 260.19.36 - several lockups on X11/KDE - especially on the desktop CUBE/direct render. there is a couple of posts on the net regarding the CUBE freezups... a bug/ticket still open. 

> [https://bugs.kde.org/show_bug.cgi?id=266182](https://bugs.kde.org/show_bug.cgi?id=266182)before I found your post I did upgrade to 260.19.44 x64 no-compat32... need to test...
you talk about blacklisting - my kernel is free of NV/VESA FB stuff - but I am using UVESAFB ( emulates vesafb via v86d in user space ) and I read, some users reported problems in the X11 v1.7.7 days with nvidia & uvesafb ( never had any issues with both running with kde 4.4 and earlier ). once I am in front of my system I will see if there is any improvement, if not, I will disable uvesafb / v86d and re-run all the tests... I'll post the results... later today....


paziu


edit:

no-compat32 drivers do not contain opengl libs ( I think 32bit compatibility for wine and others.... ) 
went with: NVIDIA-Linux-x86_64-260.19.44.run



2.6.37-gentoo-r1/86_64 / nvidia 260.19.36 / xorg-server 1.9.4 / KDE 4.6.1

---

### Post by Objekt on 2011-03-15
Yours is almost exactly the driver package that I installed (260.19.44), except I used the 32-bit version.

No random lockups so far, but I haven't been running Ubuntu the whole time.  Also the lockups are seemingly random, so by definition, I can't really test for them.

I run Ubuntu 10.04 32-bit.  It's perhaps a bit odd to run 32-bit Ubuntu on fully 64-bit capable hardware.  I went with 32-bit because I didn't want the hassles of making certain things work.  For example, the last time I checked, you had to take extra steps to install 32-bit versions of some plugins, because regular Firefox releases are still only 32-bit.

---

### Post by paziu on 2011-03-15
hello Objekt,

the xx.44 nvidia driver behaves the same way as the rest on kde 4.6.1... the CUBE freezes >all< the time - even without uvesafb. I will stick to my original kde 4.4 for now, and upgrade from the 4.6.1 "test" distro if there is anything new released...

now, regarding the 32 bit you are running on a core2: 
>bashmark< on a 64bit linux ( i5 cpu ) showed 900%+ performance increase on floating point / FPU benchmark compared to a 32bit distro - with ALMOST the same kernel config... 
simply install bashmark package or get the source, run it on your 32bit system.... than boot off a 64 bit Live CD/DVD and run it again....  ( i think it comes on the Sabayon linux live dvd ) If the difference also shows several hundred percent, you probably will be able to run a full screen netflix in a virtual_box...
from forums.gentoo.org:
> "If you are working on 64bit long variables, this  improvement seems possible. Double by default is (afair) 64bit long, so  in 32bit mode multiplying 2 doubles is 4xmultiplying 32bit registers and  then some moving and adding to create the result. Under 64bit kernel  it's just one command."If you would find some spare time, running >bashmark< on 32 and 64 bit would probably be a good idea on a core2 box....

thanks!

---

### Post by Objekt on 2011-03-16
I have no idea how to install Bashmark on Ubuntu.  I also downloaded & booted the live CD for Sabayon (both 32- and 64-bit).  Same problem - I can't figure out how to install bashmark.  So I can't run bashmark, sorry.

---

### Post by bcschmerker on 2011-07-02
Thanks for a heads up on some procedures that I may need for getting an eMachines®/Acer® EL1210-09 (Advance Micro Devices® Athlon 64™ LE-1620, nVIDIA® MCP78S chipset, planar nVIDIA® GeForce® 8200 GPU) ready for projection-computer duty.  I presume that ppa:ubuntu-x-swat/x-updates is the needed PPA at Launchpad, in the event that Lucid Main has the wrong nVIDIA-Current driver package?

```
gksudo add-apt-repository ppa:ubuntu-x-swat/x-updates
gksudo apt-get update
gksudo apt-get upgrade
```(Courtesy whorider at UbuntuGeek.com.)

---

