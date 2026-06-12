---
title: "HP ML110 g5 - Cant use hdd after install"
date: 2012-01-02
forum: Hardware
---

### Post by nx1 on 2012-01-02
After installing Ubuntu server on my used server i got for xmas, everything runs smoothly until the installation is finished. When i remove my usb stick to start from the hdd an error message shows

> "mountall disconnected from plymouth"And thats all, from here the system halts. The guy who gave it to me said that it might have a faulty disc controller. The server doesnt contain any other disc controller then those placed on the motherboard. Is there a way to check it out or replace the part, and is it possible to buy a new dc like the [*[SIZE=1]**HighPoint Rocket 620 2P SATA III**[/SIZE]*]("http://highpoint-tech.com/USA_new/cs-series_rr600.htm") and if it is is it possible to just plug and play ?

The HDD is one i used in a old computer that i know works properly. Ive tried reinstalling ubuntuserver and flashing the bios, but the same error message shows up. Any good ideas ?

---

### Post by lukeiamyourfather on 2012-01-02
I have a HighPoint controller that doesn't have native Linux support (i.e. must use their driver instead of one from the kernel). If I had to do it again I'd buy something else.

---

### Post by nx1 on 2012-01-03
so if i basicly go for a dc that is supported by the linux kernel it will be ok ? or do i need to buy a entire new mainboard ?

---

### Post by lukeiamyourfather on 2012-01-03
> **nx1 said:**
> so if i basicly go for a dc that is supported by the linux kernel it will be ok ? or do i need to buy a entire new mainboard ?

Yes to the first question, no to the second.

---

