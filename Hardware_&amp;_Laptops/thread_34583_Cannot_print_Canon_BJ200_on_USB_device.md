---
title: "Cannot print: Canon BJ200 on USB device"
date: 2005-05-15
forum: Hardware &amp; Laptops
---

### Post by govert on 2005-05-15
I don't really know what's going on here...

I have a canon BJ200 installed over my USB port using a USB-PAR bridge.
/dev/usb/lp0 is recognised and issuing

% echo "Hello World" > /dev/usb/lp0   WORKS.

lpr [file] does NOT work.  :^o 

I'm using KDE (Kubuntu)  and have installed the CUPS drivers,
for "Canon BJ-200 Foomatic". device /dev/usb/lp0


any ideas?

---

### Post by David Haas on 2005-05-16
govert--After selecting your printer, the Canon BJ200, I assume that you selected this PPD file in foomatic-ppds: Canon-BJ-200-bj200.ppd.gz. If so, then a copy of this file should have been automatically placed in /etc/cups/ppd, for this is what I've seen with the printers I've installed. By checking this, you can at least see whether the PPD file is properly installed.
David

---

### Post by govert on 2005-05-17
[QUOTE=David Haas]govert--After selecting your printer, the Canon BJ200, I assume that you selected this PPD file in foomatic-ppds: Canon-BJ-200-bj200.ppd.gz. If so, then a copy of this file should have been automatically placed in /etc/cups/ppd, for this is what I've seen with the printers I've installed. By checking this, you can at least see whether the PPD file is properly installed.
David[/QUOTE]

I have only done what kprinter prompted me to do, 
which is to select a printer. I named it "bj" and there is
a  /etc/cups/ppd/bj.ppd file. 

Where can I find the original foomatic PPDs to compare with?

---

### Post by David Haas on 2005-05-17
I can't cite the specific selections in kprinter, because I'm running Ubuntu (with Gnome) not Kubuntu (with KDE), but I think you must not have selected your specific Canon model or the specific PPD file for it, because naming the printer "bj" and selecting a PPD file called "bj.ppd" doesn't seem to represent your model. Doesn't kprinter present a long list of Canon printers?--it must. To locate the PPD file for your Canon go to the Canon directory in your Terminal (shell). The location is /usr/share/cups/model/foomatic-ppds/Canon (The command is $ cd /usr/share/cups/model/foomatic-ppds/Canon). At the Canon directory, do a ls command and you'll see all the Canon PPD files listed. Yours is Canon-BJ-200-bj200.ppd.gz.  Your printer is supported, so you can count on getting it to work.
David

---

### Post by govert on 2005-05-18
[QUOTE=David Haas]I can't cite the specific selections in kprinter, because I'm running Ubuntu (with Gnome) not Kubuntu (with KDE), but I think you must not have selected your specific Canon model or the specific PPD file for it, because naming the printer "bj" and selecting a PPD file called "bj.ppd" doesn't seem to represent your model. Doesn't kprinter present a long list of Canon printers?--it must. To locate the PPD file for your Canon go to the Canon directory in your Terminal (shell). The location is /usr/share/cups/model/foomatic-ppds/Canon (The command is $ cd /usr/share/cups/model/foomatic-ppds/Canon). At the Canon directory, do a ls command and you'll see all the Canon PPD files listed. Yours is Canon-BJ-200-bj200.ppd.gz.  Your printer is supported, so you can count on getting it to work.
David[/QUOTE]

Thanks for pointing out where the PPD files are located.

The ppd that is installed is correct. (I made a diff btw
 /usr/share/cups/model/foomatic-ppds/Canon/Canon-BJ-200-bj200.ppd.gz (unzipped) and /etc/cups/ppd/bj.ppd and they are identical)

bj.ppd _does_ represent my model, I think kprinter renamed it to "Local printer name". 

(*still not working*)
Somebody wants my CUPS logs????   :grin: 

/M

---

### Post by David Haas on 2005-05-18
Because you are running Kubuntu, at this point you might get the best help in the Kubuntu section of the Forum. Others who have set up their printers in Kubuntu might know best what could go wrong when using the KDE printer GUI.
David

---

### Post by David Haas on 2005-05-18
Another thought occurred to me, based on another's experience: "It's working!

I went into /etc/cups/ppd and found the .ppd driver for my printer. I checked the permissions and noticed that they were pretty anemic including group and root read and root write. I deleted that file (driver) from the command line and reinstalled the printer from the gui. It now works like a charm. It seems that it should have had "others" read permission. I suppose that I could also have added my user name to the group, but I just let it do its thing."

So, you could check the permissions in your ppd file. Mine are:  -rw-r--r--  1 cupsys lpadmin 19329 2005-05-12 16:58 DeskJet-5740.ppd

David

---

### Post by ajt3nc on 2005-05-20
I have a cannon BJ240 and had to install the foomatic package as the gimp drivers
refused to print on my 240.
This solved the problem.

---

