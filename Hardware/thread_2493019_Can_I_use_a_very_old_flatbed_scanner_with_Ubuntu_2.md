---
title: "Can I use a very old flatbed scanner with Ubuntu 20.04.6LTS?"
date: 2023-11-30
forum: Hardware
---

### Post by aj34 on 2023-11-30
The flatbed document scanner is a Tevion MD90009. Question is: Am I wasting my time?

Seems that Tevion never made scanning software for Linux distros so any simple generic Linux scanning package would be fine by me - in fact, the simpler the better. I've read up on some Linux scanning "apps" and SimpleScan seems to fit the bill though I couldn't get it working when I downloaded it earlier.
Taking a step back, is there any point in me continuing to try to get this old Tevion scanner working? Am I doomed to failure? Appreciate opinions on this topic.

PS The scanner worked fine in Windows 7 some time back and I believe there's nothing wrong with it.
PPS Ubuntu doesn't see the scanner when I connect scanner by USB and turn scanner on.

---

### Post by TheFu on 2023-11-30
You need drivers.  The best way to find the drivers is to get the USB ID, use lsusb, and look that up by chip used, then look for drivers for that chip.
For example, 

....
Bus 001 Device 009: ID **_046d:c341_** Logitech, Inc. 
...

The ID for my keyboard is 046d:c341 ... google found this page: [https://linux-hardware.org/?id=usb:046d-c341](https://linux-hardware.org/?id=usb:046d-c341) for my device.

However, if there were never any linux drivers for the device, then it is unlikely that GUI software would include the necessary drivers, install, configure and make use of them, if just connecting the device doesn't have it recognized by the kernel.

---

### Post by aj34 on 2023-12-10
Thanks for your reply, TheFu.

I've now got a rough idea of what's involved and I've decided not to risk wasting more of my time because I suspect it's not going to be compatible anyway. I've seen SANE supported flatbed scanners at reasonable cost (i.e. <£100) from the big names so I'll treat myself for Christmas! Thanks again.

---

### Post by Holger_Gehrke on 2023-12-10
According to [this thread on the German ubuntusers forum]("https://forum.ubuntuusers.de/topic/scannerproblem-medion-mictrotek-tevion-md-900/") that scanner is a rebranded Microtek 6000, which was unsupported in 2008 - when the post was made - and still is.

Holger

---

### Post by aj34 on 2023-12-11
> **Holger_Gehrke said:**
> According to [this thread on the German ubuntusers forum]("https://forum.ubuntuusers.de/topic/scannerproblem-medion-mictrotek-tevion-md-900/") that scanner is a rebranded Microtek 6000, which was unsupported in 2008 - when the post was made - and still is.

Holger

Thanks for the info. Decision vindicated. A new scanner it is.

But even (allegedly) fully Linux compatible scanners, like the Canon CanoScan LiDE400 (according to SANE), have problems working in Ubuntu - according to many posts I've seen. Novices like me don't understand the necessary commands that need to be input in Terminal so have to rely on more knowledgeable users like yourself, TheFu et al. Why something simple, like adding a scanner, can't be completed using just a GUI I don't know. More and more I'm feeling that Linux distributions aren't suitable for us novices who simply require their PC's/laptops and peripherals to just work! I chose Ubuntu because all guidance I read suggested it was one of the two most suitable Linux OS's for my situation. Ah well, onwards and (hopefully) upwards.

---

### Post by TheFu on 2023-12-11
> 
But even (allegedly) fully Linux compatible scanners, like the Canon CanoScan LiDE400 (according to SANE), have problems working in Ubuntu - according to many posts I've seen. Novices like me don't understand the necessary commands that need to be input in Terminal so have to rely on more knowledgeable users like yourself, TheFu et al. Why something simple, like adding a scanner, can't be completed using just a GUI I don't know. More and more I'm feeling that Linux distributions aren't suitable for us novices who simply require their PC's/laptops and peripherals to just work! I chose Ubuntu because all guidance I read suggested it was one of the two most suitable Linux OS's for my situation. Ah well, onwards and (hopefully) upwards. 

Just because something is easy to speak or write, that doesn't make actually doing it trivial.  Every scanner vendor and model is just a little different.  That's how they differentiate their value to customers.  They are only as similar as MSFT requires. For a long time, they weren't similar at all and we had to have special drivers for every different vendor + model of scanner.  Thanks to smartphones and tablets which are either iOS or Android, vendors have decided to standardize many things, but not all models are meant to be used by massive numbers of people. Scanners for the masses tend to be basic and have decided that whatever SANE has built-in is sufficient, nothing extra.

There is a standard for scanning, called "OpenScanning" which hasn't really caught on, but hopefully it will. It is similar to the "OpenPrinting" standard which provides printers the ability to speak/understand driverless requests.  If your printer or scanner requires you to install drivers specific to that vendor/model, then it isn't following the OpenScanning and/or OpenPrinting standards for driverless devices.  Whenever I install a new linux desktop, my printers are automatically seen and configured. I don't have to do anything .... just print.  That's driverless printing.  I've had that since 16.04.

As for scanning, I have 2 scanners - 

one is a huge flat panel that never worked with Linux and never will. It never got updated drivers after WinXP either.  It was made by Epson and has a slide/negative scanner capability. That was important to me 20 yrs ago.

The other is a Brother All-in-One that has drivers. Every time I want to scan something, I worry that the scanner drivers aren't there or are broken or just won't work.  It isn't driverless and won't scan without a computer.

I needed to scan about 40 pages yesterday, but I couldn't recall if I'd installed the drivers or not.   Long story short ... the scanner wasn't seen by any GUI program.  Though I never expected it to actually work, I pressed the scanning buttons to "Scan to file" on the scanner and press the "Black/Greyscale" scan button.  Things started moving, a page was sucked into the scanner (automatic feed), scanned and spit out like it should.  then in a terminal window on the computer, a TIFF filename was listed with an absolute path.  ~/brscan/xyz.........tif.  I looked in that directory and there was a file!  I was shocked.  Pulled up an image viewer and it worked.  TIFF isn't a format that interests me, so I converted it to a .png ... which took the 2.8MB .tif file to 820KB .png - and I couldn't see any difference in the results.  As long as I can find a way to scan things with it, I won't replace it.  The entire reason I have that all-in-one machine is for scanning and faxing. Since the ink ran out/dried out in 2008, I've never bought replacement. Ink printing is too expensive.  I print with a laser printer.
[B]
So, if I'm in the market for a new printer and/or scanner, I want driverless for both.  No exceptions.  Further, I want the scanner to work without any computer connected and to be able to save the files to a USB Flash storage device plugged into the scanner.  That will remove all worries about linux support and drivers.[/B]  No computing device needed for any scanning at all.

Further, I don't want any network in the printer/scanner.  Direct USB connection. I don't want my peripherals "phoning home" reporting things.  A few years ago, I was able to find a Brother all-in-one that met these needs for a friend.  Brother has a reputation for Linux support.  I used to be mainly HP, but HP has been screwing their customers recently.  Mom had a Canon printer. Zero Linux support. Proprietary drivers from a German company were available for Linux for $50.  The printer was $60, so that seemed excessive and she's have to reload drivers every OS change (LTS --> LTS --> LTS), so I convinced her that a cheap Brother driverless laser printer would be cheaper and zero hassle for her.  The printer outlived her and had no issues. Plus, since she printed a bunch - she liked paper copies of emails - she never had to buy more ink or toner.  The Canon printer was given to a grandchild who ran MS-Windows.

---

### Post by SeijiSensei on 2023-12-11
You might give VueScan a try.

[https://www.hamrick.com/linux-scanner-software.html](https://www.hamrick.com/linux-scanner-software.html)

Worked with an old HP flatbed when other alternatives did not. I paid the lifetime license fee, too, though I don't use it any more since I don't have the scanner.

---

### Post by TheFu on 2023-12-11
+1.

I've never heard anything bad about Hamrick linux drivers.  

For a dedicated $99 slide/negative scanner I got, Hamrick software for MS-Windows was included and it worked fine.  10 yrs later and that same device is 100% *plug and use* on Linux. Drivers for it are built-into the Linux kernel at some point.

If you love a specific hardware device and $50-$70 for drivers are acceptable to you, don't hesitate to choose the Hamrick software.

---

