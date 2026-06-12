---
title: "LiveCam VX-1000 not detected - HELP!"
date: 2006-09-28
forum: Hardware &amp; Laptops
---

### Post by akall on 2006-09-28
Hi everybody,
I am new to this forum, but not so new with Ubuntu since I've been using it for 6 months.

Well, I received a webcam called LiveCam VX-1000 [usb] (producer: windows) as a gift.
It is recognized as something new (I saw it by dmesg command); I downloaded and installed Camorama but, as soon as I tried to run it, its answer is 
"Cannot find media device in /dev/video0"](*,) 

Could anybody help me?

I don't want to install win* to run my cam!

Thanx a lot

---

### Post by forlau on 2006-11-01
can you give us more information? 
What about ```
lsusb
``` or ```
dmesg 
```after connecting the cam. Vendor and ProdId (both hex numbers) are interessting. Maybee its a cam comaptibel to here [http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)

---

### Post by akall on 2006-11-08
Hello forlau,
here you are
> lsusb
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 002: ID 045e:00f7 Microsoft Corp.
Bus 002 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000

and
>dmesg
[17180110.116000] usb 2-1: new full speed USB device using uhci_hcd and address 2
[17180110.916000] usbcore: registered new driver snd-usb-audio


do you need more infos?

thanx for your help!
akall

---

