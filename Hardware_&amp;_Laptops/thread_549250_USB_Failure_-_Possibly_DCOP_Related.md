---
title: "USB Failure - Possibly DCOP Related"
date: 2007-09-12
forum: Hardware &amp; Laptops
---

### Post by rmx.dave on 2007-09-12
Hello everyone. I posted regarding this issue in a different thread, only my original problem is fixed and now I am having a new one. 

I am running Ubuntu 7.04 (GNOME) on a Sony Vaio VGN-FJ170. Last week I installed BasKet and Amarok, both KDE apps. The apps worked fine, but Pidgin would not start, saying that there was a DCOP error. Also, all of my USB devices would stop working. I uninstalled both KDE applications and removed the KDE packages from my system. Pidgin worked again. 

But my USB ports keep disabling. When I boot the computer, they all work, and then out of the blue the computer will stall and everything USB dies, and sometimes my keyboard goes with it. This is a big problem because I have a USB mouse that I need and an external HDD that can't keep being disconnected like that. I'll disconnect all of the devices, and after 10 minutes or so they usually work again if I plug them back in. 

Finally, whenever I try to unmount removable volumes (flash drive or external hard drive) I get an error that says Cannot Unmount Volume. I don't know if this is directly related but it started happening at about the same time. 

Does anyone have any idea how I can fix this? I'm sorry for such a lengthy post, but I have not gotten any responses after a few tries and I would really appreciate help.

---

### Post by rmx.dave on 2007-09-12
Well, if its any help, this message is repeated in my debug.log file, and appears at the exact times that my USB support stops working. 

Sep 12 13:12:58 <hostname> kernel: [ 1475.164000] usb 5-3.3: usbfs: USBDEVFS_CONTROL failed cmd hald-addon-usb- rqt 192 rq 9 len 8 ret -71

Am I having a problem with HAL? I also tried booting into the other 386 kernel installed on my machine, and the issue is still happening.

---

### Post by rmx.dave on 2007-09-26
Okay, well it's been a week and the problem happens on and off. This stinks because I do a lot of writing, and whenever HAL decides to die, my keyboard freezes on the letter I last pressed, making a very long string of a single character (example: tesssssssssssssssssssssssssssssssssss...). I updated the kernel yesterday and now it even seems that the problem is more frequent. 

My debug log says that my USB devices are giving an error -71 seconds before they crash.

---

### Post by maxwell888 on 2008-05-07
I have this same problem my mouse will freeze with this in the logs

usbfs: USBDEVFS_CONTROL failed cmd hald-addon-usb- rqt 192 rq 9 len 8 ret -71

---

### Post by maxwell888 on 2008-05-22
I am still having this problem.  It makes Ubuntu unusable.  The mouse freezes and I have to reboot.  I tried all the solutions listed here and none of them worked.  [http://ubuntuforums.org/archive/index.php/t-499802.html](http://ubuntuforums.org/archive/index.php/t-499802.html)  if anyone has any suggestions or can direct me to any help it would be greatly appreciated.  I am using a Logitech LX7 wireless mouse.  


May 17 23:17:25 jimmy-desktop kernel: [ 7549.751577] usb 1-6: usbfs: USBDEVFS_CONTROL failed cmd hald-addon-usb- rqt 192 rq 9 len 8 ret -110

This is the error that comes up in the kernel.log file.  It repeats continuously sometimes for a hour sometimes minutes before the mouse will freeze.

---

