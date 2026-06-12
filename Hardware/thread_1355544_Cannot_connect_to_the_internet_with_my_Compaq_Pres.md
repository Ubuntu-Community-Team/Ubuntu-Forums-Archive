---
title: "Cannot connect to the internet with my Compaq Presario V2000"
date: 2009-12-15
forum: Hardware
---

### Post by Phillip Bromley on 2009-12-15
I was going to post this in the Networking and Wireless forum, but I learned that this issue is specific to the Compaq Presario V2000, so it's more laptop related.

My internet works fine on Windows 7 Ultimate (32 bit), I always connect via the built-in wireless, and never had a problem.

Just this morning I partitioned my hard drive and installed Ubuntu 9.10 to test it out. Everythig worked fine, except the internet! The Presario V2000 has a button that toggles the WiFi radio, it lights up when the WiFi radio is turned on. After several press of this button it never lit up.

I searched around on the internet, and found that this has something to do with the firmware, but all the fixes I tried didn't work.

I haven't tried connecting to the internet via cable instead of wirelessly, but that's not what I'm trying to accomplish. Somebody please help me get my wireless working! I've been trying all day, to no avail. :frown:

---

### Post by Phillip Bromley on 2009-12-15
Bump.

I've now got my computer hooked up to a wired connection, and it works fine, but the wireless still doesn't work. Please help me!

---

### Post by Phillip Bromley on 2009-12-16
Bump.

Must... Keep... Bumping!!!

---

### Post by modemsutra on 2009-12-16
You probably need the wireless card driver, probably you can use the original windows driver using ndis wrapper

---

### Post by Phillip Bromley on 2009-12-16
After browsing around, I now know I need the driver, but all attempts to install it (through various methods I found here) haven't worked. I'll play around with ndiswrapper and see what happens.

---

### Post by batterybaby on 2009-12-16
the wireless card driver cannot solve the problem ,yet?  you can turn to the seller who sold the card to you for help.he might be  more professional.

---

### Post by Phillip Bromley on 2009-12-16
I have been offered a solution from another forum, which I will try out later this morning and see how it goes.

---

### Post by Kutakizukari on 2010-03-12
Are you still having this problem? When I installed Ubuntu 9.10 I left a wired connection in and after reboot the update manager found everything and installed it automatically.

Maybe connecting with a wired connection and getting all the updates will help as this solved a lot of problem with this type of laptop.

---

### Post by viper250 on 2010-03-12
your wireless may not be supported at all by linux ! some network cards were made for windows only 
check out the hardware compatability list for your distro odds re good that you will find a wireless card that works with your distro

---

### Post by Charles07 on 2010-03-12
Betcha he needed the Broadcom BCM*wireless driver w/ the bw43XX firmware.

---

### Post by Charles07 on 2010-03-12
b43fwcutter

---

### Post by Charles07 on 2010-03-12
Sorry, not trying to post pad:

[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

There.  Done.

---

### Post by bhatchfield on 2010-03-14
I too have an hp presario on ubuntu 9.10. I got the wireless light to come on using the update feature but can not connect unless I use a wired connection.

---

### Post by Charles07 on 2010-03-16
[http://bcm43xx.berlios.de/](http://bcm43xx.berlios.de/)

[http://packages.ubuntu.com/jaunty/b43-fwcutter](http://packages.ubuntu.com/jaunty/b43-fwcutter)

[http://packages.debian.org/stable/b43-fwcutter](http://packages.debian.org/stable/b43-fwcutter)

---

### Post by Charles07 on 2010-03-16
One more:

[http://onlyubuntu.blogspot.com/2009/07/howto-install-and-enable-broadcom.html](http://onlyubuntu.blogspot.com/2009/07/howto-install-and-enable-broadcom.html)

---

