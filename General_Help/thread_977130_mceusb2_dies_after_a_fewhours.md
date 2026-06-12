---
title: "mceusb2 dies after a fewhours"
date: 2008-11-09
forum: General Help
---

### Post by phat_penguin on 2008-11-09
So I admit that I am totally new to Ubuntu and I have searched the forums, but have not found this question.  If it has already been touched on then point me in the right direction and I will gladly RTM.

I installed Mythbuntu 8.10 a few nights ago.  It's really nice, I have run myth on Fedora and Suse and for configuration mythbuntu is by far the most complete out of the box.

Only a few little annoyances remain and I think I can figure out most of them but there is one that has me totally baffeled.

Right after a reboot or a restart of lirc the irblaster seems to work perfectly, then somewhere less than 16 hours later the blaster stops working. The receiver still works great, but the blaster just stops transmitting.  To be honest I am not even sure where to start.  Anyone run into this?  for me it is not really any skin off my back I can terminal in and restart lirc in a second, but walking my wife through that over the phone across two timezones for the 3rd time is killing me.

---

### Post by phat_penguin on 2008-11-18
Still having this problem after a week.  I misspoke in the initial post.  a restart of LIRC does not fix the problem, only  a reboot fixes it.  

looks like the module is loaded:
# lsmod |grep lirc
lirc_mceusb2           21764  0
lirc_dev               22216  1 lirc_mceusb2
usbcore               175376  7 usbhid,lirc_mceusb2,usb_storage,libusual,ehci_hcd,ohci_hcd

Note, LIRC is still running because the remote still works, it is only the blaster that fails.

Thanks in advance for the help with this, I really have no idea how to address this.

---

