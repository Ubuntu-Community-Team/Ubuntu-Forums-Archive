---
title: "Unable to mount Maxtor One Touch 4 Mini..."
date: 2009-01-19
forum: Hardware
---

### Post by c4bjenglacious on 2009-01-19
I need to mount this Maxtor one touch 4 mini to my ubuntu machine. I use this external hard drive on my work computer-(win xp) and personal-(ubuntu 8.10) computer. On the windows xp machine I have to run some software called "Maxtor Manager" to get the device to mount. There is also a password on the device when you mount it. I have tried to run the software using "wine" but, with no luck. 

I can get any other hard drive (ntfs,fat32 etc.) to mount using: 

sudo mkdir /mnt/external
sudo mount -t ntfs-3g /dev/sdb1 /mnt/external -o force

Also I thought I should note: when you plug this external hd into your computer there is 1 cord with a micro usb end on it and the other end has 2 usb ends on it. I think it is a safety feature. 

Thanks for any help.

LINUX ROCKS!!! 
LOL:guitar:

---

### Post by lmarsh on 2009-04-13
I had a similar problem on a Dell Latitude D400 using Ubuntu 8.10. Irritating because I had used the Maxtor on a Dell Inspiron 2200, also using Ubuntu 8.10, and on an Asus Eee pc, using Xandros, without problem. After various Google searches, I read the little manual again and here's what worked for me:

1. Unplug the USB cable from the Maxtor.

2. Plug the Maxtor's DATA/POWER USB connector into the computer.

3. Plug the Maxtor's POWER USB connector into another port on the computer.

4. Plug the Maxtor's mini-USB connector into the Maxtor.

The drive then appeared like any other USB stick does and everything was accessible.

Good Luck!

---

### Post by Fressi on 2010-10-16
I had a similar problem with my Maxtor OneTouch 4 Mini. I kind of bypassed the problem by plugging the 'power + data' end of the usb cable into my ubuntu laptop and plugged the 'power' end of the usb cable into my Desktop computer running windows. Suddenly I saw a hard drive icon appear on my Ubuntu laptop. 

Hope this helps

---

