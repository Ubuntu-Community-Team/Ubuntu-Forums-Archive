---
title: "Noob Question on using a Scanner with Ubuntu"
date: 2009-06-10
forum: Installation &amp; Upgrades
---

### Post by oldjarhead on 2009-06-10
Hi!

I have been using Ubuntu on my secondary computer for a few months and love it.  I just upgraded to 9.04 and want to use my scanner on this computer.  I have a Xerox Documate 152 scanner.

Questions:  1 - do I need any kind of drivers?  Where would I find them?
2 - the software that came with the scanner (OmniPage Pro and Paperport) appears to be for XP only.  Is there Ubuntu compatible software that will allow me to scan and then have the computer capture it as a pdf file?

Thanks for your help!

---

### Post by cariboo on 2009-06-10
Check the [Sane Database]("http://www.sane-project.org/sane-mfgs.html#Z-XEROX") to see if your scanner is supported. Your windows software won't work on Linux. There is replacement ocr software in the repositories. Go to System-->Administration-->Synaptic Package Manager, click the search button and type ocr.

---

### Post by zadehas on 2009-06-10
You can use Gimp for scanning and save the output in just about any graphic format it supports.

If your scanner is supported, as noted in the previous post, do this:

1. Start Gimp;
2. In the File menu, choose Create -> XSane -> Device dialog;
3. A dialog will appear that will allow you to scan;
4. After scanning, you will have a new unsaved Gimp file that you can save just as you would any other graphic.

---

### Post by oldjarhead on 2009-06-10
Thanks!  It looks like it'll work.  I'll give it a shot first thing tomorrow.

---

