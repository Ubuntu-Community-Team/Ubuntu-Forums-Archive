---
title: "2tb hard disk drive extremely slow on Lenovo ideapad 320 Laptop"
date: 2019-03-26
forum: Hardware
---

### Post by tackskull on 2019-03-26
Hi there, I am using a Lenovo Ideapad 320 laptop and when I connect my external usb 3.0  2tb hard disk, I notice that the file transfer is extremely slow. Also when using it to load roms for emulators it give some sort of problem. I tried many things but the issue still remain. Sometimes, for no reason, it reads the external drive fast and well. On this laptop I am using Linux Deepin, but it give me the same problem with all the other distro I tried, like Ubuntu and Mint. The 2tb hdd transfer files on other pc very well, so basically the problem is not the hard disk but the laptop model. 

On this laptop I don't have other usb devices connected, just a bluetooth mouse and abluetooth keyboard, and also disconnecting this 2 devices the problem doesn't solve. Also trying to connect other usb drives or sd cards, the laptop read them very slow. To move 1gb file it would takes a 24 hours or more. So there is a big issue I can not understand.

I also tryed to turn off the power saving mode under Power management, nothing to do.

Can you guys help me?

Thanks

---

### Post by TheFu on 2019-03-28
I know nothing about Deepin, Ideapads, but a few common issues can happen that can be solved.

Check the system log files.  They are in /var/log/  - disk problems are usually easy to spot.  
Try a different USB cable.
Try a different USB port.
Are you certain that you are using a USB3 port on the laptop?
How is the USB drive being mounted?  FUSE or through kernel drivers?  FUSE is known to be really slow for large files.
Which file system is on the problem partition?

Have you searched for kernel bugs with USB for the kernel you have?

Please answer all questions, or ask for more help with the ones you need help with.

---

### Post by 1clue on 2019-03-28
Please give the output of 'sudo lshw' wrapped in code blocks. 


[LIST=1]
[*]It's possible that your Ubuntu does not recognize the USB3 card, or that the drive is somehow being recognized as USB1 or USB2.
[*]It's possible that there's a driver problem with the filesystem type. What filesystem is on it?
[*]It's possible that some other task is busy on the drive. Do you have something automatically looking for photos or video or music when you plug in a removable device?
[/LIST]

---

