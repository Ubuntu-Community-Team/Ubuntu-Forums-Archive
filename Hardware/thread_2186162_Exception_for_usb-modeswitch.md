---
title: "Exception for usb-modeswitch"
date: 2013-11-06
forum: Hardware
---

### Post by maspai.mail on 2013-11-06
usb-modeswitch makes easier to use USB modem. But looks like it works for any USB device, including my mobile so that I can't access the memory card because it's changed to serial device by usb-modeswitch.
When using Debian without usb-modeswitch package installed, the memory card can be accessed as storage.
So, I wonder if there's any kind of "exception" for usb-modeswitch so it doesn't turn my mobile to serial device.
Thanks for help.

---

### Post by varunendra on 2013-11-06
Hi, welcome to the forums !

You can use the "/etc/usb_modeswitch.conf" file to disable modeswitching (globally) when you connect your mobile phone. Change the value of "DisableSwitching=" from "0" to "1". To do this via command line -
```
sudo sed -i '/^DisableSwitching/ s/0/1/' /etc/usb_modeswitch.conf
```

Perhaps you can also add just a single device as an exception, but I'll have to do some searching to figure out how to do that. One possible way maybe to simply delete (or move) the configuration file where the usb_modeswitch reads the target device mode from. These files are supposed to be located in "/usr/share/usb_modeswitch/" directory, but in default Ubuntu installation, there is just a compressed .tar.gz archive of these files on that location.

If you are interested in doing some experiments, post back the output of "lsusb" after doing the above suggested 'global' change and _afterwards_ connecting the mobile.

**PS:**
All the mobile phones I have seen so far ask the user about which mode to connect in - storage, modem or something else (if it supports another mode). Most of them also have a setting to permanently set one of these modes as default. Please check if your mobile has such a setting.

---

### Post by maspai.mail on 2013-11-06
Varun, thanks for the clue.

I find configPack.tar.gz file in /usr/share/usb_modeswitch/ folder, and there's a file in it named matching the vendor-product code of the mobile found by lsusb (0e8d:0002). I open the file and comment (#) 3 lines of code there - consisting 3 variables: TargetVendor, TargetProductList, and MessageContent. Then I replug the mobile and this problem is solved :-).

Thanks once again.

---

### Post by varunendra on 2013-11-07
Great ! And thanks for the confirmation that the tar.gz archive is indeed the database for usb_modswitch. Until now, I had doubts. :)

---

