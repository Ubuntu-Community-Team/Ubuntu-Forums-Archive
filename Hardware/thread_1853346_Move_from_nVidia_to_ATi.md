---
title: "Move from nVidia to ATi"
date: 2011-10-02
forum: Hardware
---

### Post by wmdvanzyl on 2011-10-02
Hi All.

I am swapping out my nvidia 8800gt (which is giving problems) for an ati 4870.

I was wondering what the process is for doing this? Do i need to change anything before i do the swap?

Kind regards,
wmd

---

### Post by coffeecat on 2011-10-02
If you've installed the proprietary nvidia driver either from "Additional Drivers" or from a downloaded file from the nvidia site, you need to uninstall it. Once you've done that, simply close down, swap your cards and reboot. The system will autodetect the ATI card and load the open source ATI driver.

If you have been using the default open source nouveau driver for the nvidia card, simply close down, swap cards, boot up and enjoy! :) 

I went from nvidia to ATI. Never regretted it! :wink: By the way, let us know how you get on with that particular card. It's useful to know.

---

### Post by wmdvanzyl on 2011-10-02
Hi Mr Cat.

Thanks for the reply. Shamefully, i can't remember which drivers i used for my card. Right now i am forced to use the onboard card (i think a 3-series ati card) for gfx as i am typing this from windows... terrible. Anyway, the problem is that i can't seem to get into ubuntu to do the changes. I can get to grub and select ubuntu and even see the ubuntu loading screens, but come time to give me control there is only a blank screen on standby mode. Any suggestions as to how to remedy this unhappy scenario? I don't mind using live-cd's etc as i used to use gentoo before ubuntu. My pain threshold is pretty high - not that i am criticizing gentoo. It is a wonderful OS and helped to one varsity degree... but i have moved on. :-)

Getting back to my point: any suggestions? Is there a temporary bootstrap solution to getting me back into ubuntu to make these changes (if necessary)?

*** edit: Here is a screenshot of my drivers - i see what looks to be both? What does this mean?

[IMG]http://www.modh.co.za/nvidia_drivers.png

---

### Post by coffeecat on 2011-10-02
I've got an onboard HD3000 graphics and I couldn't get a desktop even with a live CD, so I've always used a PCIe card with this machine - first a nvidia 8400GS and now an ATI HD5450. Anyway, try booting in recovery mode and choose drop to root shell. It doesn't matter whether you go for the "with networking" or not. Once you have a '#' root console prompt, try this:

```
apt-get purge nvidia*
mv /etc/X11/xorg,conf /etc/X11/xorg.conf.backup
```

That will get rid of anything nvidia related, and then you should be able to boot with your PCIe HD4780 card. Don't bother with the onboard graphics. If your experience is anything like mine, you won't want to.

---

### Post by wmdvanzyl on 2011-10-10
Followed your advice. Removed the nvidia drivers and booted up with new card in palce. Everything worked perfectly. Looking for a way to really test the card under ubuntu. Want to see how the drivers perform compared to windows.

Any suggestions?

---

