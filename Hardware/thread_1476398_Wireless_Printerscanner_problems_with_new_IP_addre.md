---
title: "Wireless Printer/scanner problems with new IP address"
date: 2010-05-07
forum: Hardware
---

### Post by migs73 on 2010-05-07
Hi
I have recently installed a printer scanner (brother MFC-255CW) onto my wireless network. I followed the instructions on the Brother website and all was well.
Until I realised my router had dynamic IP addressing, meaning the next time I re-booted my printer/scanner it could get a new IP address, meaning my various software (cups/sane/simplescan etc) would not find the printer. To combat this I set the printer to a static IP outside of the range of my DHCP. This works fine with the printer modification through cups, but has caused a problem with the simple scan.
To try to change the IP address the scanners look for I just re-inputed the code;

$ brsaneconfig3  -a  name= scanner model=MFC-255CW ip=192.168.2.3

changing the IP to 192.168.2.100

unfortunately this returned the error that 'scanner' already existed, so I then did the same command changing the name to SCANNER.
This was accepted.
I then confirmed the scanner entry with;
$  brsaneconfig3  -q  |  grep SCANNER

which returned this;
  0 SCANNER             "MFC-255CW"         I:192.168.2.100
Which is correct.

I then tried to scan using Simple Scan but it just timed out. Tried to select the scanner in properties but although it shows 2 (both named Brother MFC-255CW) neither scanned. When I try to scan with Xsane it gives me the two options but with the names 'scanner' and 'SCANNER'. If I pick the SCANNER option it works fine (which is correct).

If I put in the command;
$ simple-scan -d

I get this returned;

** (simple-scan:2586): DEBUG: Starting Simple Scan 1.0.2, PID=2586
** (simple-scan:2586): DEBUG: Restoring window to 600x400 pixels
** (simple-scan:2586): DEBUG: Restoring window to maximized
** (simple-scan:2586): DEBUG: sane_init () -> SANE_STATUS_GOOD
** (simple-scan:2586): DEBUG: SANE version 1.0.20
** (simple-scan:2586): DEBUG: Requesting redetection of scan devices
** (simple-scan:2586): DEBUG: Processing request
** (simple-scan:2586): DEBUG: sane_get_devices () -> SANE_STATUS_GOOD
** (simple-scan:2586): DEBUG: Device: name="brother3:net1;dev1" vendor="Brother" model="MFC-255CW" type="scanner"
** (simple-scan:2586): DEBUG: Device: name="brother3:net1;dev0" vendor="Brother" model="MFC-255CW" type="SCANNER"
** (simple-scan:2586): DEBUG: Stopping scan thread
** (simple-scan:2586): DEBUG: Processing request
** (simple-scan:2586): DEBUG: sane_exit ()

Which also seems correct.

Anyway my question is, how do I set SCANNER as my preferred hardware or delete the 'scanner' entry, so as to make it work in simple scan.

PS I have kids, so I would like simple scan to be the main scanning software as Xsane can be a bit scary!!

---

### Post by migs73 on 2010-05-10
Bump!!

---

### Post by migs73 on 2010-05-12
Another bump!

---

### Post by migs73 on 2010-05-14
Did a clean install to solve another problem (slow boot time) and now this issue does not exist. Not really solved, just an elaborate workaround.

---

### Post by roofnron on 2011-01-06
I just had a similar problem and searched and found this thread, not really solved. 

Not sure if this is bad form, but to correct I ran at terminal

brsaneconfig3 -r SCANNER

this removes the scanner entry and you can correct with a new command

also you can run brsanceconfig3 by itself to see list of options for this command

---

### Post by Fungus on 2013-02-22
I've been going nuts for a few days since my Brother MFC-7840W wireless scanner was not being found by Xsane or Simple scan.  I confirmed driver was installed per Brother linux website.

I also ran brsaneconfig3 -d, which showed and pinged the device all ok.  it also showed its ip address as 192.168.1.101 on my wireless network (there is also a way to check and set the ip address on the machine itself. see manual)

Anyway i was poking around for configuration settings and I found the file /usr/local/Brother/sane/brsanenetdevice3.cfg.  When I opened it up I see one line of text:  

DEVICE=SCANNER , "MFC-7840W" , 0x4f9:0x1e5 , IP-ADDRESS=192.168.1.100

So, I change the ip address to 192.168.1.101.  Close the file and then xsane and simple scan both work!

---

