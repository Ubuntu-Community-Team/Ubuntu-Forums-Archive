---
title: "To build or not to build"
date: 2013-05-09
forum: Hardware
---

### Post by GaryTheCat on 2013-05-09
I have a desktop that the kids use for doing their homework from school.  This desktop is getting very old and running windows XP (just).

I have 2 options open to me:
[LIST]
[*]Buy a new desktop off the shelf with (I assume) Windows 8 preinstalled; or
[*]Build a new desktop myself to my own spec (I haven't done this before).
[/LIST]

I'm concerned about the pre-installed windows 8 path as I've had problems dual booting with Windows 7 / UEFI Issues - would this be a problem with a 'virgin' system with no OS on it?

If I go along the self build route, I intend to just have the machine running Ubuntu whereas I'd probably dual boot a desktop from a shop.

So..... my questions:
[LIST=1]
[*]Is building a PC likely to be cheaper than buying one?
[*]I have an engineering background with 'not bad' electronics skills - how difficult would I find building a PC?
[*]What are the pitfalls / common mistakes when building a PC with the specific intention of running Linux on it?
[*]Can anyone point me to some useful links? Ideally a "here are the parts" though to "here's your machine working with Ubuntu installed"?
[/LIST]

I've done plenty of dual boot installations of Ubuntu but never a "just Ubuntu" installation - is there much of a difference?

Sorry to be vague and overdo it on the questions.

TIA

G

---

### Post by ahallubuntu on 2013-05-09
~

---

### Post by papibe on 2013-05-09
Hi GaryTheCat.

Have you considered buying a desktop with Ubuntu preinstalled? 

Here are a couple of options:
[LIST]
[*][System76]("https://www.system76.com/desktops/").
[*][Alienware]("http://www.alienware.com/ubuntu/featured_systems.aspx#tab_Featured_Systems").
[/LIST]
If a laptop will do, here's another: [Dell]("http://www.dell.com/us/business/p/xps-13-linux/pd").

Just a thought.
Regards.

---

### Post by TheFu on 2013-05-09
Lots of questions that entire books have been written about, so we can't possible cover everything you hope to know here.

If you can reuse parts, then building will be cheaper and you'll knwo what the parts are inside. Be certain to lookup each part on a HCL with Linux (and/or ESX). This will ensure future problems are avoided. You want the hardware to be supported by the kernel, not require any 3rd-party drivers.  Often, those external drivers will not be maintained and will only work with specific kernel versions.  Just sayin.  I learned that the hard way.

If you can't reuse parts, then building with everything from scratch will cost more. You can't touch the massive discounts that Dell or Acer get.  Buy the system from those guys and be done with it.

Putting together a PC is easy. Lots of youtube and blog sites cover it.

Common mistakes are harder to make these days. Almost everything is key'd these days.  Don't force anything. Read the instructions for the MB.  

TomsHardware and similar sites have BOMs for building a PC.  Find someone who is building for the same purpose and follow their lead.  If you deviate, post your BOM for others to review - but be certain you don't ask overclockers when that is never your intention.   I like to start with a motherboard/CPU combo and work from there when selecting parts.

UEFI seems to always be an issue, but I don't have any experience with it. I've avoided it for this reason.
Pure boot or dual boot are about the same. Actually, dual boot is harder to get working, IMHO.

When using new HDDs and new distros, I'd choose GPT over MSDOS for the disk layout. More flexibility, but it also limits which older OSes can be installed later. That might be an issue if you plan to run WinXP or an old Linux that doesn't support GPT. GPT is very feature rich, so it is worth using, if you can. There are lots of little decisions like this to make.

I've never seen Win8 and don't intent to ever see it running in the wild. Can't help with any of those questions.  Google is your friend "ubuntu win8 uefi install" would be where I started.

Good luck!

---

### Post by GaryTheCat on 2013-05-10
Thanks guys, the I may see what I can salvage from the existing box (HDD / DVD are good candidates I imagine).

I've looked at the Dell websites and they don't seem keen on selling machines with any Linux distros on in the UK (strange but true).

I have seen windows 8 in shops and it looks a bit like a multi-coloured migraine, I'd only use it out of compulsion rather than desire.

Some good food for thought, I'll subscribe to the thread and see if any other ideas come along.  I guess the other option would be leave the desktop as it is hardware-wise and install Lubuntu.

---

### Post by papibe on 2013-05-10
> **GaryTheCat said:**
> I've looked at the Dell websites and they don't seem keen on selling machines with any Linux distros on in the UK (strange but true).Bummer :(


Second best alternative, IMHO, buy a desktop certified for Ubuntu: [Ubuntu Desktop certified hardware]("http://www.ubuntu.com/certification/desktop/").

Regards.

---

### Post by CatKiller on 2013-05-10
Building a PC isn't any cheaper than buying it pre-made, but you are likely to end up with better quality parts.

Ars Technica has semi-regular System Guides that make quite a good starting point.

Actually putting it all together is fairly straightforward, but occasionally fiddly.

---

### Post by TheFu on 2013-05-10
> **GaryTheCat said:**
> I
I'm concerned about the pre-installed windows 8 path as I've had problems dual booting with Windows 7 / UEFI Issues - would this be a problem with a 'virgin' system with no OS on it?

Just saw this article on UEFI: [http://www.howtogeek.com/149254/if-i-buy-a-computer-with-windows-8-and-secure-boot-can-i-still-install-linux/](http://www.howtogeek.com/149254/if-i-buy-a-computer-with-windows-8-and-secure-boot-can-i-still-install-linux/)  I bet there is an Ubuntu Guide about it too somewhere.

Also the Ars Guides are trustworthy.  I will say this - I haven't spent more on a GPU than $50 the last 10 years, so if you aren't gaming or planning to mine bitcoins, spending anymore than that is likely a waste of money.  These $50 GPUs easily handle dual 1920x1200 monitors, so there isn't any concern about that at all.

I find the Ubuntu HCL (hardware certified hardware list) to be entirely too restrictive.  Ubuntu is not the entire world of Linux, especially their "certified hardware list."  The more generic HCLs are best unless you plan something fancy which I define as anything outside the normal video, disk, and networking.  Non-standard audio devices are hard, the same applies for RAID hardware and wifi hardware. If there is a RAID driver to download, it probably isn't what you want. Proprietary hardware devices - even from huge vendors like Apple - are often difficult or impossible to make work. Stay with hardware that is supported directly in the kernel for the best results.

If you might want to do virtualization, this list: [http://www.vm-help.com//esx40i/esx40_whitebox_HCL.php](http://www.vm-help.com//esx40i/esx40_whitebox_HCL.php) is a good start to getting the most standard and best supported stuff. Even if you don't use it for virtualization, that support can be handy.

OTOH, most hardware sorta just works these days with Linux and Ubuntu.  It is the odd wifi card or RAID controller or printer where most people discover problems.

---

### Post by grahammechanical on 2013-05-10
Keep in mind that a certain OS vendor has set things up so that equipment manufacturers go out of their way to make sure their equipment works with that OS. These manufacturers are not very concerned if their stuff works on Linux or not. So, do not think of getting the very, very latest hardware. Linux developers are always playing catch up.

I was surprised a few months ago regarding the number of people who purchased Windows 8 machines a day or two after they were put on the market and then they came on this forum demanding tutorials on how to install Ubuntu on those machines. Which, of course, did not exist. How could they exist?

If you buy the very latest and try to install Linux/Ubuntu on it then you will be an experimenter. And we will be guessing. Today's smart phones are as powerful as a desktop machine. How much power do you need? The most powerful and therefore the very latest?

Regards.

---

### Post by oldfred on 2013-05-10
I like to look at several build guides, and adjust based on budget or planned use.
Will kids want to do games or is it more of just a "office" type build for Internet & school work?

One of the sites I look at. It has many alternative configurations many for gaming at different price points. The gaming systems all use high priced video cards to give good gaming performance, but unless you need the newest high end games you do not need to spend that much. Even the lightweight systems will play lower end games or at somewhat reduced resolution. 

[http://www.tomshardware.com/system-configuration-recommendation-51.html](http://www.tomshardware.com/system-configuration-recommendation-51.html)

If building your own system an not installing Windows, Ubuntu is just an  automatic install, but still often better to manually configure system  to have separate /home or data partitions. It will auto install in UEFI  with gpt partitions if you boot install media in UEFI mode. If not  installing Windows you can use gpt partition and install in BIOS mode  but have to create gpt partition table first as it defaults to  MBR(msdos) unless drive is over 1TB and blank. gpt is really only  required if drive is over 2TB.

Almost all the hassle on UEFI is secure boot which so far is only on pre-installed systems with Windows 8.

---

### Post by gordintoronto on 2013-05-10
Hie thee to pcmech.com

When I built this computer, I selected "best of breed" components. I doubt if I saved any money, but the system is still working very nicely.

If you avoid the very latest video cards, most things work with the latest Linux.

If you have never swapped a hard drive, or re-seated memory, building a PC from scratch might be a bit of a challenge.

Keep yourself grounded!

---

### Post by Bucky Ball on 2013-05-10
> **GaryTheCat said:**
> [LIST=1]
[*]Is building a PC likely to be cheaper than buying one?
[*]I have an engineering background with 'not bad' electronics skills - how difficult would I find building a PC?
[*]What are the pitfalls / common mistakes when building a PC with the specific intention of running Linux on it?
[*]Can anyone point me to some useful links? Ideally a "here are the parts" though to "here's your machine working with Ubuntu installed"?
[/LIST]



1. Yes.
2. Easy.
3. Not researching compatible hardware and overkill (an 800W PSU and 16Gb of RAM when you're only surfing the net and checking emails; a waste of money and energy). Lack of pre-planning. 
4. You might like to have a read through the 'Build a Linux computer' link in my signature. Dated but principles still apply.

Good luck. Build. You won't regret it. ;)

PS: I will add, as I generally do, that spending a bit more on an efficient power supply unit is key. DO NOT buy a case and use the generic silver box PSU that comes with it. I take them out and recycle them (or keep them for backup) and replace with an 85+ energy efficient PSU from a reputable manufacturer. Generic silver box PSUs are a menace and dangerous to your computer and you and your family (if you don't believe me you haven't seen one blow). You can sometimes pick up sweet deals on combo cases from Antec or the like which are quality cases with a quality 85+ (or 80+) PSU installed already, can be cheaper than buying both separately.

PPS: Plan ahead. Take your time. Get it right. Only design for what you need. Write a list of what you want to do on the machine then match the hardware to it. Unless they're running a space station or are into pro audio/video most domestic users really don't need much.

---

