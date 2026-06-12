---
title: "Slow data transfer to flash drive Xubuntu 14.04"
date: 2015-04-15
forum: Hardware
---

### Post by ckrles on 2015-04-15
I know this is an issues raised some time ago, but I haven't been able to find updated answers. So this is my problem. I'm running Xubuntu 14.04 and I have noticed that data transfer to flash drives is extremely slow on both my laptop and desktop. Both have usb 2.0 and my flash drive is 3.0. I really don't know why the speed comes down to 1 or 2 mb/s. It's annoying. If I transfer data to an external usb 2.0 hard drive (2,5") it is 22-23 mb/s. I know there got to be something wrong with the flash drive data transfer speed, but I don't know if the speed is correct in my 2,5" hdd.

Any help would be highly appreciated.

I'm no expert on Ubuntu. I have just been using it for about 2 years, so kind of a newbie ;););).

Thank you very much.

---

### Post by Namnamseo on 2015-04-15
Is both your laptop and desktop Xubuntu 14.04?
Or did you try copying on Windows?
1~2MB is pretty slow for USB flash memory, I think. Did it work faster before?
Or maybe the memory is old, i.e. something about flash cell and its life expectancy(due to voltage drop).
Oh, and just for a note, there were some issues with nautilus copying files to USB or somewhere. I experienced one myself. Just after you start copying, the progress bar is about half done, and sticks there for a long time, and then the progress bar increases as time passes. (I don't know if the problem persists in Xubuntu 14.04. I think I heard they changed the file explorer.)

---

### Post by Bucky Ball on 2015-04-15
Are you using a different file system on the USB as opposed to the HDD? EXT4 on one and NTFS on the other perhaps? How much free space is on the USB stick you are trying to transfer to?

---

### Post by ckrles on 2015-04-16
It happens both on my laptop and desktop. BOth of them are equipped with usb 2.0. Transfering files is faster under Windows. The flash drives are new and they are usb 3.0. THey are formatted in fat32 where the speed is 1-2 mb/s, but if I format them in ntfs it starts at 9 mb/s, it keeps in 4-5 mb/s for a while and then drops to 2 mb/s. I haven't tried ext4 because there are some devices which do not recognise this format when I plug the flash drive in. As for the Hdd it is formatted in ntfs.

I would really appreciate any suggestions to make it faster.

What are the approximate speeds I should have with 2.0 usb and 3.0 usb flash drives?

Thank you.

---

### Post by ckrles on 2015-04-17
No ideas?

---

### Post by ckrles on 2015-04-20
No one can suggest me a solution, please?

---

### Post by kurt18947 on 2015-04-20
Not all USB drives are created equal. Here is something I use to get a feel for maximum speeds reading/writing USB flash drives. I use Ubuntu-Gnome which has (or I can install) Disks, a useful disk utility. I think the package is called gnome-disk-utility. One of its functions is to benchmark read/write speeds. I recently checked some fairly generic flash drives. The write speeds were around 4 MB./sec, the read speeds were 24-30 MB./sec.  I too have seen slow copies using Nautilus. I hadn't considered copying from a *nix file system to FAT32 as being an issue. If I have the time & inclination I may format a flash drive to ext4 and see if there's a difference.

I thought that perhaps using USB 3 drives on a USB 2 PC might help. It doesn't seem to. I did try a USB 3 drive on a PC with USB3 running Xubuntu. Read speed was about 4X, write speed was about 2X USB2 as I recall. I suspect that if I used a higher quality USB drive, for example Sandisk Extreme that uses an SSD controller chip my results would have been better.

---

### Post by ckrles on 2015-04-20
Thank you for your answer kurt18947. My flash drive is Kingston DTSE9. It's this one [http://www.kingston.com/es/support/technical/products?model=dtse9h](http://www.kingston.com/es/support/technical/products?model=dtse9h)
I'm using the 16Gb version. It's faster under windows than under xubuntu. A workmate suggested me that the problem might be in the driver used by xubuntu with this drive. It sounds a bit strange to me. Would it be possible?

Or should I change the file explorer? How can I do it and undo it in case it doesn't work? Which file explorer would you recommend me?

Thank you very much.

---

### Post by Bucky Ball on 2015-04-21
If it is only that USB dongle that shows these symptoms, unsure why you would think it is the file manager that is the problem. There is obviously something Ubuntu doesn't like about that dongle. :-k

---

### Post by kurt18947 on 2015-04-21
One way to eliminate questions about Thunar (XFCE file manager) might be to copy some files via the command line. Time the transfers using Thunar and the command line. Here is help on copying via the command line:

[http://manpages.ubuntu.com/manpages/karmic/man1/cp.1.html](http://manpages.ubuntu.com/manpages/karmic/man1/cp.1.html)

I too find copying files to a flash drive can be pretty slow. I've tried copying the same directory to a USB hard drive and to a flash drive. The USB hard drive is nearly always faster. If the USB interface were at fault I'd expect both the hard drive and flash drive to be slow. I quit worrying about it because I have very few large copy-to-flash jobs. Most of my writes to flash drives involve rsync and some graphical front end.

---

### Post by ckrles on 2015-04-28
Thank you. I'll give the command line a try. Anyway it turns out I was wrong since the usb is actually 2.0, but I tried a 3.0 one and the speed is 7-8mb/s. I also tried other 2.0 and the speed was about 2mb/s. However, I accessed xubuntu 14 setup and, as suggested on a thread I read, I disabled the automatic mounting of external drives and the transfer speed has rosen up to 4-5 mb/s on usb 2.0.

I will try the command line Anyway.

Thank you very much.

---

