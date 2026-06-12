---
title: "Dell Latitude 110L"
date: 2005-05-25
forum: Hardware &amp; Laptops
---

### Post by levelx on 2005-05-25
Hi all! I'm new to Ubuntu and this is my 1st post.
I have just tried Ubuntu on my Dell Latitude 110L laptop and guess what? After the install all i could see was a black screen. I searched the web/forums/wiki etc and i found nothing.

I tried to configure X with xorgcfg and xorgconfig but i still couldn't open display.
I fixed this issue doing this:
Switch back to runlevel 3, kill all X and gdm.
Edit /etc/X11/xorg.conf.
Go to the section of the video card.
Replace "i810" with vesa. Save and "startx".
It magically works. I have seen on many forums people looking to fix this.
Dell Latitude 110L uses graphics card Intel 910GML chipset with UMA graphics (up to 64MB shared). No drivers found.
I'm looking forward to configure my Wireless Net card too (Broadcom is also unsupported).
Cya!

---

