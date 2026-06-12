---
title: "koala + amd 780g chipset + flgx driver= no video!?"
date: 2009-11-03
forum: Hardware
---

### Post by originalsynthesis on 2009-11-03
I'm building a cheap computer for a friend of mine, using a Asus m3a78-em MOBO with the amd 780g chipset. I put karmic on there (dual boot with xp on 500gb hd) with no problems, but when I activated the default drivers that were suggested (fglrx, if i recall properly)  I could no longer get any video signal whatsoever! I can get into recovery mode, but I really dont know what to do there, except that I checked for any broken packages and found none.  My first instinct is to wipe that install and try again, but with what? 

If I try 9.10 again, are there any alternative drivers that will work with a ati radeon based chipset?  Ideally though, I'm wondering how I can fix this without a reinstall. Everything seemed plum dandy until I activated those graphics drivers. Any suggestions here would be great! 


EDIT: this might be noteworthy: I installed from a usb setup disk made in the 9.10 usb startup disk creator. After installing koala on the machine and having this trouble I tried to boot into linux using live mode from the usb disk, and now it wont work either. BIOS tells me to 'reboot and select proper boot media' when I use it as the boot device. I have heard of some bugs in the program, but could that have somehow caused this trouble? 


As an aside, I have been having a few headaches working with this chipset. The computer is to be used as a cheap audio workstation, but on the windows side, Im having trouble with feedback loops and latency while recording. I am not using an outboard audio interface, just the stock mic in/ line out inputs on the mobo. And I don't see why I should have to. But..this is why I started working with linux, as i've never had issues like that with ALSA and JACKD.

---

### Post by originalsynthesis on 2009-11-04
(bump)

im starting to find a few similar problems here and there on the forums. and no real solutions it seems.

is jaunty (9.04) still available anywhere? Going through canonical so far I've only been linked to 9.10 and 8.04. And since JACK in hardy was complete garbage, no way im going back.

 This is the worst problem I found with the same chipset and fglrx drivers but using Jaunty: [http://ubuntuforums.org/showthread.php?t=1178269](http://ubuntuforums.org/showthread.php?t=1178269)

This would be much better than no Xserver at all...

---

