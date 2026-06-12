---
title: "SD slot stopped working"
date: 2007-03-30
forum: Hardware &amp; Laptops
---

### Post by Apreche on 2007-03-30
So I have a Fujitsu P7230. it has a Ricoh Co Ltd RFC822 SD/SDIO/MMC/MS/MSPro Host Adapter in the front. Just two days ago I put an SD card in the slot, and it appeared on my Gnome desktop ready for action. Today, I put two different SD cards in the slot, and neither of them appear. All I see in dmesg are a bunch of I/O errors on mmcblk0. This is weird because my Edgy Desktop has no problem reading these cards. Did my SD slot just break yesterday? I have a USB SD reader I'm going to try when I get home. However, I do think this may be the result of the huge Feisty update I did on the laptop last night. Anyone else have their SD slot just stop working?

---

### Post by rwb on 2007-04-09
yep had the same problem......
seems that it originates frfom the kernel update from 2.6.20-12 to 2.6.20-14 

i get this in the sys log

Apr  9 15:54:58 rwb-laptop kernel: [  190.920000] tifm_7xx1: sd card detected in socket 3
Apr  9 15:54:58 rwb-laptop kernel: [  191.104000] mmcblk0: mmc3:aaaa SD01G 992000KiB 
Apr  9 15:54:58 rwb-laptop kernel: [  191.104000]  mmcblk0: p1
Apr  9 15:54:59 rwb-laptop kernel: [  192.108000] end_request: I/O error, dev mmcblk0, sector 1983936
Apr  9 15:54:59 rwb-laptop kernel: [  192.108000] end_request: I/O error, dev mmcblk0, sector 1983936
Apr  9 15:54:59 rwb-laptop kernel: [  192.108000] end_request: I/O error, dev mmcblk0, sector 1983984
Apr  9 15:54:59 rwb-laptop kernel: [  192.108000] end_request: I/O error, dev mmcblk0, sector 1983984
Apr  9 15:54:59 rwb-laptop kernel: [  192.108000] end_request: I/O error, dev mmcblk0, sector 0
Apr  9 15:54:59 rwb-laptop last message repeated 4 times
Apr  9 15:54:59 rwb-laptop kernel: [  192.112000] end_request: I/O error, dev mmcblk0, sector 0
Apr  9 15:54:59 rwb-laptop last message repeated 13 times
Apr  9 15:54:59 rwb-laptop kernel: [  192.116000] end_request: I/O error, dev mmcblk0, sector 0
Apr  9 15:54:59 rwb-laptop last message repeated 9 times
Apr  9 15:54:59 rwb-laptop kernel: [  192.124000] end_request: I/O error, dev mmcblk0, sector 1983609
Apr  9 15:54:59 rwb-laptop kernel: [  192.124000] end_request: I/O error, dev mmcblk0, sector 1983610
Apr  9 15:54:59 rwb-laptop kernel: [  192.124000] end_request: I/O error, dev mmcblk0, sector 1983611
Apr  9 15:54:59 rwb-laptop kernel: [  192.124000] end_request: I/O error, dev mmcblk0, sector 1983612
Apr  9 15:54:59 rwb-laptop kernel: [  192.124000] end_request: I/O error, dev mmcblk0, sector 1983613
Apr  9 15:54:59 rwb-laptop kernel: [  192.124000] end_request: I/O error, dev mmcblk0, sector 1983614
Apr  9 15:54:59 rwb-laptop kernel: [  192.124000] end_request: I/O error, dev mmcblk0, sector 1983615
Apr  9 15:54:59 rwb-laptop kernel: [  192.124000] end_request: I/O error, dev mmcblk0, sector 1983616


Im working on a HP nc6120 with Ti multiCard reader

---

### Post by uranus0206 on 2007-04-09
i have the same problem with my ASUS A6Q laptop

---

### Post by flammenwurfer on 2007-04-16
same problem here on a Lenovo N100

---

### Post by johnny99 on 2007-04-20
Same here on a hp nc6120c

---

### Post by yodermk on 2007-04-21
Didn't try -14, but under -15 the SD card slot works fine on my Asus Z84JP.

---

### Post by jadda on 2007-04-21
mine does not work either. I think it is because the kernel does not support it...so I am on the  live cd reinstalling 6.10. I got a kernel panic after trying to fix it...frustrating. has anybody found a fix?

---

### Post by Apreche on 2008-05-01
Even in the new Hardy Heron, I still have this problem.

---

