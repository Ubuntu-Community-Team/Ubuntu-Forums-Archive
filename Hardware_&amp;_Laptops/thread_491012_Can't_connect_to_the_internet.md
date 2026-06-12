---
title: "Can't connect to the internet"
date: 2007-07-03
forum: Hardware &amp; Laptops
---

### Post by shahrimanz on 2007-07-03
I just run ubuntu on the liveCD.I am truly amazed.But I found out that I can not connect to the internet.Everything working just fine except the networking.I still new with linux.Can anyone help me.Does the problem solve after I install ubuntu into my laptop?If not,how can I solve this problem..?
thanks

---

### Post by teaker1s on 2007-07-03
to ways we can possibly go with this.
1)on desktop panel Applications>Accessories>Terminal
then type
```
lspci
``` this will show all pci devices and you should be able to find your ethernet port make in the list.
2) Possibly the Alternate text install iso will have a driver

Lastly have you considered a duel boot system? you can have both windows and ubuntu as boot options.

welcome to the forums

regards

Daniel

---

### Post by DalekClock on 2007-07-03
It would also help if we knew how you are trying to connect(ie: wired or wireless). If you connect wirelessly, it would mean your network adapter is not supported.

---

### Post by shahrimanz on 2007-07-03
I connect to the internet wirelessly.I still can't connect.Do you have other suggestions..?

---

### Post by teaker1s on 2007-07-04
if your wireless is internal then
```
lspci
```
if your wireless is usb then
```
lsusb
```
we will try to see what you have,please post output(copy to text doc and use floppy or cd to paste output to internet connected pc, if you don't have ethernet access on the one with wireless)

---

