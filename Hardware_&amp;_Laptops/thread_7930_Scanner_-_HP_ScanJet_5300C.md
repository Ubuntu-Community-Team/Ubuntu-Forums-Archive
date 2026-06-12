---
title: "Scanner - HP ScanJet 5300C"
date: 2004-12-12
forum: Hardware &amp; Laptops
---

### Post by adpsimpson on 2004-12-12
Hi, I was wondering if anyone could help me get this USB scanner working (it works fine under Mandrake, Windows etc). I've googled for it, and searched here, but didn't manage to find anything to help me sort it out.  It appears to be a re-packaged Avision scanner. I've tried installing **hpoj**, but that didn't find it. It's not currently seen by the system at all, so far as I can tell. 

Thanks.

---

### Post by adpsimpson on 2004-12-22
[QUOTE=adpsimpson]Hi, I was wondering if anyone could help me get this USB scanner working (it works fine under Mandrake, Windows etc). I've googled for it, and searched here, but didn't manage to find anything to help me sort it out.  It appears to be a re-packaged Avision scanner. I've tried installing **hpoj**, but that didn't find it. It's not currently seen by the system at all, so far as I can tell. 

Thanks.[/QUOTE]
 Can anyone help with this one? Getting annoyed...

---

### Post by donski on 2004-12-29
Hi,

I have a 5300c which I too cannot get working, but maybe we can help solve each others problem.

What I've done so far and what I've found:

First I installed through synaptic:

sane 1.0.12-2 (this contains the avision backend for the 5300c)
sane-utils 1.0.14-5
libsane 1.0.14-5 (don't know if this is needed)
xsane 0.94-3ubuntu1

dmesg gives:

  Vendor: HP        Model: ScanJet 5300C     Rev: 6.00
  Type:   Scanner                            ANSI SCSI revision: 02
usbcore: registered new driver hpusbscsi
usbcore: registered new driver hiddev


sane-find-scanner gives:

found USB scanner (vendor=0x03f0, product=0x0701) at libusb:001:002
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

I enabled a line in /etc/sane.d/avision.conf to match the sane-find-scanner output:

usb 0x03f0 0x0701

I commented out every line except net and avision in /etc/sane.d/dll.conf

when I run scanimage -L it gives:

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

I don't know if this may be a permission problem (possibly not as scanimage gives the same output when run as root)

Anyone got any ideas?

---

### Post by zarrelli on 2005-02-21
Hi,

> found USB scanner (vendor=0x03f0, product=0x0701) at libusb:001:002
 
> I enabled a line in /etc/sane.d/avision.conf to match the sane-find-scanner >output:

> usb 0x03f0 0x0701

You are quite there. Don't use usb 0x03f0 0x0701 but

usb libusb:001:002

and have libusb find the scanner for you.

Remember to add your user to the "camera" group or you won't have enough rights to access the device.

Ciao

Giorgio Zarrelli

---

### Post by angelus on 2005-11-10
Hello,

I have almost the same trouble, i have a HP scanjet 4400c and sane has not support for it, how can i set it? i tried to do what u did with your 5300c but i still see the message :

No scanner were identified. If u were expecting something diferent...

The only diference is when i execute sane-find-scanner the message is found USB scanner (vendor=0x03f0, product=0x0705) at libusb:001:002

How u can see my producto name is 0x0705 instead of 0x0701

What i have to do???

Thanks in advance.
angelus

---

