---
title: "karmic : lsusb / printer / not recognised."
date: 2010-02-11
forum: Hardware
---

### Post by dotdot on 2010-02-11
Hi there,
Been running with ubu since... breezy.
I , like many folks out there, got tired with printing not working.
So got a hold of virtualbox and lo everything now works again....


so my trouble.

I've installed 9.10 .. brought my virtual machine over...

Now I find 9.10 can't even see my printer.. let alone share it out to my virtual machine....

any ideas folks ?

(dmesg.. says..
[ 1145.921174] usb 3-1: new full speed USB device using uhci_hcd and address 4
[ 1146.094462] usb 3-1: configuration #1 chosen from 1 choice
[ 1146.104430] usblp0: USB Bidirectional printer dev 4 if 0 alt 0 proto 2 vid 0x04A9 pid 0x1082
[ 1147.163460] usb 3-1: usbfs: interface 0 claimed by usblp while 'usb' sets config #1

lsusb... nothing... on my 904 box - it all works fine no problem).

thanks in adv people.

..

---

### Post by dotdot on 2010-02-11
prob solved - doh - now added myself as a member (!) of the lp group.

I've got to hand it to the use and group management section of user/groups.

generally it works but when stuff like this is buried... can't help but think - how do you seriously expect normal people to use this os - if it's not simple.

rant over..

now working fine - lsusb interestingly now tells me i have a printer - why do i have to a member of lp just to see the device ? (i have no idea..)

..

---

