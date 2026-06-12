---
title: "Toshiba Portege M400"
date: 2007-02-26
forum: Hardware &amp; Laptops
---

### Post by Eagleon on 2007-02-26
Hi everyone,

This is my first post in the ubuntu community. I am very new to Ubuntu, and I love it. In fact I am never going back to anything else. I had used ubuntu on and off using the live CD, but the experience is wild when you actually install it and try to use it for your daily activities. Ubuntu ROCKS! Now, because I never want to go back to any other operating system, I was wondering how new hardware support can be requested for ubuntu. I have a Toshiba M400 tablet PC, and it has a lot of features that I can't use in ubuntu. Sadly, Toshiba only has software for Windows. Some of the features I can't use are the special keys, biometric fingerprint scanner, HDD protection, and several others. I really wish I could take advantage of those features. Also, this is a business laptop, so I think a lot of people who own this laptop might like having such support as well. By the way, does ubuntu take advantage of dual core processors? I got the pen to work so I am really happy about that. Any advice will be greatly appreciated, and GO UBUNTU!!

Thanks,
Antony

---

### Post by jharbert on 2007-02-27
[I created a howto for basic tablet setup here.]("http://ubuntuforums.org/showthread.php?p=2219293")  I'm not sure how to handle the fingerprint reader (my computer doesn't have one), but it should help with a few other things.  I'm glad you like Ubuntu.

---

### Post by moldy86 on 2007-03-01
i have a a135 series toshiba.. I tried everything i could find via google to get the finger print reader to work.. gave up..

but then it kept bugging me and found thinkfinger... Its made for ibms but works with sonys and toshibas. the site gives you everthing you need in the 2 documents on how to build it from source then install it which is very easy.. make sure to install mods into /etc/security.
i had a little problem with the tf-tool. just move the lib its asking for to /usr/lib and all goes by great! any questions just pm me k

[http://thinkfinger.sourceforge.net/download.php](http://thinkfinger.sourceforge.net/download.php)

kevin kricfalusi

---

### Post by juanfi on 2007-03-02
Lets see. I have the same model. And I have to say there are some glitches, but nearly everything is working.

Thinkfinger takes care of the fingerprint reader. Load the toshiba utils for support of the extrafeatures (buttons, hotswap of slimbay, do apt-cache search toshiba). The stylus works nicely. Same for the wireless, graphic card, sound, ethernet card, pad. Both cpus are running nicely.

The basic instructions can be found in:
[http://www.math.upenn.edu/~vincentb/UbuntuPortege.html](http://www.math.upenn.edu/~vincentb/UbuntuPortege.html)

I only have some issues with the rotated screen, and the wireless card being slow to respond with network manager. Also I do not know how to switch the resolution and the monitor (external/internal) on the fly.

Enjoy

Juan

---

### Post by Eagleon on 2007-03-02
Thank you jharbert, moldy86, juanfi for your help! I really appreciate the information. This is extremely useful information for me. :) I wonder if the hot-keys on the tablet panel will work.

---

### Post by kiwioperator on 2007-10-27
My M405 crashes with any movement. I have dual boot and on the XP side there is a HDD protection driver and there is no problem but not on the Gutsy side.

Anyone know anything about this?

Kiwi

---

