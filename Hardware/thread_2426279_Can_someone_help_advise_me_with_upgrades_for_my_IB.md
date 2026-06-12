---
title: "Can someone help advise me with upgrades for my IBM thinkcentre M52?"
date: 2019-09-06
forum: Hardware
---

### Post by james273 on 2019-09-06
Hi 
Im new sorry for the long post but would be very grateful if someone can give me some advice.

So I have a generic old IBM thinkcentre, its has a floppy drive and cd drive. Two things my laptop doesn't so I wanted to make into a project. By the nature of the compact design ive notice that rebuilding the whole pc would be a challenge.

Im a big fan of thinkpads had one for years so when I saw this I thought project time ! And im glad as its a really interesting design and learning process.

It had xp and was reasonably fast considering the 900mb ram, I had a laptop harddrive laying around so plugged that in and replacedd 80gb with 160gb and alot faster write speeds, un expectedly it booted into windows ten, it was so slow so decided to try ubuntu as from previous experience I thought it was less demanding than windows.

This was also fairly slow so I ordered a 2gb ram and it runs like a different machine. So much faster! Apparently xp can only handle maximum of 3gb so i have 2.9 so im wondering if worth another £6 and ubuntu is the same? And the extra 1gb might not be much of a jump.

 intresting fact i made the mistake of pulling out the ram for a second and that was intresting as the screen whent like green blocks ! 

So ive since decided all I want is a fairly capable linix machine that looks as original to the thinkcentre as can be. But im running into alot of problems thats making me think I should turn back to xp. 

I will be using it as another web browser pc, maybe some basic emulation and storage. Nothing too crazy. 

I am fairly new to linux im trying to learn it to tell the truth not 100% sure what cpu it has ect. I think its like most m52's and an intel chipset with a Pentium D - Can anyone help me find this information? I understand i'll have to use command line but what do I even type ? I would bet the cpu is whats going to make the most difference and jump in speed and power but dont really know where mine is compared to what the maximum upgrade is i can do. As far as i understand I cant just plug in a i5 right ? 

It now has 18.04 that took ages to install and I think the cpu is less than recommended. 

I dont mind upgrading the parts but i suppose the motherboard is too much and a compact design. Most parts are quite cheap for this like the £6 ram so want to keep cost effective. It currently has no wifi and im having to connect to the internet by using my phone as a wired usb connection. My generic bluetooth adapter is not working and have spent a lot of time looking into why only to conclude its likely just not supported. Ive seen a tp link wireless card thats like £6

Given my situation can someone advise me on upgrades? If anypoint ect/ level of difficulty? 

Ssd?
Extra ram?
Silent fans ? (Its really lould)
Cpu?

Anywireless cards that will be 100% compatible? 

Many many thanks!

---

### Post by Skaperen on 2019-09-06
i'd say more ram first.

---

### Post by Skaperen on 2019-09-06
doing installs more often gets you better at it.

---

### Post by Skaperen on 2019-09-06
when you get a new fan, be sure it is a ball bearing type.

---

### Post by mörgæs on 2019-09-06
Hi, welcome to the fora.

Please see the link in my signature. It's not a given fact that you need to upgrade hardware.

---

### Post by Autodave on 2019-09-06
With 3G RAM, it should run OK.  You could also consider a lighter desktop like Xubuntu.  I really don't think that another gig of RAM would make a lot of difference at this point.

---

### Post by TheFu on 2019-09-06
I'm retiring 2010 Core i5 systems, so keep that in mind as you keep reading ...  already got rid of a 2009 Core i7.

If your total upgrades cost more than $45, I think you'd be better off buying a Raspberry pi v4 or a Rock64 instead.  Below that amount, and it is less clear whether you are wasting money or not.  A Raspberry Pi will support video playback than your system will without a GPU upgrade costing $30, probably.  All the r-pi v2 and later version support h.264 video in hardware, so youtube and most other video websites are fine.  The v4 Pi has 2 HDMI outputs and supports 4K video.

If you can boot a Linux, install inxi, then run it as **inxi -Fz** and post those results here, we'll have a good overview of the system.

1G of RAM was tight for a full Ubuntu.  If you loaded TinyCore, it would fly.  2G works with Lubuntu and Xubuntu fine.  Since about 2007, all Linux can handle at least 16G of RAM, even the 32-bit installs.  It is just that each process is limited to 4GB of addressable RAM.   I suspect that your machine shares the RAM with the GPU, so you'll always see less RAM inside the OS that it really has.  That missing part is given to the GPU.

There is point where newer is better than reusing really old stuff, but that line is fuzzy for everyone.

---

### Post by CatKiller on 2019-09-06
Other people have already given helpful comments on what's feasible, and I'd imagine that people will comment further, but I wanted to highlight this bit. 

> **james273 said:**
> But im running into alot of problems thats making me think I should turn back to xp. 

I will be using it as another web browser pc, maybe some basic emulation and storage.

This is not a viable option. No Windows XP machine should be allowed to connect to the Internet. Ever.

---

### Post by guiverc on 2019-09-07
To list specs of your cpu `lscpu` , the list details of your hardware `sudo lshw` (`sudo` to elevate your privileges with the command lshw being list-hardware; ls=list, which people usually associate with 'list files' its meaning if not attached to something specific).

Ubuntu 18.04 LTS uses GNOME which is heavy; relies on much run-time processing by design and would not be my choice. Already suggested is Lubuntu (Ubuntu with LXDE up to 18.04, LXQt 18.10 & later) or Xubuntu (Ubuntu with XFCE). I have a similar spec'd *hp dx6120* that is reasonable with Xubuntu/Lubuntu, but I sure don't have the patience to use GNOME on it  (and I only use it for testing purposes).

*hp dx6120mt (mini-tower, pentium 4 dual core, 3gb, winfast clone of nvidia 7600gt)  [specs of my comparison box]*

---

### Post by james273 on 2019-09-07
Thanks for all the advice ! I'm going give Lubuntu a try and see how things go, will update with specs and how I get on later. Just out of interest would a newer PC run super fast with Lubuntu compared to ubuntu, doesn't seam much difference? are there any drawbacks to lubuntu ? 

I was thinking of using it as a big case for a raspberry pie, but I decided I want to keep some originality, when it boots up the screen displays thinkcentre logo, I guess the project goal is make the most out of the think centre, not dress something else up as a thinkcentre. Haven't seen a floppy disk drive in years, would it even be possible to connect this up to a raspberry pie ?

is it possible this may solve my bluetooth issue ? - Also I'm guessing any wireless cards that say they work with ubuntu will also work with xubuntu and lubuntu right ?

---

### Post by guiverc on 2019-09-07
I much prefer LXQt/Lubuntu over GNOME, even LXDE/Lubuntu over GNOME (3). I also prefer XFCE & MATE over GNOME but it's a personal preference.  Which will be best for you, only you can decide.

Yes a faster computer will run faster if running Lubuntu over GNOME, however the difference isn't anywhere near as noticeable (or noticeable at all) to users as it's often just fewer wait-cycles of a super-fast-cpu waiting for input from the human, where as with slower boxes the human is waiting for their boxes.

The base of all Ubuntu systems is the same, so out-of-the-box differences are minor in regards hardware-support, and if something works in one, it'll work with others in almost every case, so Ubuntu, Xubuntu & Lubuntu will have the same support for the same release. The difference is the desktop or GUI over that base (or no gui for ubuntu server).  Different releases, eg. 18.04/2018-April release may have different hardware-support to say 19.04 which came out a year later, but you can add HWE (hardware-enablement stack support) to 18.04 to close this difference...

---

### Post by TheFu on 2019-09-07
First, you are getting lots of good advice from everyone else posting here. Different viewpoints should help you make a good choice.

> **james273 said:**
> Thanks for all the advice ! I'm going give Lubuntu a try and see how things go, will update with specs and how I get on later. Just out of interest would a newer PC run super fast with Lubuntu compared to ubuntu, doesn't seam much difference? are there any drawbacks to lubuntu ? 

Stick with 18.04.3 Lubuntu/Xubuntu/Ubuntu-Mate.  That will get you the newest HWE software/drivers too.  As someone new and not a developer, really need to stay on LTS releases.  I've been around a long time and only run LTS releases to avoid many of those tiny little issues that happen on non-LTS releases.

> **james273 said:**
> 
I was thinking of using it as a big case for a raspberry pie, but I decided I want to keep some originality, when it boots up the screen displays thinkcentre logo, I guess the project goal is make the most out of the think centre, not dress something else up as a thinkcentre. Haven't seen a floppy disk drive in years, would it even be possible to connect this up to a raspberry pie ? 
The thinkcentre logo is from the BIOS, so if you change the motherboard, then you won't see it, unless you find an image and put it into any new motherboard's boot image cache.  I've not done that, but suspect you can make it happen.
I looked at a few images of the case for thinkcentre M52 - there seem to be lots of different types. They look like corporate models, so it could be they have non-standard everything inside. 

The newest kernels have removed support for floppy disk controllers.  If you want anything currently on a floppy, best to move it to USB storage or optical media or you can buy a USB-based floppy device.  I've retained some older hardware with support for 5.25" disks, though I haven't gone through all the floppy media and moved it over. They are CPM and DOS and early Windows or OS/2 programs.  Someday, I might finally use MathCAD or TK Solver! again like I did in college, but I doubt it.  Saw a copy of Desqview/X a few days ago. Seeing that run could be fun for people at my local LUG, I suppose.

USB should work with a raspberry pi, but I honestly don't know.  Google it a little. See what you find.

> **james273 said:**
> 
is it possible this may solve my bluetooth issue ? - Also I'm guessing any wireless cards that say they work with ubuntu will also work with xubuntu and lubuntu right ?
I don't use bluetooth. Too much of a security risk for me after being hacked on a 100% patched, Ubuntu install through BT.  I disable it in the BIOS everywhere since then.  To troubleshoot wifi, you'll need to get the exact chips used in the device.  lspci, lshw, lsusb are tools to gather that information. Each has multiple options to get at exactly the information needed.  For someone really new, it is probably easier to look up a device that is well-known to work.  It might be just a little tweak needed to get the current device working with automatic updates
 or
 it might require hunting down some code from a coding site, compiling it for any new kernel released, and installing it.  New kernels come out a few times a month, so you'd need to recompile and reinstall a few times a month.  You will definitely learn a bunch, which is great if that is your interest.  If that isn't your interest, ... well ... then $12 for a replacement can make you happy, probably.

Turns out that bluetooth hasn't ever been safe to use: [https://www.howtogeek.com/438712/could-your-bluetooth-devices-be-hacked-in-2019/](https://www.howtogeek.com/438712/could-your-bluetooth-devices-be-hacked-in-2019/)> 
There&#8217;s ample evidence that Bluetooth is about as secure as a padlock sculpted from fusilli pasta.

Sorry, I'm no help.

---

### Post by Autodave on 2019-09-07
You also had asked about an SSD.  That will definitely speed things up on there.

---

