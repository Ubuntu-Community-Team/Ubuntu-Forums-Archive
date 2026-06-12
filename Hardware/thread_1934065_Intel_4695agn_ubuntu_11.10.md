---
title: "Intel 4695agn ubuntu 11.10"
date: 2012-03-01
forum: Hardware
---

### Post by chrissodey on 2012-03-01
Hello All,

I am trying to get my Intel 4695agn wireless card to work with 11.10.  It works great with 10.04LTS, but unfortunately it doesn't work with 11.04 or 11.10.  I have researched the iwlwifi drivers and have not found a fix.  My laptop is a Lenovo Y710 with out a hardware switch to turn on the wireless.  The fn+F5 is the software switch and that will toggle on the wireless device for a second and then it will turn off again.  I read on some sites there were issues with the new Kernal, but then other sites I read have this device working great with 11.10.  Does anyone have any ideas?  

Thanks

---

### Post by ahallubuntu on 2012-03-01
I'm surprised it works in 10.04 but not in 11.04.  11.04 does use a newer kernel but not the 3.0 kernel used in 11.10, where I'd expect more problems.  This is a really old wireless card and has been supported in Linux for a long time.

Are you saying it doesn't work on the live CD of 11.04 or an install of 11.04?

In 11.04, open a terminal.  What does

sudo lshw

say?

How about

dmesg | grep iwlagn

?

---

### Post by chrissodey on 2012-03-02
Thank you for your reply.  In 11.04 the wireless doesn't work on the live version or the full install.  I have tried dmesg | grep iwlagn and rebooted and it didn't bring back the wireless.  It shows up as an active card, but will not connect or turn on.  When I view the driver profile with the terminal it shows up correctly, just will not turn on much like I had a hardware switch turned off.  I know this card has been supported since I think version 8.  At this point I am hoping that version 12.04 will fix the issue.  I need to find the beta when it is released and test it.

---

