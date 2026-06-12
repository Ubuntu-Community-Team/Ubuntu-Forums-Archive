---
title: "xsane refuses to detect scanner"
date: 2006-03-09
forum: Hardware &amp; Laptops
---

### Post by sparX CG on 2006-03-09
Hi all, I installed Dapper Drake on my computer, setting it up to be as productive as Windows... :)  It's rather stable and funtional for me.

Here's my problem though:

I have both a Logitech QuickCam webcam and a UMAX Astra scanner plugged into my computer.  When I load up xsane, it only detects the webcam and I can't figure out how to use the scanner.

Any ideas?

---

### Post by Stealth on 2006-03-10
[Is it supported?]("http://www.sane-project.org/sane-mfgs.html#Z-UMAX")

---

### Post by sparX CG on 2006-03-10
Yup, it is.  It's an Astra 610P.  The problem is that I don't know how to select it.

---

### Post by rayburn on 2006-03-10
There is some useful info in this thread:


[http://www.ubuntuforums.org/showthread.php?t=106647](http://www.ubuntuforums.org/showthread.php?t=106647)


Different scanners I know, but should prove helpful in solving your problem.

---

### Post by sparX CG on 2006-03-10
Thanks for that thread...  Didn't help much though.

Isn't there a way to switch devices?  Oh, and my scanner is connected through a parallel port.  My printer is hooked up to the scanner.  The printer isn't detected either.  It worked fine in Fedora though, although I never tried using the scanner there.

---

### Post by sparX CG on 2006-03-12
Hmm...  Anyone?  I really want to get that scanner working...

---

### Post by jal on 2006-10-25
*bump*

I have exactly the same problem (which is what led me to this thread).
Same scanner Umax Astra 610P,on parallel port, scanner has a 'pass through' to the printer which is working fine.

I changed the /etc/sane.d/dll.conf, commenting out umax and umax1220u, and adding (uncommenting) umax_pp.

I changed the /etc/sane.d/umax_pp.conf so it has these lines:
option buffer 2097152
port /dev/parport0
option astra 610

there are some files in /usr/lib/sane:
libsane-umax_pp.la
libsane-umax_pp.so.1
libsane-umax_pp.so.1.0.17

I reckon I'm good to go. Sadly, xsane pops a dialog, "no devices available"

Any advices from the friendly Ubuntu tribe?

---

### Post by magog45 on 2006-11-27
I have a similar problem with a hp3200c(umax1220p) and by commenting out the umax references in etc/sane.d/dll.conf and only retaining the umax_pp. I also added permissions for myself to lp and parport0, I now get xsane to see the scanner and startup but that is it. The program refuses to respond after that, I have not however changed anything in umax_pp.conf. I see this is an old thread anyone having any success out there?:-k

---

