---
title: "INTEL Braswell HDMI issue : Display blank after power cycling TV"
date: 2015-12-02
forum: Hardware
---

### Post by aniketvb on 2015-12-02
I have Kubuntu 15.10 installed on an ASRock Beebox N3150. It has the new intel Braswell N3150 CPU. I have an LG TV connected to the Beebox via HDMI. I get audio and 1080P video perfectly and Kubuntu generally works very well, but I have the problem where if I turn off the TV and turn it back on, the display is blank. 

then if I use xrandr via SSH to turn on the display, it turns on the display but KDE is frozen. 

So, basically the problem is , how do we tell Kubuntu to ignore the TV turn off event!! I have searched around and tried a few solutions , like adding option "UseHotplugEvents" "False" in the xorg.conf file, but it seems that is Nvidia specific option and Xorg.0.log tells me that it ignored the option. 

Thanks

---

### Post by aniketvb on 2015-12-03
It turned out that it was not the display driver, but KDE that was freezing when monitor/TV was turned off. I am now able to have the session running while power cycling the TV. So the original problem can now be marked as solved. 

As a side note, I am not having issues with suspend to RAM. It looks like suspend works fine as syslog seems to show that the system suspended fine, but when I press keys on the keyboard to resume, the power light comes on and the HDD makes a little noise, but the system is frozen totally. after a hard reset, looking at syslog , there is nothing in the log after the suspend event, and I see the logs about the bootup only after that.

---

### Post by Bucky Ball on 2015-12-04
Please mark this thread as solved and post a new one for any further issues (see first link in my signature). This will improve your chances of support as your new issue has nothing to do with the title or topic of this thread.

Snipping the last part of your last post and posting that in the first post of the new thread with a descriptive title should just about do it. Good luck. :)

---

