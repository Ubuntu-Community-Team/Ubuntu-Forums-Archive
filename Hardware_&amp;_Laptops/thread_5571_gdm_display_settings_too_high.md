---
title: "gdm display settings too high"
date: 2004-11-19
forum: Hardware &amp; Laptops
---

### Post by amg on 2004-11-19
Hello,

How do I go about changing the default resolution/refresh rate/what-have-you with GDM?

Whenever my system loads Gnome Display Manager on boot-up my monitor enters Power Save Mode. I can blindly login to my account, which works fine because I logged in and CTRL+ALT+NUM(+/-) until my monitor turned on, then changing my refresh rate from 85Hz (which my monitor can't handle at 1024/864, to 75Hz).

If I try to CTRL+ALT+NUM(+/-), while at the GDM screen, my system will freeze (or at least the keyboard will stop responding), and I have to reboot.

I'm thinking it's something to do with GDM and it's default refresh rate, although I don't know where/how to change that.

I've edited my XF86config file to represent what my manufacturer recommends for refresh rates, but to no avail.

I've tried to change it through gdmsetup, but I can't see an option for refresh rates.

---

### Post by sn33kyP3t3 on 2005-09-13
I am having a similar problem, on boot up dispay is 1920 x 1200, and should be 1280x1024 yet changing xorg.conf has not worked. 

Please let me know if you found a solution for this

---

### Post by Teroedni on 2005-09-14
To both of you 
Can you post your config file where you got the horinz and vertical adjustment for your monitor?

---

### Post by heimo on 2005-09-14
I have no personal experience on this logon screen resolution issue, but here's couple links that may help:

[http://ubuntuforums.org/showpost.php?p=253944&postcount=3]("http://ubuntuforums.org/showpost.php?p=253944&postcount=3")
[http://www.ubuntuforums.org/showpost.php?p=129379&postcount=21]("http://www.ubuntuforums.org/showpost.php?p=129379&postcount=21")


EDIT: Watch for differences between Warty<->Hoary

---

