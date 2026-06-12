---
title: "Mounting USB flash disc problem"
date: 2010-09-14
forum: Hardware
---

### Post by jurco on 2010-09-14
Hi guys, I have following problem with my USB card reader.

I take out my CF card from my Hama card reader when the computer is off. Then I boot to kubuntu 10.04 and find out error message under kubuntu logo "error mounting device, press S to skip or M to manualy repair" (or similar) so I always hit S.

Kubuntu starts fine and problem is when I insert the CF card in the card reader the card is recognized but not mounted. When I click to mount, I get error like "Disc cannot be mounted, permission denied".

So I mount it from terminal
```
sudo mount /dev/sdc1 /media/sdc1
```

After this I can read from the usb drive but I can not write to it.

Anyone please help. Thanks!

---

### Post by kimsmarkin on 2010-09-14
Plug the flash drive into a USB port on your computer. These are normally found on the back of your computer. Some newer models also have ports on the front panel. Once you turn, you all want to open a terminal window and become root. This is the only user who can access the controls to manually mount your disk.

---

### Post by jurco on 2010-09-14
I have another USB which I stick in, the USB drive is mounted automatically and is ready for read & write.

I have different problem described in my (upper) thread.

---

