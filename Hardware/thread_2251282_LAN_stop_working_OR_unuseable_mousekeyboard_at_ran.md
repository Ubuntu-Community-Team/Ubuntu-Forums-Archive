---
title: "LAN stop working OR unuseable mouse/keyboard at random intervals"
date: 2014-11-03
forum: Hardware
---

### Post by riksoft on 2014-11-03
Hi there,

I've got this problem on a P4 2.8Ghz 1GB RAM:
_**ANY kind of Ubuntu**_ based distro (ubuntu, xubuntu, lubuntu, mint), have a problem that _**not a single direct Debian**_ based distro has (Debian, Mint LMDE, SolidXk, etc).


That's what happens: at random time
1) I lost connectivity. Trying to restart the network is useless. Creating a new connection and restart the network is useless. The only that solve the problem is a soft reboot.

OR ALTERNATIVELY

2) Mouse and keyboard becomes very slow and I must type one letter per second or it loses characters. CPU usage 10%/20% so it's not because of CPU overload.
Even restarting X is useless: the only solution is, again, a soft reboot.

On the contrary, nothing bad happens with any kind of Debian flavour or Debian distro based (except Ubuntu).
Debian XFCE=OK, Mint LMDE Mate=OK, SolidXK=OK, Mint Mate=BAD, Mint XFCE=BAD, Xubuntu=BAD.

**What could have that effect** on the Ubuntu based distros and not on the Debian ones? I've stessed Debian XFCE to the limit (CPU 100%, ram usage, etc.) and nothing bad happens while on Xubuntu even without doing almost nothing (e.g. I'm reading a pure HTML page with no JS) and something bad happen (point 1 or 2).

I'd prefer Xubuntu LTS than a Wheezy that I'll have to reinstall in about 2 years.

Thanks in advance,
Rik

---

### Post by tgalati4 on 2014-11-03
On a 10-year-old computer, I would suspect the power supply.  It's possible that the graphical effects on Ubuntu are causing the graphics card to work harder and use more power, causing the network and mouse/keyboard to drop out.  What is the graphics card that you are using?  What voltages are shown when you boot into BIOS?  Is 5VDC really 5VDC?

---

### Post by riksoft on 2014-11-04
I'd like it would be so simple, but unfortunately it isn't.

The computers are relatively old because only the M/B and proc are old, everything else is new including ram and power supply that originally was a ~400W and now is a brand new 700W.

And these 2 computers has nothing in common: asus vs gigabyte M/B, different ram modules, different processor, different VGA (the older PC has FX 5500, the newer Radeon 9200: they are both more than sufficient for thunderbird and openoffice).
I've tried 3 different NIC starting from an old 10mbps to a new 1000mbps. Nothing to do. Different cables, different lenght of cable, different router port. In the meantime I've also change broadband from a 4Mbps to a new 38D/19U Mbps fibre.

One of these computers (that I would turn into a nix computer) is used 10 hours/day with Windows Xp :-& with Gimp, OpenOffice, Corel Draw, Firefox, Thunderbird, Youtube, etc. 
Not a hitch up to now and for YEARS. Everything runs smoothly. _Only Ubuntu based distros have problems here._

_On both computers Debian runs very well_  I've tried many distros with any sort of torture (e.g. loop of youtube HD videos playlist for hours.
I've also opened EVERYTHING IN THE MENU: gimp, every libreoffice app, firefox with multitabs on yahoo with tons of images, and youtube videos, etc, etc. Even stuffing the RAM with CPU 100% no problem at all.

Yesterday I've also tried Sparky live (it's a Debian Jessie on steroids), with desktop extended in dual monitor: not a single problem. On the contrary the live of Xubuntu or Mint XFCE drop the net in a minute WITHOUT EVEN TOUCHING the mouse, just watching the desktop.

So the problem is only Ubuntu related, there's no doubt about it. Obviously it'll also be related to some kind of hardware but strange to say I have 2 completely different PC with this problem.

Maybe the problem is that Ubuntu it's no longer a good base for P4 PC no matter what is the DE. However I've made a distro myself with Ubuntu server (that is basically a pure Debian) + OpenBox + TOR Browser and it runs 24hours per day with automatic navigation without interruption for months on a P3-500 with only 512MB ram, _SAME NIC_ which is problematic on the other PC.
So?! Where is the problem? Probably some scripts/config that only comes with Ubuntu Desktop base, not with Ubuntu Server nor with Debian.

I don't know. I only know that XP and Debian distros work well, while not a single ubuntu flavour do.
I'll try to find out what's the problem... eventually I'll simply take the easier way: Using Sparky Linux instead of Xubuntu/Mint XFCE.

---

