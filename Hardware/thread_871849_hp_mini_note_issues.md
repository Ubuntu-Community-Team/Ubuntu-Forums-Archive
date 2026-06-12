---
title: "hp mini note issues"
date: 2008-07-27
forum: Hardware
---

### Post by m.musashi on 2008-07-27
I just received an hp mini note 2133 (with suse and 1.2 ghz processor) and the suse install was borked - grub error on first boot. HP is sending the install media but I thought I'd end up with Ubuntu on this anyway so I installed it. I got everything working but there are some issues and I'm wondering if they are possible Ubuntu related or mini note related. I have used one with Suse and didn't notice these issues but I didn't use it for long.

Anyway, the first big issue is video. This is supposed to have a 1280 x 800 display per the hp site but that resolution doesn't work. 1280 x 768 does. That is not a big deal but it may be related to the other issues. For example, the desktop shows video artifacts - small strips with the wrong color. Also, video playback of movies "stutters" from time to time.

Second, I followed the steeps to fix the audio ([https://wiki.ubuntu.com/LaptopTestingTeam/HP2133](https://wiki.ubuntu.com/LaptopTestingTeam/HP2133)) but the alsa driver fails to install. I used 1.0.17 from [http://www.alsa-project.org/main/index.php/Download](http://www.alsa-project.org/main/index.php/Download). It will configure and make but make install exits with errors. Sorry, I didn't save them unless they are in some log file?

Just curious if others using the mini note have seen similar issues and if you were able to solve them.

Thanks.

---

### Post by jtappin on 2008-07-28
Video: To get the VIA-supplied drivers working properly, you need to use the original Hardy kernel (2.6.24.16), otherwise the kernel modules won't laod and you won't get 3D acceleration. [BTW -- I think 1280x800 is a misprint, every source I've seen says 1280x768].

If you don't mind not having 3-D acceleration, then the VIA drivers, the vesa driver (or, with a bit of work, the current openchrome-but not the one in the distro) will all work with the up-to-date kernel.

For the sound: I think that if there is a problem with the 1.0.17 release it lies in a different card so if you do the configure with:
./configure --with-cards=hda-intel
you should be successful.

---

### Post by elbertcuenca on 2008-08-01
Hi, I'm trying to install 8.04.1 Hardy Heron into a brand new HP Mininote 2133 (model no. [KZ980PA]("http://h10010.www1.hp.com/wwpc/ph/en/sm/WF06b/321957-321957-64295-306995-306995-3687084-3727983.html"))

I am following the instructions in the [Ubuntu wiki]("https://wiki.ubuntu.com/LaptopTestingTeam/HP2133"). I'm able to go as far as running Ubuntu live and use the Install assistant to configure. During actual installation at the stage where it says *Installing System Copying Files... 29%,* It'll halt and I get the error message "**Failed to copy files; faulty Cd/DVD or hard disk?**" [**errno 5] input/output error**.

I'm using an external Samsung Writemaster (and I've burned three different CD installers using three different Macs), but I'm not sure if the installer disk or external optical drive is the problem since I'm able to run Ubuntu Live. Been trying over and over again to no avail.

Any clues?

Thanks in advance.

---

### Post by mattdm on 2008-08-01
So, what about wireless and native drivers? I'm looking to buy one of these things, but if I'm stuck with a) Suse or b) nsdiswrapper, I'll look elsewhere. The [wiki](https://wiki.ubuntu.com/LaptopTestingTeam/HP2133) has a note at the top about how it just works with kernel 2.6.25.4 and beyond. Can someone confirm this for me before I go ahead with the purchase?

And, is this the case on all models of the HP2133? The Wiki warns that the 4GB SSD model uses a different network card -- is that card also natively supported in the new kernel?

Thanks!

It's nice that laptop manufacturers are finally getting around to selling Linux laptops, but sheesh, can't they use hardware that *just works*?

---

### Post by phidia on 2008-08-01
> **elbertcuenca said:**
> Hi, I'm trying to install 8.04.1 Hardy Heron into a brand new HP Mininote 2133 (model no. [KZ980PA]("http://h10010.www1.hp.com/wwpc/ph/en/sm/WF06b/321957-321957-64295-306995-306995-3687084-3727983.html"))

I am following the instructions in the [Ubuntu wiki]("https://wiki.ubuntu.com/LaptopTestingTeam/HP2133"). I'm able to go as far as running Ubuntu live and use the Install assistant to configure. During actual installation at the stage where it says *Installing System Copying Files... 29%,* It'll halt and I get the error message "**Failed to copy files; faulty Cd/DVD or hard disk?**" [**errno 5] input/output error**.

I'm using an external Samsung Writemaster (and I've burned three different CD installers using three different Macs), but I'm not sure if the installer disk or external optical drive is the problem since I'm able to run Ubuntu Live. Been trying over and over again to no avail.

Any clues?

Thanks in advance.

I think you need to check the downloaded file for integrity, and you can also check the burned cd for integrity from the boot menu. You need to do both.
In OS X you have a terminal app. You can open that and type md5 (name of the iso file) to check the md5sum. In OS X, as I said the command is just md5. The md5sum values to check against should be available where you downloaded or check [this page]("http://www.ubuntu.com/getubuntu/downloadmirrors").

---

### Post by jtappin on 2008-08-01
> **elbertcuenca said:**
> Hi, I'm trying to install 8.04.1 Hardy Heron into a brand new HP Mininote 2133 (model no. [KZ980PA]("http://h10010.www1.hp.com/wwpc/ph/en/sm/WF06b/321957-321957-64295-306995-306995-3687084-3727983.html"))

I am following the instructions in the [Ubuntu wiki]("https://wiki.ubuntu.com/LaptopTestingTeam/HP2133"). I'm able to go as far as running Ubuntu live and use the Install assistant to configure. During actual installation at the stage where it says *Installing System Copying Files... 29%,* It'll halt and I get the error message "**Failed to copy files; faulty Cd/DVD or hard disk?**" [**errno 5] input/output error**.


That does sound like a bad install CD especially as it's always happening in the same place. Try running the CD-checking option on the install CD (sorry I don't recall exactly where to find it on the live-CD startup options).

Another way to check is to compare the MD5SUM values of your downloaded iso file, the MD5SUMS list on the servers and the CD you burned (md5sum /dev/scd0 [or wherever your cd device appears]), I'd suggest trying that on another box with an internal cdrom. They should all be the same. 

Alternatively you could try booting the CD on another machine and running its internal check on that (if it succeeds there then it's probably the drive and a somewhat marginal CD).

---

### Post by elbertcuenca on 2008-08-03
> **jtappin said:**
> That does sound like a bad install CD especially as it's always happening in the same place. Try running the CD-checking option on the install CD (sorry I don't recall exactly where to find it on the live-CD startup options).

Another way to check is to compare the MD5SUM values of your downloaded iso file, the MD5SUMS list on the servers and the CD you burned (md5sum /dev/scd0 [or wherever your cd device appears]), I'd suggest trying that on another box with an internal cdrom. They should all be the same. 

Alternatively you could try booting the CD on another machine and running its internal check on that (if it succeeds there then it's probably the drive and a somewhat marginal CD).

I solved the problem. It was a bad DL of the iso. I downloaded another copy and got it working. Thanks for all the assistance! The 2133 is now running ubuntu!

---

### Post by m.musashi on 2008-08-04
> **jtappin said:**
> Video: To get the VIA-supplied drivers working properly, you need to use the original Hardy kernel (2.6.24.16), otherwise the kernel modules won't laod and you won't get 3D acceleration. [BTW -- I think 1280x800 is a misprint, every source I've seen says 1280x768].
Sorry to tune out on ya. I discovered the problems were hardware related and I'm sending it back for repair/replacement. I will look into your suggestions when I get it back. Thanks.

> **mattdm said:**
> So, what about wireless and native drivers? I'm looking to buy one of these things, but if I'm stuck with a) Suse or b) nsdiswrapper, I'll look elsewhere. The [wiki](https://wiki.ubuntu.com/LaptopTestingTeam/HP2133) has a note at the top about how it just works with kernel 2.6.25.4 and beyond. Can someone confirm this for me before I go ahead with the purchase?
I can't say how Sled deals with the wifi but I know that does work out of the box. However, Sled is very disappointing compared to Ubuntu. It feels very incomplete and rather hard to configure. There isn't even a movie player and no simple way to add one.

Ubuntu does run fine on this if you take the time to deal with a few of the hardware hassles - wifi being one of them. You do have to use ndiswrapper but once you do it works fine. This is a pretty cool laptop and the more I use it the more I like it. I wouldn't pass just because of the ndiswrapper issue. I've haven't seen the new 901 eee but I think the mini note is much nicer based on what I've read. The metal case is almost sexy and the keyboard is fairly easy and comfortable to use. The touchpad is a bit annoying but that's solved with a usb mouse. However, I don't really have much issue with the touchpad.

I'm not sure about the kernel issues you refer to but I followed that wiki and got mine running without much issue.

---

### Post by earlycj5 on 2008-08-06
The native resolution *is* 1280x768 not 1280x800 so that's not an issue.  See this PDF from the HP website: [http://h10010.www1.hp.com/wwpc/pscmisc/vac/us/product_pdfs/2133.pdf](http://h10010.www1.hp.com/wwpc/pscmisc/vac/us/product_pdfs/2133.pdf) :)

---

### Post by jtappin on 2008-08-07
> **earlycj5 said:**
> The native resolution *is* 1280x768 not 1280x800 so that's not an issue.  See this PDF from the HP website: [http://h10010.www1.hp.com/wwpc/pscmisc/vac/us/product_pdfs/2133.pdf](http://h10010.www1.hp.com/wwpc/pscmisc/vac/us/product_pdfs/2133.pdf) :)

There does however appear to be an issue with the vesa driver using a resolution of 1280x720 instead of 1280x768 which generates the horizontal lines.

---

### Post by m.musashi on 2008-08-10
Quick update. I got my new machine from HP and installed Ubuntu right away. It's all working fine and there are no video issues (although I keep hearing that desktop effects work but not for me). The only thing right now seems to be the mic but I haven't really tried to use it. Thanks for the help.

---

### Post by genoteich on 2008-08-11
I sure hope someone can help me with this issue.  I installed Hardy Heron on an old Sony PCG-R505TE laptop a few days ago and I've been fighting with the display ever since.  Display hardware is Intel 8215 integrated chipset.

No matter what I do, I cannot get Ubuntu to recognize that the display is capable of 1024x768.  The highest I can get is 800x600 which creates a desktop screen that is more than an inch too small around the whole perimeter of the display and is very hard to use and read.  :mad:

I have tried everything I've read in the Ubuntu Documents and in the forums including changing the display driver and changing the xorg.conf file both manually and through the update interface.  When I access the list of possible display settings in the GUI, it always says that only 800x600 and 640x480 are available.

Please help - I would be happy to post the results of some troubleshooting steps.

---

### Post by genoteich on 2008-08-14
NO responses yet?  Is anyone out there?

---

### Post by andif62 on 2008-08-15
Maybe you should have had a look on the thread name:[B]
HP[/B] mini note issues

---

### Post by genoteich on 2008-08-15
Okay good point, I'll search for a thread that relates to my hardware and issue and post a new one if I don't find anything.

Thanks for responding.

---

### Post by andif62 on 2008-08-16
You're welcome :)

---

### Post by pj_ramirez_1 on 2008-09-10
hello, I recently bought a mini note with the 120Gb+Suse option. I installed Hardy following the steps from the LaptopTestingTeam wiki, and everything worked for 3 weeks. About two weeks ago, wireless stopped working, I can connect to a wired network just fine, but the machine doesn't detect any wireless connection, encrypted or not. I have reinstalled Hardy and followed all steps again, since I thought it was a hardy issue, but to no avail. I am starting to think it is a physical problem with the card and might have to send the computer back. Has anyone had similar problems?, and if so, are they fixable? Thank you all

---

### Post by m.musashi on 2008-09-11
I've run into similar issues. However, in my case I can connect to some networks (usually open) but not my Linksys 600n running dd-wrt. I can't figure out if it's a dd-wrt issue or something with the laptop but I'm thinking it might be a bit of both. A mac will connect just fine as will Linux computers with non-broadcom hardware. Therefore, I'm thinking it's in part due to the poor support for broadcom (for which I blame broadcom and HP for choosing them on a Linux computer).

Timing is about the same too so I wonder if it could be some update to the drivers or wpasupplicant that could have caused the issue.

---

### Post by thejort on 2008-09-24
Hi,

Were you able to get your Desktop effects working for your HP Mini note?

I have same problem here.

Thanks,

---

### Post by m.musashi on 2008-09-25
> **thejort said:**
> Hi,

Were you able to get your Desktop effects working for your HP Mini note?

I have same problem here.

Thanks,

Nope. I gave up. I'm not very please with the mini-note. I think they had one target in mind - schools where no one would do anything other than run Suse using the default install. I can get ubuntu to run and in many ways it runs better than Suse - well probably all ways. But I've had nothing but problems - returned twice already for screen issues and the 3rd screen now has a stuck red pixel right in the middle. I'm just glad this was a work purchase.

---

