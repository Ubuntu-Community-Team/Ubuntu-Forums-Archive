---
title: "Hp Deskjet 1512 printer failed after updates, running Ubuntu 18.04"
date: 2020-04-30
forum: Hardware
---

### Post by jjconstru1 on 2020-04-30
Hello, 


CLOSED: Not fixed. Going with a fresh install. Thank you all for your time.

Printer won't print, print menu pops up, clicking print does nothing on the hardware. HP Deskjet 1512 works from windows 7 in dual boot. Used to work in Ubuntu 18.04, before updates. Cups was not running, got it running, printing worked once, stopped working, Tried upgrading hplip printer software 3.17.10 to hplip-3.18.3.run, downloaded from SourceForge. Twice, taking 10 or 15 minutes each, it failed to load. 
Is it likely to fix this problem, or should I just reinstall Ubuntu OS? I have installed Timeshift but not until after the printer trouble started, so a good restore point does not exist.
Thanks,
jjconstr

---

### Post by johngalt42 on 2020-04-30
I used the link the HP Website provided for my HP Officejet Pro 8620 and downloaded the printer software.  Are you using the WIFI or USB connection for the printer?  I had to load the software using the USB port first.  After first, it acted like it wasn't but after rebooting it started working.

---

### Post by johngalt42 on 2020-04-30
wasn't but = wasn't working but

---

### Post by jjconstru1 on 2020-04-30
Am using the usb cable with my printer. I'll try to find the usb software. Are you referring to the linux usb software? where would I look for that? I have synaptics Package Manager. Or do I look in Hp linux printer site? I got the printer download from sourceforge.net/projects/hplip/#.
Thanks

---

### Post by jjconstru1 on 2020-04-30
> **johngalt42 said:**
> wasn't but = wasn't working but

Sorry, but I don't understand your reply. 

Searching in Synaptics Package Manager, for hplip usb printer, I get no files referring to usb, only;

hplip

libhp mud-dev

libhpmud0

printer-driver-hpcups

printer-driver-hpijs

---

### Post by jjconstru1 on 2020-05-01
I figured out post 3 was referring to post 2. Sorry, my confusion.

---

### Post by jjconstru1 on 2020-05-01
> **johngalt42 said:**
> wasn't but = wasn't working but

When I tried to install the hplip 3.18.3.run package, it opened in Gedit, text editor. I  didn't realize what was happening at first.

SourceForge Reviews (of installing hplip software), has an interesting idea. Does it make sense to you? 

                      [Managed to install it for my hp 1415cfnw on Ubuntu 17.10 in  order to be able to scan (Ubuntu already recognizes printer and allows  printing). Though I replaced 17.10 by a fresh 18.04 and cannot install  the driver anymore. Some characters are not recognized.  EDIT  _I was not installing properly_. _You need to locate into install directory  and "sh hplip-3.18.3.run"_ or other version of hplip         .]

     
                                              
What would be the exact commands to use?

Sorry for my lack of knowledge.

jjconstr

---

### Post by jjconstru1 on 2020-05-02
> **johngalt42 said:**
> I used the link the HP Website provided for my HP Officejet Pro 8620 and downloaded the printer software.  Are you using the WIFI or USB connection for the printer?  I had to load the software using the USB port first.  After first, it acted like it wasn't but after rebooting it started working.


Can anyone tell me how to load the software using the USB port?

Regards

---

### Post by brian_p on 2020-05-02
Give the output of ```
lpinfo -v
```

---

### Post by jjconstru1 on 2020-05-03
> **brian_p said:**
> Give the output of ```
lpinfo -v
```

Output is 
jjconstr@Aspire-5733Z:~$ lpinfo -v
network lpd
network beh
file cups-brf:/
network socket
direct hp
network ipps
network http
network ipp
network https
direct hpfax
jjconstr@Aspire-5733Z:~$ 


i tried saving printer software 3.18.3 to usb stick, then double clicking it from there. It opened in text editor gedit. As it did when double clicked from home folder. There is a very slow progress bar at the top. I wonder if it should be opened in Terminal.

Thanks for your reply.
Jerry

---

### Post by CelticWarrior on 2020-05-03
Please install hplip from the repositories. Ubuntu 20.04 already has v. 3.20.

---

### Post by brian_p on 2020-05-03
You have the printer USB connected but the *lpinfo -v* output does not display a line beginning with **direct usb**. I do not know of any way to set up the printer without this information.

---

