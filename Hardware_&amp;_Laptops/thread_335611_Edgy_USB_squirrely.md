---
title: "Edgy USB squirrely"
date: 2007-01-10
forum: Hardware &amp; Laptops
---

### Post by allwin on 2007-01-10
I have an old PC with onboard USB ports, ca 1999.  They are USB 1.1.  I slapped in a whitebox two port USB 2.0 card.  I THINK I did so before actually installing UBUNTU 6.10, hoping that hardware detect during install would see the thing.  It did.

So my devices show a USB controller 1.1 and a USB 2.0 controller.  I plug an external USB drive (old drive in USB enclosure).  It mounts as USB 1.1 if I plug it into the original 1.1 plugs.  Performance is like molasses (1MB/sec tops).

I plug it into the USB 2.0 ports.  For a brief moment, Device Manager (GNOME) shows it as a storage device under the 2.0 controller.  Then it disappears, and eventually shows up under the 1.1 controller!  It works...but at 1.1 rates, which is ludicrous.

Seems like UBUNTU sees the onboard 4 port controller PLUS the 2 USB 2.0 ports as "all the same six port hub", like it's merged the two in its mind.  I have tried rmmod ehci_cd, but that just gets me the 1.1 speed.

There are some error messages in syslog where ehci_cd complains about DEAD DEVICE and then won't let me mount the external drive.  But if I unplug and replug, the second chance lands it in 1.1-sville, as if it was attached to the 1.1 ports!  But it's NOT, it's attached to the add on PCI board.

Any chance I will ever see 2.0 speeds with this external drive?

---

### Post by allwin on 2007-01-13
Bumperino.

---

### Post by allwin on 2007-01-14
Bumpamos!  Don't there be nobody out there who knows about USB stuff?  I got a nice external hard drive in a USB enclosure that I'd surely like to use if I could only figger this out!  Thank you!

---

### Post by glabouni on 2007-01-29
have you tried to disable the usb 1.1 in BIOS ?

---

### Post by allwin on 2007-01-29
> **glabouni said:**
> have you tried to disable the usb 1.1 in BIOS ?

The BIOS on this machine does not allow me to do so.  The card is a USB2.0/PCI card I added, and the USB 1.1 support is on the motherboard.  The Windows on the box is Windows ME, and it doesn't recognize the external HD either...basically I admit USB support under ME was flakey.  I've since bought another brand of enclosure and a new HD, which I formatted as NTFS on another system.  Still can't get the new box to detect either.  However, a flash card reader mounts at 2.0 speeds under ME or Ubuntu OK.  Thus I think the hardware path is functional for USB 2.0, trick being to get Ubuntu to see the device.

I did an awful lot of searching on Google, and I can see tens of thousands of posts of people with all kinds of distros who never get their external USB boxes to work.  I'm beginning to think it can't be done, which is another reason I can't dump Windows at this point.

Thanks for replying, though.  This has been out there for a while with no interest!

---

### Post by RandomJoe on 2007-01-30
I've plugged a number of USB2 cards into USB1.1-only systems and had no issues, even with the legacy ports enabled.  And I have a small tower of USB/Firewire external drives as well that work just fine.  (Although I only use USB when I have to, most of my machines have Firewire as well and I prefer to use it.)

As to fixing your issue, I don't have any ready advice - since I've never seen that happen!

You mention "Edgy USB" - have you tried Dapper, just to see what happens?  You ought to be able to boot off a Live CD and test from there, no need to reinstall.  Or perhaps even a different distro's live CD entirely, just to rule out Ubuntu in general.  

I have only just started playing with Edgy, and not on a desktop yet, so I can't say I've tried an add-in card with Edgy yet.  I do have an older USB-1.1 system sitting here that I could try that with - might do that in a bit...

---

### Post by allwin on 2007-01-30
> **RandomJoe said:**
> I've plugged a number of USB2 cards into USB1.1-only systems and had no issues, even with the legacy ports enabled.  And I have a small tower of USB/Firewire external drives as well that work just fine.  (Although I only use USB when I have to, most of my machines have Firewire as well and I prefer to use it.)

As to fixing your issue, I don't have any ready advice - since I've never seen that happen!

You mention "Edgy USB" - have you tried Dapper, just to see what happens?  You ought to be able to boot off a Live CD and test from there, no need to reinstall.  Or perhaps even a different distro's live CD entirely, just to rule out Ubuntu in general.  

I have only just started playing with Edgy, and not on a desktop yet, so I can't say I've tried an add-in card with Edgy yet.  I do have an older USB-1.1 system sitting here that I could try that with - might do that in a bit...

Well, I'm a retired ex bit fiddler myself with a lot of time on my hands.  Since I posted this a while ago, I bought another brand of enclosure and another IDE drive to put in there.  No better luck.  I have a second system with firewire ports, and they behave just as flakey, although I was able to get the old enclosure (which is USB2 and 1394) to be recognized once or twice at full speed.  That was a 1.3G Pentium III dell that's a 2001 model.

Now going back to the problem at hand...with the new enclosure, and a new disk installed and formatted 80GB as one NTFS partition, I'm getting a KERNEL OOOPS when I plug it in, which then seems to kill usbcore completely.

I'm at my wit's end here.  I will try some other distros of UBUNTU and others to see if I can find one thing that gets it to mount.  I'm trying to get to a point where I can toss out the old Windows ME installs.  Can't do that if I can't access these drives.  Thanks.

---

### Post by allwin on 2007-01-30
[http://ubuntuforums.org/showthread.php?t=349279]("http://ubuntuforums.org/showthread.php?t=349279")

BTW...above is the kernel oops thread I opened just today.  Let's say that with changing the brand of enclosure and brand of enclosed hard drive, I now have a kernel oops to add to the squirreliness!

---

### Post by RandomJoe on 2007-01-30
Strange.  I just finished the Edgy install on my older system - Dell GX200 1Ghz P3 - and the PCI card is working fine.  Plugged in the USB drive, and it's recognized without issue.

PCI card is a cheapie left in a computer someone gave me - think it was an IOGear or something, with ALi chipset.

My USB enclosures are all the same - rather pricey ADS Technologies DualLink (USB/Firewire).  But I have in the past used a few other enclosures with no issues either.

Only other software-related thing I can think of is the NTFS filesystem.  I don't run Windows at home, so I can't format one that way to try out right now...

---

