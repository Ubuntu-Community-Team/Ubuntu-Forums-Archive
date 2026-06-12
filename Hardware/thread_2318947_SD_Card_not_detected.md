---
title: "SD Card not detected"
date: 2016-03-30
forum: Hardware
---

### Post by Pietro_ on 2016-03-30
Hello everyone,

I'm a new Ubuntu user, with a very limited experience in UNIX systems. I recently installed Ubuntu 14.04 4 LTS on my[ ASUS VivoBook e200ha]("https://www.asus.com/Notebooks/ASUS-Vivobook-E200HA/specifications/"). The installation went without problems. I already installed the WiFi drivers because the device wasn't working out of the box.
Now I'm trying to fix the issues with the microSD card reader, which is critical for me (I really need to get it working since the laptop only has 32GB of internal MMC memory).
When I plug the card in nothing happens.[B] The card reader with the same SD card works perfectly under Windows 10.
[/B]
What I did so far:

[LIST]
[*]Tried removing and re-inserting the card, and reading 'dmesg' from the terminal. No message appeared; 
[*]Probably foound the device ID with 'lsusb':
[IMG]http://s14.postimg.org/l1qdf4dkh/Screenshot_from_2016_03_30_21_00_27.png[/IMG] 
[*]Looked up the device ID in the [usb device ID repository]("https://usb-ids.gowdy.us/read/UD/0bda"), nothing found; 
[*]Tried doing 'sudo modprobe rtsx_usb', still nothing. 
[/LIST]

Could please someone point me to a solution? This is crucial for my experience on Ubuntu!
Thank you very much in advance.

Pietro

---

### Post by tihomir-tsvetcov on 2016-08-04
Hello,

does anyone found a solution to this problem? 

I tried adding  ```
options sdhci debug_quirks=0x8000
``` into ```
/etc/modprobe.d/sdhci.conf
``` but without any luck. This should work for ASUS-X205TA on Debian, but maybe the card readers are different.

---

