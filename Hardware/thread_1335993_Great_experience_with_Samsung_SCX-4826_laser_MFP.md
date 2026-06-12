---
title: "Great experience with Samsung SCX-4826 laser MFP"
date: 2009-11-24
forum: Hardware
---

### Post by tobiasly on 2009-11-24
**UPDATE: I take back my recommendation of Samsung. DO NOT BUY ONE OF THEIR PRINTERS!! Their device no longer works fully under 10.04 or later and they have not / will not update their proprietary drivers. See post #3 below.**
[COLOR="DimGray"]
So many people only write when they have problems with something, so instead I wanted to report on how happy I am with the Samsung SCX-4826FN laser multifunction printer and how well it worked in Karmic due to the vendor's support.

I'm running Karmic x86_64 and my wife is running Windows Vista. I previously had a USB printer hooked to a server running CentOS 5 but we wanted a scanner we could both use also. I found a great price on the [Samsung SCX-4826FN]("http://www.amazon.com/Samsung-Monochrome-Multifunction-Printer-SCX-4826FN/dp/B001OI2YQK/ref=sr_1_1?ie=UTF8&s=electronics&qid=1281323942&sr=8-1") (just under $250). Looked like it had everything we need: built-in ethernet server, duplexing, print/scan/fax, plus some nice extras such as scan to USB thumb drive or email etc.

I was kinda leery as to whether everything would work on my system, especially the networked scanner, but a look at [Samsung's website]("http://www.samsung.com/us/consumer/office/printers-multifunction/black-and-white-multifunction-printers/SCX-4826FN/XAA/index.idx?pagetype=prd_detail") showed that they had not only Linux drivers for all functions, but a GUI control panel as well.

Once the printer arrived, I installed all the software and must say that I'm very impressed. They integrate fully with CUPS and SANE so that printing and scanning is handled by the correct subsystems and not some proprietary protocol. My wife and I can both print, scan, change settings, etc. from our own PC.

It even has a built-in web server for viewing status and changing config settings so I don't really need to open the GUI tool.

Is it perfect? No... it still uses a proprietary, binary-blob driver instead of open source, and the installer is a proprietary tool that doesn't integrate with apt-get. It created a new menu under my Applications menu instead of putting the settings tools under Administration. And the included instructions are, for the most part, terrible and very poorly translated into English.

However, it's still better support for Linux than many other printer makers care to provide, so I'm giving them credit for that. I highly recommend this printer for anyone looking for a similar solution.

(Note: the printer which this one replaced was a Brother HL-5150D, which has served me very well under Linux for many years, so kudos to Brother as well for making a very solid Linux-supported printer.)[/COLOR]

---

### Post by ubuntologist on 2009-12-16
thanks a million tobiasly. really useful.

the 4828 is mentioned on openprinting.org; however, the ubuntu hardware support wiki doesn't have either 4826 nor 4828.

it'd be great if you can add your experience to [https://wiki.ubuntu.com/HardwareSupportComponentsPrintersSamsung](https://wiki.ubuntu.com/HardwareSupportComponentsPrintersSamsung)

cheers

---

### Post by tobiasly on 2010-08-08
Just in case anyone may read this and be persuaded into getting a Samsung printer or multifunction device, DON'T. Their scanner drivers no longer correctly work on 10.04 64-bit and despite the efforts of [community members such as Tweedledee]("http://ubuntuforums.org/showthread.php?t=341621"), the fact that these drivers are proprietary is tying their hands in getting them fixed.

I should have done more research and bought a device from a company like HP that [actually provides open-source drivers]("http://hplipopensource.com/hplip-web/about.html").

---

### Post by Jean-Marc Valin on 2010-08-29
> **tobiasly said:**
> Just in case anyone may read this and be persuaded into getting a Samsung printer or multifunction device, DON'T. Their scanner drivers no longer correctly work on 10.04 64-bit and despite the efforts of [community members such as Tweedledee]("http://ubuntuforums.org/showthread.php?t=341621"), the fact that these drivers are proprietary is tying their hands in getting them fixed.

I was a bit discouraged when reading this (after I bought an SCX-4828)) but it turns out that it's not a bit deal. What I did was extract the .ppd file from the driver that comes with the printer and tell the printer config to use it. Problem solved for printing (without the ppd file, it's still manageable, but you may lose some functionality). As for the scanner, it was again just a matter of adding its usb device id to the sane configuration. I've only had the printer for a day, but so far it seems to work well on Linux. I'm not sure what the proprietary drivers do, but it doesn't see that important.

---

### Post by jmspeex on 2010-09-04
Sorry, I just realised that the SCX-4826 and the SCX-4828 are two totally different beasts. The SCX-4828 works fine for me because it's postscript, but apparently the SCX-4826 doesn't handle postscript, so apparently it requires the proprietary driver.

---

### Post by Berduchwal on 2011-02-07
Samsung made an updated on 6 January 2011 and my Samsung SCX-4828FN no longer scans! It used to work fine before the update.

For those of you that own the device please raise a service call with samsung as I did. 

Today I escalated it to a complain and will sue them if needed.

---

### Post by frog662 on 2011-04-16
Have great experience with on-line chat at Samsung site. Try it. You'll like the prompt service.

---

