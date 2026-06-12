---
title: "Brother MFC-7860DW Prints but no Scan"
date: 2017-10-13
forum: Hardware
---

### Post by mblanco2000 on 2017-10-13
I have my Brother All in One MFC-7860DW connected to my computer via USB.  I installed the printer/scanner drivers from the brother website, and the printer works just fine.  However, the scanner will not work.  When using simple scan it says unable to connect to scanner.  Any help is appreciated, I could even pay if that would help.  Thanks

scanimage -L
device `brother4:bus3;dev1' is a Brother MFC-7860DW USB scanner

Any help on this is appreciated.

---

### Post by kurt18947 on 2017-10-13
Did you try scanning as a sudo user? There was a problem with non-sudo users scanning that required editing of a Udev file, I don't know if that has been fixed or not. The fix is for USB connections only, network connections are not affected. When scanning over a network it may be necessary to issue a one line command via terminal in order for the device to be recognized.

Here's the fix for USB scanners:

[http://support.brother.com/g/s/id/linux/en/instruction_scn1c.html?c=us_ot&lang=en&redirect=on](http://support.brother.com/g/s/id/linux/en/instruction_scn1c.html?c=us_ot&lang=en&redirect=on)

One thing about Brother's linux support pages is that there's some old information there. A goodly amount of the stuff there isn't applicable to current Ubuntu systems.

---

### Post by pdc on 2017-10-14
so mblanco; there are several steps that one seems to need to do; to get a brother scanner working on usb

1) you need to download and install this small file [http://support.brother.com/g/s/id/linux/en/instruction_scn1c.html?c=us_ot&lang=en&redirect=on#u13.04](http://support.brother.com/g/s/id/linux/en/instruction_scn1c.html?c=us_ot&lang=en&redirect=on#u13.04) that allows you as a normal user to access the scanner; (otherwise as kurt says, you would need to use the sudo command ..)

2) you need to libusb-0.1-4 as per [http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&redirect=on#f00107](http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&redirect=on#f00107)

3) so your device is a brscan4 device; so you need to copy some files as per [http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&redirect=on#f00101](http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&redirect=on#f00101) ....... you need to COPY the lines below; one by one; and paste each into a terminal; and hit the ENTER key after each paste .. please ask for a how to if you need it .......

```
sudo cp /usr/lib64/sane/libsane-brother4.so.1.0.7 /usr/lib/sane
```
```
sudo cp /usr/lib64/libbrscandec4.so /usr/lib
```
```
sudo cp /usr/lib64/libbrscandec4.so.1 /usr/lib
```

_________
phew; that was easy;

Brother do provide an installer tool; I would have thought it should be able to do all of the above; did you use the installer tool please, so we know if it works?

---

### Post by mblanco2000 on 2017-10-16
> **pdc said:**
> so mblanco; there are several steps that one seems to need to do; to get a brother scanner working on usb

1) you need to download and install this small file [http://support.brother.com/g/s/id/linux/en/instruction_scn1c.html?c=us_ot&lang=en&redirect=on#u13.04](http://support.brother.com/g/s/id/linux/en/instruction_scn1c.html?c=us_ot&lang=en&redirect=on#u13.04) that allows you as a normal user to access the scanner; (otherwise as kurt says, you would need to use the sudo command ..)

2) you need to libusb-0.1-4 as per [http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&redirect=on#f00107](http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&redirect=on#f00107)

3) so your device is a brscan4 device; so you need to copy some files as per [http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&redirect=on#f00101](http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&redirect=on#f00101) ....... you need to COPY the lines below; one by one; and paste each into a terminal; and hit the ENTER key after each paste .. please ask for a how to if you need it .......

```
sudo cp /usr/lib64/sane/libsane-brother4.so.1.0.7 /usr/lib/sane
```
```
sudo cp /usr/lib64/libbrscandec4.so /usr/lib
```
```
sudo cp /usr/lib64/libbrscandec4.so.1 /usr/lib
```

_________
phew; that was easy;

Brother do provide an installer tool; I would have thought it should be able to do all of the above; did you use the installer tool please, so we know if it works?

PDC and Kurt wow you guys are the best thanks so much.  This is solved!!  I can print and scan.  Thanks guys

---

### Post by pdc on 2017-10-17
glad it is working well; enjoy

PS as it is your thread, you can use the Thread Tools Options ........... and change it to SOLVED

---

