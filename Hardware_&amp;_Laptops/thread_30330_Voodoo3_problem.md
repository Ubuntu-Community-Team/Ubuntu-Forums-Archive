---
title: "Voodoo3 problem"
date: 2005-04-28
forum: Hardware &amp; Laptops
---

### Post by darranz on 2005-04-28
Hi, after installing 5.04 Hoary my graphic card doesn't work right, resolution is fixed to 640x480 (frequency fixed to 60 Hz too). When I run resolution configurator, it shows only that option, so I can't change it to a higher resolution. When I run "sudo dpkg-reconfigure xserver-xorg" it detects my card right, I set options for resolution and frequency, restart xserver but the problem remains the same.

I've used Debian Woody in the past and the card worked right. I've read Hoary uses x.org server instead xfree server. 

Maybe a x.org problem with voodoo3?

Anyone with this problem?

Thanks

---

### Post by heimo on 2005-04-28
I'm putting together a small howto on resolution related problems.
[http://www.ubuntuforums.org/showpost.php?p=129379&postcount=21]("http://www.ubuntuforums.org/showpost.php?p=129379&postcount=21")

It could be driver, it could be wrong modes being selected. Lots of information in the logfiles.


Welcome to Ubuntu! :)

---

### Post by darranz on 2005-04-28
Thanks very much. I'll try vesa driver. If this not works... is it possible (=easy  ;-) ) install xfree86 instead xorg?

I appreciate your answer, but I don't want go back to low level tricks like setting monitor frequency manually (I've occasionally used Linux for years). It would be justifiable if I had a very new card, but my voodoo3 has 5 years old ;-)

Maybe I'm wrong, but I think it's a problem concerning x.org and voodoo3 or ubuntu and voodoo3.

---

### Post by rmjokers on 2005-04-28
Just an FYI, I have a Voodoo3 card in my desktop at home and it is running Hoary just fine at 1280x1024.  Have you looked at the configuration file /etc/X11/xorg.conf for any obvious problems?

---

### Post by darranz on 2005-04-28
I've looked at  /etc/X11/xorg.conf and I think there is no problem, though I'm not a xorg expert :)  Furthermore, xorg configuration tool detects my Voodoo3, assigns it tdfx driver, etc. and I'm using default settings too.

I'll post here my /etc/X11/xorg.conf if vesa driver doesn't work and neither does downgrading to XFree86

Thanks again

---

### Post by darranz on 2005-04-29
Hi guys, vesa driver worked fine!!!  \\:D/ 

I'm running to explore Ubuntu, bye bye

Thanks!!!

---

