---
title: "Xorg bug in rs400 ATI chipsets - black screen on resume"
date: 2009-11-16
forum: Hardware
---

### Post by bertmanphx on 2009-11-16
All,
I have an ATI 200m video card that suspended to RAM perfectly in Jaunty, but gives a black screen upon resume in Karmic.
A number of posts can be found on the forums about this problem. One such post I have been participating in [here]("http://ubuntuforums.org/showthread.php?t=1307618") has right now, over 250 posts, and 21,000 views.  That tells me that quite a few people are looking for solutions to suspend / resume problems.
One interesting [post I found was here]("http://ubuntuforums.org/showthread.php?t=1315291&highlight=radeon+xorg").  This lead me to the patch, proposed on the Xorg mailing list at [SourceForge here]("https://sourceforge.net/mailarchive/forum.php?thread_name=1256605062-3237-1-git-send-email-airlied%40gmail.com&forum_name=dri-devel").  It may solve my problem.

My problem is, how do I track if this change has made it into a backport, proposed, or some PPA package?

Any help would most appreciated.

Thank you,

bertmanphx

---

### Post by ali780 on 2009-11-17
I have same problem on my Znote 6224w with ubuntu 9.10.
Hope this problem fix ASAP.

---

### Post by bertmanphx on 2009-11-17
Ok,
I am not recommending this to anyone, so try at your own risk!!

It seems I can now successfully suspend, at least 5 times so far and resume properly, using the following parameters:

Kernel from mainline - 2.6.32-rc7, using parameter "modeset=0"

and

The ATI driver only from the following PPA
[https://launchpad.net/~xorg-edgers/+...e/drivers-only](https://launchpad.net/~xorg-edgers/+...e/drivers-only)

While this has worked for my HP DV8040, with ATI 200m Video card RS480 5955, I do not know if this works for you. 

bertmanphx

---

### Post by bertmanphx on 2009-11-22
Hello all,
the fix i posted above, did not llast long, and was not consistent.  I did solve the problem  by installing the xorg drivers for ATI and Radeon card.

bertmanphx

---

### Post by hfdragon on 2009-11-23
Hi 

Which drivers did you install for the ATI card ?

Those from the ppa you mention ?

I'm also having the black screen on resume problem with karmic, with an ATI card : ATI Mobility Radeon HD 4670

---

### Post by bertmanphx on 2009-11-23
hfdragon,
I pulled these from the Jaunty repos.  I'm not sure this would apply to your machine though, because i think with that chipset, you are using the radeonHD driver.

See the[ link here]("http://ubuntuforums.org/showthread.php?t=1307618&page=29") for the other thread that lists the drivers that have fixed the issue for me bertmanphx

---

### Post by fbugnon on 2009-12-30
The solution on post **#3** works for me, at least for the moment....

Thanks a lot bertmanphx! Even if this does not last very long, as you mentioned, it is good to be able to come "back to life" after suspending.

The only different thing I did was using the parameter "modeset=0" on the default kernel I already had (2.6.31-16), not the one you mentioned (2.6.32-rc7), but is working fine so far -- truth be said: just did my first resume :)

If this does not works in the future I'll try your suggestion **#6**.

_My computer:_
HP Pavillion a1130n
AMD Athlon(tm) 64 Processor 3500+
ATI RS480 [Radeon Xpress 200G Series]

_Running:_
Ubuntu 9.10 x86_64
with all regular updates + xorg-edgers PPA drives
"modeset=0" added in the end of the default kernel module in grub.cfg

---

### Post by bertmanphx on 2009-12-30
fbugnon,
I'm glad that it's working for you.
I have NOT had anyone contact me on my bug reports.  I guess I'll see if it get fixed in 10.04.

bertmanphx

---

### Post by fbugnon on 2009-12-30
> **bertmanphx said:**
> (...) I'm glad that it's working for you (...)

Well, it was... It didn't last long.... but it was good meanwhile :)

Now I got it working again following advice #4, i.e., installing the following jaunty packages:

- xserver-xorg-video-ati (1:6.12.1-0ubuntu2)
- xserver-xorg-video-radeon (1:6.12.1-0ubuntu2)

I use those packages because of my hardware (see previous post).  People interested in this experience should look for drivers accordingly to their specific hardware.

I know most information about this problem is located on [this thread]("http://ubuntuforums.org/showthread.php?t=1307618&page=28"), but for some reason I'm not able to post there, so I'll use this space to share some more details on how to achieve this -- hope you, bertmanphx, don't mind this friendly thread hijacking. ;)

fbugnon

____________________________


little **[SIZE="4"]HOW-TO:[/SIZE]**

**[COLOR="Red"]WARNING:[/COLOR]** **This worked for me, it does not means it will work for you. Use this instructions at your own risk. If you are not familiarized with the use of terminal, it might be preferable not to suspend / hibernate until an official solution is implemented.** 

**1. [COLOR="Red"]Back-up your sources.list[/COLOR]**, located in /etc/apt/ with this command:

```
$ sudo cp /etc/apt/sources.list /etc/apt/sources.list-bkp-original
```

**2. [COLOR="Red"]Edit the original sources.list[/COLOR]:**
2.1 open the file in gedit with this command:
```
sudo gedit /etc/apt/sources.list
```
2.2 change repository from karmic to jaunty:
the firs lines should look like this:
> # deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release amd64 (20091027)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) **karmic** main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) **karmic** main restricted

In the last 2 lines, where it's written "**karmic**", change it to "**jaunty**", save it and close the document.

**3. Get to know your [COLOR="Red"]video card / chipset[/COLOR]:**
If you don't have this information on some sticker glued into your computer, you might use the product/model to search on the Internet or use the command "lshw" to get a complete list of your hardware and look for this information under the section "*-display"

**4.** With your [COLOR="Red"]hardware information[/COLOR],** look for your specific[COLOR="Red"] jaunty drive[/COLOR]** in:
[http://packages.ubuntu.com/jaunty/x11/](http://packages.ubuntu.com/jaunty/x11/)
For example:
I have an ATI-Radeon video card, so I've installed these drives:
- xserver-xorg-video-ati (1:6.12.1-0ubuntu2)
- xserver-xorg-video-radeon (1:6.12.1-0ubuntu2)

**5. [COLOR="Red"]Update repositories[/COLOR]** using the command:
```
$ sudo aptitude update
```

**6. [COLOR="Red"]Install[/COLOR] your specific jaunty drives** with the command:
```
$ sudo aptitude install xserver-xorg-video-[drive_name]=[drive_version]
```
replacing [dirve_name] and [drive_version] accordingly.
For instance, for "xserver-xorg-video-ati (1:6.12.1-0ubuntu2)" shown in the ubuntu packages site, use it:
```
$ sudo aptitude install xserver-xorg-video-ati=1:6.12.1-0ubuntu2 
```

**7. Lock this drives using [COLOR="Red"]Synaptic[/COLOR]:**
Go to **System > Administration > Synaptic**, search for the drives you just installed, select it/them and go to Package > Lock version.
(This will avoid your drives being replaced with newer versions where suspension/hibernation don't work)

[B]
8. [COLOR="Red"]Remove or back-up your "jaunty"sources.list[/COLOR][/B] with the command:
- _Remove_ ```
$ sudo rm /etc/apt/sources.list 
```
- _Back-up_ ```
$ sudo cp /etc/apt/sources.list /etc/apt/sources.list-bkp-jaunty
```
(Backing-up is preferable in the case you have to go through this again)

**9. [COLOR="Red"]Restore your original sources.list[/COLOR]** with the command:
```
$ sudo cp /etc/apt/sources.list-bkp-original /etc/apt/sources.list
```

**10. [COLOR="Red"]Reboot your computer[/COLOR] and hopefully suspend / hibernation should work now!**

---

### Post by hfdragon on 2010-01-11
I'm still having problems with suspend.

I tried to install the jaunty packages, but I still have the black screen after suspend.

I've checked, and my card is using the fglrx driver (ati) and not radeon...

I've tried thins without installing the -RC7 kernel... is there a repo fir this kernel ?

---

### Post by bertmanphx on 2010-01-14
hfdragon,
I do not know if you can compare these issues if you are running a different driver.  If you have an rs400 chipset, my opinion would be to use the stock radeon driver.  I had thought that fglrx dropped support for this chipset .

bertmanphx

---

