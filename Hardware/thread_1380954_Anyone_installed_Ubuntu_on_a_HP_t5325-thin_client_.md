---
title: "Anyone installed Ubuntu on a HP t5325-thin client? Marvell ARM-prosessor"
date: 2010-01-14
forum: Hardware
---

### Post by eklem on 2010-01-14
I've been running Ubuntu on some of HP's thin clients with pretty good results. The ones I have used has been based on AMD's Geode processor. The only thing missing is a good graphic chip on it, and I'm looking for alternatives. I'm using it as a Media-PC, playing music and movies/TV-shows, and it can't show 720p video. :popcorn:

But now I see HP is starting to push some thin clients with the Marvell ARM-processor. Anyone got Ubuntu running on this one, and if so, have you gotten OpenGL working?

[Specifications for the HP t5325]("http://h10010.www1.hp.com/wwpc/us/en/sm/WF06a/12454-12454-321959-338927-3640405-4063703.html").

---

### Post by eklem on 2010-01-23
Hmm, seems I need to buy it to find out. I always do this, and hoped not to walk into something stupid this time =/ I'll let you know if I find out.

---

### Post by gspat on 2010-01-23
It would probably be best to contact HP directly to see if it will do what you want it to...

looking at the specs, the best resolution SEEMS to be 1024x768, but I am probably wrong.

---

### Post by eklem on 2010-01-24
> **gspat said:**
> It would probably be best to contact HP directly to see if it will do what you want it to...

looking at the specs, the best resolution SEEMS to be 1024x768, but I am probably wrong.

Yes, maybe I should ask HP. A little worried I won't get an answer, tried before, and just got some bureaucratic lingo without content back.

Anyway, on a Norwegian online store, this is written about possible screen resolution:

[...]1680 x 1050 med 16-bits fargedybde og opptil 1440 x 900 med 24-bits[...]

---

### Post by bhtooefr on 2010-03-13
An Ubuntu install is definitely within the realm of possibility, the device is already running Debian.

Here's a blog entry I just posted: [http://my.opera.com/bhtooefr/blog/2010/03/13/hp-t5325-thin-client-risc-os-and-maybe-combining-the-two-or-just-running-linu](http://my.opera.com/bhtooefr/blog/2010/03/13/hp-t5325-thin-client-risc-os-and-maybe-combining-the-two-or-just-running-linu)

The GPU is 2D-only, though, so OpenGL will be purely CPU.

Oh, and 1600x1200 (or 1680x1050) 24-bits works. That's what my monitor DEFAULTED to.

---

### Post by eklem on 2010-03-15
Thanks bhtooefr,
Interesting reading!

Also, seems your link isn't working anymore, but this one should: [http://my.opera.com/bhtooefr/blog/hp-t5325-thin-client-risc-os-and-maybe-combining-the-two-or-just-running-linu](http://my.opera.com/bhtooefr/blog/hp-t5325-thin-client-risc-os-and-maybe-combining-the-two-or-just-running-linu)

---

### Post by boerner on 2010-03-15
bhtooefr,

That is very interesting. I found your blog via this post on the plugcomputer forum:

[http://plugcomputer.org/plugforum/index.php?topic=1452.0;topicseen]("http://plugcomputer.org/plugforum/index.php?topic=1452.0;topicseen")

Thanks for buying the unit and doing the detective work. I would love to see Ubuntu on this, but if I am not mistaken anything past 9.04 won't run on this processor. I do have Debian Squeeze running on a SheevaPlug which runs quite well though:

[http://www.cyrius.com/debian/kirkwood/sheevaplug/]("http://www.cyrius.com/debian/kirkwood/sheevaplug/")

I may be tempted to buy one of these myself. As of today Newegg.com has them for $179.99:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16859105659]("http://www.newegg.com/Product/Product.aspx?Item=N82E16859105659")

Thanks again for your efforts.

---

### Post by clarknova on 2010-03-19
I will likely be geting one of these for testing LTSP on Ubuntu. If you're not in a hurry I should be able to post some insights in a month or so (I have to go through a purchaser).

---

### Post by boerner on 2010-03-19
Another thread that also may prove useful about the device:

[https://www.riscosopen.org/forum/forums/5/topics/279?page=1]("https://www.riscosopen.org/forum/forums/5/topics/279?page=1")

---

### Post by eklem on 2010-03-22
> **clarknova said:**
> I will likely be geting one of these for testing LTSP on Ubuntu. If you're not in a hurry I should be able to post some insights in a month or so (I have to go through a purchaser).

I'll be waiting :D

---

### Post by maj21093 on 2010-03-23
I'm working with the HP instructions on how to update the CITRIX client software to install a copy of Xubuntu on either an HP T5135 (Linux) or rewrite a T5530 (Windows CE). 

I did get a KDE distro on a USB Drive to load up on a T5530, but then had an "output exceeded" error show up on my monitor.

I'll let you know how it comes out in the next day or so.

---

### Post by clarknova on 2010-04-13
I just got a pair of these. I haven't had much time to play, nor to write, but here's some quick first impressions.

-The HP OS is a little easier to use compared to older versions I've played with (on the t5710 and t5730). It will connect to Server 2008 but not 2008R2.

-No BIOS? This is the first time I've worked on an ARM machine. How do I adjust boot device priority, etc?

-I have the VY623AT#ABA part. The VY623AA#ABA generally sells for ~$70 more, but I have yet to spot any differences between these models.

-This thing reports 486M of total flash storage with 0 in use. Obviously it's not counting a system partition.

-No GUI access to a terminal. The menus are minimal. Alt-F2 doesn't let me run stuff. ctrl-alt-F1 doesn't switch virtual terminals. I'm feeling locked down here.

-A quick port scan shows 111 and 6000 are open.

Anybody got any ideas how to boot this thing from USB or pxe? I'll have to play some more with this tomorrow.

---

### Post by Jeffrey Bourgeois on 2010-04-21
Or, somebody can cross-compile a new uImage and run it ? :)

---

### Post by clarknova on 2010-04-21
I haven't had a minute to look at this thing as it's been a crazy couple of weeks here, but I'm a bit stumped as to how I'll go about it. The HP ThinState utility that's included creates a bootable USB stick from the running image, but then I don't see any way to boot it from USB!

On the other hand, if a person had an image of a working filesystem you could just use the ThinState utility to restore that image to the unit, as I'm pretty sure ThinState is just using gzip and dd to write the image to the root device.

---

### Post by clarknova on 2010-05-04
It turns out the t5325 can be booted from USB by pressing the power button again immediately after powering on the device. Unfortunately though, I haven't been able to locate a bootable USB image of Ubuntu or Debian; it appears both distros are designed to use netboot on the ARM arch. The way to netboot, meanwhile, appears to be through uboot, which can only be configured on the serial interface. The t5325 doesn't have a standard DB9 serial port, just what appears to be a 4-pin TTL connector.

On top of this, the processor is ARMv5, not supported in Ubuntu since 9.04.

I could buy a TTL to USB cable, but at this point it just looks like too much hassle. I can build or buy x86 units at a comparable price that will consume comparable power, much less trouble to set up, and have continuing software support (no, I don't count HP as providing continuing software support, and not without cause).

Nice to see HP using OSS in their bundled OS, but they really miss the mark with these closed systems, and in this case it's going to cost them a sale of a hundred or so units.

---

### Post by eklem on 2010-05-04
> **clarknova said:**
> On top of this, the processor is ARMv5, not supported in Ubuntu since 9.04.

So it's not any of these?

Marvell Dove boards:
[https://wiki.ubuntu.com/ARM/MarvellDoveKarmicInstall](https://wiki.ubuntu.com/ARM/MarvellDoveKarmicInstall)

Freescale i.MX51 Babbage boards:
[https://wiki.ubuntu.com/ARM/BabbageKarmicInstall](https://wiki.ubuntu.com/ARM/BabbageKarmicInstall)

---

### Post by clarknova on 2010-05-04
Apparently not.

[http://marc.info/?l=ltsp-discuss&m=127252734221513&w=2](http://marc.info/?l=ltsp-discuss&m=127252734221513&w=2)

---

### Post by eklem on 2010-05-04
> **clarknova said:**
> Apparently not.

[http://marc.info/?l=ltsp-discuss&m=127252734221513&w=2](http://marc.info/?l=ltsp-discuss&m=127252734221513&w=2)

Too bad, but thanks for good answers clarknowa.

---

### Post by langerak on 2011-06-22
Ltsp will be difficult to accomplish, as uBoot is not PXE compliant, since it's from intel.

I own this device myself for around 3 months now, with one rma between due to a faulty uboot rom.

Between this time I've managed to install Debian Sid onto it and runs pretty good, only the crappy GPU is a drawback, but can be tuned a bit to improve performance.

Since there goes great time and knowledge in this process, I've written it all down in my blog at:
[http://lacie.busfreaks.nl](http://lacie.busfreaks.nl)

There may be some errors in it, but if you leave those as a comment, I can fix that!

About RISC os, that's a difficult one, one I really would like to try and if I have some spare time, I might start crosscompiling it :).

Sorry for the bump, but I hope my information might come at handy for other users using this device :)

---

### Post by vodas89 on 2012-01-20
hi everyone ... right now i have one fo those damn machines on my desk ... can u give any clue how to boot and install any linux like operating system except the original one ??

---

### Post by clarknova on 2012-01-21
The closest I can offer:

[http://people.debian.org/~vagrant/hpt5325/HP_t5325_Debian_Ltsp_Howto](http://people.debian.org/~vagrant/hpt5325/HP_t5325_Debian_Ltsp_Howto)

Those instructions are for netbooting the t5325, but you may be able to glean enough useful information there to accomplish your goal. I haven't tried any of this myself (although I do have a couple new t5325 on the bench that are of no use to me, if somebody wants to make an offer :P ).

---

