---
title: "5min freeze upon startup/login, device descriptor error in dmesg"
date: 2013-03-28
forum: Hardware
---

### Post by Anaphylaxis on 2013-03-28
I have been having my dad on ubuntu since way back in 2008. 4 weeks ago, I reinstalled ubuntu to upgrade from 10.04 to 12.04. 

A week afterwards, the screen froze at random, and seemingly always in conjunction with connecting/disconnecting a garmin gps usb unit, and attempting to upload from the device. 
Upon every startup after shutdown -h, the pc now hangs several minutes after auto-login, the pointer cannot be moved. 

Here is the output of dmesg on [pastebin]("http://pastebin.com/DEve5JqK").

As you can see, there are a lot of ```
device descriptor read/8, error -110
``` errors, seemingly related to the usb ports. I didn't change anything on the computer before this error occured. The error occurs even without anything but the keyboard/mouse plugged in. 
I then tried to add another USB PCI controller, and plugged the USB cables into that. Didn't fix the issue. (I also at the same time added a new hard drive, mentioned for completion). 

I am a little stuck, and would like some input on where the problem might be, where I should look.

---

