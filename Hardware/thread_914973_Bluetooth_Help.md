---
title: "Bluetooth Help"
date: 2008-09-09
forum: Hardware
---

### Post by Jim Gupta on 2008-09-09
Hi, I'm no linux expert so please feel free to over-explain things.

I have a Dell XPS M1530 laptop and just recently purchased a sony ericsson w580i phone.  I wanted to pair my phone with my laptop.

I can not get bluetooth working.  I believe I've downloaded and installed all the packages needed from the download manager.

I can start bluetooth:
```

$ sudo /etc/init.d/bluetooth start
 * Starting bluetooth                                                    [ OK ]

```

but I still can't see the computer from my phone.  I searched around a little and some have mentioned using hcitool... so I gave that a try and got this:
```

$ hcitool scan
Device is not available: No such device

```

I don't know what files other info I should post that would be helpful.

Can anyone help me get this working?

-Jim

---

### Post by Jim Gupta on 2008-09-09
Just a little more info:

```

$ uname -a
Linux Uranus 2.6.24-19-generic #1 SMP Wed Aug 20 17:53:40 UTC 2008 x86_64 GNU/Linux

```

---

### Post by IntuitiveNipple on 2008-09-09
Make sure the computer actually does have the *optional* TruMobile Bluetooth adapter fitted - many don't. If you search my posts over the past 3 weeks for Bluetooth you'll find another user who was caught out the same way, and the steps we took to check.

---

