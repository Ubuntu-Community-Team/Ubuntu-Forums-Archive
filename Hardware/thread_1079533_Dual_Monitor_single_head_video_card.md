---
title: "Dual Monitor single head video card"
date: 2009-02-24
forum: Hardware
---

### Post by merkel04 on 2009-02-24
Hello,

I have an onboard graphics card, VIA Unichrome Pro, in my laptop. It only has 1 head:

lspci -x | grep VGA
01:00.0 VGA compatible controller: VIA Technologies, Inc. UniChrome Pro IGP (rev 01)

Can I use dual monitors with this card? Right now my second monitor is cloned, but I want to be able to use dual monitors with this card like I did in Windows. So far I cannot find a clear answer if this is even possible.

The "closest" I have gotten was getting an Entity already in use error when starting x, but I believe that is because it is calling the same piece of hardware for two different screens.

Thanks for any help,
Brian

---

### Post by sowelie on 2009-02-24
It may be, you'd have to set it up manually though in your xorg.conf I'd assume.  nVidia and ATI both have tools you can use to configure dual monitors.  If you google xorg.conf dual monitors, there's plenty of info out there.  There should also be a button on your laptop to toggle how the external display is handled.

---

### Post by merkel04 on 2009-02-24
Yes, i've been searching for hours and hours now. I've probably tried about 900,000 different things in xorg. So you're saying that it is possible, even though I technically only have 1 graphics adapter?

Also, its a POS Via Unichrome integrated video card, so unfortunately ATI and nvidia tools aren't available to me.

I have no problem configuring xorg manually, I just don't know how to do it since I only have a single head video card, and I am unable to find a clear answer on if its even possible to use dual monitors with this type of card.

Thanks,
Brian

---

### Post by sowelie on 2009-02-26
It may be possible.  Most laptops with a vga port are capable of dual monitors.  However, it's definitely not easy on linux apart from nvidia...even ATI WITH the tool isn't all that easy.  What video driver are you using?  I'd say this page would be a good start, get the official driver for the adapter: [https://help.ubuntu.com/community/UniChrome]("https://help.ubuntu.com/community/UniChrome").  That installer may contain a utility for setting up dual monitors...if the adapter can do it.

---

