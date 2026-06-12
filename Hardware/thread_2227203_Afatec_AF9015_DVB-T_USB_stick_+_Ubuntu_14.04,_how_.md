---
title: "Afatec AF9015 DVB-T USB stick + Ubuntu 14.04, how to enable driver? Option grayed out"
date: 2014-05-31
forum: Hardware
---

### Post by Janiporo on 2014-05-31
Can you see my problem? I can not tick proprietary driver on (Manual one does not work), it is grayed out, any ideas how to "unlock" this option?

[IMG]http://kuvaton.com/k/yjiu.jpg[/IMG]

Tags: This device is using a manually-installed driver. Continue using manually installed driver. This device is not working.

---

### Post by Janiporo on 2014-06-03
I googled around and this helped me --> [http://askubuntu.com/questions/447521/how-do-you-use-ubuntu-drivers-common-or-software-properties-in-the-command-line]("http://askubuntu.com/questions/447521/how-do-you-use-ubuntu-drivers-common-or-software-properties-in-the-command-line--") 
I did the following, and it solved everything:
```
sudo apt-get install linux-firmware-nonfree
```

Here is what the Additional Drivers window looks now.
[IMG]http://kuvaton.com/k/yjxp.jpg[/IMG]

---

### Post by tea for one on 2014-06-03
Another solution is to download the driver from [http://www.otit.fi/~crope/v4l-dvb/af9015/af9015_firmware_cutter/firmware_files/4.65.0/](http://www.otit.fi/~crope/v4l-dvb/af9015/af9015_firmware_cutter/firmware_files/4.65.0/)

Then install the driver in /lib/firmware

---

