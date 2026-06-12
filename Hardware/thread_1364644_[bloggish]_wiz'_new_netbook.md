---
title: "[bloggish] wiz' new netbook"
date: 2009-12-26
forum: Hardware
---

### Post by wizard10000 on 2009-12-26
Crossposted from the Kubuntu forums...

mrs. wiz bought me an HP Mini 110 netbook for Christmas - it's Compaq branded but it's the same netbook everybody else is selling - Atom N270, 1GB RAM, 160GB hard drive, bluetooth, webcam.  Best Buy had them online for $179 on Thanksgiving Day.  Anyway, I sneaked a 2GB DIMM I bought from newegg for $40 into the machine before the spousal unit wrapped it.  Once I unwrapped it yesterday it had Windows on it for about half an hour before I wiped the hard drive   :P

I'd intended to optimize for performance and was gonna install just an Ubuntu minimal install and kde-minimal to start but the tiny little iso for ubuntu-minimal didn't have a NIC driver for the netbook and I didn't feel like installing one manually so I installed Kubuntu Netbook Remix instead.

Sorry, developers - but IMO KNR's user interface is just awful and may be worse than Ubuntu Netbook Remix.  Following claydoh's suggestion in [this thread]("http://kubuntuforums.net/forums/index.php?topic=3107594.0") I removed plasma-netbook and kubuntu-netbook-default-settings and installed kubuntu-desktop instead.

So how did the install go?  Glad you asked   :)

KNR had a driver for the Atheros NIC in the machine and as soon as the install was completed I removed the netbook bits, installed a proper desktop and restricted driver manager offered up a driver for the Broadcom WLAN card.  I installed wicd since the default network manager applet prompts you for the superuser password every time you log onto the thing and had everything straightened out in pretty short order.  I did have to reduce the default system font size in system settings but all the hardware works - even the webcam, which is a little slow and the video quality leaves a lot to be desired but I don't have much need for a webcam anyway.  NIC, WLAN card, audio and video worked out of the box.

Performancewise I was a little surprised to see the Atom N270 supports hyperthreading - thought I had a dual core processor there for a bit.  The machine seems to run just a tad slower than my old 2.8GHz Pentium 4 desktop did and for what it is performance is completely acceptable.

I have had a tiny bit of trouble with a couple of applications that don't like bring run on a screen that short (1024x576) - synaptic needed its default font changed to be really usable and audacious' configuration screens work fine as long as you don't need something from the bottom of the window but everything else seems to work okay but changing the default system font from 8-point to 7-point solved almost everything.

Screenshot here -

[IMG]http://ebassist.com/pix/netbook-screenshot.jpg[/IMG]

---

### Post by 5BallJuggler on 2009-12-26
Fantastic, Finally a good news story.

All you need now is Conky, Lua & Cairo and you'll be sorted ;-)

---

### Post by wizard10000 on 2009-12-26
> **5BallJuggler said:**
> All you need now is Conky, Lua & Cairo and you'll be sorted ;-)

Meh.  I outgrew conky and cairo (although I prefer awn) and I'm not a developer [IMG]http://ebassist.com/forum/images/smilies/grin.gif[/IMG]

I had originally planned to put an SSD in the machine but decided that an SSD big enough to hold my music and pictures would be prohibitively expensive and the 160GB Samsung hard drive works pretty well, actually.  I've grown fond of Samsung hard drives over the last few years anyway  :)

So now I'm going after performance.  I've got some tweaking to do, some services to turn off and a six-cell battery would be nice but all in all I'm fairly impressed with the thing so far.

---

