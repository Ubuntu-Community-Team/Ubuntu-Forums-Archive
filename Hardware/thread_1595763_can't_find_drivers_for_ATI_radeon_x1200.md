---
title: "can't find drivers for ATI radeon x1200 ?"
date: 2010-10-13
forum: Hardware
---

### Post by princeofnam on 2010-10-13
my laptop currently is : [http://www.buy.com/prod/toshiba-satellite-a215-s7422-notebook-computer-1-9ghz-amd-athlon-64-x2/q/loc/101/205632241.html](http://www.buy.com/prod/toshiba-satellite-a215-s7422-notebook-computer-1-9ghz-amd-athlon-64-x2/q/loc/101/205632241.html)

Unfortunately I'm having trouble finding proper driver support for the ATI radeon x1200 as described by another poster:

--
You should still be able to get full 3D support for your hardware by downloading & installing the drivers manually.

This is where it gets complicated, unfortunately. 

ATI dropped support for some "older" 3D devices some time back (actually not all that old in many cases - it made a lot of ATI card owners very upset). So I'm not sure which drivers you'd need to download & install to get your 3D hardware working.

The Radeon x1200 device in your notebook is, confusingly, not the same as a desktop Radeon x1200 card. Which is kind of nuts.

I don't own any ATI products any longer, so this is really outside my experience. I hope someone who does know can help.
--

has anyone had better luck?

---

### Post by brokenromeo on 2010-10-13
You have to use the built in Ubuntu drivers for that card...I have an older Toshiba laptop with that chipset and it does most of the desktop effects, but I don't do any gaming on that laptop...

---

### Post by André Oliva on 2010-10-15
Hello, I have the same problem. 

I use the default drivers and in Lucid, the 3d cube, and other effects work well. (Dell Inspiron 1721, ATI Radeon X1200). Proprietary drivers are not available for Lucid or Maverick. But recently I wanted to try the new Unity interface and nothing works. I partitioned my hardrive and did a new installation of Ubuntu 10.10 Netbook Edition. In Unity I get a blank screen. The default drivers report that everything works well (*glxinfo | grep rendering* reports *direct rendering: Yes*). Lucid shows the gears in glxgears, but Maverick does not. I installed Compiz in UNE Maverick. Compiz is terribly slow, but in Lucid I have no problems with compiz. I also tried to install Unity in Lucid and it didn't work.

It's very strange. Any ideas?

---

### Post by CPL2010 on 2010-10-15
I just finished rebuilding XP and I'm on a build of linux 10.10 on a dual boot.

Gots to have my games...although other Dell/ATi users are having some similar problems right now.  I might be dropping the lappy down to 10.04 so I can use it.

---

