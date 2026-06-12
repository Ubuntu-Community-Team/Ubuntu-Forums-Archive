---
title: "HP PSC All-In-One machine"
date: 2004-11-14
forum: Hardware &amp; Laptops
---

### Post by hyde on 2004-11-14
I have USB connected HP 1350 PSC (printer/scanner/copier).

Printing and scanning does work ok, but I have little problem, though;

Scanning with Xsane is working right after booting. But printing isn't working until I go to root shell and write *ptal-init stop*

After that I can print with my HP. Otherwise print tool says something like usb device is not available or it is in use (by ptal, obviously). I would like to disable ptal-init starting at boot up process, since I need printing more often than scanning. 

How do I do a little script (like .bat file in windows)  that when I need to use scanner, I could double click my scan script launcher on my desktop which does these things:
- ptal-init start
- launch xsane
- ptal-init stop after I exit from Xsane

That would make my Ubuntu less hassle free.
I've had this same issue with all other linux distros that I've been testing. This is yet another drawback of "Windows only" devices on the market...

---

### Post by fishd on 2004-11-22
Not sure if this will work for you, but I've had a similar issue recently on my Mandrake 10 box with a new LaserJet 3015 mfp.

I'd originally configured the printer to use the USB0 connection via CUPS and then later added the configuration for scanning with *ptal-init setup*... this caused printing to stop.

All I did was delete the original printer configuration and re-run the printer setup, it then detected a new port was available which was the *ptal* one... I set the output to this and now printing and scanning work fine.

Sorry for the lack of Ubuntu specific knowledge in here but I've only just (6 hours ago) installed it so I'm still finding my feet.

---

### Post by mr_ed on 2004-11-23
I'm in agreement with fishd.

Just delete your exising printer entry, and then re-add it.  It should show up under "Use a detected printer" as a PTAL device..

I have a PSC 1210.

My problem comes with Gimp-print.  I can print with everything, but Gimp.  I don't think it's supported, although the PSC 2xxx series can apparently use the Epson 900 series.

---

### Post by fishd on 2004-12-14
Recently moved from Mandrake over to Unbuntu full time... dunno why but Gnome feels so much nicer on Debian than silly Fedora...

Anyways, I've set my MFP device up and here's how I did it.

Make sure there are no entries for your printer and launch a terminal session. Type *sudo -s* to get a root console then run *ptal-init setup*. Configure the device as found.

I'm not in front of my machine right now (and I can't get SSHD working over my router, but that's another post :)) but in /etc/ptal/ (I think) there is a file called ptal-init, edit this file and look for *init.printd.start*, change this from 1 to 0 (zero) to prevent the print daemon section of ptal from starting.

Then do */etc/init.d/cups stop*, then *ptal-init restart* and finally */etc/init.d/cups start*

In the standard printer manager goto add printer and it should list your device*, add normally.

Hopefully this'll work for you. If you've any questions let me know and I'll do some more digging on my machine.


*Mine listed two detected devices, I just picked each of them and sent a test page to each, one worked, one didn't. Delete the one that doesn't! :)

---

### Post by hyde on 2004-12-14
I got my HP PSC working well with deleting old printer setting and adding it again.
Thank you for advice!

---

### Post by grnorton on 2005-03-20
This is useful and I suspect that it is the answer to my issues...

"Make sure there are no entries for your printer and launch a terminal session. Type sudo -s to get a root console then run ptal-init setup. Configure the device as found.

I'm not in front of my machine right now (and I can't get SSHD working over my router, but that's another post ) but in /etc/ptal/ (I think) there is a file called ptal-init, edit this file and look for init.printd.start, change this from 1 to 0 (zero) to prevent the print daemon section of ptal from starting....."

BUT I am not able to modify the file mentioned above as it denies me permission to modify .. I am not the owner!  It belongs t; "root" and yet I have logged in at a terminal as sudo -s and typed the password...

any ideas?

---

### Post by fletc900 on 2007-02-23
Hi there,
I was able to run the HP PSC 1350 printer on my Ubuntu 6.10 Server  box.
I just had to install  the hpijs, hp-ppds, hplip, and hplip-data packages via Synaptic and then setup the printer using Ubuntu's printer  GUI to select the new devicer from the "drop box".

If you want to share your new Ubuntu printer with a windows XP machine, then follow
these instructions (no need to play around with Samba!):

[https://help.ubuntu.com/community/NetworkPrintingFromWinXP](https://help.ubuntu.com/community/NetworkPrintingFromWinXP) 

To print to your new Ubuntu printer from a Windows machine you will have to select the appropriate driver for the HP PSC printer (after you set the printer's ip address within the Windows setup GUI). There was no HP PSC 1350 driver option to select (the closest was a HP PSC 950 but it did not work),  so I just chose the Generic MS Publisher Color Printer driver and it finally worked! 

PS. You might have to disable driver signing from within Windows.

Cheers,
Bruno

---

