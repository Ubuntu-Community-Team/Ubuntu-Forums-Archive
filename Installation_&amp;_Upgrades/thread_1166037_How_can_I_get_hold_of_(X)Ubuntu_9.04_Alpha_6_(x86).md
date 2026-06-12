---
title: "How can I get hold of (X)Ubuntu 9.04 Alpha 6 (x86)?"
date: 2009-05-21
forum: Installation &amp; Upgrades
---

### Post by lioncub33 on 2009-05-21
Hi,

I'm pretty much a Linux newby, so please bear with me if the question seems stupid & the answer's plain obvious..

Because of problems installing Ubuntu 9.04 on a quirky laptop (Hi-Grade Green320 - VIA C3 processor, CLE266 video), I've been trying to get hold of an (X)Ubuntu 9.04 Alpha 6 (x86) install CD - having read:

[http://ubuntuforums.org/archive/index.php/t-1104693.html](http://ubuntuforums.org/archive/index.php/t-1104693.html)

I've tried BitTorrent sites without success.. would anyone know if there is an archive mirror somewhere I can just download the CD .iso? I couldn't find it anywhere obvious on the main Ubuntu website..

Thanks in advance to anyone out there who can help  ):P

---

### Post by Mighty_Joe on 2009-05-21
[http://www.ubuntu.com/testing/jaunty/alpha6]("http://www.ubuntu.com/testing/jaunty/alpha6")

---

### Post by lioncub33 on 2009-05-21
> **Mighty_Joe said:**
> [http://www.ubuntu.com/testing/jaunty/alpha6](http://www.ubuntu.com/testing/jaunty/alpha6)

Thanks for the link Mighty_Joe - looks like the downloads are no longer supported from that page though.. the download links just come up "404 Not Found".. :(

---

### Post by Mighty_Joe on 2009-05-21
Well shucks.  My advice is to use one of the currently supported releases.  If you have another problem on the Alpha 6 build, the first response you'll get is: "update".
Next, search [the bug reports]("https://launchpad.net/ubuntu") to see if anyone is getting the same symptoms on the same hardware.  If you can't find a bug that matches, report one.  
BTW: I'm using a [VIA C3 mobo]("http://www.newegg.com/product/product.aspx?Item=N82E16813185043") as a low-power home server. It sounds like the hardware in the post you linked. It's rock solid with Hardy Server, but it's headless, so if it's a video problem, I wouldn't see it.

---

### Post by lioncub33 on 2009-05-21
Thanks for that Mighty_Joe - I'll try the bug reports..

---

### Post by lioncub33 on 2009-06-01
FIXED: OPENCHROME VIA & MOBILE BROADBAND ALL WORKING NICELY NOW :-)

After weeks of trial & error, I finally got my VIA C3 / CLE266 laptop (Hi-Tech Green320) past the Ubuntu 9.04 "Jaunty Jackalope" install GDM/KDM/Xfce/X.Org crash - by doing a "vesa" install from the Xubuntu Alternate CD & then updating the OpenChrome VIA driver from the ensuing command prompt, as per:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/367442](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/367442)
[https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)

Reason for the upgrade, was to get my shiny new Vodafone Top-Up & Go Mobile Broadband USB GSM Modem - Huawei K3565 (also referred to as an E160X, apparently..) - to work under Linux:

[http://ubuntuforums.org/showthread.php?p=7159131](http://ubuntuforums.org/showthread.php?p=7159131)

Once I was actually up & running with Xubuntu 9.04, the Mobile Broadband setup wizard ran automatically when the dongle was plugged in & connected it all up fine, no problem (OK, after another switch-off or two..) - WITHOUT ANY CONSOLE/CONFIG-FILE-EDITING STUFF!! :-D

Well done again, all you Ubuntu & OpenChrome guys! :-D

Wasn't immediately obvious from the Vodafone website / documentation though, how to £top-up the account.. :-(

But eventually found out (not from Vodafone, of course..) how to link the GSM SIM to an online Vodafone account:

[http://ubuntuforums.org/showthread.php?t=1061368](http://ubuntuforums.org/showthread.php?t=1061368) :-)

But not before I'd wasted loads of time (& crashed Firefox - had to restore its settings from a (fortuitously made) backup copy of ~/.mozilla/firefox/..), trying & failing to get various versions of Betavine's Vodafone Mobile Connect (up to & including the latest .deb downloads) to work. :-(

I'd previously thought that Betavine's contribution would be necessary, in order to obtain the privilege of topping-up the account with fivers. So I've been pleased enough, to discover that the above has made that bit of "not officially supported" brokenware entirely redundant :-)

Looks like Jaunty would plug & play the other Mobile Broadband offerings (e.g. T-Mobile, O2, etc.) just as readily, too.. suppose if Vodafone (or any of them) had smelt the coffee & bothered to officially support Linux, I might feel inclined to show them a bit of brand loyalty, eh?

Anyway.

:-D happy now

---

