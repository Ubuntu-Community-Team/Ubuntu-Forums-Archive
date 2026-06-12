---
title: "Bluetooth crashed after trying to copy pairing keys from windows to ubuntu"
date: 2017-05-23
forum: Hardware
---

### Post by nedmaj on 2017-05-23
Hi guys,

I am dual booting Ubuntu Gnome 17.04 and Windows 10 and I  have a bluetooth Microsoft Designer Keyboard and Mouse. My machine is  an Intel NUC6i5SYH.

I have followed the steps described here  ([https://ubuntuforums.org/showthread.php?t=1479056](https://ubuntuforums.org/showthread.php?t=1479056)) to copy pairing keys  from windows to ubuntu. I found actually 3 keys, copied them from  Windows Registry to Ubuntu /var/lib/bluetooth.../info files from each  device.

The procedure didn't work so after restarting the machine  I thought (my mistake) it had something to do with  /var/lib/bluetooth.../cache folder from each device, so I deleted them.  After doing so bluetooth completely stopped working. The icon under All  Settings disappeared and when clicking on the bluetooth icon from the  task bar it tells me "No device found. Plug a usb dongle to use  bluetooth" like my machine had no bluetooth at all. So I reinstalled all  the packages related to bluetooth. After reinstalling package  gnome-bluetooth, the icon under All Settings appeared again, but I was  still getting same message "No device found...". Also tried a apt-get  dist-upgrade and bluetooth still not working.

For my dispair,  after booting under Windows, I realized bluetooth was not working under  it. Device management shows a device error. Even after reinstalling the  driver it remains with error, like my machine had no bluetooth at all. I  have disabled bluetooth under BIOS, restarted the machine, and enabled  it again and the problema remains.

Now I have no bluetooth at all.

Any ideas?

Thanks in advance.

---

