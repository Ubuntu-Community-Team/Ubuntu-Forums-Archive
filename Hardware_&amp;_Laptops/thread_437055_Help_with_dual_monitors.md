---
title: "Help with dual monitors"
date: 2007-05-08
forum: Hardware &amp; Laptops
---

### Post by woodz on 2007-05-08
I've searched around the forums and found a lot of posts on this topic already, but I can seem to find a howto that works for me. I worry that I'm missing something simple but I hope that isn't the case. If it helps I'm running an Dell Inspiron 1505 with an Intel 950 GM. Again, if I am missing something simple feel free to let me know in any manner required (ie. insults, gentle hints, etc...):) Also if any additional info is needed let me know.

---

### Post by jjordan on 2007-05-08
OK, simple things you might have missed:

Make sure the external monitor is plugged in when Xwindows starts so that it will be detected.

Try using the function key to switch between the laptop display, external monitor and both.

Can you switch between the two monitors with the function key (even if the resolution is wrong)?

If you can then it is probably your configuration file: xorg.conf.

You say you have looked at the howtos, have you edited your xorg.conf?  If you have post it and someone will take a look.

-j

---

### Post by woodz on 2007-05-08
Well, the good news is that I did miss those things. However, the bad news is that it didn't change anything :(  However, if I use the function key to switch between the monitors I can get a clone on the other screen, but that seems to be the extent of it. Also, I noticed for the first time that when the secondary screen is off a small grey box appears that says "Input not supported"

I have changed the xorg file before but each time it didn't work I restored it to the backed up version ... so the file that I currently have is not modified at all.

---

