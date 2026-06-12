---
title: "right click not working on Lenovo Y480 w/12.04"
date: 2012-06-29
forum: Hardware
---

### Post by prcdslnc13 on 2012-06-29
I recently installed 12.04 on my laptop and while my touchpad works and mumulti finger scroll works correctly, im unable to right click. I tried uninstalling the synaptic drivers and now it doesn't work at all ha ha.  
Has anyone had any issues like this? Obviously i need to reinstall the drivers. But how can i get my right click to work.

---

### Post by prcdslnc13 on 2012-07-01
no one?

---

### Post by paniti on 2012-07-19
Original post solved thread using this link : [http://ubuntuforums.org/showthread.php?t=1388164](http://ubuntuforums.org/showthread.php?t=1388164)
 with code:
sudo su
echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe
reboot

---

### Post by berturion on 2012-11-02
> **paniti said:**
> Original post solved thread using this link : [http://ubuntuforums.org/showthread.php?t=1388164](http://ubuntuforums.org/showthread.php?t=1388164)
 with code:
sudo su
echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe
reboot

Thank you very much ! That worked very well for my Lenovo Z580 with  Ubuntu 12.04 LTS as well.
I just copy-pasted the 3 commands you gave and after reboot my right click worked perfectly !
Hope this helps for other lenovo z580 users :)

---

