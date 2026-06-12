---
title: "Which scanner?"
date: 2007-08-09
forum: Hardware &amp; Laptops
---

### Post by dryder on 2007-08-09
Hi,

A question I guess mainly for Aussie members ... :-)

I have the flatbed Microtek Scanmaker E6 (SCSI) and Scanmaker 5600 (USB) both of which work very well in Windows. But not at all in Ubuntu.

The SANE site does not give me models which I can find as available in Australia. So can somebody tell me what scanner they have working in Australia in Ubuntu that is currently available? I need the resolution of of  2400x4800 non-interpolated?

Many thanks,
David

---

### Post by linuxwizard on 2007-08-10
I was looking around in Sane and your Scanmaker 5600 is unsupported but your Microtek Scanmaker E6 should work in Ubuntu it is classified as good. 

[http://www.sane-project.org/man/sane-microtek.5.html](http://www.sane-project.org/man/sane-microtek.5.html)

[http://www.sane-project.org/sane-mfgs.html#Z-MICROTEK](http://www.sane-project.org/sane-mfgs.html#Z-MICROTEK)

[https://help.ubuntu.com/community/ScanningHowTo](https://help.ubuntu.com/community/ScanningHowTo)


good: means the device is usable for day-to-day work. Some rather exotic features may be missing.

What make/models scanners are you finding in Australia ?

---

### Post by dryder on 2007-08-13
Hi,

My apologies for not replying earlier.

I will try hooking up the ScanMaker E6 but I would prefer a more recent model for speed.
> What make/models scanners are you finding in Australia ?
I have looked for Microtek USB models in the Scanmaker range but none are supported and Epson scanners of the Perfection range that are completely supported. Of the latter, I can not find the models in Australia that are fully supported by SANE.

Whatever I get I need 2400x4800dpi. As I don't know other manufacturers well enough I felt asking what others use (here) was a good starting point :-)

David

---

### Post by dryder on 2008-01-21
May I bump this up please?

Does anybody know of [COLOR="Red"]**any**[/COLOR] USB flatbed scanner [COLOR="Red"]**currently available in Australia**[/COLOR] that works with SANE/Ubuntu?

Preferably (but only *preferably*) 4800x9600 dpi. I don't need film scanner 'parts'.

I have gone through the SANE site many times but trying to cross reference to a currently available model has sent me cross-eyed ](*,)

Many thanks,
David

---

### Post by stroyan on 2008-01-21
You may get better results by looking at multifunction printers.
They often support 4800 dpi scanning.  Some support 9600 dpi scanning.
There are many, many MFPs that are supported for scanning by the HPLIP project.
See [http://hplip.sourceforge.net/supported_devices/inkjet_aio.html](http://hplip.sourceforge.net/supported_devices/inkjet_aio.html) for the long list.

---

### Post by dryder on 2008-01-21
Thanks stroyan but I am avoiding MFDs.

I had a phone call from Epson after bumping this (yes, they 'know' me. Does somebody there use Ubuntu/watch these sites ??? ):P ) Epson's Perfection V350 Photo has a SANE driver. It requires DFSG non-free iscan-plugin-gt-f700<br>overseas version of the GT-F700, whatever that is, but at least there is a driver.

I can not find an email address for SANE to ask questions.

The compatibility is 'good' = the device is usable for day-to-day work. Some rather exotic features may be missing. Does anybody know if this is simply the quick function buttons? I need it primarily for photo scanning. Could I expect it to scan an image properly to the dpi I want? Any ideas on what 'good' means would be a great help - Epson do not know what is meant by 'exotic features'.

Many thanks and my apologies to be pushing this thread so much for help.

David

---

### Post by mikeize on 2008-02-13
I have an HP PSC series (print, scan, copy).  It works great with Ubuntu, and from what I hear, this is often the case with HP.  Mine is 4 or 5 years old, but I believe it is 9600 dpi, works with xSane, and you can get them in the US for maybe $100-$200 usd.  I imagine they are available in Australia as well.

---

### Post by Rhubarb on 2008-02-13
I've recently bought an Epson V200 scanner here in Australia.
It works in xsane fine, 300, 2400, and 4800dpi is available.

Though I am mostly interested in scanning in positive slides, you might discover more here:
[http://ubuntuforums.org/showthread.php?t=627650](http://ubuntuforums.org/showthread.php?t=627650)

Please note that this scanner only really works if you have the 32bit version of Ubuntu.
(I've yet to try to get it working in 64bit yet).

---

### Post by dryder on 2008-02-14
Thanks people,

While I was writing another post it seems Ubuntu lovers read my mind and renewed this one - I thought this had 'died' ....

Unfortunately the V200 lid opens sideways up - I need a lid that opens front up (personal needs) - - but I now know what epkowa does/is ...

... and I would like it to work in 64 bit as well for when I move up to that ...

As I started a new thread (could not find this one!) [**[COLOR="Blue"]here[/COLOR]**]("http://ubuntuforums.org/showthread.php?t=696386") could we close this thread, please?

(Bad etiquette I know and I apologise).

David

---

