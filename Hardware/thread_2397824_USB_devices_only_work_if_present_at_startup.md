---
title: "USB devices only work if present at startup"
date: 2018-08-03
forum: Hardware
---

### Post by christawney on 2018-08-03
I have recently updated from 16.04 to 18.04 on a ~09 Dell studio laptop.  My issue is that USB devices are not recognized unless present at boot.  If I swap in a thumb drive while Ubuntu is up and running the device will appear in lsusb, but not in the file manager.  A game controller was also tested to similar results.  This problem was not present in previous Ubuntu versions.  Any help would be much appreciated.

---

### Post by christawney on 2018-08-03
Update:

Further issues, possibly connected, have arisen.  Machine is running very hot, and htop shows processor is running at 95-100% on a process called: 

/lib/systemd/systemd-udevd

This issue is very similar to one demonstrated here:

[https://unix.stackexchange.com/questions/233247/why-is-systemd-udev-pegging-my-cpu](https://unix.stackexchange.com/questions/233247/why-is-systemd-udev-pegging-my-cpu)

The workaround suggested in that thread seems to have sated libmtp and brought CPU usage back to normal, however the USB issue remains.

---

### Post by christawney on 2018-08-07
Also, if I attempt "sudo apt-get upgrade" while the unsuccessfully mounted flash drive is in place,  the process is prevented by a lock file.  

"E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?"


I would assume that this is due to the failure of the system to mount the drive?

---

### Post by kurt18947 on 2018-08-10
Not an answer you're looking for but this sort of thing is why battle scarred Ubuntu veterans usually recommend a fresh install over an in-place upgrade.

---

