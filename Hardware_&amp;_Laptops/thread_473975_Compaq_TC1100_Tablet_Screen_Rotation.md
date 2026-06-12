---
title: "Compaq TC1100 Tablet Screen Rotation"
date: 2007-06-14
forum: Hardware &amp; Laptops
---

### Post by hr6999 on 2007-06-14
I just recently got a TC1100 Tablet in a trade, and feisty fawn runs great, i was just wondering if anyone knows how to get the screen to rotate to ladscape and out of landscape, and also how to get it to let you actually write on the screen not just use the pen as a mouse.

Thanks for helping the nube in advance.

---

### Post by hr6999 on 2007-06-15
Come on someone has to have an idea...

---

### Post by francisco_athens on 2007-06-16
> **hr6999 said:**
> Come on someone has to have an idea...

There are some good tips (some not Ubuntu specific) [HERE]("http://wiki.linuxquestions.org/wiki/Tc1100")

Basically to get rotation support you will need the restricted "nvidia" drivers. 

You can use then "nvidia-settings" tool to setup your xorg.conf to support the rotation.
```
$sudo nvidia-settings
```

you will also need to rotate the wacom stylus orientation (see the script in the link above)

There is a nice applet called [Grandr]("http://dekorte.homeip.net/download/grandr-applet/") for the panel for quick changes.

If you need more specifc halp feel free to ask!

Francisco

---

