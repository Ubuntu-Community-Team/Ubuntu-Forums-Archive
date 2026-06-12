---
title: "Confused on Hardware"
date: 2015-04-18
forum: Hardware
---

### Post by Mike_Ohlhausen on 2015-04-18
I am simply looking for a list of hardware that just works. No fixing required, no stop here, type this, aptget this and update that via a web control app from a windows machine...  Just a simple list of hardware. I found the thread here that is forever long, and I would have to read each thread, etc, write all the bits down, sort it alpha, and I really don't feel like doing that. I also found the certified list of hardware on ubuntu's site. But that is simply off the shelf prebuilt systems. Dell, etc... Just want a PCI video card that works, tired of trying to get the Intel server board's onboard ATI video to work. Just need a simple console I can log into... seems like a basic requirement... I tried searching the HCL for PCI Video... get all the PCI, and Video stuff that has issues, but nothing says buy this one, it works out of the box, lol.

---

### Post by Mike_Ohlhausen on 2015-04-18
I guess that sounds like I'm whining, but there used to be 'go to' video cards for Linux. Trident was one, they just worked. Figured there out to be something like that.

---

### Post by ian-weisser on 2015-04-18
You are looking for Ubuntu Friendly, the project that aggregates hardware testing results and lists which components work and which don't.

Unfortunately, Ubuntu Friendly ended itself back in 2013 - too few users in your situation were willing to help maintain the project.
See [https://wiki.ubuntu.com/UbuntuFriendly](https://wiki.ubuntu.com/UbuntuFriendly)

The hardware testing continues...but it's rolled into Certification of completed systems instead of components now.

You are welcome to step up and ressurrect it.

---

### Post by Mike_Ohlhausen on 2015-04-18
Looks NLA... 404 etc after the page that says, "Sorry, this is decommissioned", lol. I guess it's kinda like a forum... all you see are the problems, all the stuff working great, well there is no need for them to come post... kinda sad, but the reality. Just hate to buy a stack of old pci cards in hopes one will work. I tossed all those boxes out when I moved, lol

---

### Post by user_of_gnomes on 2015-04-18
Are you looking for just a recommendation or something more elaborate?

---

### Post by buzzingrobot on 2015-04-18
Linux hardware compatibility lists are typically dependent on users reporting about their own hardware.  There's is no -- can be no -- organized effort to buy, evaluate and report on all hardware. And, re-evaluate and re-report as soon as a driver or the kernel updates.

The most effective way I've found is to narrow down possibilities and then search for *complaints* about the specific components.  If I find several people complaining that a system, or a component, does not work with Linux, then I don't buy it.

As for video, the most reliably supported is onboard Intel video. Intel opensources their driver, it's in a default install, it works, will be used automatically if the system is using Intel video,  and there are no concerns about breakage when a kernel update happens, as there often is when using a proprietary Nvidia/AMD card. 

I'm on Intel Haswell and find it's more than sufficient.  (Someone who games a lot might say something else, though.)

I've also found Lenovo systems to be pretty Linux friendly. 

In general, avoid buying bleeding edge hardware, especially with non-mainstream components.

---

### Post by Mike_Ohlhausen on 2015-04-18
Yea, I am not looking for gaming at all, and possibly not even X. Just a basic PCI card so I can see the console. The Intel server board I have has an ATI onboard. Black screen at boot etc. Tried all the 'fixes' I could, and can't seem to get it to light up. tired of using putty from windows, and just want to log in to set up the silly thing and be done. Not in the budget to buy a new system just so ubuntu will work, so a Lenovo system is out. I already bought all the stuff for this, I figured a server board should be good for Linux, especially Ubuntu Server.

I was just thinking there used to be lists at the dist I used to use..  some were known to be trouble, some worked easy. I just figured the OS had to be figured to work with something, but maybe there is just std code for vid and cross fingers it might work, then the user has to finish it from there.. Used to be you could use VGA drivers and all was good. Getting too old, lol. I keep thinking, whatever vid driver they use for the install would be perfect, I can see all the install screens, until it reboots. I just have a few more drives, and I will have 16 or so drives on hardware Raid 5 arrays from 2 controllers. Had to use a customized old full sized box with lots of fans, on controllers etc, so a fancy new system with 3 or 4  drives won't quite cut it, lol. Sounds like buying a pile of old PCI vid cards is the easy route.. And we used to call Windows 95 Plug and Pray... lol

---

### Post by user_of_gnomes on 2015-04-19
> Used to be you could use VGA drivers and all was good. Getting too old, lol.

You can. As long as the videocard in question works with the open source driver. 

> Sounds like buying a pile of old PCI vid cards is the easy route.. And we used to call Windows 95 Plug and Pray... lol 

No because there's a good chance driver support for legacy devices has been dropped in more recent kernels. You should just buy up-to-date hardware because Linux Ubuntu is a modern operating system. And sometimes devices aren't properly supported and sometimes they are. 

Like Buzzingrobot wrote: Intel has good open source drivers.
I am perfectly content with AMD, their proprietary drivers work well for the 57xx and 67xx range of videocards.

---

### Post by Mike_Ohlhausen on 2015-04-19
Yea, well, new hardware is way out of this budget, lol... Especially for dual processor, hyperthreading / ECC Server stuff. Guess I could also buy Windows Server, if I had an open budget, lol. (Then I would REALLY be unhappy I bet!) I Did find a great page that might help other folks here. - [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCards](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCards) . I do understand about dropping support for old stuff, just hate to be part of that old stuff myself.. sigh... I wish Intel would have had their video on this board, but that's the way it goes. Going to look for the 57 - 67 card, or any another PCI one on the good part of the list. Want to keep the faster slots (PCI-x and PCI-e) for the Raid cards, since thats the important part here. Thanks for your help! Trying to not sound like I am complaining to you guys, lol, I really do like Linux for a server, once I get the kinks ironed out of my machine... And I am grateful for the guidance the forums give!

---

### Post by gordintoronto on 2015-04-20
My main system has an nVidia 9400 GT which has always worked just fine, and I look at a lot of distros and versions. I think the 610 is the current version of that card.

---

### Post by ian-weisser on 2015-04-20
> **Mike_Ohlhausen said:**
> I also found the certified list of hardware on ubuntu's site. But that is simply off the shelf prebuilt systems. Dell, etc.

There is an Ubuntu Certified [Component Catalog]("http://www.ubuntu.com/certification/catalog/"), too...the components of those certified systems. I missed it my first time looking.

The component catalog includes it's own search feature.
I just priced out a build, and it was terribly handy to be able to copy-and-paste component model names into the catalog search, and find out instantly if they are likely to work.

It's not perfect, of course, but it is easy. And seems close to what the OP is looking for: A list of certified components.

---

