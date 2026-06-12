---
title: "Wireless scanner just broke"
date: 2014-12-20
forum: Hardware
---

### Post by dorlow on 2014-12-20
I have an Epson WorkForce 845 printer scanner combo.  Right out of the box, scanning works using Simple Scan.  I've used it for years.  A few distros ago, Simple Scan worked right out of the box perfect with duplex scanning (scanning both sides of the paper.)  Something went wrong in the last few distro versions and now duplex scanning, when I try doing that, it messes up.  It will start to scan then half way through the scan, the printer's LCD screen will turn all green and flash on and off and I have to power it off and kill simple scan.

But simple scan works with the document table and single side document feeder scans fine.  Just not duplex scanning.

Well, I went out to the web and found another scanning program.  It's called Vue Scan.  I downloaded the demo and the demo worked great other than it put watermarks on each scan.  But document table and duplex scanning worked perfect.  I paid $80 to register for the pro version of Vue Scan.  Since registering for Vue Scan, Vue Scan doesn't scan any more and also Simple Scan quit working too.  How do I go about fixing scanning in general?  I'm thinking it's something to do with connecting the xsane service to my wireless scanner.  Somehow it lost connection.

---

### Post by dorlow on 2014-12-20
Ok, I'm baffled.  After troubleshooting about an hour, I decided I'll just reinstall Ubuntu.  I've installed Ubuntu a handful of times over the last few years.  This scanner works right out of the box flawlessly everytime.  But I reinstalled and it still doesn't work.  I formatted and reinstalled again just incase I was thinking maybe I forgot to format and some settings carried through the reinstall.  Nope, still broke.

---

### Post by sammiev on 2014-12-20
I just did an Epson Printer/Scanner today in about 2 min.

I use the [Epson Download Site]("http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX").

Just enter 845 in the search bar.

---

### Post by dorlow on 2014-12-20
I tried installing the base installer, networking, etc. from the epson site.  Didn't work either.  Every time I've ever installed Ubuntu in the past with the same PC and scanner, it just worked right out of the box even with the same version of Ubuntu months ago.  Somehow I install a new scanning program earlier and it breaks everything.  Then format it and somehow what the program broke is still broke, which makes absolutely no sense after a full format and reload.

---

### Post by sammiev on 2014-12-20
I would erase all that you have tried before you try the link I have supplied.
Have you also try rebooting the router?
Maybe your router has been the problem all along.

---

### Post by dorlow on 2014-12-21
> **sammiev said:**
> I would erase all that you have tried before you try the link I have supplied.
Have you also try rebooting the router?
Maybe your router has been the problem all along.

No, I formatted and reloaded the whole OS.  I've done this many times over the years and the scanner just works everytime without any setup.  I just load Ubuntu, open Simple Scan and it just works without any setup.  Now I broke it, formatted and it's still broke.  I'll keep the router thing in mind.  I have some transfers going right now that I don't want to reboot the router for.  I'm loading Windows 7 in a VM so I can use the scanner.  All my files are sitting on a NAS so it's not too big of a deal to use a VM.  But I do like Simple Scan in Linux much better than the Epson software, so hopefully I figure out why it won't work.

---

### Post by pqwoerituytrueiwoq on 2014-12-21
If you are accessing the scanner via a sane share you need to configure the client
* you will need to have the scanner's IP address in here [FONT=courier new]/etc/sane.d/net.conf[/FONT] just add it at the end of the file
if you are using 14.04 i suggest grabbing  the necessary deb files from 14.10, scanimage has been crashing left/right for the last few versions
here is a copy of the 14.10 32bit/64bit debs [https://www.mediafire.com/?iq2s6qaw9y4slcs](https://www.mediafire.com/?iq2s6qaw9y4slcs)

if you can get the scanner to show up in scanimage -L the software in my signature will work

if you look in this thread it tell you how to share a scanner and connect to a shared scanner
[http://ubuntuforums.org/showthread.php?t=1519201](http://ubuntuforums.org/showthread.php?t=1519201) (if you want the web interface the current version is in my signature)

---

### Post by dorlow on 2014-12-21
Ok, not sure what just happened.  I just got a prompt to update my Ubuntu.  It installed a new kernel.  After the update, my scanner is magically working again.

---

