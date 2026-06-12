---
title: "scanning with HP Officejet 6110 all-in-one"
date: 2006-12-20
forum: Hardware &amp; Laptops
---

### Post by zdl on 2006-12-20
Hi guys

I have just decided to move completely to Ubuntu when I purchased a new PC. So far everything is fine including the new environments and software with 2 exceptions: the webcam and scanning with my Officejet 6110 all-in-one. I've been searching the web for help and done all sort of updates and fixes... but the printer (which was immediately) recognized) still does not scan :( 

I have now installed the gspcav1-20061216.tar.gz pack and also added the 'hpaio' line to the /etc/sane.d/dll.conf

still faxing and scanning facilities are not available.

x-sane finds the printer but still reports  fail accessing  'hpaio:/usb/Officejet_6110_series?serial... ... ...'


and from within writer  [ insert/picture/scan/select source ]  it also finds the same 'hpaio:/usb/Officejet_6110_series?serial... ... ...' end then either stops or crashes  

:( :( :( 

any ideas? thanks

zdl

---

### Post by aleska on 2007-02-13
This question may have been answered through some other medium, but I'm very curious about the answer.  I too have an Officejet 6110 and was just looking around to find out how to scan.  So, can anyone point in the right direction here?

---

### Post by aleska on 2007-02-14
Well, I found a program in the repositories, named **hpoj**, which supposedly loads all the necessary scanner drivers for most HP all-in-one models.   My problem is that it too looks for scanners attached by usb or parallel port.  Mine is attached to a nas device (Buffalo Linkstation - running samba).  
If anybody knows what I could should do, I'd love the advice.  
Should I be looking into contacting the publishers/maintainers of **hpoj**?
Thanks in advance.

ps - if anyone knows how to get one of those crappy logitech usb connected webcams working...I'd love to hear about it.

---

### Post by zdl on 2007-02-15
Hi! No. Unfortunately not. I did download an endless string of things that were supposed to fix it. To be honest I was unable to follow the instructions to the end because everytime I did it somewhere along the line some other stuff was required and if/when I tried to install that other stuff, something else generated an error message and, well, past the holidays I simply could not afford 24h attention to the ideosyncracies of Ubuntu. For the time being I decided that when I need to scan some stuff I just resort to that other OS that I kept on my laptop. In spite of all my sympathy to Linux and my decision not to go back to 'you no what', there is a limit to what I think is acceptable in terms of hassle to install a printer and this one was way too much. I'll give it a try next time I have some time off. 

zdl

---

### Post by tajreed on 2007-02-15
Have you tried setting up with HPLIP in the repos. I have a 5180 all-in -one and it was set up perfectly using HPLIP.

---

### Post by Matt Yun on 2007-05-23
> **aleska said:**
> ps - if anyone knows how to get one of those crappy logitech usb connected webcams working...I'd love to hear about it.

This is off-topic, but I couldn't resist answering.  You need the *gspca* kernel module, which is a generic driver for many, many different models of web cam.  Do the following (as sudo or root):

# apt-get install gspca-source libpt-plugins*
# module-assistant build gspca
# module-assistant install gspca
# modprobe gspca

To check if the module is loaded, do:
$ lsmod | grep gspca

If you want this module loaded automatically at next boot, then add gspca to your /etc/modules list.

See if Ekiga recognizes your webcam.  The libpt-plugins* are a series of plugin libraries for different webcams.  Ekiga should automatically detect and load the correct library, but just in case, libpt-plugins-v4l should work for most usb webcams.

See this thread:  [http://ubuntuforums.org/showthread.php?t=303330](http://ubuntuforums.org/showthread.php?t=303330)

---

