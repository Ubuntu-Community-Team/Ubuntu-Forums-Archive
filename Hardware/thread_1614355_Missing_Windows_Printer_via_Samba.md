---
title: "Missing Windows Printer via Samba"
date: 2010-11-05
forum: Hardware
---

### Post by Paul A C on 2010-11-05
Just installed Lubuntu 10.10 and went to add a printer, however, I do not see Windows Printer via Samba as one of the Network options.

I have installed Samba, and I can 'see' file shares, The printer IS shared, and can be seen by a Windows PC.

Any idea why I am not seeing Windows Printer via Samba, and what I need to install to get it to work/

---

### Post by IcarusR on 2010-11-05
Have you tried these instructions ?

[https://help.ubuntu.com/10.10/printing/C/printing.html#network]("https://help.ubuntu.com/10.10/printing/C/printing.html#network")

---

### Post by Morbius1 on 2010-11-05
See if you have the following packages installed:
```
libsmbclient
smbclient
python-smbc
```
If you don't then install them and see if that option reappears.

You may need to restart cups:
```
sudo service cups restart
```

---

### Post by Paul A C on 2010-11-05
> **IcarusR said:**
> Have you tried these instructions ?

[https://help.ubuntu.com/10.10/printing/C/printing.html#network](https://help.ubuntu.com/10.10/printing/C/printing.html#network)

Yes this is exactly what I was trying, the issue is I do not see the option :-

*Windows Printer via SAMBA*

---

### Post by Paul A C on 2010-11-05
Morbius1, you are a genius thanks!

For some reason smbclient was missing (the others were present).  Any idea why this was .missing'?

Now I see the printer I have on my Windows machine, but I am NOT seeing the printer connected to the other Linux (Lubuntu 10.4) machine...which I can see fromthe windows machine, what do I need to get to use that?

---

### Post by cavalier911 on 2010-11-05
[SIZE="3"][B]_LUBUNTU PRINTER SETUP_
[/B][/SIZE]
Menu/Preferences/Printing/Printing-localhost/ADD button/New Printer/Network Printer(click triangle to expand)/Windows Printer via SAMBA/click Browse button/SMB browser/refresh/Click triangle by windows computer with printers name/highlight printer name/click OK button/smb:// is now filled in with correct path to printer/click Forward button/select your printer from list or search for a PPD file and install/Forward/Print test page

---

### Post by Paul A C on 2010-11-06
Seem to have found the solution.  It is the settings on the host machine that needed to be changed.  Although this is a Samba share, the printer in questin is connected to a Linux box.  I had not gone to Printer Server settings and set 'Publish' and the various other options.  Having done that I can now see and print to the printer.

_Summary_
To add a printer from a Linux share, you must set the printer as sharable AND set the printer server settings to Publish (and grant any controls that are required)

---

### Post by travlemon on 2011-06-19
> **Morbius1 said:**
> See if you have the following packages installed:
```
libsmbclient
smbclient
python-smbc
```If you don't then install them and see if that option reappears.

You may need to restart cups:
```
sudo service cups restart
```

This worked perfectly for me, thanks very much!  I've had this problem on some other distros, and it was killing me as I couldn't figure out what packages I needed to install to get that option.

On a VirtualBox Lubuntu guest, all 3 packages needed to be installed.  However, on a laptop I have running Lubuntu, only the **smbclient** package needed to be installed.  I must have installed a whole bunch of Samba stuff, trying to get that option, and missed the one I really needed.

I used your fix in a How-To YouTube video.  It'll be uploaded in a little while, at my channel: 

[www.youtube.com/WebHunterification](www.youtube.com/WebHunterification)

Thanks again!

---

