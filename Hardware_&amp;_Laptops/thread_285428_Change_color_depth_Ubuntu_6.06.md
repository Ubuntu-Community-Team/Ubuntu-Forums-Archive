---
title: "Change color depth Ubuntu 6.06"
date: 2006-10-26
forum: Hardware &amp; Laptops
---

### Post by dmorlow on 2006-10-26
I can't figure out how to change my color depth from 24-bit to 16-bit.  I have an HP DV4000 laptop with an Intel 915 video card.  I tried going to /etc/X11/xorg.conf and modifying this line...

Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"

I changed it to...

Monitor         "Generic Monitor"
        DefaultDepth    16
        SubSection "Display"

I've read everywhere this is the right way.  But when I do this and reboot the computer, it comes up where my whole screen is black except the bar and I cannot get around at all.  The only way to get the computer back functional is for me to use Ctrl + Alt + an F key and go in and change it back to 24.  Any idea what I'm doing wrong?

Thanks,

David

---

