---
title: "Aspire 5315-2153 Sound help"
date: 2007-12-08
forum: Hardware &amp; Laptops
---

### Post by maig on 2007-12-08
I can't seem to get the sound to work on my Acer Aspire 5315-2153 laptop. Any and all help would be greatly appreciated.

---

### Post by maig on 2007-12-09
bump

---

### Post by IndyGunFreak on 2008-01-09
Don't know if you're still trying to get this working, but I have the same laptop as you do...

I was able to get mine working by re-compiling alsa following the instructions here:

[https://help.ubuntu.com/communijty/HdaIntelSoundHowto](https://help.ubuntu.com/communijty/HdaIntelSoundHowto)

Then while messing with Xandros, I hosed my Ubuntu partition.  So I reinstalled Ubuntu, and the above instructions no longer worked.  Don't ask me why, as I used the same alsa files(had them stored w/ my backup), followed same instructions, etc. it just didn't work.  Maybe there was a kernel change or something, I don't know.

So did some Googling, and came across this in another thread here...

[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

Following the instructions for the Acer 5315 laptop, worked perfectly.

IGF

---

