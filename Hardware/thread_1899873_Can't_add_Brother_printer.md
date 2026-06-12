---
title: "Can't add Brother printer"
date: 2011-12-24
forum: Hardware
---

### Post by Madwand on 2011-12-24
I'm having a great deal of trouble adding a printer to my Dell Inspiron Mini netbook with Ubuntu 11.10. Using system-config-printer (It's a crime this isn't available from the menus) I've tried to add support for my Brother MFC-8640D, with no luck. The "printer state" shows "Processing - waiting for printer to become available". Test pages won't print, it's as if the printer isn't recognized at all.

I can successfully print from the dual-booted Windows OS on the netbook, as well as another laptop running Ubuntu 10.04, so it isn't a hardware problem.

The device URI I set to: usb://Brother/MFC-8640D

"lsusb" gives me a line reading:
Bus 001 Device 005: ID 04f9:01a2 Brother Industries, Ltd MFC-8640D
which is the only acknowledgement I've gotten that the printer even exists.

At one point, system-config-printer gave me a command line error reading:
No match for device usb://Brother/MFC-8640D:
MFG:Generic;MDL:Printer;DES:Generic Printer;
Using lsb/usr/cups-included/textonly.ppd (status: 3)

Can anyone help me set up this printer? It's ridiculous that something so simple isn't correctly supported, and is so difficult to get working in the first place. What newbie would have any idea what a "device URI" is?

---

### Post by Madwand on 2011-12-30
Can anyone help? This is a really serious problem and I have no idea what is wrong.

---

### Post by Bucky Ball on 2011-12-30
Sure you got the model right? I just looked at the Brother site and tells me that model isn't found.

The 8 series is here:

[http://welcome.solutions.brother.com/bsc/public/SearchResult.aspx?reg=as&c=au&lang=en&FLG=1&TXT=MFC#mfc-8](http://welcome.solutions.brother.com/bsc/public/SearchResult.aspx?reg=as&c=au&lang=en&FLG=1&TXT=MFC#mfc-8)

---

### Post by Bucky Ball on 2011-12-30
Here you go:

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html)

... linked from here:

[http://welcome.solutions.brother.com/bsc/public/us/us/en/dlf/download_top.html?reg=us&c=us&lang=en&prod=mfc8640d_us](http://welcome.solutions.brother.com/bsc/public/us/us/en/dlf/download_top.html?reg=us&c=us&lang=en&prod=mfc8640d_us)

That should be what you need. Follow the instructions and read 'Before Installation'. I couldn't find it before because I was looking on the Australian site and it doesn't look like it's available here. ;)

---

### Post by Madwand on 2011-12-30
Thanks. I did try installing the "BR8640_2_GPL.ppd" driver following the instructions at the indicated link -- it didn't work. I put the file into the "/usr/share/ppd" directory as indicated. cupsys didn't exist in the indicated directory, so I restarted the computer instead. Trying to print a test page from system-config-printer gives the message: "Processing: Waiting for printer to become available".

I try installing the ppd.gz file using the built-in facility to select a ppd.gz file in system-config-printer. During the installation attempt I get the error message, "CUPS server error" and "server-error-internal-error".

Why isn't this working?

---

### Post by Bucky Ball on 2011-12-31
The cups driver is the one.

---

### Post by Madwand on 2012-01-01
Yes, I'm using the Cups driver provided by the Brother web site. It doesn't work, or doesn't at least on my Inspiron Mini.

---

