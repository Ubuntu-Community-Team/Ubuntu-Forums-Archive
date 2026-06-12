---
title: "Supermicro AOC-USAS2-L8e SAS/SATA card compatibility"
date: 2012-01-07
forum: Hardware
---

### Post by pnorman on 2012-01-07
I'm considering purchasing a [Supermicro AOC-USAS2-L8e]("http://www.supermicro.com/products/accessories/addon/AOC-USAS2-L8i.cfm?TYP=E") SAS/SATA card. Would this card be compatible with Ubuntu? 

Apparently it uses the [mpt2sas module and has a LSI 2008 chip]("http://blog.zorinaq.com/?e=10"). A closely related product is the [AOC-USAS2-L8i]("http://www.supermicro.com/products/accessories/addon/AOC-USAS2-L8i.cfm?TYP=I") which has the same chip, but also has RAID capability, which I do not require. In spite of that, it may be cheaper and easier for me to buy.

Supermicro has drivers for RedHat and OpenSUSE, but not Ubuntu or Debian. Their drivers are difficult to install and the installer won't work on Ubuntu systems.

LSI's version of the card is the [LSI SAS 9211-8i Sgl]("http://store.lsi.com/store.cfm/Host_Bus_Adapters/9211_Adapters/LSI00194")

I am aware that the supermicro card uses a non-standard UIO bracket but I am confident of my ability to modify the bracket, use no bracket, or produce a new bracket.

If anyone has alternative recommendations for an appropriate 4 or 8 port card, I'd welcome them.

---

### Post by DantePasquale on 2012-04-25
Did you ever figure this out? I have ordered an SAS 9211-8I and will try it this weekend. I'm hoping that the bios figures it out and lets me present it as a single drive, but I'm not optimistic.

---

### Post by pnorman on 2012-04-26
> **DantePasquale said:**
> Did you ever figure this out? I have ordered an SAS 9211-8I and will try it this weekend. I'm hoping that the bios figures it out and lets me present it as a single drive, but I'm not optimistic.

I ended up ordering a LSI SAS 9211-8i myself since it was on sale and didn't involve any hardware hacking. I have it set to JBOD mode so it just presents the drives to the OS and doesn't do anything with RAID, allowing me to use software RAID.

Ubuntu has worked flawlessly with it. I've been having other unrelated hardware issues with my motherboard.

---

