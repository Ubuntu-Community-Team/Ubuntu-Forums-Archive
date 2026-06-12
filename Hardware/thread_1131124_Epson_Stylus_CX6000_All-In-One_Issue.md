---
title: "Epson Stylus CX6000 All-In-One Issue"
date: 2009-04-20
forum: Hardware
---

### Post by delirium85 on 2009-04-20
Ooookay, I've long been a lurker here, never even registered until today.  After searching the interwebs extensively I have found no answer.  I have an Epson Stylus CX6000 All-in-One.  The printer works fine without an issue.  But my scanner is not working.  I am using 8.10 Intrepid Ibex.  I made the mistake of editing my /etc/sane.d/dll.conf and not backing it up first :shock:  So I don't remember exactly what I enabled and what I disabled.  If this question has already been answered, I apologize for asking it again, but I'm tired and it's been a long day of searching under every rock for this issue.  Any, and I mean any, help will be GREATLY appreciated.  Thanks!!

DJ

---

### Post by ajgreeny on 2009-04-20
If you mean that your scanner used to work but now does not, since you edited those files, you should uninstall completely libsane and probably also xsane applications if you have them (completely remove in synaptic) and then reinstall.  As the file you edited is in /etc and not in your home, it should ber removed when you do a complete removal of the application, but then added back when you reinstall.

If your scanner never worked, then I don't know what to suggest other than look at the hardware info in these two sites for help.
[http://www.ubuntuhcl.org/browse/search](http://www.ubuntuhcl.org/browse/search)
[https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport)

---

### Post by delirium85 on 2009-04-20
I apologize for the confusion in my previous post, it worked on windows, but since the switch to Ubuntu it hasn't worked.  I haven't had a reason to even test it until today when it became a big issue as I need to scan some important documents to send around the world.  It have never worked on Ubuntu.  I have read several things where people have gotten the scanner to work for them, but it was on older versions, and it isn't working for me on Ibex.  Thanks for the reply though!

DJ

---

### Post by ajgreeny on 2009-04-20
Here's some info on related scanner/printer machines from the second site I referred to earlier which may help.
 ```
Epson 
    Stylus CX5500 
    gutenprint 
    Yes 
    Yes 
    8.04 (Hardy) 
    Use the Stylus D68 CUPS + Gutenprint Driver (Don't choose the 'simplified' one though), Scanner instructions [http://ubuntuforums.org/showthread.php?t=627471](http://ubuntuforums.org/showthread.php?t=627471) 
    2007-Mar-14 
```
     ```
Epson 
    Stylus CX6500 
    ?? 
    Yes 
    Yes 
    

   To enable the scanner you need to add the product ID and device ID to /etc/sane.d/epson.conf, ie set the usb line to usb 0x04b8 0x0813. You can get the IDs with sane-find-scanner -q. 
    2006-Oct-02 
```
     ```
Epson 
    Stylus CX6600 
    stp-escp2-cx6600.5.0.ppd 
    Yes 
    Yes 
    6.10 (Edgy) 
    To enable the scanner (for non-root): add the vendor ID (0x04b8) and product ID (0x0813) to /etc/udev/rules.d/45-libsane.rules
2006-Oct-09 
```

---

### Post by rickyrockrat on 2010-03-09
I got this to work on Hardy. Here's the link I followed:
[https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/314485](https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/314485)

Basically, just add the vid:pid to the sane file:
1) sudo gedit /etc/sane.d/epson.conf
Add this to the last line:
usb 0x04b8 0x082e
2) Restart the udev service or reboot:
sudo /etc/init.d/udev restart
3) Unplug and replug the scanner.

Cheers!

---

