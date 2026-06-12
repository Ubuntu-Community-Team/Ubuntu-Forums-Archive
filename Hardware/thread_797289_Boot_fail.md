---
title: "Boot fail"
date: 2008-05-17
forum: Hardware
---

### Post by teH2SO4 on 2008-05-17
Hi all

I was recently trying to install Compiz fusion on my Asus laptop, and noticed some settings seemed to not be working...so I went and found the "correct" driver for my machine, which is a 945 chipset.

After I changed to the "correct" driver, I rebooted my machine because it required me to log out.

I am running Gusty Gibbon 7.10, and had just recently updated to 8.04 (which seemed to make my machine run slower...but that's another issue altogether)

Now it just gets stuck saying the following:

*Starting anach(h)ronistic cron anacron       [ok]
*Starting deferred exectuion scheduler atd    [ok]
*starting periodic command scheduler crond    [ok]
*Checking battery state...                    [ok]
*Running local boot scripts (/etc/rc.local)   [ok]

And it stops there. I would use the recovery command line mode to revert back to the old driver but I'm not sure how to do that...could someone please help out, like np.

Thanks a lot.

---

### Post by EXCiD3 on 2008-05-18
First of all, its always better to do a fresh install when you are moving to a new version. Usually something breaks, wifi, sound and video cards are the most common.

If you know the name of the driver you can boot into recovery mode, login and do ```
sudo nano /etc/X11/xorg.conf
``` and change the Driver "<driver>" section for the video card. Save and then try starting the xserver with "startx". You can always change <driver> to vesa which is compatible with any video card and will at least get you into the xserver for the time being.

---

