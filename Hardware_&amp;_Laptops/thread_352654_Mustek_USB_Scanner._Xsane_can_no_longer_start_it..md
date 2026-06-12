---
title: "Mustek USB Scanner. Xsane can no longer start it."
date: 2007-02-03
forum: Hardware &amp; Laptops
---

### Post by robc02 on 2007-02-03
I managed to get my Mustek Scanmagic 1200 USB scanner working under Xsane, after downloading the firmware and changing the gt68xx.conf  and  mustek_usb.conf files. I did a few scans with it and then shut down Xsane.

A while later I tried again and, when trying to scan or preview I got the message "Failed to Start Scanner:Invalid Argument"

I used this How To to help get set up in the first place:

[http://ubuntuforums.org/showthread.php?t=24087](http://ubuntuforums.org/showthread.php?t=24087)

I have the latest Sane-backends. "sane-find-scanner" finds something that it thinks might be a scanner. "scanimage -L" can not find a scanner. "lsusb" identifies the scanner as:

ID 055f:0003 Mustek Systems, Inc. ScanExpress 1200 USB

Xsane opens a window identifying the scanner as "1200 USB (unsupported)" but then fails to operate it. 

Since the scanner did work at first, I wonder if I am just not using Xsane properly? Or has something else gone wrong?

Any suggestions gratefully received.

---

### Post by alienexplorers on 2007-02-06
ALong with xsane, did you also load libsane and libsane-extras.  I needed all of these to get my mustek 4800 running.

---

### Post by robc02 on 2007-02-07
Libsane was already installed. Libsane extras was not but I have now installed it. In the meantime I had discovered that it would scan greyscale OK but not colour. Now it scans colour after a fashion - everything is either very purplish or green! Still, it is an improvement! My scanner is officially unsupported so maybe I can't expect too much. Thanks for your help.

---

### Post by alienexplorers on 2007-02-07
I have trouble scanning graphics in color.  They came out off color and distorted.  Still trying to work this out.

---

### Post by pdk on 2007-03-13
I have an Acer scanner. I like yourself got it working once.
I now get the libusb invalid argument message.
The driver manager sees the scanner. scanimage -L also sees the scanner.
I note that if you switch off the scanner and then on again, the usb address ups by one. Still the same type of error message.
You say you loaded libsane extras. Was that the reason you now obtain some results.
Your quote says 'in the meantime" which sort of says it started working before libsane was installed.
Have you succeeded yet ?
Peter Knight  (knightp@intekom.co.za)

---

### Post by robc02 on 2007-03-13
I get the error message if I set Xsane to Colour.

It works OK on Grey or Lineart.
As I said, my scanner is not officially support, so perhaps I can't expect much more.

---

### Post by wookieman on 2007-04-23
> **robc02 said:**
> I get the error message if I set Xsane to Colour.

It works OK on Grey or Lineart.

If I try to scan in colour I get the same error message, BUT if I first do a scan in Grey or Lineart and then try a colour scan it works, albeit the colours are messed up.

Also as far as I can tell the native resolution of this scanner is 600dpi, if I scan at this resolution the colours arn't that badly messed up as say at 50dpi. Anyone got any ideas why ?

If I have anymore sucess I'll post again here.

---

