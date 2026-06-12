---
title: "Dual graphics with AMD 6670 and A6 APU broken"
date: 2014-04-02
forum: Hardware
---

### Post by dylan16 on 2014-04-02
I have an AMD HD 6670 graphics card, a MSI FM2 motherboard, and an AMD A6 APU with 7540D graphics.  The motherboard has an option in the bios for dual graphics, but I cannot get the fglrx driver to work while the mode is set to dual graphics.  The temporary solution is to disable the APU's graphics, but I would really like to be able to use it like I can on windows.

---

### Post by Mark Phelps on 2014-04-03
> but I would really like to be able to use it like I can on windows.

Then first, you need to tell us HOW you use it on Windows.  IS it a hybrid solution where the internal graphics work by default and then the card kicks in when more graphics power is needed?  Do you have one of the graphics sets disabled and are using the other all the time? If so, which set is disabled?

What happens in Windows when you have dual graphics enabled?  What happens when you disable it?

---

### Post by dylan16 on 2014-04-04
I found out that the BIOS was 7 versions behind... updated it, and the drivers started working (at least enough not to do a black screen).   Now the only problem is to get crossfire to work.  I believe that crossfire in windows uses my 6670 card by default and uses the 7540 when it needs more power... not sure though.  When dual graphics in windows is enabled, it seems to provide a FPS increase in demanding games, and when disabled my 6670 is the only GPU doing work.

---

