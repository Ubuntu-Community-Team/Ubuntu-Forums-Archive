---
title: "USB Flash Drive Does not Work!!"
date: 2008-12-11
forum: Hardware
---

### Post by iamthebest235 on 2008-12-11
My USB Flash drives were perfectly fine on my laptop until 5 minutes ago.  BTW I am running Intrepid on Inspiron E1405.  There were no problems before.  When I plug in the USB Flash Drive the usual big light on the flash drive does not light up; installed "sudo apt-get usbview" it does not recognize the drive and gives an error that says: "Can not open the file /proc/bus/usb/devices"

So at this point I figured may be its my flash drive, so I tried the same drive on another laptop with XP, and the light blinks and its recognized just to confirm tried the flash drive on almost everything (xbox, satellite receiver other computers)...the light blinks on all.

I even tried all the other flash drives on my ubuntu laptop, none of them work.

Need Help! I use my Ubuntu laptop for all my schoolwork, and need the drive to transfer my files between other computers for projects and stuff.

I appreciate your help regarding this matter and thank you for the help in advance!!!

---

### Post by taurus on 2008-12-11
With a USB plugged in, post the output of this command from a terminal.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by iamthebest235 on 2008-12-11
```
Disk /dev/sda: 58.5 GB, 58506416640 bytes
255 heads, 63 sectors/track, 7113 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6817    54757521   83  Linux
/dev/sda2            6818        7113     2377620    5  Extended
/dev/sda5            6818        7113     2377588+  82  Linux swap / Solaris
```

---

### Post by iamthebest235 on 2008-12-12
Still nothing, did a lot of search around the forums and tried all kinds of different stuff doesn't work.

---

### Post by iamthebest235 on 2008-12-14
Anyone who could help me out with this problem????

---

### Post by brandon88tube on 2008-12-14
Did you properly remove the USB drive the last time you used it by unmounting it if you were using Linux or by safely removing if you were using Windows?

---

### Post by iamthebest235 on 2008-12-14
Actually yes, the last time I used before it stopped working, I did remove it safely.  But before that I seldom used to remove the drive safely and never had a problem.  Plus it is just not the Flash Drive that is not working, nothing that I plug into the USB works (Printer...that used to work before now it doesn't)

---

### Post by vandorjw on 2008-12-14
if you plug in a usb mouse? does the mouse work?

Obviously the USB-key is fine, I just think the problem might be with the USB port.
If you have windows installed on the Dell, and you plug the USB-key in then, or anything else for that matter, does it work?

If it does work, then there is neither a problem with the key, nor the physical USB port, but a software problem....did you install anything new 5 days ago, or, in the time period when you USB worked and right up to the moment it stoped working?

- Cheers CC7

---

### Post by brandon88tube on 2008-12-14
> **iamthebest235 said:**
> Actually yes, the last time I used before it stopped working, I did remove it safely.  But before that I seldom used to remove the drive safely and never had a problem.  Plus it is just not the Flash Drive that is not working, nothing that I plug into the USB works (Printer...that used to work before now it doesn't)

What about something like a mouse or keyboard that is USB? If even those do not work it might be your USB port. Linux has some problems with printers so we can't really use that as another example.

---

### Post by iamthebest235 on 2008-12-14
Good news...somehow it has started working again...all that I did was restarted the laptop again and that's it.....its all good now...

Thanks everyone for all your help...

We can kinda mark this thread as solved now (don't know how that works???)

---

