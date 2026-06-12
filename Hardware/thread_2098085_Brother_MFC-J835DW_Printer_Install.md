---
title: "Brother MFC-J835DW Printer Install"
date: 2012-12-25
forum: Hardware
---

### Post by idcrewdawg on 2012-12-25
Okay so I admit I'm not smart enough to figure out what version of the install files to download so I can install my printer.

What I do know:
[LIST]
[*] The printer is recognized by the OS, but can't find the drivers.
[*] The OS is asking for either a PPD file, but when going to the brother solution center I don't see that extension but do see rpm or deb formats. Trying to download either of those the installation program doesn't recognize them.
[*][http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-J835DW]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-J835DW")
[*] I'm using 12.10
[/LIST]

What I don't know:
[LIST]
[*]How to install the files using terminal if that's required.
[*]What versions of the installation files to use.
[/LIST]

---

### Post by Kirk Schnable on 2012-12-25
I have an MFC-7840W working on my Ubuntu print server, but unfortunately for you, a PPD was available from Brother. I don't see one for your printer. 

However, Brother has a walk through on how to use their DEB packages to install a Brother printer on Linux. 
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html)

Let us know if you get stuck. 

Kirk

---

### Post by idcrewdawg on 2013-01-06
Sorry for the long pause in reply.

I got to the part where I am to modify the printer settings (have the printer on wireless). I'm being asked for a User Name and Password, and there wasn't one on the instructions page.

I'm on [This]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html#cwi_img2") page step 5b-2.

---

### Post by Kirk Schnable on 2013-01-08
> **idcrewdawg said:**
> Sorry for the long pause in reply.
Not a problem.

I got to the part where I am to modify the printer settings (have the printer on wireless). I'm being asked for a User Name and Password, and there wasn't one on the instructions page.

> **idcrewdawg said:**
> I'm on [This]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html#cwi_img2") page step 5b-2.
Of course there isn't one in the instructios... it's probably asking for your user's password for administrative access to your coputer...

---

### Post by idcrewdawg on 2013-01-08
I tried my network username and password, as well as the name for my computer, and administrator password. Neither of these were correct.

I've attached a screen shot of the login window.

---

### Post by greenchiliishot on 2013-09-01
What I did for use the Brother MFC-J835DW under Ubuntu 12.04.3 LTS 64 bits

[LIST]
[*]I go to [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html)
[*]I downloaded LPR driver [http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/mfcj835dwlpr-3.0.0-1.i386.deb&lang=English_lpr](http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/mfcj835dwlpr-3.0.0-1.i386.deb&lang=English_lpr)
[*]I did mkdir /var/spool/lpd
[*]I followed the instructions for LPR: [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn3.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn3.html)
[*]I downloaded CUPS wrapper [http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/mfcj835dwcupswrapper-3.0.0-1.i386.deb&lang=English_gpl](http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/mfcj835dwcupswrapper-3.0.0-1.i386.deb&lang=English_gpl)
[*]I did sudo[COLOR=#9191b0][/COLOR]apt-get install apparmor-utils apparmor-profiles apparmor-notify
[*]I followd the instructions for CUPS [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html)
[/LIST]

---

### Post by idcrewdawg on 2013-09-01
Not yet, and I stopped trying. I got the drivers to load well enough to allow printing, but wireless printing doesn't work.

---

### Post by kurt18947 on 2013-09-01
> **idcrewdawg said:**
> Not yet, and I stopped trying. I got the drivers to load well enough to allow printing, but wireless printing doesn't work.

My experience with Brother wireless printing is that it only requires changing the device URI.  I do it via the app "system-config-printer (gnome?).  This is installed by default in Xubuntu & Lubuntu and can be installed from repository on Ubuntu & gnome-shell.  The default printer app borders on useless IMO.  I created a desktop launcher but it can be invoked from a 'run'(alt-F2) box or terminal.  I changed the I.P. address of the printer to static then change the device URI to
```
socket://xxx.xxx.xxx.xxx:9100
```
where x=the printer's I.P. address.  This has worked quite reliably for me.

---

### Post by idcrewdawg on 2013-09-01
> **kurt18947 said:**
> My experience with Brother wireless printing is that it only requires changing the device URI.  I do it via the app "system-config-printer (gnome?).  This is installed by default in Xubuntu & Lubuntu and can be installed from repository on Ubuntu & gnome-shell.  The default printer app borders on useless IMO.  I created a desktop launcher but it can be invoked from a 'run'(alt-F2) box or terminal.  I changed the I.P. address of the printer to static then change the device URI to
```
socket://xxx.xxx.xxx.xxx:9100
```
where x=the printer's I.P. address.  This has worked quite reliably for me.

The printer IP is currently all 0's, and I changed it to that, but there was no success. In the print que status page it indicates the printer isn't connected. [ATTACH=CONFIG]245893[/ATTACH]

I've got several machines on the network, and the one that is windows will print to the printer wirelessly, so it's not connectivity. Just some kind of setting somewhere.

---

### Post by kurt18947 on 2013-09-01
> **idcrewdawg said:**
> The printer IP is currently all 0's, and I changed it to that, but there was no success. In the print que status page it indicates the printer isn't connected. [ATTACH=CONFIG]245893[/ATTACH]

I've got several machines on the network, and the one that is windows will print to the printer wirelessly, so it's not connectivity. Just some kind of setting somewhere.

All zeros?  I'm not surprised it doesn't work.  If your router's I.P. address is for example 192.168.1.1 (a common one),  The printer should be something like 192.168.1.xxx for my method to work.  The reason for the static I.P. is I'm telling the printer driver to send data to a certain address.  If that address changed via DHCP, it'd be like moving without letting the post office know.  Mail would go to your last know address even if you're no longer there.  There are numerous other  network connections that don't require a fixed printer address, mine has worked for years and I'm not inclined to change what works without good reason :).  Here's what my 'system-config-printer' shows-

[ATTACH=CONFIG]245902[/ATTACH]

---

### Post by wjbite-gmail on 2013-09-08
Sorry - I am new to this forum and did an QUICK REPLY instead of a REPLY WITH QUOTE.
Please see next message for the correct stuff.

---

### Post by wjbite-gmail on 2013-09-08
> **greenchiliishot said:**
> What I did for use the Brother MFC-J835DW under Ubuntu 12.04.3 LTS 64 bits

[LIST]
[*]I go to [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html) 
[*]I downloaded LPR driver [http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/mfcj835dwlpr-3.0.0-1.i386.deb&lang=English_lpr](http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/mfcj835dwlpr-3.0.0-1.i386.deb&lang=English_lpr) 
[*]I did mkdir /var/spool/lpd 
[*]I followed the instructions for LPR: [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn3.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn3.html) 
[*]I downloaded CUPS wrapper [http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/mfcj835dwcupswrapper-3.0.0-1.i386.deb&lang=English_gpl](http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/mfcj835dwcupswrapper-3.0.0-1.i386.deb&lang=English_gpl) 
[*]I did sudoapt-get install apparmor-utils apparmor-profiles apparmor-notify 
[*]I followd the instructions for CUPS [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html) 
[/LIST]

                     You may be able to forget doing the command line stuff on the 4th and later line of this set of instructions.
I say YOU MAY because I am doing it with a different printer - HL-3040.
When you download the LPR driver, open the folder that contains the file and double left click on it.
That will give you opportunity to let it use the UBUNTU SOFTWARE CENTER, which will do all the work for you.
Then do the same thing with the CUPSWRAPPER.
Now go the the SYSTEMS SETTINGS> PRINTER and ADD the printer.
One quirk for the HL-3040 is that when the add printer wizard is looking  for the driver, it can't find it. You just need to go to the option  provided that allow you to get the driver from the data base. HOWEVER it  doesn't look like it is there because Brother left out the hyphen in  the printer name (HL3040 instead of HL-3040). Because of the alphabetic  sorting the HL3040 appears way up at the top of the other HLs.
Maybe that is also true of other drivers downloaded in this way, eh?

Sorry that this may be a fit off topic - but I am not allowed to start a new thread until I get older LOL.
Walt

---

### Post by paul142 on 2014-05-27
To make this printer work over a wireless network I changed the device URI in the properties of the printer to read: socket://10.0.0.4:9100 (10.0.0.4 is my printer ip, change it to reflect yours).

---

### Post by kurt18947 on 2014-06-02
> **paul142 said:**
> To make this printer work over a wireless network I changed the device URI in the properties of the printer to read: socket://10.0.0.4:9100 (10.0.0.4 is my printer ip, change it to reflect yours).

I use that as well but I assigned a fixed i.p. addresss to the printer.  If you used the above address and the printer for whatever reason was assigned 10.0.0.5:9100 it wouldn't be found. Apologies if this was addressed earlier in the thread.

---

### Post by paul142 on 2015-04-12
This instruction worked really well and is easy to install this printer: [https://sites.google.com/site/easylinuxtipsproject/15](https://sites.google.com/site/easylinuxtipsproject/15)

---

