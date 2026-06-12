---
title: "External USB hard drive is not available after reboot"
date: 2012-06-20
forum: Hardware
---

### Post by tdn on 2012-06-20
I have a 3TB Seagate GoFlex drive attached to USB 3.0 port on Ubuntu Server 12.04 LTS. 
When I boot the computer after a poweroff, it come up just fine, however, if I then reboot, the USB disk does not show up in /dev nor does it show up in fdisk -l. It does show up af reboot on a Debian Squeeze server with USB 2 port. 

How do I make the drive "reconnect" on reboot in Ubuntu?


I can see the drive after reboot on lsusb and usb-devices. Output is here: [http://paste.adora.dk/P2431.html](http://paste.adora.dk/P2431.html)   
So I guess I have to send some kind of USB "wake up" command or something?

Any help will be greatly appreciated.

Thank you.

---

