---
title: "monitor usb modem signal strength"
date: 2010-04-20
forum: Hardware
---

### Post by @mi|- on 2010-04-20
how to monitor signal strength of USB modems through commandline ??

---

### Post by anttu on 2010-04-20
This is one way to do it:

1. Install terminal program cu : sudo apt-get install cu

2. Connect to the modem : cu -l /dev/ttyUSB0
  - this may be also ttyUSB1, 2 or bigger, depending on your modem

3. Give AT command to check the signal : at+csq
- this gives you the RSSI, see further below

Notice:
- Exit cu by keys: "~" and "." (Ctrl+C or else do not work) 
- Some modems work with the connection on, some do not, so it may be wise to disconnect from internet before trying cu.

The table [http://www.siptune.net/tiki-index.php?page=Signaalinaytot](http://www.siptune.net/tiki-index.php?page=Signaalinaytot) helps you realize the RSSI (Radio Signal Strength Index) compared to other indicators of signal strength. (The table headings are in Finnish, but it is very easy to figure out.)

---

### Post by ali amiri on 2013-03-28
when I write "cu -l /dev/ttyUSB0" I get this error: 
"cu: open (/dev/ttyUSB0): Permission denied
cu: /dev/ttyUSB0: Line in use"
but I tried it with root and also modem is not connected.
when modem is connected I get this :
"cu: /dev/ttyUSB0: Line in use"

---

