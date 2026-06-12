---
title: "Dell c610 backilght issue"
date: 2006-12-20
forum: Hardware &amp; Laptops
---

### Post by sloof3 on 2006-12-20
I've been grappling this one for a bit.

After about 20 minutes the backlight on my laptop turns off and will never turn back on until I re boot or sometimes I have to remove both batteries.

I set all the power management settings to do nothing.  Nothing should happen when I close the lid, which is true.  

I'm not using anything special like Xgl or fglrx.  

Yet I still have a backlight that won't turn back on if I touch the keyboard or move the mouse.
](*,) 

Anything suggestions?

---

### Post by mkosmo on 2006-12-21
Are your batteries maintaining voltage?  It could turn off if the voltage dropped.  Do you see anything in the messages?

---

### Post by sloof3 on 2006-12-21
Happens whether I'm plugged in or running on batteries.  

What messages?

If the batteries weren't maintaining voltage then then laptop would turn off.  I know it's just the backlight since I can see the faint image of my desktop.

---

### Post by mkosmo on 2006-12-21
`dmesg`, I mean.  Does it show anything after the backlight cuts out, such as a module being unloaded?

---

### Post by sloof3 on 2006-12-21
I tailed /var/log/dmesg and walked away without closing the lid.  When I came back the backlight was off.  After getting the backlight back on by going into the terminal (held the laptop up to a light and squinted) and typing: xset s off, t here was no output from the dmesg tail.

---

