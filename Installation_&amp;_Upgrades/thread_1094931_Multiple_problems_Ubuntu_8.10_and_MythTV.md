---
title: "Multiple problems Ubuntu 8.10 and MythTV"
date: 2009-03-13
forum: Installation &amp; Upgrades
---

### Post by markosjal on 2009-03-13
I have done at least three previous installations of ubuntu incluting 8.,04 and 6.06 PPC version. I have some experience with other distros of Linux as well.

I want to bring up the following issues as it relates to 8.10.

First the 8.10 CD takes substantially longer than 8.04 on the SAME system. IN fact it took so long, i thought the system had frozen initially.

The drivers for some older ATI cards appear to have been removed, I think think 8.04 had GATOS drives that supported the ATI all in Wonder Rage Pro. I did find another package that supports NEWER ATI cards but the Rage Pro is not listed. I suspect my ATI card is probably only being supported as a standard VGA. I know that the ATI all in wonde ris somewhat limited, but this system was only to test the possibilities of MythTV.

Myth TV is almost a joke, after multiple attempts and reading multiple threads it appears I am not alone in the issues configuring Myth TV. There is a need to ensure that this set up actually works and is easy and not a week long project. 

It is a sad state that Ubuntu 8.10 is in , and I only chose it over 8.04 because supposedly it had better integration of MythTV , but in BOTH cases I was greeted with the same myth Database errors. 

Also on a side note I find the name references to the various Ubuntu releases as quite confusing, especially when not used in conjunction with the release version number such as 8.10 or 8.04, etc. I am sure I am not the only one that has had to look up which was feisty and which was Dapper. I am sure it is easy for those who have followed Ubuntu, but when looking to resolve issues, one really needs to understand what issues were relevant to which versions, without making it more work.

I had to get this off my chest and will be looking for a new solution to my media center needs, despite having been a proponent of previous versions of Ubuntu. 

My test system is an intel Celeron 2.8 Ghz 1 Ghz of RAM, ATI all in wonder, IDE drives. No weird hardware here. I must ask what good is an OS that one needs to waste a week trying to configure the one application they want to use? Ubuntu and Myth TV has been a Major let down , and I have no reason to believe that it works reliably for many folks.

---

### Post by komputes on 2009-03-14
I understand and agree with the concept that an operating system should just work, but here are some things you may not know.

Ubuntu is cutting edge: Every 6 months Ubuntu developers work on a new batch of submitted packages from debian-unstable and try to get other developers to come together and work on bug reports, fixes and patches. These packages (of which there are in the thousands: [http://packages.ubuntu.com/jaunty/allpackages](http://packages.ubuntu.com/jaunty/allpackages)) are taken from different sources and from many projects with developers of their own.

Manufacturers are not always helpful: Manufacturers of the ATI and nVidia video cards are not always helpful with drivers and often cripl..ahem...limit the capability of older video cards to have users renew their commitment to one of the companies by buying something new, even though the card you already have is in working condition. I can agree with you on this point on a very personal basis. I think it was at Hardy (8.04 ;)) that my ATI Rage Pro 128MB video card no longer had advanced video hardware support. I went out and I bought a $30 nVidia Corporation NV34 GeForce FX 5200. Now since yours is an all in wonder i bet it has a TV tuner and a whole lotta goodies you're missing out on. But in this fight against the manufacturers, one must stay strong and keep requesting that they provide compatible drivers that work for Linux. Give ATI/AMD a call and voice your opinion, as I did.

Canonical is still small: There are <300 people who are paid by Canonical, the sponsor of the Ubuntu project. Many of these are not the distribution developers. And of those developers not many will spend a large ammount of time on packages in multiverse and universe repositories like MythTV unless they have a motivation to hack at it.

But these guys are interested in hacking at MythTV: [http://www.mythtv.org/wiki/Bug_Tracking_System](http://www.mythtv.org/wiki/Bug_Tracking_System)

So do not despair, there is hope. There is currently a lot of work being done in the area of X to simplify the usability and transparancy of video driver configuration. If you have not tried these steps yet for the video card, please do:

1 - Go to System > Administration > Hardware Drivers and look if there are any drivers you can activate for your video card.

2- When booting you will have 3 seconds usually to press esc to enter the grub menu. Once you do, select the secon option (recovery mode). This will boot in text mode and bring you to a quick fixit menu, select xfix (fix x server) with the arrows and press enter. Some text may pass in front of the screen. Once back at the menu select resume normal boot.

You may be interested in viewing the bugs that may be related to your video card issue:
[https://launchpad.net/+search?field.text=ATI+all+in+Wonder&field.actions.search=Search](https://launchpad.net/+search?field.text=ATI+all+in+Wonder&field.actions.search=Search)

If you would like to report a bug to find or start a possible fix for developers to look at the issue, you can do this here: [https://bugs.edge.launchpad.net/bugs/+filebug/+login](https://bugs.edge.launchpad.net/bugs/+filebug/+login) 

The files to submit as an attachment to this kind of bug can be found by clicking on "filesystem" and navigating through these folders:
/etc/X11/xorg.conf
/var/log/X.0.log

In a terminal run this command and upload lspci.txt:
```
$sudo lspci -vvnn > lspci.txt 
```I hope this helps and that if you find a solution you will post is here.


EDIT:
Note, I found an article here saying that ATI may be releasing/may have released a driver that fixes a MythTV issue: [http://www.linux-gamers.net/modules/news/article.php?storyid=2535](http://www.linux-gamers.net/modules/news/article.php?storyid=2535)

---

### Post by markosjal on 2009-03-18
Yes, but you also point out an interesting problem. ATI drivers removed from 7,X ubuntu and MythTV better integrated into 8.10 . 

I want to point out that some other OSes take into acc0ount of keeping compatibility with existing drivers. I see this as a shortcoming with Ubuntu, it is more like Mac OS and they abandon the older hardware. Maintaining compatibility with Legacy hardware (and driver) should be a priority, not rewriting the code from the ground up and losing said compatibility.

BTW I have Ubuntu 6.06 PPC on an Imac, which has an ATI Rage (no TV)  built in  I see nothing that indicated that it is using any accelerated driver at all. IN fact I can not even change color depth , nor screen resolution on it!

As for MythTV the problems seem insurmountabe and it is the issue with the Database access that appears to be the killer for me and others I see posting on the forums. I install Trixbox/Elastix/FreePBX systems that use databases and these problems do not arise as they do with MythTV.

---

### Post by theozzlives on 2009-03-18
I have 2 systems that are very old (400 & 500 MHz w/256 RAM) and Ubuntu hasn't abandoned them. 8.10 runs just fine (granted I don't get Compiz). One of my systems has an ATI 3D Rage Pro, ATI has Windows drivers but not Linux so it's the manufacturer, not the OS.

---

