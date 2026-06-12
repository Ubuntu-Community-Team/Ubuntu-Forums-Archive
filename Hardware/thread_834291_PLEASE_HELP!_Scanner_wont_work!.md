---
title: "PLEASE HELP! Scanner wont work!"
date: 2008-06-19
forum: Hardware
---

### Post by chad2408m on 2008-06-19
Hi, I have a HP Scanjet 4470c and it doesnt work at all with XSane.  I have installed the libextras for Xsane and it finds my scanner, but whenever I scan nothing works.

When I use CCD Type 0, I get a black page
When I use CCD Type 1, It says 'Error during device I/O'

Does anyone know how to change the settings to work.  If anyone has this scanner, can you please tell me what you did to make it work. I have already removed Windows XP from the hard drive, but I might need to put it back because I need to make copies of important documents.  Please tell me how to make the scanner work, even without color!  Any help is greatly appreciated.

---

### Post by phidia on 2008-06-19
When you enter (in a terminal window) sane-find-scanner or scanimage -L what output do you get?
From the sane site I see [your scanner]("http://www.sane-project.org/cgi-bin/driver.pl?manu=hewlett+packard&model=4470c&bus=any&v=&p=") is listed as "good". Have you looked at the rts8891 [backend]("http://stef.dev.free.fr/sane/rts8891/index.html") & manual page links? The manual page link seems to be broken, but from the bottom of the backend page there is this:
> Sources
The full SANE CVS sources patched with the backend are at sane-backends-rts8891.tar.gz
Unpack the sources, configure and compile.
Or you can grab it as patch against SANE 1.0.19 rts8891.patch.gz
You may use the script to do a preview with scanimage and full debug activated, and xrun to run xsane before doing a system wide install.
You can send me or SANE devel (registration required) feedback about your success or problem reports. 

---

### Post by chad2408m on 2008-06-25
I got it to work, however in a wierd way.  I relized that while the image was being scanned, if i didnt move the mouse, everything came out near perfect.  if i moved the mouse a lot, it would either not work or everything would be scrambled.  thanks for the link and support!

---

