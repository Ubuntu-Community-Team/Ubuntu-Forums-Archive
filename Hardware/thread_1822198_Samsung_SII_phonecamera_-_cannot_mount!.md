---
title: "Samsung SII phone/camera - cannot mount!"
date: 2011-08-10
forum: Hardware
---

### Post by frankh on 2011-08-10
I cannot mount my Samsung SII phone/camera in Ubuntu 11.

It shows up in nautilus, as a "SAMSUNG_Android" camera device.

lsusb shows the following:

[FONT="Courier New"]Bus 003 Device 004: ID 04e8:6860 Samsung Electronics Co., Ltd[/FONT]

However, when I click on the device in nautilus:
[FONT="Courier New"]
Unable to mount location
Error initializing camera: -1: Unspecified error[/FONT]

There are very little info on this to find on the web. I've tried a couple of "hacks", modified, for some other Samsung devices like Galaxy Tab, but none works. The device doesn't even show up under /dev

Anyone got any ideas? Or is the fact of the matter that an Android (Linux-based) device will not work in Linux/Ubuntu, while Apple's iPhone will?

---

### Post by CatKiller on 2011-08-10
I don't know if the S II is the same, but with the Galaxy S there's a setting to say that you haven't been lobotomised and so you aren't going to use Samsung's POS Windows-only software. Then it works a treat.

On the Galaxy S, the setting's at Settings -> Wireless and network -> USB settings -> Mass storage.

---

### Post by s8472 on 2011-08-13
Thanks.  This also works for GS2.

---

### Post by dez93_2000 on 2012-06-04
not in galaxy S3 though - the settings link is gone.

---

### Post by lile001 on 2012-06-10
The method on this page worked for me, with a Samsung Galaxy SII.  Really simple:

[http://www.tuxtrix.com/2011/07/how-to-access-samsung-galaxy-s-ii-usb.html](http://www.tuxtrix.com/2011/07/how-to-access-samsung-galaxy-s-ii-usb.html)

```
1. On Galaxy S II , go to
Menu -> Settings -> Wireless and network -> USB utilities 
2. Click on Connect Storage to PC
3. Connect the USB cable to your pc.
4. Click on Connect USB storage
5. Use your file manager to install/copy/paste.
6. Once finished, click on Disconnect storage from PC to disconnect and unmount drive from Ubuntu.
```


Only problem is, you have to remember to do this every time you plug in the phone, and remember to unmount the internal and SD card memory from Linux. 

I tried a bunch of other very geeky methods recommended elsewhere, and none of them worked for my phone.  This included a program called gMTP, which didn't seem to find the phone at all.

---

### Post by lile001 on 2012-06-10
> **lile001 said:**
> The method on this page worked for me, with a Samsung Galaxy SII.  Really simple:

[http://www.tuxtrix.com/2011/07/how-to-access-samsung-galaxy-s-ii-usb.html](http://www.tuxtrix.com/2011/07/how-to-access-samsung-galaxy-s-ii-usb.html)

```
1. On Galaxy S II , go to
Menu -> Settings -> Wireless and network -> USB utilities 
2. Click on Connect Storage to PC
3. Connect the USB cable to your pc.
4. Click on Connect USB storage
5. Use your file manager to install/copy/paste.
6. Once finished, click on Disconnect storage from PC to disconnect and unmount drive from Ubuntu.
```


Only problem is, you have to remember to do this every time you plug in the phone, and remember to unmount the internal and SD card memory from Linux. 

I tried a bunch of other very geeky methods recommended elsewhere, and none of them worked for my phone.  This included a program called gMTP, which didn't seem to find the phone at all.
[http://www.humans-enabled.com/2011/12/how-to-fix-samsung-galaxy-nexus-mtp.html](http://www.humans-enabled.com/2011/12/how-to-fix-samsung-galaxy-nexus-mtp.html)

I DID, however, install a bunch of MTP stuff as recommended here:
[]("http://www.humans-enabled.com/2011/12/how-to-fix-samsung-galaxy-nexus-mtp.html")  It didn't work for me, but it was installed when I did the above setting on the phone, so if the simple way doesn't work, this MTP stuff may be necessary for you.  I kind of think it is not necessary, but your mileage may vary.

---

