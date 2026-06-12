---
title: "USB Flash Drives"
date: 2008-01-17
forum: Hardware &amp; Laptops
---

### Post by supergogirl on 2008-01-17
I am using the most recent version of Ubuntu (Feisty Fawn I believe) and whenever I put a usb flash drive/SD card/Any type of memory card I am not given the option to 'eject' it.... like when I right click the icon, or anywhere.
My one friend who its very knowledgeable in Linux suggested that dragging the icon into the trash could work as an eject (It doesn't.)
Also when I just pull them out I do get a message telling to me use the "eject" feature... so I was wondering if anyone could tell me how I could fix this problem (if there is a viable solution)... or tell me where eject is incase I'm just being painfully oblivious 
 
Thank you :3


PS: I would also like to apologize if I posted this in the wrong section (maybe should've gone into general help in retrospect but the problem is with hardware... and I am technically on a laptop.... soo.... yeah. O_o

---

### Post by pytheas22 on 2008-01-17
If you open the contents of the device in Nautilus to browse them, you should be able to select "Unmount Volume" from the file menu.  Can you do that?

If not, you should be able to unmount the volume using the umount command.  I believe that Ubuntu mounts stuff like USB sticks always in the /media directory.  So for example, if the volume were called TRAVELDRIVE, you could unmount it with:
```

sudo umount /media/TRAVELDRIVE
```

note that the unmount command is indeed spelled umount, not unmount

In any case, it shouldn't really matter whether the device is unmounted or not.  If data is being written to it at the precise moment that you pull it out of the computer there's a relatively small risk of corrupting the data on your device, but especially with USB sticks that flash on and off when they're in use, it's easy to avoid removing them at unsafe times.  Although it's always safest to just unmount the volume, of course, especially if you have important data on it.

---

