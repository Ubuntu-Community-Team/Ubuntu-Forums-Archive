---
title: "Strange USB total crashes"
date: 2005-09-11
forum: Hardware &amp; Laptops
---

### Post by theoburt on 2005-09-11
Hi, was hoping someone could help - I haven't found anything that similar to this yet.   
Am new to Ubuntu, installed for the first time today. However, when I had ANY usb device plugged in, the install boot cd would stick on the 'initialising USB 2.0' after the initial Ubuntu screen. I resolved this by disconnecting all USB devices. 

I need to use USB, as my only modem is a speedtouch ADSL one (which I see has been covered many times).  

However, Ubuntu boots fine etc, but the second I attach any USB device, everything freezes (mouse/keyboard) permanently and I have to do a hard reset. If I boot with devices in, it freezes as its initialising Hotplug stuff.

Any idea what it could be? 

I'm running an MSI 648 max mainboard, PIV 2.4, 1GB ram

Would be really grateful for any pointers
Thanks, Theo

---

### Post by mlomker on 2005-09-11
Are your devices USB 1.1 or 2.0?  You could try disabling the 2.0 driver.

You can do that by adding a line to the /etc/hotplug/blacklist file.  Just put **echi_hcd** in there.

---

### Post by theoburt on 2005-09-11
Thanks, will try...

---

### Post by theoburt on 2005-09-11
Still no joy... Put it in blacklist as you suggested (all my devices will happily function as USB 1.1). Turned off, plugged in modem, booted up, froze again on 'Starting HotPlug subsystem' exactly as before. 

I hope I can sort this out or its going to be a showstopper (I just don't know enough about linux at present to resolve this myself...). 

Any more ideas would be much appreciated!!! Cheers, T

---

### Post by theoburt on 2005-09-12
Does anyone have any ideas on this? Really don't know how to solve!
Thanks

---

### Post by mlomker on 2005-09-12
[QUOTE=theoburt]Does anyone have any ideas on this? Really don't know how to solve!
Thanks[/QUOTE]

It sounds like something unique with your system board.  Have you verified that you are using the latest BIOS firmware for your board?

---

### Post by theoburt on 2005-09-13
I flashed my BIOS, and after resetting the CMOS noticed some USB options in my BIOS I didn't notice before. A bit of tinkering fixed the problem, and after that the modem worked pretty easily..

So thanks a lot for your help!

---

