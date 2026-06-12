---
title: "HP LaserJet 1320 printing speed is very slow"
date: 2009-03-20
forum: Installation &amp; Upgrades
---

### Post by bhuvankrishna on 2009-03-20
I have a HP LaserJet 1320 series which is connected to the system through serial port. I checked the dmesg output and it is giving this as the output "[   21.584064] parport0: Printer, Hewlett-Packard hp LaserJet 1320 series" The device is located at /dev/lp0. This printer is shared in the network via the system to which it is connected. This printer is suppososed to run at a speed of 22 ppm as per the hp's [website]("http://h10010.www1.hp.com/wwpc/us/en/sm/WF06b/18972-236251-236263-14638-f51-410622-410624-410625.html") what i get is hardly 7 ppm which is very slow. But when i give an empty page print the printer works with full speed. Is there an way to increase the speed of the printer?

I am using Ubuntu 8.10 updated till yesterday. the printer driver is "HP LaserJet 1320 series Foomatic/hpijs, hpijs 2.8.7".

---

### Post by jayshomebrew on 2010-10-17
I have the HP1300 printer, and had the same problem. I changed the driver to be generic, PCL 5e Foomatic/hpijs-pcl5e shown below, and it works perfectly.

symptom: 15 minutes to print pdfs, or any other file.
after fix: 10 - 20 seconds to print the same pdf image.

add a new printer, then when it asks for the driver select: **generic**
[IMG]http://img838.imageshack.us/img838/8573/screenshotnewprinter1.png[/IMG]

then: **PCL 5e Printer Foomatic/hpijs-pcl5e**
[IMG]http://img828.imageshack.us/img828/6584/screenshotnewprinter2.png[/IMG]

thats it!:)

---

### Post by wujastyk on 2010-12-09
Worked like a treat for me too.  Pages pouring out of my LJ1300, with no pauses.  Thank you very much!
Dominik Wujastyk

---

### Post by feistybird on 2010-12-30
Thanks very much, jayshomebrew, 

My hp-1200 printer now prints very fast!

---

### Post by leoperbo on 2011-01-10
Worked for me too! Thank you!:D

---

### Post by bingotailspin on 2011-01-15
Thank you! Thank you!

---

### Post by MonkeyWrench32 on 2011-02-27
This also worked for my HP LaserJet 1200. Thanks a million!

---

### Post by yavoh on 2011-03-01
This worked for me as far as speed is concerned but now the printing quality is worse- everything looks much lighter.  There doesn't seem to be an option for increasing the "darkness," so to speak. Is this happening to anyone else?

---

### Post by QBX on 2011-06-12
Thanks, this still works well in Natty in 2011! Much appreciated.

---

### Post by walt.smith1960 on 2011-06-12
Not an HP printer, but there may be similarities.  The first thing that comes to mind is HP-LIP, the utilities for HP printers found in Synaptic.  Install that and see if it makes a difference.  I have a Brother MFD which is often found as an HP4050 laser. It was slow--like 1-2 pages/minute slow.  There were CUPS drivers available in Synaptic.  I downloaded them then then went to the printers page.  Look through the available drivers.  One choice was CUPS for Brother laser or something like that.  I picked it as the driver and speed went back to what it was under Windows. Just a couple other things to look at.

---

### Post by Chriske on 2011-07-11
> **jayshomebrew said:**
> I have the HP1300 printer, and had the same problem. I changed the driver to be generic, PCL 5e Foomatic/hpijs-pcl5e shown below, and it works perfectly.

symptom: 15 minutes to print pdfs, or any other file.
after fix: 10 - 20 seconds to print the same pdf image.

add a new printer, then when it asks for the driver select: **generic**
[IMG]http://img838.imageshack.us/img838/8573/screenshotnewprinter1.png[/IMG]

then: **PCL 5e Printer Foomatic/hpijs-pcl5e**
[IMG]http://img828.imageshack.us/img828/6584/screenshotnewprinter2.png[/IMG]

thats it!:)

Hussah! :D

It also worked for my HP2200D Laserjet (chose a different generic driver obviously).

Many thanks.

---

### Post by dragonfly41 on 2011-07-12
I started a new thread a few minutes ago on slow printing of PDF .. 
but then found this thread ..

I have Hewlett Packard HP Laser Jet 2100 series

any tips on what generic driver to use?

I'm seeing error message when trying generic drivers ..

[COLOR=Navy]CUPS server error

client-error-not-possible[/COLOR]

---

### Post by foresthill on 2011-07-12
With 10.19, the solution to slow printing PDF files is pretty simple. Install the program XPDF from Software Center, and use that as your default program to open and print PDF's. PDF's should print about as fast as in Windows from XPDF.

However, if you are running 11.04 (I gave up on that noise a while back) there's not much I know that can be done. Reason being that XPDF crashes like crazy in 11.04, and trying to print PDF's using the Document Viewer takes literally days, just like in 10.10 and 10.04, and 9.10.

HTH.

---

### Post by Chriske on 2011-07-13
> **dragonfly41 said:**
> I started a new thread a few minutes ago on slow printing of PDF .. 
but then found this thread ..

I have Hewlett Packard HP Laser Jet 2100 series

any tips on what generic driver to use?

I'm seeing error message when trying generic drivers ..

[COLOR=Navy]CUPS server error

client-error-not-possible[/COLOR]

Before I had this current issue I had a problem printing a large PDF too.

I'm *pretty sure* what I did was to install Adobe Reader and use that for printing and it worked fine.

[http://www.liberiangeek.net/2011/04/install-adobe-reader-ubuntu-11-04-natty-narwhal/](http://www.liberiangeek.net/2011/04/install-adobe-reader-ubuntu-11-04-natty-narwhal/)

Hope that helps.

---

### Post by dragonfly41 on 2011-07-13
Thanks for the tips .. I installed xpdf and that now prints PDF files very smartly.  Solved.

I've also now installed Adobe Reader 9 to try that too.

I'll also try printing from Okular.

I should have mentioned that I'm on ubuntu 10.10.

---

### Post by foresthill on 2011-07-13
Hmmm. Maybe I will try Adobe Reader and Ocular in 11.04. Though I prefer XPDF because it's such a minimalistic program, where as Adobe Reader most certainly is not. And Ocular, IIRC, requires a bunch of KDE desktop environment-type programs to get installed so it will work.

---

### Post by foresthill on 2011-07-14
OK, I finally got around to installing Okular in 11.04. It prints PDF files at normal speed and doesn't crash like XPDF does. 

So anyone out there reading this thread who's running 11.04, using an HP printer, and having problems printing PDF files, install Okular and you should be good to go.

---

### Post by mksundaram on 2011-08-02
Will it work with HP Inkjet 3940 too ?

---

### Post by imcampos on 2011-10-09
I have the same problem with the HP Laserjet 1200,connected directly to my notebook via USB cable. How do I get to these screens that allow me to choose the driver? 
I tried the following path: deleted the printer, reconnected, but Ubuntu 11.04 just reinstalls it without asking anything.

---

### Post by jfklingler on 2012-05-24
I so want to live the Linux life, but it's stuff like this that makes people insane. If you pick the driver that *exactly *matches your printer, it doesn't work. If, on the other hand, you pick "Generic", everything works just fine. How are "regular" people supposed to know they should try random drivers when the one for their printer doesn't work? How is it that printing is still a challenge? Sorry, I'm not trying to be inflammatory - just expressing my frustration.

---

### Post by oldos2er on 2012-05-24
Old thread closed.

"If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful."

---

