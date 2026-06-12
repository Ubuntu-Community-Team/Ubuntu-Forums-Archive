---
title: "Lenovo T500 - Problems with Ubuntu?"
date: 2009-01-25
forum: Hardware
---

### Post by bravemenrun333 on 2009-01-25
im a webdesigner and ill be upgrading from r61 to t500 in the coming weeks. which are the glitches i have to count with? how do the ati graphics / switchable graphics work with ubuntu?

:popcorn:

---

### Post by richard.fickling on 2009-01-25
I have a T500 with switchable graphics, 1680x1050 res, 2GB ram, webcam, Ubuntu 8.10 32bit

The graphics are only switchable via BIOS as AFAIK there are no drivers for linux which will let you do this.

After you switch from discrete to integrated or vice-versa, you will need to reconfigure your X-Server ([sudo dpkg --reconfigure xserver-xorg], if I remember correctly) and all should be good.

I use ATIs Catalyst Control Center and proprietary drivers for linux and they run compiz like a dream.

Got a phone call now.  Will finish this later.
EDIT: Back

The ThinkVantage button can be remapped to open anything (it opens Firefox for me)

Battery life sucks on discrete graphics - use integrated for a long flight.

The webcam is the only major problem - it just refuses to work.  I'll update this if I get it to.

If there's anything I missed or if you have a problem with anything on your T500, don't hesitate to ask.

 - Dick

---

### Post by Squid Spectre on 2009-01-27
Long time Ubuntu user and short time forgot-my-old-login forum member here, it is an old post but I'm still interested in getting feedback or helping future T500 owners. I've been doing some reading on a few problems with the latest release in anticipation for my new T500, sadly there isn't a lot on the T500 specifically. This could either be because everything works perfectly or few don't go for the T400 (I personally preferred the WSXGA+ screen.) Either way from what I read a T500 owner can expect a few things based off other recent posts:

**Video card:**
-They both work, but you have to turn off "OS Detected" in the BIOS and manually switch between the cards, editing xorg.conf as needed. Be sure to  do that before install so it doesn't just find the first video card on the bus, which is the Intel integrated graphics card.

**Bluetooth / Wireless:***(5300agn)*
-Works out of the box, no need to mess with it.

**Camera:**
-Sounds like there *may* have been an issue getting the built in camera to work, but it seems to be a contested issue.

**Memory:**
-I heard wind of an issue where Ubuntu was only detecting 2.5gb of 3gb of install ram, but it hasn't been a major topic of discussion so it may or may not be an issue.

**Battery life:**
-If the T500 is anything like the T400 in respect to the way Ubuntu manages power then the battery life for the computer will likely be staggeringly short, from what I read the reasons are unclear. I suspect it may be related to the CPU scaling issues and the fan always running, but that's just a stab in the dark.

**CPU Scaling/Heat:**
-Its my understanding the latest release has issues with fan control and CPU scaling resulting in excessive heat or outright overheating. People *seem* to be seeing it across the board so I would expect something of a fix soon, until then they say just to disable CPU scaling. It may not be something that specifically impacts the T500, but it would certainly be something I'd watch closely in the first few days of operation.

Personally I think it should be a pretty smooth install and the few existing issues will likely be addressed sooner rather than later. However, if I forgot anything or am just outright wrong I'd be glad to be corrected, most of what I listed was speculation based off other posts. So yeah, correct away.

---

### Post by uncleop on 2010-12-23
More old-topic posting:

I have inherited a T500.  Xorg 1.7.6, Ubuntu x86 10.4, Lenovo T500 with Intel Integrated chipset (4 series): no xorg.conf.  System->Preferences->Monitors shows 1280x800 as max screen res, but it should go to 1680x1050. 

From your post, I gather I need to  manually switch.  Is this still true for 10.4 (or 10.10), or is there an on-the-fly way to switch between cards.  E.g., you want to go to reduced-power mode on the plane without rebooting.

I did a fresh install of 10.4 since attempting to upgrade from Fedora 11 to 13 resulted in munched data.  Unfortunately I hadn't poked around here yet. 

What is the new-fangled (non-xorg.conf?) way to add 1680x1050 to the list? Or do I just have to generate an xorg.conf?  As I noted above, there's no default xorg.conf in /etc/X11.

Thanks!

---

### Post by merlin666 on 2011-02-22
> **Squid Spectre said:**
> 

**Video card:**
-They both work, but you have to turn off "OS Detected" in the BIOS and manually switch between the cards, editing xorg.conf as needed. Be sure to  do that before install so it doesn't just find the first video card on the bus, which is the Intel integrated graphics card.
**CPU Scaling/Heat:**
-Its my understanding the latest release has issues with fan control and CPU scaling resulting in excessive heat or outright overheating. People *seem* to be seeing it across the board so I would expect something of a fix soon, until then they say just to disable CPU scaling. It may not be something that specifically impacts the T500, but it would certainly be something I'd watch closely in the first few days of operation.


Thanks for this post which may explain some of my expereinces. I have used an external HDD with Jaunty installed form another laptop and found it work smoothly through upgrades up to 10.04. Then I enabled fglrx and I assume that I get a blank screen because it found the Intel card. Now I am wondering how to get into terminal and change drivers (help please).

Also noted that CPU and GPU were going up to 75C with fan at over 3000rpm during the various upgrades - has this been fixed in 10.10?

---

