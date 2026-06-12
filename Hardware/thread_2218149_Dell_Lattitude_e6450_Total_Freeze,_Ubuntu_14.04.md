---
title: "Dell Lattitude e6450: Total Freeze, Ubuntu 14.04"
date: 2014-04-19
forum: Hardware
---

### Post by jykaminski-g on 2014-04-19
Hi, 

I just installed ubuntu 14.04 on my dell lattitude e6450. Every I login, at most 2 minutes after, the system freezes completely. Now way to recover from it. 

Any help would me greatly appreciated.

Cheers,
Jeremy.

---

### Post by BeachBuddah on 2014-04-19
[SIZE=2]Hi,
No help here, but a fellow traveler on the road of freezing.  Installed 14.04 on release day and recieved the first update and itnstalled it.
Running: hp Envy dv6 with Intel® Core&#8482; i7-3630QM CPU @ 2.40GHz × 8 and GeForce GT 650M/PCIe/SSE2 with 64 bit architecture and the same version of 14.04. , 750 gig HDD
I have only added the wine-compholio in a (thus far) failed attempt to be able to watch Netflix and a few little doo-dads - compizconfig, changed the 'click on launcher icon to minimize' setting and added Tomboy Notes, KeePassX, 7zip,Iced Tea Java, VLC Media Player, and first used Empathy, then removed and added Pidgin, and Chromium.

At first, Tahr seemed to lock while using Chromium.  Switched to Firefox and found it locking there too.  Also locked during both Empathy and Pidgin use, as well as when trying to delete Pidgin and also while installing (via the Software Center) yet another messenger service - assuming that maybe it was one of the other two that was causing the lock-up.

The strange thing was at one point after removing Pidgin, I was still getting messages and at another freeze I would recieve messages, but the screen was frozen, so there was no visual indication (just the sound, eh?) and couldn't move the mouse...was using the trackpad, but the wireless mouse didn't have any legs either.

Am now running for 20 minutes without a freeze and am using only Firefox, no messenger service, no Software Center or anything else.

If there are any suggestions or help out there on this issue, it would br greatly appreciated.  

TIA for your help.

Chris[/SIZE]

Thanks, drac-noc...I have the exact opposite issue...when usong Firefox all is well, but when I use either Chromium or Midori - it freezes...

---

### Post by drac-noc on 2014-04-20
I'm getting the same freeze problem, but only on Firefox. As soon as I hit a site it freezes immediately, no error messages. 

Chrome and Opera both seem to work fine. Thankfully, I can kill the Firefox process and it hasn't managed to freeze my entire computer - yet. :|

---

### Post by jykaminski-g on 2014-04-20
Hi,

I could install the nvidia driver (which comes instead of the nouveau driver). Apparently, this solved the problem. 

J.

---

