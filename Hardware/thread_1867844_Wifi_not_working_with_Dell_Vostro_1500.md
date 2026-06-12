---
title: "Wifi not working with Dell Vostro 1500"
date: 2011-10-23
forum: Hardware
---

### Post by isaac12345 on 2011-10-23
Hi guys,

I am a recent ubuntu convert and found 11.04 to be very good. But since the upgrade to 11.10 I have been quite dissatisfied. Apart other little buggy things like the trackpad stopping to work etc, my wifi has stopped working at all. With 11.04 it didnt work out of the box but I downloaded the b43 firmware and was then able to get it up and running. With 11.10, the OS recognises the chip and suggests a driver. I installed that driver but the wireless doesnt work. I tried the way I got the wireless working on 11.04 but in vain. Could someone please help me out? 

Thanks!

---

### Post by isaac12345 on 2011-10-23
Found a solution at [http://ubuntuforums.org/showthread.php?t=1859668](http://ubuntuforums.org/showthread.php?t=1859668)

If you've activated the Broadcom STA additional driver then remove it  (System Settings => Additional Drivers = STA => remove)

Restart your computer.

Click on the Connection icon.
If  it says it's turned off via hardware then you're on a Dell laptop or  something similar so use the Fn-F2 (or whatever yours is) key and have  another look

If it says the firmware isn't loaded then proceed

Connect to the net via ethernet

sudo apt-get update
sudo apt-get install b43-fwcutter
sudo apt-get install firmware-b43-installer

Click the Connection icon again and you should see Wireless Networks as per normal

---

