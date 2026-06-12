---
title: "RAM: Crucial vs. Kingston"
date: 2007-03-03
forum: Hardware &amp; Laptops
---

### Post by newagelink on 2007-03-03
I'm about to spend $200 upgrading my RAM from 0.5 GB to 2.0 GB.

I'm looking at [ Crucial 1GB 200-Pin DDR SO-DIMM DDR 333 (PC 2700) Notebook Memory - OEM]("http://www.newegg.com/Product/Product.asp?Item=N82E16820145068") and [ Kingston ValueRAM 1GB 200-Pin DDR SO-DIMM DDR 333 (PC 2700) Notebook Memory - Retail]("http://www.newegg.com/Product/Product.asp?Item=N82E16820172105"); not sure what 'OEM' has to do with it ...

The product that's $1 more has over two hundred more reviews; should I get it? Are both brands good? Or bad?

What would you recommend? Can I get it for significantly less than $95? (I want to get two 1 GB chips.)

---

### Post by tgalati4 on 2007-03-03
Yes, yes, no,both,no.

Run memtest overnight and worry about something more important.  Like global warming.

---

### Post by newagelink on 2007-03-03
How do I do that?

*sigh*
My Ubuntu partition crashed; some I/O read error. (It messed up while writing data to one sector?) I'm going to download the latest version and see if it's possible to grab my data off it, then erase and reinstall Ubuntu.

---

### Post by tgalati4 on 2007-03-03
You can run memtest from the live CD or from grub:

title           Ubuntu, memtest86+
root            (hd0,2)  #Your location may vary, typically where Ubuntu is located
kernel          /boot/memtest86+.bin
boot

Sorry to hear of your troubles.

Was this a new disk drive?  Sometimes they need breaking in before using.

---

### Post by K.Mandla on 2007-03-03
Just curious, but do you really need 2Gb of memory? Do you dual boot to play games in Windows?

---

### Post by newagelink on 2007-03-04
> **K.Mandla said:**
> Just curious, but do you really need 2Gb of memory?I have 504 MB, and things are unbearably slow. Running Firefox, iTunes, Incredimail, Trillian, Windows Explorer, and any other multitasking kills my computer. Diablo II + iTunes = stalls. I figure I'll upgrade this laptop to 2 GB, and then if it's still slow, I'll sell it and buy a new desktop. I may have spyware or something on my computer, though.
> **K.Mandla said:**
> Do you dual boot to play games in Windows?Yes. If it wasn't for webcam, iPod + iTunes, and video games, I might not even use Windows.

---

### Post by newagelink on 2007-03-04
> **tgalati4 said:**
> You can run memtest from the live CD or from grub:

title           Ubuntu, memtest86+
root            (hd0,2)  #Your location may vary, typically where Ubuntu is located
kernel          /boot/memtest86+.bin
bootI'm not sure I follow.
> **tgalati4 said:**
> Sorry to hear of your troubles.Mm, 'ppreciate it. I don't know if I've screwed up my computer or if Gateways aren't good ...
> **tgalati4 said:**
> Was this a new disk drive?  Sometimes they need breaking in before using.I bought this laptop August 2005, and it was shipped from Gateway July 2005.

---

### Post by newagelink on 2007-03-04
I just spent $213.84 on two of the Crucial chips. "Projected" to arrive "in two business days".

---

