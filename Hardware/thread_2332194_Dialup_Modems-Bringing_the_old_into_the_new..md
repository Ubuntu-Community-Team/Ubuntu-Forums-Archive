---
title: "Dialup Modems-Bringing the old into the new."
date: 2016-07-29
forum: Hardware
---

### Post by kyrithis on 2016-07-29
So I've completely taken the plunge into Linux. My hard drive is now single-boot Ubuntu, no Win-OS in sight. Most of my hardware has gone along with the switch just fine, including my graphics card (Where I foresaw the biggest problem). The only issue I've noticed so far is that my Dialup modem is now completely non-functional.

Being a self-proclaimed computer whiz, I've always wanted to know how things were back in the older days of computing. Shortly before my switch to Linux from Win10, I salvaged a PCI Dialup Modem (SV92PP is what I can remember of it) and started experimenting with the few BBSes left in existence. The trouble is, Ubuntu (16.04) seems to lack the capability to use the modem.

----Rambling ends here---

Simply put, I'd like to know if my PCI Modem can be used in Ubuntu at all, or if we're too far into the digital age for such things. If it's possible to do so, I'd like someone with more knowledge than myself to help guide me through the installation and setup of the modem. If this is not possible, there's no harm done. It is NOT an essential component by any means, simply something I'd like to experiment with.


Thanks in advance,
Lexi.

---

### Post by coldraven on 2016-07-29
If it is a soft modem (also known as a Winmodem) you probably will not get it to work. I have one built into this HP laptop and there is zero chance to get it working.
I ran the  scanModem tool from the linmodem site and my chipset is not supported. I don't know if this site is still maintained. Edit: I think it is dead :(
 See here:
[https://en.wikipedia.org/wiki/Soft_modem](https://en.wikipedia.org/wiki/Soft_modem)
[http://www.linmodems.org/](http://www.linmodems.org/)

---

### Post by kyrithis on 2016-07-29
Yea, I went through all of that before. They're completely dead, and as far as I can tell, are 10 years old. That's why I had hoped we had a chance of making it work with newer information.

I'm not sure how to tell if it's a soft modem, but I seem to remember that being in it's name in Windows Device Manager. That'd make it almost impossible then.

Thanks for the quick reply, I wasn't sure what to expect yet. It's nice to know I'm not alone in this, and I have a lot of people to help and get help from ^-^.

*Not exactly solved, but I'll mark it as such and call it a failure.*

---

### Post by Kale_Freemon on 2016-07-29
Do you, by chance, know the brand of the modem? I ask because I use to have an old Pentium 3 with a soft modem, and was able to make it work in Ubuntu 7.04 with the martian driver.

If it's a Lucent branded modem, it should work (theoretically).

The info is about a decade or so old, but may still work.

[https://help.ubuntu.com/community/DialupModemHowto/Lucent](https://help.ubuntu.com/community/DialupModemHowto/Lucent)

---

### Post by kurt18947 on 2016-07-30
I have not messed with this at all so take what I'm about to type with that in mind. I have looked at this in the past and from what I've read, there's only one modem chipset that is sort of supported, a Rockwell V92 something-or-other. That chipset is usually found in external modems. There were distros that had software made connecting via dial-up fairly simple. Some flavor of Puppy, perhaps? I don't recall. IMO Ubuntu is not really optimized for old hardware and technologies like some distros are.

Your posting made me curious so I searched and guess what popped up?

[https://www.thinkpenguin.com/gnu-linux/56k-usb-dial-modem](https://www.thinkpenguin.com/gnu-linux/56k-usb-dial-modem). 

It looks like newer more modern distros are indeed supported. Not inexpensive but if you need it .............

---

