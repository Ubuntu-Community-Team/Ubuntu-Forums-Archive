---
title: "Sony Vaio Widescreen issues"
date: 2006-08-02
forum: Hardware &amp; Laptops
---

### Post by smpolymen on 2006-08-02
Ok, I have a Sony PCG-TR3A with a wide screen monitor. I cannot get the wide screen working at all. I have tried:

sudo dpkg-reconfigure xserver-xorg

The first time i tried this i selected the "try to talk to the monitor" option and it flipped out and crashed X. The second time I pretty much used defaults except enabled 1280x768, but no dice.

I tried the 955resolution mentioned somewhere here
did apt-get install etc. it installed I guess and ran I guess. It appeared to already put itself in init.d and xorg.conf had the 1280x768 lines, but still no widescreen.

Any ideas?

BTW, I had a lot of trouble installing dapper. The cd drive doesn't work well in this laptop and it would be very noisy and it would get burning hot when using the cd, but otherwise the laptop is fine. The Ubuntu install kept freezing during, so I installed Xubuntu and apt-get install ubuntu-desktop. If there is an easier way (less cd intensive as a livecd) to install ubuntu, I'll install straight Ubuntu (which is what I really want).

---

### Post by smpolymen on 2006-08-02
Also, I just realised that ctrl-alt-backspace doesn't restart X. I'm very confused.

---

### Post by ysse on 2006-08-02
> **smpolymen said:**
> If there is an easier way (less cd intensive as a livecd) to install ubuntu, I'll install straight Ubuntu (which is what I really want).

You could download and burn the ubuntu-6.06-alternate-i386.iso. It's a more traditional installer, with a text based user interface. Obviously, it would still need to read a lot from the CD in order to install, but it doesn't need to boot up a whole system first.

Good luck!

---

### Post by smpolymen on 2006-08-02
Yay! This works!!!! [http://users.skynet.be/thomasvst/linux-on-laptop/#wide](http://users.skynet.be/thomasvst/linux-on-laptop/#wide)
Just have to change it to x768 and it's good

---

