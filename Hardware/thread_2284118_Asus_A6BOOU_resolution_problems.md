---
title: "Asus A6BOOU resolution problems"
date: 2015-06-27
forum: Hardware
---

### Post by BADGER.BRAD on 2015-06-27
Hello,
I have a problem after a new install of Lubuntu on the Asus A6B00U.The only resolution option I have is 640X480 which means I never see the full page . I have tried various options for drivers but none seem to work (most likley due to my lack of understanding) I could do with some one giving me a step by step ,press this type that bit of help. The graphics card apears to be an sis 661/741/760 .

Many thanks for any help you can give.


Brad

---

### Post by dino99 on 2015-06-27
support for sis hardware has been removed; we only can try some oldish driver found via some ppa.
the required driver is named: xserver-xorg-video-sis
and can be found here: [https://launchpad.net/~dtl131-deactivatedaccount/+archive/ubuntu/mediahacks](https://launchpad.net/~dtl131-deactivatedaccount/+archive/ubuntu/mediahacks)
select your ubuntu version, update the repo, install the driver, and deactivate the ppa, then update again

---

### Post by Yellow Pasque on 2015-06-27
@dino99: That is/was my PPA. The version of the sis driver in it was for older Ubuntu releases (before Trusty/14.04).
Ubuntu 14.04 has the sis driver available in the default repositories, though a couple reports I've seen make me wonder whether it works with the newer Xserver (1.16.x) found in Ubuntu 14.04**.2**

At any rate, you should be able to get a better resolution than 640x480 without using the sis driver by forcing the generic vesa driver. Make an /etc/X11/xorg.conf file with following contents:
```
Section "Device"
        Identifier      "Configured Video Device"
        Driver         "vesa"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection
```

---

