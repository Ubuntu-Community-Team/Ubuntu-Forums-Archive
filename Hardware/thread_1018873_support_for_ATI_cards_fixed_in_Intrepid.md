---
title: "support for ATI cards fixed in Intrepid?"
date: 2008-12-22
forum: Hardware
---

### Post by velozoom on 2008-12-22
tried searching about and didn't get any definitive answers, sorry for the lame question....

I upgraded my Thinkpad T500 to Intrepid when it was officially released and it broke my video so badly I could not get X to start at all, even when reverting to the vesa driver.  It was only then that I read that with 8.1 ATI video card support had been seriously compromised.  This is disappointing because 8.04 had great support for my card, even during installation I had full resolution on my X display.  

I read a few weeks ago that these issues would be fixed "in a couple weeks" and since it's been well over twice that, I'm curious if anyone has any feedback- *has* it been fixed?  Do I dare try the upgrade again?  (I reverted back to 8.04 after 8 hours of trying to fix the display) 

Thx...

---

### Post by markbuntu on 2008-12-22
Upgrades can be problematic when using restricted drivers so personally I avoid that. But anyway, the ati fglrx driver is working in Intrepid now but I would suggest removing any previous fglrx version and disabling compiz before upgrading.

I think that if you upgrade while using the VESA driver and get the system fully updated to the 2.6.29 kernel you can then install the new restricted driver with hardware manager and avoid difficulties.

I did a couple of clean installs of Intrepid and it seems to me that updating before installing the restricted driver is critical to success. 

I also noticed this in the /boot/grub/menu.lst that may be important

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		f2b95b53-ec80-4583-b08f-9ecb89d8cc48
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=f2b95b53-ec80-4583-b08f-9ecb89d8cc48 ro xforcevesa  single
initrd		/boot/initrd.img-2.6.27-9-generic

I hope this helps.

---

### Post by velozoom on 2008-12-23
thanks for the input but I'm in the same boat I was a few weeks ago.  

I wasn't using the restricted driver and ran the upgrade.  After the reboot X won't start and I get the error message "no screens found" when I try to start it.  

Any suggestions?  Card is a Radeon HD3650

Intrepid doesn't seem to be much of an upgrade for me, it seems.  :(

[EDIT] and I can't seem to get the kernel up to 2.6.29...I'm stuck at 2.6.27

[EDIT]Is .29 even out yet, I just read a post from last month that says .28 is still under development....is .27 the latest version?

---

### Post by markbuntu on 2008-12-23
Did you try adding the "xforcevesa" to the /boot/grub/menu.lst to the kernel line as above?

This will force the kernel to use vesa which should work no matter what.

I am running the .29 kernel on my intrepid install. I may have the proposed repository enabled but I am not sure about that. Anyway, I have had no problems with my HD3650 so it is not a problem with the card.

If you boot up in recovery mode you should get an option to reconfigure x, choose the vesa driver and a resolution that matches your screen. This will also give you a clean xorg.conf. Then you can try to reboot into the regular kernel and when you get to the login screen change session to gnome safe mode and that should get you to a desktop. Run update manager first thing.

---

### Post by velozoom on 2008-12-24
sorry, my bad, didn't notice the xforcevesa option.  I'll try that this morning....

---

### Post by velozoom on 2008-12-24
the xforce vesa option didn't work.  I also tried adding the following lines to the device section of my xorg.conf

Driver "vesa"
BusID  "PCI:01:0:0" 

no luck with that with and without xforcevesa.  the log files shows that there may be confusion over x seeing multiple devices and tanking when it has no idea which one to use.  I added the BusID to force it to use the HD 3650 instead of the intel chipset.  

I'm completely lost at this point.  No clue what to do....

---

### Post by velozoom on 2008-12-24
omg...wtf...downloaded the latest image of 8.10 and can't even get the install disk to show an x display...I don't even get to the installation choices menu before it drops to the command line.  At this point even windows is an option, as much as I hate to say it.  At least I know I can get a working machine...  :(

---

### Post by velozoom on 2008-12-25
thanks for the help, but I found the answer.  it wasn't in ubuntu at all, it was a BIOS video setting.  see this thread-
[http://ubuntuforums.org/showthread.php?t=1019736](http://ubuntuforums.org/showthread.php?t=1019736)

thanks for your help!

---

