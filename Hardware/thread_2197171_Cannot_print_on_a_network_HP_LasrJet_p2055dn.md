---
title: "Cannot print on a network HP LasrJet p2055dn"
date: 2014-01-02
forum: Hardware
---

### Post by hojjat on 2014-01-02
I am having a hard time getting this HP LaserJet p2055dn printer to work with my Ubuntu machine. It works fine when I send a print using a Mac machine or a Windows machine, but I think I have driver issues on the Ubuntu machine.

I took a look at [https://wiki.ubuntu.com/DebuggingPrintingProblems](https://wiki.ubuntu.com/DebuggingPrintingProblems) and ran the commands suggested there. I am pasting the results below, except I am replacing the printer's URI ot *hp.printer.com* and changed the IP addresses for privacy reasons.

Any advice is highly appreciated.

=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=

Step 7)
```

$ nmap hp.printer.com
Not shown: 994 closed ports
PORT     STATE SERVICE
23/tcp   open  telnet
80/tcp   open  http
280/tcp  open  http-mgmt
443/tcp  open  https
515/tcp  open  printer
9100/tcp open  jetdirect

```

Step 8) The result of these two commands:

```

$ /usr/lib/cups/backend/snmp
$ sudo /usr/lib/cups/backend/dnssd 

```

Did not include the printer in question or any of the other network printers that I have currently installed and can use flawlessly with my Ubuntu machine.

Step 9)
```

$ /usr/lib/cups/backend/snmp hp.printer.com
network socket://10.11.12.13:9100 "HP LaserJet P2055x" "HP LaserJet P2055x" "MFG:Hewlett-Packard;MDL:HP LaserJet P2055x;CMD:PJL,POSTSCRIPT,PCL,PCLXL;CLS:PRINTER;DES:HP LaserJet P2055x;FWVER:20100308;" "LOC"

```

Step 10)
```

$ lpinfo -vnetwork https
network ipps
network http
network ipp
network lpd
network socket
network ipp14
network beh
direct hp
network smb
direct hpfax
network socket://123.456.789.012

```

The IP Address belongs to another printer, not the one I have problem with.

Step 11) The following commands:

```

$ avahi-browse -a -v -t -r
$ avahi-browse -a -v -c -r

```

Do not list the printer in question, or any of the other printers that I have installed and can use without any problem. They do list a bunch of other printers that I don't intend to use.

Step 12) The result of following two commands looks normal:

```

$ ifconfig
$ route 

```

And my CUPS error_log is attached.

---

### Post by tgalati4 on 2014-01-02
Open a terminal:

```
hp-toolbox
```

Does your printer show up in the Left Column?  If not install it through "Device".=>"Add Device".   If it does show up, then delete it and reinstall it.

I just replaced the fuser sleeve on this model printer--what a complete pain.  Two hours to replace a $10 sleeve.  Dump it while you can.

---

### Post by cmcanulty on 2014-01-02
HP actually offers linux support and drivers , might be worth a call.

---

### Post by hojjat on 2014-01-06
Thanks for both responses. I just got my hands on this Ubuntu machine again and had a chance to try the first recommendation. Turns out (to my surprise) that hp-toolbox wasn't even installed (isn't supposed to come with Ubuntu?)

Anyways, I opened hp-toolbox and it didn't list my HP printer (in fact, it didn't list any of the other HP devices either, including those that work perfectly now). I tried the "Manual Discovery" option, and using the printer's IP I could find it. But I still cannot print to it. The response I get is "Unknown error" with code 1018. Any recommendations?

As for ditching the printer: not an option as I don't own it; owned by my employer. And as for calling HP, I want to try the recommendations given by this community first, as I trust it more than the corporate help desk of HP.

---

### Post by hojjat on 2014-01-06
Actually, the issue is resolved simply by changing the Jetlink portnumber in the hp toolbox.

---

### Post by tgalati4 on 2014-01-06
Glad you got it fixed.  When you get lines in your printout, don't call me, call HP.

---

