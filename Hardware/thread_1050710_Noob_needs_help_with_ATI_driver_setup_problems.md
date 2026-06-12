---
title: "Noob needs help with ATI driver setup problems"
date: 2009-01-25
forum: Hardware
---

### Post by TerryArnott on 2009-01-25
Hi all,

I am pretty new to Ubuntu (and linux in general) but am convinced it is the way to go, so WindowZ can go in the bin where it belongs as far as I'm concerned.... lol

I have installed on a couple of machines now, in the process of converting all the home machines, and the others have gone fine so far, BUT.....

On this machine which is fitted with a pair or ATI Radion 9xxx adaptors (one on board and one AGP) and a pair of Dell 15" LCDs, which ran 1280x1024 perfectly under windows, I can't get anything better than 800x600 on Ubuntu.

This is the same adaptor/LCD combo and I know the native rez for the LCD is 1280x1024, that's why I ran at that rez eventhough the adaptor is capable of 1600x1280+

I have gone through the various ATI drivers in the repositry with no luck, and now I have downloaded the linux driver from ATI from [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.28.8-inst.html]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.28.8-inst.html") but when I try to run it  following the instructions on the ATI web-page, I get this
```

terry@Black-Ubu:~/Desktop$ sudo sh ./ati-driver-installer-8.28.8.run
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.28.8...............................
................................................................................
................................................................................
................................................................................
................................................................................
................................................................................
......................................
-e ==================================================
-e  ATI Technologies Linux Driver Installer/Packager 
-e ==================================================
Detected configuration:
Architecture: i686 (32-bit)
X Server: unable to detect
Removing temporary directory: fglrx-install
terry@Black-Ubu:~/Desktop$ 

```

I don't know what to do about this, so if anyone could make some suggestions to help me get it up and running I would be a very happy little Ubuntuan.

I am not too worried about the dual screen set-up yet, I just really want to get the one running properly first so I can at least see a full web-page without having to scroll the screen around.

Thanks In Advance
Terry

---

### Post by TerryArnott on 2009-01-26
UPDATE:

I just removed and re-installed all the ATI drivers from the repository (for the 15th or 16th time) and it is now allowing 1024x768 and...... 1152x865 and 1360x768 ??????

I have never heard of 1152x865 before and there is still no sign of the illusive 1280x1024

Any ideas on how to get the official ATI driver installed would be appreciated.

Thanks
Terry

---

