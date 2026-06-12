---
title: "Patch USBHID driver"
date: 2012-07-28
forum: Hardware
---

### Post by Gecco3 on 2012-07-28
Hi,
I'm trying to connect a Yamaha MOX6 directly to my computer (running Ubuntu Studio 12.04)  via a USB cable.  This worked with the Yamaha driver on my Mac.  However, Yamaha doesn't have a driver for Linux.  It also seems that only a handful of people have tried to use the MOX6 with Linux.  The only coherent information on this I could find was on this page: [http://www.spinics.net/linux/fedora/alsa-user/msg10565.html](http://www.spinics.net/linux/fedora/alsa-user/msg10565.html).  The page says that I need to apply a patch (which they supply on the page) to the USBHID driver.  However, I cannot figure out what file to patch, or even if this patch (originally for Fedora) will work.
If someone could please help me out and either tell me how to patch this driver or if there is a different driver I should try to use, that would be great.
Thanks in advance,
-Gecco3

---

### Post by dazastah on 2012-08-14
Hey Gecco,
I've got a mox6 too and stumbled across the exact same issue.. There's some other pages [http://www.phoronix.com/scan.php?page=news_item&px=MTA0ODA](http://www.phoronix.com/scan.php?page=news_item&px=MTA0ODA) that mention that the mox6/8 has usb support but i'm not sure how to get it working either... If you find out please post back!!! 
And vice versa if i do...

---

### Post by dazastah on 2012-08-19
Apparently the diver for mox is included in the latest alsa drivers... But still no go.. I'm gonna give ubunutu studio a go and see if it works right out of the box...

I updated the firmware and still get the same issue...  (haven't tried studio yet.)

---

### Post by Gecco3 on 2012-08-23
I have been using ubuntu studio, and it hasn't been working.  I don't know if I'm using the latest version of ALSA, but unless there's been an update within the past few weeks, I probably am.

---

### Post by dazastah on 2012-09-02
yeah i installed a fresh lubuntu and installed and updated alsa and jack to latest versions... But have no luck.. I also updated the firmware in the mox to see if that was the issue but still no go.. when typing sudo lsusb -v  it shows the yamaha is there. But it wont start the usb audio driver(i understand it uses the standard usb-audio driver?)

I tried ubuntu studio live to see if that would work and it didn't.. 

Hopefully someone will have some luck or info.. Its weird because the latest version of alsa states on the site it supports yamaha mox ... I;ll try and tinker more and see if i can come up with something...

---

### Post by lauas on 2013-01-08
Has someone tried to hook up the MOX6 via a compatible MIDI interface instead of using the USB?
If so, and if it Works, is it possible to have the same funcionality as in Windows/MacOSX yamaha's software?

---

