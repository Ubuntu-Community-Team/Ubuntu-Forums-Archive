---
title: "Brother MFC-215C scanner does not work"
date: 2018-01-06
forum: Hardware
---

### Post by masro on 2018-01-06
Hi,

I installed the scanner following the documentation on  [https://sites.google.com/site/easylinuxtipsproject/15](https://sites.google.com/site/easylinuxtipsproject/15) .

lsusb shows:
```
Bus 003 Device 005: ID 04f9:0193 Brother Industries, Ltd MFC-215C
```

When I use simple-scan, the scanner is recognized, but does not work:
```
[COLOR=#000000][FONT=&amp][+0,00s] DEBUG: simple-scan.vala:674: Starting Simple Scan 3.20.0, PID=2559[/FONT][/COLOR][+0,00s] DEBUG: Connecting to session manager
[+0,10s] DEBUG: ui.vala:2032: Loading state from /home/ubuntu/.cache/simple-scan/state
[+0,10s] DEBUG: ui.vala:1995: Restoring window to 800x400 pixels
[+0,10s] DEBUG: autosave-manager.vala:64: Loading autosave information
[+0,10s] DEBUG: autosave-manager.vala:259: Waiting to autosave...
[+0,10s] CRITICAL: gtk_event_controller_reset: assertion 'GTK_IS_EVENT_CONTROLLER (controller)' failed
[+0,14s] DEBUG: scanner.vala:1447: sane_init () -> SANE_STATUS_GOOD
[+0,14s] DEBUG: scanner.vala:1453: SANE version 1.0.25
[+0,14s] DEBUG: scanner.vala:1514: Requesting redetection of scan devices
[+0,14s] DEBUG: scanner.vala:803: Processing request
[+0,20s] DEBUG: autosave-manager.vala:281: Autosaving book information
[+0,26s] DEBUG: ui.vala:2124: Saving state to /home/ubuntu/.cache/simple-scan/state
[+5,93s] DEBUG: simple-scan.vala:404: Requesting scan at 300 dpi from device '(null)'
[+5,93s] DEBUG: scanner.vala:1560: Scanner.scan ("(null)", dpi=300, scan_mode=ScanMode.COLOR, depth=8, type=ScanType.SINGLE, paper_width=0, paper_height=0, brightness=0, contrast=0)
[+6,07s] DEBUG: scanner.vala:338: sane_get_devices () -> SANE_STATUS_GOOD
[+6,07s] DEBUG: scanner.vala:350: Device: name="brother2:bus2;dev3" vendor="Brother" model="MFC-215C" type="USB scanner"
[+6,07s] DEBUG: scanner.vala:803: Processing request
[+6,08s] DEBUG: scanner.vala:864: sane_open ("brother2:bus2;dev3") -> SANE_STATUS_INVAL
[+6,08s] WARNING: scanner.vala:868: Unable to get open device: Invalid argument
[+6,43s] DEBUG: ui.vala:2124: Saving state to /home/ubuntu/.cache/simple-scan/state
[+15,63s] DEBUG: ui.vala:2124: Saving state to /home/ubuntu/.cache/simple-scan/state
[+19,57s] DEBUG: autosave-manager.vala:195: Deleting autosave records
[+19,57s] DEBUG: scanner.vala:1587: Stopping scan thread
[+19,57s] DEBUG: scanner.vala:803: Processing request 
```

If I use Vuescan the program crashes, but the scanner starts reading the scan
and after this i can use simple-scan without problems, but it takes a long time to do that every time.
Any ideas why the scanner does not work?

sane-find-scanner shows the following:

found USB scanner (vendor=0x04f9, product=0x0193) at libusb:003:005
could not fetch string descriptor: Pipe error

---

### Post by pdc on 2018-01-06
Hi masro; welcome to the forum and the linux community; sorry to hear of your issues with your scanner; 

you don't say which version of Ubuntu you are using; there are now many reports of scanners not working after an "upgrade" to 17.10; Ubuntu has LTS (long-term support) releases that come out April every second year; and they are supported for up to 5 yrs; in between, the innovative team at Ubuntu explore; innovate and push boundaries; which is why Ubuntu has come so far in the time that it has; it falls to those who install these releases to discover the issues; report them; and hope that the LTS will be all good; so if you please report this to Ubuntu as a bug; please google how to do this if not familiar; hopefully by April with 18.04 released as the latest LTS, it will be a paragon of stability and virtue

Pjotr from the Mint forum; who wrote the guide you quote; suggests a final try for a scanner with ```
gksudo simple-scan
``` and I wondered for completeness if you had tried that; 

Brother do have an FAQ page [http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&redirect=on](http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&redirect=on) and one thing they suggest is [http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&redirect=on#f00107](http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&redirect=on#f00107)

---

### Post by masro on 2018-01-07
Hi pdc, thanks for your answer, 

my version is Lubuntu 16.04.3, the brother mfc-215c is quite old, it is a printer with integrated scanner, the printer works so far without problems.
I already tried everything written on the FAQ, also starting the scanner with root rights, but the scanner program cannot make a connection although the scanner is recognized.
So far the workaround is to use the vuescan program and then simple-scan.

---

### Post by pdc on 2018-01-07
thanks very much masro; great that you just get ahead and use vuescan; the guy who developed it is very good at supporting folks; despite the scanning issues, we hope you enjoy Ubuntu and it all goes well for you

---

