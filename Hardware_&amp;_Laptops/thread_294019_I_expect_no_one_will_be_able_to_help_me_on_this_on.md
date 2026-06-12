---
title: "I expect no one will be able to help me on this one..."
date: 2006-11-06
forum: Hardware &amp; Laptops
---

### Post by xxFelixDCatxx on 2006-11-06
Okay I just looted (legally) a toshiba portege 3500.  Being a huge fan of linux and ubuntu, I decided to see how ubuntu 6.10 would work on a tablet pc, and I was able to find a bunch of tips on getting tablets to work.

The Problem:  a toshiba portege has no cd drive.... this of course makes an install of an OS very difficult.  Luckily for me (so I thought) I have another toshiba laptop.... the toshiba l25-s1192 (black friday deal).  So I decided to put the harddrive in the l25 and install it there, and transfer it back after the install was complete.  What could possibly go wrong?

I would like to note that I also tried this with windows.  Device signing on it of course killed the installation, but I had to try.  I know linux is infinitely customizable, and I also know that ubuntu 5.something ran fine on the protege.

My main question is this.  Doing the install the way I did... would that mess with the driver configuration at all?  And if so is there a way to run an auto detector?

Right now, xorg server fails massively.  I haven't done anything else, I just want a GUI (i was weaned on win98) so i can start from somewhere visual and familiar.

If anyone knows anything post any thought or random comment. I would love the help and be very grateful.

---

### Post by phersotty on 2006-11-06
no cd drive hmm maybe you could connect it to an external usb cd/dvd drive

---

### Post by xxFelixDCatxx on 2006-11-06
okay call me crazy but i'm fairly sure i've been through this before.... there's a command prompt that basicially takes you through an ascii based configuration for everything over again, but way more detailed.... any ideas?

---

### Post by xxFelixDCatxx on 2006-11-06
> **phersotty said:**
> no cd drive hmm maybe you could connect it to an external usb cd/dvd drive

yea thought so too, unfortunately the BIOS doesn't support any USB bootables at all.... I'm really trying to avoid buying an 80 dollar PCMCIA cd drive that I know would do this a lot easier.

---

### Post by xxFelixDCatxx on 2006-11-06
okay so i viewed detailed error reports...

it's saying the device is the ati 200m that's in the other computer... i think that may be the problem lol, anyone know how to fix that?

---

### Post by Tomas007 on 2006-11-06
have you tried the "vesa" or "vga" driver in xorg.conf Should work with any card (correct me if im wrong) and gives you a running X-Server at least.

---

### Post by larsemil on 2006-11-06
sudo dpkg-reconfigure xserver-xorg

---

### Post by Decade on 2006-11-15
Hi, I just received one of these laptops, too, except I'm trying to use Gentoo on it, and my Ubuntu machine is currently down, so I can't help with the autoconfig stuff.

So far, I've had no luck with the vesa driver, and I prefer not to use the vga driver.

The trident driver does work, except that it doesn't support screen rotation, which makes it not so nifty as a tablet.

Also, mine came with a PCMCIA drive, which usually doesn't work because most distro installers don't configure PCMCIA drives.

However, what does work is netboot. I think there are netboot install images in some infrequently seen directory of the Ubuntu distribution, typically ubuntu/dists/edgy/main/installer-i386/current/images/netboot. You have to configure DHCP and TFTP servers, but there are plenty of guides and HOWTOs for that.

---

