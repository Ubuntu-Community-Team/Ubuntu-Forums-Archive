---
title: "external monitor support for laptops?"
date: 2004-10-26
forum: Hardware &amp; Laptops
---

### Post by Vulc on 2004-10-26
hey guys, I'm trying to hook up my monitor to a dell 9100 laptop with an ati radeon (not sure if that helps) but when I plug the vga cable into the back of the laptop, the monitor is unresponsive, is there something I need to enable?

edit: just noticed we have a laptop section, not sure how to move my thread so if I a mod wishes to move it, please do

---

### Post by daniels on 2004-10-28
Try googling for 'atitvout', and seeing if that utility is useful to you.

---

### Post by bsherman on 2004-11-01
Perhaps this is a silly question, but have you checked for the BIOS setting and/or a key combo that enables/disables the external VGA port?

On both my IBM's, Dell's I've used, and a Toshiba at work, there are BIOS settings to set the default display mode: VGA only, LCD only, or Both 
The keyboard combo simply cycles those options.

---

### Post by babui on 2004-11-02
With my toshiba laptop (whiit an ati card) the externar monitor has to be plugged  in when I boot the computer.

---

### Post by Denizen on 2004-11-03
I have an HP ze5232 and needed to test a 17" CRT at the weekend.

I just plugged it in and on it came.

Maybe the HPs are configured as default to use both screens when a monitor is plugged in.

I haven't amended anything in my Ubuntu to get this working.

- Jon

---

### Post by mduduzi on 2004-11-03
My problem is a little different.
On a  Packard Bell Easynote E3245, when I use the keyboard to cyle between the three video output options, the X just breaks up into 4 to six static, vertical, fragmented displays. Anybody seen this and is there any help?
The mobo chipset is VIA KN266 and the intergrated graphics is by S3 Savage ProDDR.
Apart from that my X is very stable.

---

### Post by metron on 2004-11-07
Mine works for one or the other, but not both at the same time. It works in Knoppix, but the second display cuts off part of the image. I tried just stealing the knoppix xf86config file, but for some reason that didn't work. I just gave up and settled for one or the other since I don't even use it.

---

### Post by celarent on 2005-11-26
On my Dell 700m, I installed the **i810switch** package (from the universe/utils section)  .  That allowed me to control the video output as to enable an external monitor.

The package description goes:

"i810switch enables/disables the output to the CRT display and LCD, depending on the i810 graphics controller hardware.  Such hardware is found on some laptops (eg, Sony Vaios, some Dell models, etc.)  Chipsets also supported include i855, i830, i845".

If your computer has one of those chipsets, with this package you can control if you want to enable either (or both) displays.

for example, to enable the external CRT monitor, just enter on a console:
```
i810switch crt on
```

---

