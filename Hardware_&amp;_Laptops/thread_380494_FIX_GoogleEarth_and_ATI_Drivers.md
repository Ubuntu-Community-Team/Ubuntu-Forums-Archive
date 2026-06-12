---
title: "FIX: GoogleEarth and ATI Drivers"
date: 2007-03-09
forum: Hardware &amp; Laptops
---

### Post by mertle on 2007-03-09
I have an ATI Radeon Mobility X300 and for quite some time, I've had the typical problem of GoogleEarth either running like total mud (with the open source 'ati' driver) or hanging at the splash screen (with the 'fglrx' proprietary driver). I tried for quite some time, sifting through forum posts and HOW TOs, but was never able to get it to work and eventually gave up. This morning, however, I decided to take another crack at it being that I just did a fresh install of Kubuntu the other day. Figured.. what the hell.

And it worked! I dunno if anyone else has posted a possible fix for this, and if they have, I do apologize for the repost.

What I did:

First, I installed GoogleEarth while I was still using the Linux provided open source ATI driver. Dunno if this made a difference, just putting it out there.

$ sudo apt-get xorg-driver-fglrx
((installs the driver))

$ sudo apt-get fglrx-control
((installs the ATI control panel- dunno if this is needed or not, though))

[highlight]WARNING: BACKUP YOUR XORG.CONF (/etc/X11/xorg.conf)[/highlight]

I just saved a copy as 'xorg.conf-safe' in case I messed something up and couldn't boot back into X. Learned that lesson the hard way. ;)

Edit your xorg.conf file with your preferred text editor, just make sure you have root permissions.

Where it says something like:

```
Section "Device"
   Identifier   "ATI Technologies, Inc. M22 [Radeon Mobility M300]"
   Driver       "ati"
   BusID        "PCI:1:0:0"
EndSection
```
Replace "ati" with "fglrx"

Then add this at the end of the file:

```
Section "Extensions"
   Option	"Composite"   "0"
EndSection
```

The following are also in my xorg.conf (red highlighted ones pertain to the ATI driver, I believe), but they may be different for others:

```
Section "Module"
   Load         "i2c"
   Load         "bitmap"
   Load         "ddc"
   [COLOR="Red"]Load         "dri"[/COLOR]
   Load         "extmod"
   Load         "freetype"
   [COLOR="Red"]Load         "glx"[/COLOR]
   Load         "int10"
   Load         "type1"
   Load         "vbe"
   Load         "dbe"
EndSection

Section "DRI"
   Mode	        0666
EndSection
```
I rebooted and then ran GoogleEarth- all was well. It moves swiftly, no choppiness, and more importantly, it runs without any errors or hanging.

Hope this helps some people. :)

- mertle

---

### Post by Icarosaurus on 2007-03-13
Hello,
there are problems running Googleearth with ati free drivers, due to drivers limitations for my radeon 9600 (RV350), it seems.
Fglrx proprietary drivers work better, but don't support composite, so you cannot use Beryl with aiglx.

I'm using beryl and aiglx with ati free drivers, and I'd like to have a full 3d support.
When I use fglrx I'd like to have composite support.

Next time, I'll buy an Nvidia card for my linux box...

---

### Post by mertle on 2007-03-13
> **Icarosaurus said:**
> Hello,
there are problems running Googleearth with ati free drivers, due to drivers limitations for my radeon 9600 (RV350), it seems.
Fglrx proprietary drivers work better, but don't support composite, so you cannot use Beryl with aiglx.

I'm using beryl and aiglx with ati free drivers, and I'd like to have a full 3d support.
When I use fglrx I'd like to have composite support.

Next time, I'll buy an Nvidia card for my linux box...

Yeh... I found this out only yesterday. I thought "*Hey, if I can get GE to work, mebbe I can finally get Beryl/Compiz to work!*" ... wrong. I /almost/ had it working with XGL, but I kept getting an error. I'd fix that error, get another... and the cycle went on until I gave up. I'm hoping that ATI will put out a fully working driver for Linux sometime soon so I /won't/ have to ponder a new video card.

Then again, Beryl/Compiz really isn't all that necessary to me, I just wanted to see what it looked like in person. GE, on the other hand, I need... it's awesome at directions. :)

- mertle

---

