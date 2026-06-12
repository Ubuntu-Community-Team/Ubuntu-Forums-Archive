---
title: "Second HDD make freeze Hardy"
date: 2008-10-17
forum: Hardware
---

### Post by segalion on 2008-10-17
Please help me with this strange error with the second hard disk of my laptop.

Recenltly, I installed a second IDE 250GB Wenster Digital harddisk in my HP Pavilion 8113 (it has space for a second HD) (as slave).
It seems to work fine, correctly mounted, and I can use it with no problem (read, write, etc.)
I have automounted it on fstab with this options...
```
# Entry for /dev/hdb1 :
UUID=5a328c44-1f09-4d6f-bd2f-0a4eccd641ed /media/hdb ext3 defaults 0 1

```

The problem seems to appear after a day with PC running without any interation, and suddenly I begin to use it. After a few minutes working with desktop, suddenly the computer become slower and slower, and when I make a "top" at console, I can see the CPU goes allways with WA at 97% but no process consumming high CPU, and the led of the HDD lighthing. In less than 30 seconds the computer is absolutely freeze, with even no mouse movement, and I have to restart.

Please help me. 

I cant fount any log, any strange dmesg or any error.

---

### Post by segalion on 2008-10-21
I have found the error log at /var/log/kernel:

```
Oct 21 07:56:15 webstar kernel: [18982.460987] hdb: dma_timer_expiry: dma status == 0x61
Oct 21 07:56:26 webstar kernel: [18992.451157] hdb: DMA timeout error
Oct 21 07:56:26 webstar kernel: [18992.451176] hdb: dma timeout error: status=0xff { Busy }
Oct 21 07:56:26 webstar kernel: [18992.451179] ide: failed opcode was: unknown
Oct 21 07:56:26 webstar kernel: [18992.451651] hda: DMA disabled
Oct 21 07:56:26 webstar kernel: [18992.451663] hdb: DMA disabled
Oct 21 07:56:26 webstar kernel: [18992.499108] ide0: reset: success

```
Please help me with this...

I´ve been read somethig about hdparm config, and bug kernels about wake up the hdd from sleep mode, but I dont understand anything...

Thaks in advance and sorry by bump

---

### Post by segalion on 2008-10-27
Finally I have found the error, and seems that it isnt the Hard Disk. 
My problem was a nautilus window with iconsize=150% showing thumbs in this hard disk.
With this nautilus config, metecity begin to eat more and more memory until get all even swap, and finally the computer freeze.

This happens in all nautilus gnome window with icons and size=150%.

When put size=100% the problems go off.

Thanks in advance, and hope this strange error can help somebody.

---

