---
title: "Nvidia Driver Problem"
date: 2008-04-24
forum: Hardware
---

### Post by FatmanC on 2008-04-24
Hello, i have just upgraded to hardy heron. I have the nvidia restricted driver installed and my current screen resolution is 1024x768. when i was running Gutsy G. i was able to configure it to 1280x768 through means that i don't remember. If i chouse 1280x760 on the resolution menu under adminstration, i have to pan left and right to get around. Also, during my login page, the screen is expanded to the point where i can't see the username prompt. Does anybody know how i can configure it back to 1280x768. Also, i how do i check to see what version i am running, regular or 64bit version.

Thanks

---

### Post by overdrank on 2008-04-24
> **FatmanC said:**
> Hello, i have just upgraded to hardy heron. I have the nvidia restricted driver installed and my current screen resolution is 1024x768. when i was running Gutsy G. i was able to configure it to 1280x768 through means that i don't remember. If i chouse 1280x760 on the resolution menu under adminstration, i have to pan left and right to get around. Also, during my login page, the screen is expanded to the point where i can't see the username prompt. Does anybody know how i can configure it back to 1280x768. Also, i how do i check to see what version i am running, regular or 64bit version.

Thanks

Hi and first to see if you are using 64 bit use this command ```
uname -a
```
Example
@overdrank-desktop:~$ uname -a
Linux overdrank-desktop 2.6.24-16-generic #1 SMP Thu Apr 10 12:47:45 UTC 2008 x86_64 GNU/Linux
As for the graphics you can install nvidia-settings either by synaptic manager or the terminal ```
sudo apt-get install nvidia-settings
```
Then you can use them to adjust your resolution. ```
gksudo nvidia-settings
``` Hope this helps and good luck!

---

### Post by FatmanC on 2008-04-24
thanks for your help.

what i had to do was uninstall the nvidia driver, reboot and since i have my laptop dual boot, i went into recovery mode and had it check for the hardware again. I then reinstalled the nvidia driver under restricted hardware under adminstration. rebooted. And went into nvidia settings and everything went back to normal. Thanks for the help

---

