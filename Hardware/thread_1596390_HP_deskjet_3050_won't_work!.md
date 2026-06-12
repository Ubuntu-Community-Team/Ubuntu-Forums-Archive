---
title: "HP deskjet 3050 won't work!"
date: 2010-10-14
forum: Hardware
---

### Post by drazgo on 2010-10-14
Hi there, 

just bought a new HP deskjet 3050, updated hplip from source (since there isn't an ubuntu update yet), and still I get an error saying "/usb/lib/cups/filter/foomatic-rip-hplip failed" when I tried installing the printer. Can somebody pleaaaseee help me with this one? Or can somebody tell me when the hplip ppa will be updated to 3.10.9 so i can try and install hplip from there?

thanks in advance!
Drazgo

---

### Post by drazgo on 2010-10-14
Nevermind, found it already. Turns out I just had to reinstall hplip from source!

---

### Post by daka on 2010-12-09
Hi Drazgo

I just bought the same printer and I am having no luck.  It is not being identified... no driver in the database... I downloaded hplip as suggested.... the printer shows up on the wifi as HPJ610a.093004 but I can't connect to it.   The printer can be try to connect via wifi but doesn't seem able to.

Could you possibly explain step by step how you got yours working. I will try to do the same things in another distro and see if it works.

Many thanks


daka

---

### Post by heliko on 2010-12-12
what ubuntu do you use? 10.10?
Heliko

---

### Post by daka on 2010-12-12
Yes, I use 10.10.  Mint LMDE  Linux Mint Debian edition.... 10.10

daka

---

### Post by Marky Mark on 2010-12-22
Hi guys.

I'm having the same problem, I've run the hplip 3.10.9, added all of the dependencies using the Synaptic Package Manager so that now I only get 3 warnings when I run the hplip 3.10.9. I can't add the last three as the files requested are not there to add. The thing runs to completion even auto detects the printer but won't print because of this foomatic-rip-hplip filter issue.
Any more ideas?

Cheers
Mark

---

### Post by daka on 2010-12-24
still frustrated... I had it working for a bit then had to re-install op sys and can't get it working yet.... It doesn't seem to identify the usb when I connect the printer by usb after running hp-setup ... says...

"error: No devices found on bus: usb"

also the hp management program doesn't seem to be installed on the applications menu although I did (through synaptic) install hplip and hpijs and hpijs-ppds and hplip-cups and hplip-dataand hplip-gui

This I think has something to do with the driver for the HP3050 not actually installing.  Does anyone have clear instructions on how to backtrack and redo everything correctly?

Thanks

daka

---

### Post by russtoku on 2010-12-27
I got HPLIP 3.10.9 to work with my HP 3050 under Linux Mint 10 (Julia) which based on Maverick Meerkat (10.10).  See the reply I posted on their forum at:

  [http://forums.linuxmint.com/viewtopic.php?f=90&t=61918&start=0](http://forums.linuxmint.com/viewtopic.php?f=90&t=61918&start=0)

Hope this helps.

---

### Post by narcisgarcia on 2010-12-31
In Ubuntu GNU/Linux 10.04 (Lucid Lynx)

I've solved it with a HP DeskJet 3050 plugged on USB installing [HPLIP 3.10.9]("http://hplip.sourceforge.net/") and making the wizard to uninstall previous HPLIP versions.

I added some packages needed, such as python-dev

* Take care of running **hplip-3.10.9.run** in a terminal, to see any error message if installer breaks instead of complete.

---

### Post by randcoop on 2011-03-23
This continues to be a major problem.  HPLIP won't install on one of my 10.10 computers because it says that it is missing the GCC dependency.  Of course, GCC is installed and so that makes no sense.  Moreover, HPLIP installed on another computer with the exact same GCC on it.  

I've tried with both HPLIP 3.10.9 and HPLIP 3.11.3.

I did get the 3050 printing wireless using the Ubuntu printer setup...by unzipping the tar.gz HPLIP and then pointing the Ubuntu printer installation to the 3050 ppd file.  The problem is that I can't then get the scanner to work.

It does work when HPLIP is installed properly...which brings me back to the GCC dependency.  

Any suggestions?

---

### Post by randcoop on 2011-03-23
Solved the GCC problem.  You need to install build-essential in order for it to work.  Then everything goes smoothly.

---

