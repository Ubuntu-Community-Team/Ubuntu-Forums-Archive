---
title: "Enabling Atheros AR9285 wireless on Toshiba NB205 from UNBR"
date: 2009-07-24
forum: Hardware
---

### Post by audiorevolution on 2009-07-24
I just bought a Toshiba NB205-N310.  I hurried home and immediately booted from a usb drive Ubuntu Netbook Remix.  Unfortunately, I did not know that the NB205 ships with the Atheros AR9285 wireless card disabled, and that it must be enabled in XP (simply by pressing FN+f8 ) or Ubuntu will not recognize it.  In my initial haste, I wiped the HDD clean of XP, without seeing any need to make an image backup - until now.

Now I cannot find a way to enable my wireless card, and I'm asking you for help.  I have an acquired image of XP Home, but it's not the one shipped with the NB205.  If I wrote this to my usb drive, and reinstalled XP (*shudder*), would I be able to enable my card with those two simple buttons?

Or can anyone else figure out another way to enable the card without wiping off Ubuntu?

---

### Post by heatpumpcontrol on 2009-08-06
I'm pretty sure you can go to the Toshiba website. I went there and noticed that they have all the drivers for the netbook. I too wiped my XP and the recovery partition. Now I'm trying to do without it as I don't want to mess with Windows.

My wireless isn't working but that's because I installed Hardy. Sound works nice on Hardy, louder too, but I can't get the wireless to work. Trying to upgrade it to Intrepid to see if it'll take. If not, I'll just do the upgrade again up to Jaunty. Live and learn.

You can copy XP onto a thumb drive but it's pretty tricky. I can post the links I used later on if you'd like them. I don't have them here on this netbook. Oh, you won't need a 2gig thumb drive as recommended if you don't plan on adding additional software to the thumb drive for the XP installation.

---

### Post by calibre97 on 2009-08-07
FYI, I don't think Intrepid or Jaunty will make a difference. I tried Linux Mint which is basically Jaunty with a pretty face and some custom tools, but they use the same kernel (2.6.28-11) as Ubuntu did and that just doesn't have the support for the Atheros AR9285. I HAD to go with Netbook Remix (following instructions available elsewhere here) to get wireless working.

As for the XP on this thing...for others coming here to read this...BOOT INTO XP and use the built-in utility to make the recovery DVDs!!! It only takes a few minutes and enables you to recover if you need to. Heck, just boot into XP to get wireless working for once and THEN go to town on the drive with Linux. You might want to think about leaving that recovery partition alone, though...just in case.

---

