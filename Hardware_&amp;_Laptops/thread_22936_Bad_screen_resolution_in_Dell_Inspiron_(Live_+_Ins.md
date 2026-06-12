---
title: "Bad screen resolution in Dell Inspiron (Live + Install)"
date: 2005-03-30
forum: Hardware &amp; Laptops
---

### Post by pamtomaket on 2005-03-30
Good afternoon from Barcelona!

I tried to install hoary and when the installation process finished (all worked perfectly) I saw the screen resolution was 800x600. It's a problem, because in the laptop, that resolution makes the screen smaller than at 1024x768. I saw that in the xorg conf file the resolution was set to 1024x768, but in gnome i couldn't put it at more than 800x600.

I tried the same with the live cd, without any results. The laptop is a Dell Inspiron 1100 with an Intel 855GM graphics card.

Thanks for your help!

---

### Post by daniels on 2005-03-30
Could you please attach /var/log/Xorg.0.log and /etc/X11/xorg.conf?

---

### Post by pamtomaket on 2005-03-31
Thanks for your answers. If you need it, i will post that log.

I downloaded the 5.04 Hoary RC and saw that it was worse!!! the resolution was fixed to 640x480. Finally, I found the solution in the ubuntu-es.org forums. I post here:

I changed the
[PHP]
Section "Monitor"

        Identifier      "Monitor generico"

        Option          "DPMS"

EndSection[/PHP]

for 

[PHP]Section "Monitor"

        Identifier      "Monitor generico"

        HorizSync       28-49

        VertRefresh     43-72

        Option          "DPMS"

EndSection[/PHP]

in the xorg conf file, i restarted gdm and it worked perfectly @ 1024.

I would be nice to fix it for the final 5.04 version, for the Inspiron 1100 laptops (i dont know if in other 855gm-graphics-based laptops the problem persists).

Thanks!

---

### Post by daniels on 2005-03-31
Yeah, the log would still be really nice.

---

### Post by JeremyStein on 2005-04-09
Adding HorizSync and VertRefresh worked for me also.  I'm not exactly sure what type of display my laptop has -- I got it from LinuxCertified.com, but wanted to upgrade.  (I didn't think to back up my fedora X settings.)

What I really want to know is *why* does that work?

---

