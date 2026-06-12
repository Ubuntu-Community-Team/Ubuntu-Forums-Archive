---
title: "Want to install iwlwifi on Linux CNC 10.04... backports?"
date: 2013-10-04
forum: Hardware
---

### Post by SwarfEye on 2013-10-04
Hello,

I just bought a new box to run Linux CNC for a robot that I am building.

Linux CNC is based on the 10.04LTS release.

The new machine that I bought has an Intel-Centrino Wireless-N 2230 card in it that is supposed to "run fine with linux".

It seems that the driver and firmware for the card are for use with newer kernals... 3.2+.  I'm told it works just fine under 12.04?

I am under the impression that I can get this thing up and running by using backports.

I have installed the package 'linux-backports-modules-wireless-lucid-generic' which a couple of web posts have said is the trick... but things still aren't working.

At this point I'm a bit lost, and I don't know what to try next.  I'm thinking I ought to just run out and buy a usb wireless dongle and be done with it... though it would be infinitely cooler to get this thing working properly.

Any suggestions would be welcome.

Thanks so much,

Bill

---

### Post by Bashing-om on 2013-10-04
SwarfEye; Hi!

As "Linux CNC is based on the 10.04LTS release". Maybe, there is no access to the repository as ubuntu DESKTOP version has reach End Of Life and no longer enjoys support.
Please post back the out put - between code (#) tags - of terminal code:
```

cat -n /etc/apt/sources.list

```

And you will get our best advisement.

[INDENT][INDENT]try'n to help
[/INDENT][/INDENT]

---

### Post by mörgæs on 2013-10-04
Are you sure that the latest LinuxCNC (2.5.3 released a few months ago) is still based upon Ubuntu 10.04? Please run
```
uname -a 
```
too see which kernel is in use.

Enabling the backport repository does not help if noone has backported the package in question.

---

### Post by SwarfEye on 2013-10-04
Ok!  Thank you.

Here is the output of 'cat -n /etc/apt/sources.list'

>      1	# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
     2	# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
     3	# newer versions of the distribution.
     4	
     5	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted
     6	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted
     7	
     8	## Major bug fix updates produced after the final release of the
     9	## distribution.
    10	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
    11	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
    12	
    13	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14	## team. Also, please note that software in universe WILL NOT receive any
    15	## review or updates from the Ubuntu security team.
    16	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
    17	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
    18	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe
    19	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe
    20	
    21	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22	## team, and may not be under a free licence. Please satisfy yourself as to 
    23	## your rights to use the software. Also, please note that software in 
    24	## multiverse WILL NOT receive any review or updates from the Ubuntu
    25	## security team.
    26	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
    27	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
    28	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
    29	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
    30	
    31	## Uncomment the following two lines to add software from the 'backports'
    32	## repository.
    33	## N.B. software from this repository may not have been tested as
    34	## extensively as that contained in the main release, although it includes
    35	## newer versions of some applications which may provide useful features.
    36	## Also, please note that software in backports WILL NOT receive any review
    37	## or updates from the Ubuntu security team.
    38	# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
    39	
    40	## Uncomment the following two lines to add software from Canonical's
    41	## 'partner' repository.
    42	## This software is not part of Ubuntu, but is offered by Canonical and the
    43	## respective vendors as a service to Ubuntu users.
    44	# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
    45	# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
    46	
    47	deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
    48	deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
    49	deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
    50	deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
    51	deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
    52	deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
    53	
    54	deb [http://linuxcnc.org](http://linuxcnc.org) lucid base linuxcnc2.5
    55	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports restricted main multiverse universe
    56	deb-src [http://linuxcnc.org](http://linuxcnc.org) lucid base linuxcnc2.5



Out of 'uname -a'

> Linux CNC-Winder 2.6.32-122-rtai #rtai SMP Tue Jul 27 12:44:07 CDT 2010 i686 GNU/Linux

Also, just went to BestBuys to trya nd find a wireless adaptor that would work out of the box... none do?  who knew this would be so hard?

Thanks for you help.

Bill

Thanks.

---

### Post by Bashing-om on 2013-10-04
SwarfEye;
This :
[http://en.wikipedia.org/wiki/LinuxCNC](http://en.wikipedia.org/wiki/LinuxCNC)
> 
 Internally some refer to LinuxCNC by EMC or EMC2 as it was historically known. EMC Corporation proposed that the LinuxCNC project, as previously named, would be confusing for customers or potential customers with their (mainly) storage related products.
Platforms[edit]

Due to the need of fine grained, precise real time control of machines in motion, EMC requires a platform with real-time computing capabilities. It uses Linux kernel with real time extensions (RTAI). Installing EMC2 (and the underlying real time extension) is a daunting task, therefore prebuilt binary packages have been built and are being distributed. The policy for EMC2 is to build packages and offer support on Ubuntu LTS (long-term support) releases.[1]

Tells me I do not have the knowledge to advise in this situation. However, a thought, Do you really want to start a long term project with an operating system that the supporting software had reached End Of Life ? What would it take to upgrade your system 10.04 to the current Long Term Support 12.04 ...continued support until 2017.

[INDENT][INDENT]going back into my hole
[/INDENT][/INDENT]

---

### Post by SwarfEye on 2013-10-04
I've used Linux CNC before and it is great!  Really cool system and pretty easy to use.

The issue I am having is not with Linux CNC.  The issue I have having is getting wireless internet connectivity.

So, I have given up with trying to get the new wireless card the box came with to work with 10.04.  What I am now trying to do is to find a usb wireless adapter that I can go buy that will work out of the box with 10.04.  

This is also proving extremely difficult as well?!

Turns out that there are plenty of old usb wireless adapters available cheap... take your pick and spend $15.  So I figure I just need to find a model number that gets the thumbs up and buy one.  

The trouble is that I'm not able to find any information on stuff that works with 10.04... I'm only able to find information on problems.  I suppose this makes sense as folks who have stuff that work for the most part aren't making noise about it, but I'm starting to pull my hair out here.

There are posts out there that say "this thing works great with" 8.04 or 11.10, but it seems that stuff that drivers get deprecated and new drivers aren't backwards compatible.

So much work!!!  So little joy!

Thanks,

Bill

---

### Post by Bashing-om on 2013-10-04
SwarfEye; I do feel for you.

There is this possibility - applicable to the desktop editions of 10.04 that are no longer supported - change your sources to the archived repository (old releases) and there may be a driver available.
As to what the long term affect on the server kernel's updates and security updates I do not know - by reverting to the dead old releases archive.

[INDENT][INDENT]it is but a thought
[/INDENT][/INDENT]

---

### Post by mörgæs on 2013-10-05
Do you need internet connection while programming the robot or only as a convenience for normal browsing and the like? If the latter you could consider a double boot where you run a supported Buntu next to LinuxCNC. 

By the way, it might be a good idea to write the developers and ask if a version of LinuxCNC is planned for Buntu 14.04.

---

### Post by SwarfEye on 2013-10-05
Guys,

Thanks so much for your suggestions and help.  I really do appreciate it.

It occurred to me that this issue was likely one that the LinuxCNC people had come across and so I should ask over there.

A couple of interesting things have come out of that discussion.

1) Some folks are running Linux CNC with the 3.8 rtai kernel.  Running this way would get my wireless card working no problem... but LinuxCNC on 3.8 rtai is still just for the super advanced developer crowd and probably a feat that is over my head at this point.

2) Wireless in general is not a great choice for CNC connectivity because the PWM control of the motors gives off a lot of RFI and screws up the wireless as soon as you turn the motors on!  Fascinating.

The general wisdom over there is to use power line connectivity instead... which is where I am now headed.

Thanks again for your help.

Best,

Bill

---

