---
title: "Scanning with Canon Pixma TS8151/TS8000-series"
date: 2019-03-17
forum: Hardware
---

### Post by forteller2 on 2019-03-17
Hi, all. I'm having issues getting the scanner on my dad's Canon printer/scanner working with his Ubuntu box. Really hope you can help me out! Here's the facts:

- Canon Pixma TS8151 (that is: the TS8000-series) with latest firmware installed (1.100)
- Ubuntu 18.10 64-bit with all latest updates installed and Gnome-session
- After installing the official printer driver from Cannon's website the printer part of the TS8151 works fine
- Simple scan does not find the scanner part of the TS8151, even after installing the official scangearmp driver from Cannon's website
- Installing a ton of SANE driver things after recommendation from a website I found, and restarting the computer, did not help
- I can't find anything in the settings for adding a scanner, or anything about scanning in the printer settings area. Am I just blind?

Any help would be greatly appreciated! Thank you!

---

### Post by brian_p on 2019-03-17
> **forteller2 said:**
> Hi, all. I'm having issues getting the scanner on my dad's Canon printer/scanner working with his Ubuntu box. Really hope you can help me out! Here's the facts:

- Canon Pixma TS8151 (that is: the TS8000-series) with latest firmware installed (1.100)
- Ubuntu 18.10 64-bit with all latest updates installed and Gnome-session
- After installing the official printer driver from Cannon's website the printer part of the TS8151 works fine

For future reference (and for other readers): you didn't need these printer drivers.

[https://wiki.debian.org/QuickPrintQueuesCUPS](https://wiki.debian.org/QuickPrintQueuesCUPS)

> 
- Simple scan does not find the scanner part of the TS8151, even after installing the official scangearmp driver from Cannon's website

SANE outlines the support it has for the TS8000-series and what appear to be other similar devices at

[http://www.sane-project.org/lists/sane-mfgs-cvs.html](http://www.sane-project.org/lists/sane-mfgs-cvs.html)

The TS8151 isn't mentioned. Unsupported? But you would expect the scangear stuff to work with its own GUI interface. After all, that is Canon's reason for supplying it. Try again. It works?

BTW, scangear is not designed to be used with simple-scan and xsane.

[https://wiki.debian.org/Scanner#canon](https://wiki.debian.org/Scanner#canon)

---

### Post by him610 on 2019-03-17
I don't know about Canon multi-function devices, but Brother has separate, distinct drivers for its printer, scanner, and fax functions. 
You might find some help here, [https://help.ubuntu.com/community/SANE%20-%20Installing%20a%20scanner%20that%20isn%27t%20auto-detected]("https://help.ubuntu.com/community/SANE%20-%20Installing%20a%20scanner%20that%20isn%27t%20auto-detected")

---

### Post by forteller2 on 2019-03-17
Thank you both! It now kinda-sorta works, but I'd still like some more help:

I didn't realize until now that there is a GUI frontend for scangearmp. Why? Because it doesn't show up in the list of applications in Gnome Shell/Activities. I had to start it from terminal. When I did it had no issues scanning! So the basics works. But Simple scan still doesn't work, and I wish it did.

I went to [https://help.ubuntu.com/community/SANE%20-%20Installing%20a%20scanner%20that%20isn%27t%20auto-detected](https://help.ubuntu.com/community/SANE%20-%20Installing%20a%20scanner%20that%20isn%27t%20auto-detected) and tried to do everything there, but not everything made total sense:

Step 2 said to remove the # in front of "example-backend" in /etc/sane.d/dll.conf, but there was no "example-backend" in that file. So I added it instead

Then I tried using sane-find-scanner, and it did actually find the scanner and identify it correctly!

The last step said to "Find the line that reads:  usb" in the file /etc/sane.d/example.conf, but that file was completely blank. I added the line it asked me to, and also added it to canon.conf and dll.conf just in case, but it didn't work.

So that's how far I am now. Basic scanning works trough scangearmp2 launched trough terminal, but nothing else. Is there anything else I can do to make it work in Simple scan and/or other scanning applications?

Thanks again!

---

### Post by brian_p on 2019-03-17
> **forteller2 said:**
> Thank you both! It now kinda-sorta works, but I'd still like some more help:

I didn't realize until now that there is a GUI frontend for scangearmp. Why? Because it doesn't show up in the list of applications in Gnome Shell/Activities. I had to start it from terminal. When I did it had no issues scanning! So the basics works. But Simple scan still doesn't work, and I wish it did.

Wishing is fine but just because scangearmp2 works is not sufficient. As explained in the link given, Canon's scanning uses its own backend which it does not share with SANE.

> 
I went to [https://help.ubuntu.com/community/SANE%20-%20Installing%20a%20scanner%20that%20isn%27t%20auto-detected](https://help.ubuntu.com/community/SANE%20-%20Installing%20a%20scanner%20that%20isn%27t%20auto-detected) and tried to do everything there, but not everything made total sense:

Step 2 said to remove the # in front of "example-backend" in /etc/sane.d/dll.conf, but there was no "example-backend" in that file. So I added it instead

You scanner (if it worked or you got it to work with SANE) would probably use the pixma backend.

```
man sane-pixma
```

> 
Then I tried using sane-find-scanner, and it did actually find the scanner and identify it correctly!

Thats good but it only tells you that you have permission to use the USB bus. That is also in the link you were given. Look there at 

```
scanimage -L
```

> 
The last step said to "Find the line that reads:  usb" in the file /etc/sane.d/example.conf, but that file was completely blank. I added the line it asked me to, and also added it to canon.conf and dll.conf just in case, but it didn't work.

You want pixma.conf

> 
So that's how far I am now. Basic scanning works trough scangearmp2 launched trough terminal, but nothing else. Is there anything else I can do to make it work in Simple scan and/or other scanning applications?

Possibly.  Give what you get with

```
avahi-browse -rt _uscan._tcp
```

---

### Post by him610 on 2019-03-17
> scanimage -L will show if the scanner is being recognized, and you can use it for testing and scanning also. 
> scanimage -h

---

### Post by forteller2 on 2019-03-17
Thanks again! Tried adding it to pixma.conf also, but still nothing happening in Simple scan.

Here's the output you asked for:

```

+   eno1 IPv6 Canon TS8100 series                           _uscan._tcp          local
+   eno1 IPv4 Canon TS8100 series                           _uscan._tcp          local
=   eno1 IPv6 Canon TS8100 series                           _uscan._tcp          local
   hostname = [338D34000000.local]
   address = [192.168.10.104]
   port = [80]
   txt = ["duplex=F" "is=platen" "cs=grayscale,color" "rs=eSCL" "representation=http://338D34000000.local./icon/printer_icon.png" "vers=2.63" "UUID=00000000-0000-1000-8000-00182140f369" "adminurl=http://338D34000000.local./index.html?page=PAGE_AAP" "note=" "pdl=image/jpeg,application/pdf" "ty=Canon TS8100 series" "txtvers=1"]
=   eno1 IPv4 Canon TS8100 series                           _uscan._tcp          local
   hostname = [338D34000000.local]
   address = [192.168.10.104]
   port = [80]
   txt = ["duplex=F" "is=platen" "cs=grayscale,color" "rs=eSCL" "representation=http://338D34000000.local./icon/printer_icon.png" "vers=2.63" "UUID=00000000-0000-1000-8000-00182140f369" "adminurl=http://338D34000000.local./index.html?page=PAGE_AAP" "note=" "pdl=image/jpeg,application/pdf" "ty=Canon TS8100 series" "txtvers=1"]

```

---

### Post by forteller2 on 2019-03-17
That was from avahi-browse -rt _uscan._tcp

scanimage -L also gives a long output, and I have no idea what to do with it:

```

MIB search path: /home/dagarne/.snmp/mibs:/usr/share/snmp/mibs:/usr/share/snmp/mibs/iana:/usr/share/snmp/mibs/ietf:/usr/share/mibs/site:/usr/share/snmp/mibs:/usr/share/mibs/iana:/usr/share/mibs/ietf:/usr/share/mibs/netsnmp
Cannot find module (SNMPv2-MIB): At line 1 in (none)
Cannot find module (IF-MIB): At line 1 in (none)
Cannot find module (IP-MIB): At line 1 in (none)
Cannot find module (TCP-MIB): At line 1 in (none)
Cannot find module (UDP-MIB): At line 1 in (none)
Cannot find module (HOST-RESOURCES-MIB): At line 1 in (none)
Cannot find module (NOTIFICATION-LOG-MIB): At line 1 in (none)
Cannot find module (DISMAN-EVENT-MIB): At line 1 in (none)
Cannot find module (DISMAN-SCHEDULE-MIB): At line 1 in (none)
Cannot find module (HOST-RESOURCES-TYPES): At line 1 in (none)
Cannot find module (MTA-MIB): At line 1 in (none)
Cannot find module (NETWORK-SERVICES-MIB): At line 1 in (none)
Cannot find module (SNMPv2-TC): At line 15 in /usr/share/snmp/mibs/UCD-DISKIO-MIB.txt
Cannot find module (SNMPv2-SMI): At line 34 in /usr/share/snmp/mibs/UCD-SNMP-MIB.txt
Cannot find module (SNMPv2-TC): At line 37 in /usr/share/snmp/mibs/UCD-SNMP-MIB.txt
Did not find 'enterprises' in module #-1 (/usr/share/snmp/mibs/UCD-SNMP-MIB.txt)
Did not find 'DisplayString' in module #-1 (/usr/share/snmp/mibs/UCD-SNMP-MIB.txt)
Did not find 'TruthValue' in module #-1 (/usr/share/snmp/mibs/UCD-SNMP-MIB.txt)
Unlinked OID in UCD-SNMP-MIB: ucdavis ::= { enterprises 2021 }
Undefined identifier: enterprises near line 39 of /usr/share/snmp/mibs/UCD-SNMP-MIB.txt
Did not find 'DisplayString' in module #-1 (/usr/share/snmp/mibs/UCD-DISKIO-MIB.txt)
Did not find 'ucdExperimental' in module UCD-SNMP-MIB (/usr/share/snmp/mibs/UCD-DISKIO-MIB.txt)
Unlinked OID in UCD-DISKIO-MIB: ucdDiskIOMIB ::= { ucdExperimental 15 }
Undefined identifier: ucdExperimental near line 19 of /usr/share/snmp/mibs/UCD-DISKIO-MIB.txt
Cannot find module (SNMPv2-TC): At line 10 in /usr/share/snmp/mibs/UCD-DLMOD-MIB.txt
Did not find 'DisplayString' in module #-1 (/usr/share/snmp/mibs/UCD-DLMOD-MIB.txt)
Did not find 'ucdExperimental' in module UCD-SNMP-MIB (/usr/share/snmp/mibs/UCD-DLMOD-MIB.txt)
Unlinked OID in UCD-DLMOD-MIB: ucdDlmodMIB ::= { ucdExperimental 14 }
Undefined identifier: ucdExperimental near line 13 of /usr/share/snmp/mibs/UCD-DLMOD-MIB.txt
Cannot find module (SNMPv2-TC): At line 15 in /usr/share/snmp/mibs/LM-SENSORS-MIB.txt
Did not find 'DisplayString' in module #-1 (/usr/share/snmp/mibs/LM-SENSORS-MIB.txt)
Did not find 'ucdExperimental' in module UCD-SNMP-MIB (/usr/share/snmp/mibs/LM-SENSORS-MIB.txt)
Unlinked OID in LM-SENSORS-MIB: lmSensors ::= { ucdExperimental 16 }
Undefined identifier: ucdExperimental near line 32 of /usr/share/snmp/mibs/LM-SENSORS-MIB.txt
Did not find 'ucdavis' in module UCD-SNMP-MIB (/usr/share/snmp/mibs/UCD-DEMO-MIB.txt)
Unlinked OID in UCD-DEMO-MIB: ucdDemoMIB ::= { ucdavis 14 }
Undefined identifier: ucdavis near line 7 of /usr/share/snmp/mibs/UCD-DEMO-MIB.txt
Cannot find module (SNMP-TARGET-MIB): At line 1 in (none)
Cannot find module (SNMP-FRAMEWORK-MIB): At line 9 in /usr/share/snmp/mibs/NET-SNMP-AGENT-MIB.txt
Cannot find module (SNMPv2-SMI): At line 8 in /usr/share/snmp/mibs/NET-SNMP-MIB.txt
Did not find 'enterprises' in module #-1 (/usr/share/snmp/mibs/NET-SNMP-MIB.txt)
Unlinked OID in NET-SNMP-MIB: netSnmp ::= { enterprises 8072 }
Undefined identifier: enterprises near line 10 of /usr/share/snmp/mibs/NET-SNMP-MIB.txt
Cannot find module (SNMPv2-TC): At line 21 in /usr/share/snmp/mibs/NET-SNMP-AGENT-MIB.txt
Did not find 'SnmpAdminString' in module #-1 (/usr/share/snmp/mibs/NET-SNMP-AGENT-MIB.txt)
Did not find 'netSnmpObjects' in module NET-SNMP-MIB (/usr/share/snmp/mibs/NET-SNMP-AGENT-MIB.txt)
Did not find 'netSnmpModuleIDs' in module NET-SNMP-MIB (/usr/share/snmp/mibs/NET-SNMP-AGENT-MIB.txt)
Did not find 'netSnmpNotifications' in module NET-SNMP-MIB (/usr/share/snmp/mibs/NET-SNMP-AGENT-MIB.txt)
Did not find 'netSnmpGroups' in module NET-SNMP-MIB (/usr/share/snmp/mibs/NET-SNMP-AGENT-MIB.txt)
Did not find 'DisplayString' in module #-1 (/usr/share/snmp/mibs/NET-SNMP-AGENT-MIB.txt)
Did not find 'RowStatus' in module #-1 (/usr/share/snmp/mibs/NET-SNMP-AGENT-MIB.txt)
Did not find 'TruthValue' in module #-1 (/usr/share/snmp/mibs/NET-SNMP-AGENT-MIB.txt)
Unlinked OID in NET-SNMP-AGENT-MIB: nsAgentNotifyGroup ::= { netSnmpGroups 9 }
Undefined identifier: netSnmpGroups near line 545 of /usr/share/snmp/mibs/NET-SNMP-AGENT-MIB.txt
Unlinked OID in NET-SNMP-AGENT-MIB: nsTransactionGroup ::= { netSnmpGroups 8 }
Undefined identifier: netSnmpGroups near line 536 of /usr/share/snmp/mibs/NET-SNMP-AGENT-MIB.txt
Unlinked OID in NET-SNMP-AGENT-MIB: nsConfigGroups ::= { netSnmpGroups 7 }
Undefined identifier: netSnmpGroups near line 515 of /usr/share/snmp/mibs/NET-SNMP-AGENT-MIB.txt
Unlinked OID in NET-SNMP-AGENT-MIB: nsCacheGroup ::= { netSnmpGroups 4 }
Undefined identifier: netSnmpGroups near line 505 of /usr/share/snmp/mibs/NET-SNMP-AGENT-MIB.txt
Unlinked OID in NET-SNMP-AGENT-MIB: nsModuleGroup ::= { netSnmpGroups 2 }
Undefined identifier: netSnmpGroups near line 495 of /usr/share/snmp/mibs/NET-SNMP-AGENT-MIB.txt
Unlinked OID in NET-SNMP-AGENT-MIB: netSnmpAgentMIB ::= { netSnmpModuleIDs 2 }
Undefined identifier: netSnmpModuleIDs near line 24 of /usr/share/snmp/mibs/NET-SNMP-AGENT-MIB.txt
Unlinked OID in NET-SNMP-AGENT-MIB: nsTransactions ::= { netSnmpObjects 8 }
Undefined identifier: netSnmpObjects near line 55 of /usr/share/snmp/mibs/NET-SNMP-AGENT-MIB.txt
Unlinked OID in NET-SNMP-AGENT-MIB: nsConfiguration ::= { netSnmpObjects 7 }
Undefined identifier: netSnmpObjects near line 54 of /usr/share/snmp/mibs/NET-SNMP-AGENT-MIB.txt
Unlinked OID in NET-SNMP-AGENT-MIB: nsErrorHistory ::= { netSnmpObjects 6 }
Undefined identifier: netSnmpObjects near line 53 of /usr/share/snmp/mibs/NET-SNMP-AGENT-MIB.txt
Unlinked OID in NET-SNMP-AGENT-MIB: nsCache ::= { netSnmpObjects 5 }
Undefined identifier: netSnmpObjects near line 52 of /usr/share/snmp/mibs/NET-SNMP-AGENT-MIB.txt
Unlinked OID in NET-SNMP-AGENT-MIB: nsDLMod ::= { netSnmpObjects 4 }
Undefined identifier: netSnmpObjects near line 51 of /usr/share/snmp/mibs/NET-SNMP-AGENT-MIB.txt
Unlinked OID in NET-SNMP-AGENT-MIB: nsExtensions ::= { netSnmpObjects 3 }
Undefined identifier: netSnmpObjects near line 50 of /usr/share/snmp/mibs/NET-SNMP-AGENT-MIB.txt
Unlinked OID in NET-SNMP-AGENT-MIB: nsMibRegistry ::= { netSnmpObjects 2 }
Undefined identifier: netSnmpObjects near line 49 of /usr/share/snmp/mibs/NET-SNMP-AGENT-MIB.txt
Unlinked OID in NET-SNMP-AGENT-MIB: nsVersion ::= { netSnmpObjects 1 }
Undefined identifier: netSnmpObjects near line 48 of /usr/share/snmp/mibs/NET-SNMP-AGENT-MIB.txt
Unlinked OID in NET-SNMP-AGENT-MIB: nsNotifyRestart ::= { netSnmpNotifications 3 }
Undefined identifier: netSnmpNotifications near line 482 of /usr/share/snmp/mibs/NET-SNMP-AGENT-MIB.txt
Unlinked OID in NET-SNMP-AGENT-MIB: nsNotifyShutdown ::= { netSnmpNotifications 2 }
Undefined identifier: netSnmpNotifications near line 476 of /usr/share/snmp/mibs/NET-SNMP-AGENT-MIB.txt
Unlinked OID in NET-SNMP-AGENT-MIB: nsNotifyStart ::= { netSnmpNotifications 1 }
Undefined identifier: netSnmpNotifications near line 470 of /usr/share/snmp/mibs/NET-SNMP-AGENT-MIB.txt
Cannot find module (SNMP-MPD-MIB): At line 1 in (none)
Cannot find module (SNMP-USER-BASED-SM-MIB): At line 1 in (none)
Cannot find module (SNMP-FRAMEWORK-MIB): At line 1 in (none)
Cannot find module (SNMP-VIEW-BASED-ACM-MIB): At line 1 in (none)
Cannot find module (SNMP-COMMUNITY-MIB): At line 1 in (none)
Cannot find module (IPV6-ICMP-MIB): At line 1 in (none)
Cannot find module (IPV6-MIB): At line 1 in (none)
Cannot find module (IPV6-TCP-MIB): At line 1 in (none)
Cannot find module (IPV6-UDP-MIB): At line 1 in (none)
Cannot find module (IP-FORWARD-MIB): At line 1 in (none)
Cannot find module (SNMP-FRAMEWORK-MIB): At line 10 in /usr/share/snmp/mibs/NET-SNMP-PASS-MIB.txt
Cannot find module (SNMP-FRAMEWORK-MIB): At line 10 in /usr/share/snmp/mibs/NET-SNMP-EXAMPLES-MIB.txt
Cannot find module (SNMPv2-TC): At line 12 in /usr/share/snmp/mibs/NET-SNMP-EXAMPLES-MIB.txt
Cannot find module (INET-ADDRESS-MIB): At line 13 in /usr/share/snmp/mibs/NET-SNMP-EXAMPLES-MIB.txt
Did not find 'SnmpAdminString' in module #-1 (/usr/share/snmp/mibs/NET-SNMP-EXAMPLES-MIB.txt)
Did not find 'netSnmp' in module NET-SNMP-MIB (/usr/share/snmp/mibs/NET-SNMP-EXAMPLES-MIB.txt)
Did not find 'RowStatus' in module #-1 (/usr/share/snmp/mibs/NET-SNMP-EXAMPLES-MIB.txt)
Did not find 'StorageType' in module #-1 (/usr/share/snmp/mibs/NET-SNMP-EXAMPLES-MIB.txt)
Did not find 'InetAddressType' in module #-1 (/usr/share/snmp/mibs/NET-SNMP-EXAMPLES-MIB.txt)
Did not find 'InetAddress' in module #-1 (/usr/share/snmp/mibs/NET-SNMP-EXAMPLES-MIB.txt)
Unlinked OID in NET-SNMP-EXAMPLES-MIB: netSnmpExamples ::= { netSnmp 2 }
Undefined identifier: netSnmp near line 16 of /usr/share/snmp/mibs/NET-SNMP-EXAMPLES-MIB.txt
Did not find 'SnmpAdminString' in module #-1 (/usr/share/snmp/mibs/NET-SNMP-PASS-MIB.txt)
Did not find 'netSnmpExamples' in module NET-SNMP-EXAMPLES-MIB (/usr/share/snmp/mibs/NET-SNMP-PASS-MIB.txt)
Unlinked OID in NET-SNMP-PASS-MIB: netSnmpPassExamples ::= { netSnmpExamples 255 }
Undefined identifier: netSnmpExamples near line 14 of /usr/share/snmp/mibs/NET-SNMP-PASS-MIB.txt
Cannot find module (SNMPv2-TC): At line 16 in /usr/share/snmp/mibs/NET-SNMP-EXTEND-MIB.txt
Did not find 'nsExtensions' in module NET-SNMP-AGENT-MIB (/usr/share/snmp/mibs/NET-SNMP-EXTEND-MIB.txt)
Did not find 'DisplayString' in module #-1 (/usr/share/snmp/mibs/NET-SNMP-EXTEND-MIB.txt)
Did not find 'RowStatus' in module #-1 (/usr/share/snmp/mibs/NET-SNMP-EXTEND-MIB.txt)
Did not find 'StorageType' in module #-1 (/usr/share/snmp/mibs/NET-SNMP-EXTEND-MIB.txt)
Unlinked OID in NET-SNMP-EXTEND-MIB: nsExtendGroups ::= { nsExtensions 3 }
Undefined identifier: nsExtensions near line 39 of /usr/share/snmp/mibs/NET-SNMP-EXTEND-MIB.txt
Unlinked OID in NET-SNMP-EXTEND-MIB: nsExtendObjects ::= { nsExtensions 2 }
Undefined identifier: nsExtensions near line 38 of /usr/share/snmp/mibs/NET-SNMP-EXTEND-MIB.txt
Unlinked OID in NET-SNMP-EXTEND-MIB: netSnmpExtendMIB ::= { nsExtensions 1 }
Undefined identifier: nsExtensions near line 19 of /usr/share/snmp/mibs/NET-SNMP-EXTEND-MIB.txt
Cannot find module (SNMP-NOTIFICATION-MIB): At line 1 in (none)
Cannot find module (SNMPv2-TM): At line 1 in (none)
Cannot find module (SNMP-FRAMEWORK-MIB): At line 9 in /usr/share/snmp/mibs/NET-SNMP-VACM-MIB.txt
Cannot find module (SNMP-VIEW-BASED-ACM-MIB): At line 16 in /usr/share/snmp/mibs/NET-SNMP-VACM-MIB.txt
Cannot find module (SNMPv2-TC): At line 25 in /usr/share/snmp/mibs/NET-SNMP-VACM-MIB.txt
Did not find 'SnmpAdminString' in module #-1 (/usr/share/snmp/mibs/NET-SNMP-VACM-MIB.txt)
Did not find 'netSnmpObjects' in module NET-SNMP-MIB (/usr/share/snmp/mibs/NET-SNMP-VACM-MIB.txt)
Did not find 'netSnmpGroups' in module NET-SNMP-MIB (/usr/share/snmp/mibs/NET-SNMP-VACM-MIB.txt)
Did not find 'vacmGroupName' in module #-1 (/usr/share/snmp/mibs/NET-SNMP-VACM-MIB.txt)
Did not find 'vacmAccessContextPrefix' in module #-1 (/usr/share/snmp/mibs/NET-SNMP-VACM-MIB.txt)
Did not find 'vacmAccessSecurityModel' in module #-1 (/usr/share/snmp/mibs/NET-SNMP-VACM-MIB.txt)
Did not find 'vacmAccessSecurityLevel' in module #-1 (/usr/share/snmp/mibs/NET-SNMP-VACM-MIB.txt)
Did not find 'DisplayString' in module #-1 (/usr/share/snmp/mibs/NET-SNMP-VACM-MIB.txt)
Did not find 'RowStatus' in module #-1 (/usr/share/snmp/mibs/NET-SNMP-VACM-MIB.txt)
Did not find 'StorageType' in module #-1 (/usr/share/snmp/mibs/NET-SNMP-VACM-MIB.txt)
Unlinked OID in NET-SNMP-VACM-MIB: netSnmpVacmMIB ::= { netSnmpObjects 9 }
Undefined identifier: netSnmpObjects near line 28 of /usr/share/snmp/mibs/NET-SNMP-VACM-MIB.txt
Cannot adopt OID in UCD-SNMP-MIB: logMatchRegExCompilation ::= { logMatchEntry 101 }
Cannot adopt OID in UCD-SNMP-MIB: logMatchErrorFlag ::= { logMatchEntry 100 }
Cannot adopt OID in UCD-SNMP-MIB: logMatchCycle ::= { logMatchEntry 11 }
Cannot adopt OID in UCD-SNMP-MIB: logMatchCount ::= { logMatchEntry 10 }
Cannot adopt OID in UCD-SNMP-MIB: logMatchCounter ::= { logMatchEntry 9 }
Cannot adopt OID in UCD-SNMP-MIB: logMatchCurrentCount ::= { logMatchEntry 8 }
Cannot adopt OID in UCD-SNMP-MIB: logMatchCurrentCounter ::= { logMatchEntry 7 }
Cannot adopt OID in UCD-SNMP-MIB: logMatchGlobalCount ::= { logMatchEntry 6 }
Cannot adopt OID in UCD-SNMP-MIB: logMatchGlobalCounter ::= { logMatchEntry 5 }
Cannot adopt OID in UCD-SNMP-MIB: logMatchRegEx ::= { logMatchEntry 4 }
Cannot adopt OID in UCD-SNMP-MIB: logMatchFilename ::= { logMatchEntry 3 }
Cannot adopt OID in UCD-SNMP-MIB: logMatchName ::= { logMatchEntry 2 }
Cannot adopt OID in UCD-SNMP-MIB: logMatchIndex ::= { logMatchEntry 1 }
Cannot adopt OID in NET-SNMP-VACM-MIB: nsVacmAccessEntry ::= { nsVacmAccessTable 1 }
Cannot adopt OID in UCD-SNMP-MIB: extErrFixCmd ::= { extEntry 103 }
Cannot adopt OID in UCD-SNMP-MIB: extErrFix ::= { extEntry 102 }
Cannot adopt OID in UCD-SNMP-MIB: extOutput ::= { extEntry 101 }
Cannot adopt OID in UCD-SNMP-MIB: extResult ::= { extEntry 100 }
Cannot adopt OID in UCD-SNMP-MIB: extCommand ::= { extEntry 3 }
Cannot adopt OID in UCD-SNMP-MIB: extNames ::= { extEntry 2 }
Cannot adopt OID in UCD-SNMP-MIB: extIndex ::= { extEntry 1 }
Cannot adopt OID in UCD-DEMO-MIB: ucdDemoPublic ::= { ucdDemoMIBObjects 1 }
Cannot adopt OID in UCD-DLMOD-MIB: dlmodTable ::= { ucdDlmodMIB 2 }
Cannot adopt OID in UCD-DLMOD-MIB: dlmodNextIndex ::= { ucdDlmodMIB 1 }
Cannot adopt OID in NET-SNMP-EXAMPLES-MIB: netSnmpExamples ::= { netSnmp 2 }
Cannot adopt OID in NET-SNMP-MIB: netSnmpConformance ::= { netSnmp 5 }
Cannot adopt OID in NET-SNMP-MIB: netSnmpNotificationPrefix ::= { netSnmp 4 }
Cannot adopt OID in NET-SNMP-MIB: netSnmpExperimental ::= { netSnmp 9999 }
Cannot adopt OID in NET-SNMP-MIB: netSnmpEnumerations ::= { netSnmp 3 }
Cannot adopt OID in NET-SNMP-MIB: netSnmpObjects ::= { netSnmp 1 }
Cannot adopt OID in UCD-SNMP-MIB: versionDoDebugging ::= { version 20 }
Cannot adopt OID in UCD-SNMP-MIB: versionSavePersistentData ::= { version 13 }
Cannot adopt OID in UCD-SNMP-MIB: versionRestartAgent ::= { version 12 }
Cannot adopt OID in UCD-SNMP-MIB: versionUpdateConfig ::= { version 11 }
Cannot adopt OID in UCD-SNMP-MIB: versionClearCache ::= { version 10 }
Cannot adopt OID in UCD-SNMP-MIB: versionConfigureOptions ::= { version 6 }
Cannot adopt OID in UCD-SNMP-MIB: versionIdent ::= { version 5 }
Cannot adopt OID in UCD-SNMP-MIB: versionCDate ::= { version 4 }
Cannot adopt OID in UCD-SNMP-MIB: versionDate ::= { version 3 }
Cannot adopt OID in UCD-SNMP-MIB: versionTag ::= { version 2 }
Cannot adopt OID in UCD-SNMP-MIB: versionIndex ::= { version 1 }
Cannot adopt OID in NET-SNMP-EXAMPLES-MIB: netSnmpExampleHeartbeatNotification ::= { netSnmpExampleNotificationPrefix 1 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsCacheStatus ::= { nsCacheEntry 3 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsCacheTimeout ::= { nsCacheEntry 2 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsCachedOID ::= { nsCacheEntry 1 }
Cannot adopt OID in UCD-SNMP-MIB: unknown ::= { ucdSnmpAgent 255 }
Cannot adopt OID in UCD-SNMP-MIB: dragonfly ::= { ucdSnmpAgent 17 }
Cannot adopt OID in UCD-SNMP-MIB: macosx ::= { ucdSnmpAgent 16 }
Cannot adopt OID in UCD-SNMP-MIB: aix ::= { ucdSnmpAgent 15 }
Cannot adopt OID in UCD-SNMP-MIB: hpux11 ::= { ucdSnmpAgent 14 }
Cannot adopt OID in UCD-SNMP-MIB: win32 ::= { ucdSnmpAgent 13 }
Cannot adopt OID in UCD-SNMP-MIB: openbsd ::= { ucdSnmpAgent 12 }
Cannot adopt OID in UCD-SNMP-MIB: bsdi ::= { ucdSnmpAgent 11 }
Cannot adopt OID in UCD-SNMP-MIB: linux ::= { ucdSnmpAgent 10 }
Cannot adopt OID in UCD-SNMP-MIB: irix ::= { ucdSnmpAgent 9 }
Cannot adopt OID in UCD-SNMP-MIB: freebsd ::= { ucdSnmpAgent 8 }
Cannot adopt OID in UCD-SNMP-MIB: netbsd1 ::= { ucdSnmpAgent 7 }
Cannot adopt OID in UCD-SNMP-MIB: hpux10 ::= { ucdSnmpAgent 6 }
Cannot adopt OID in UCD-SNMP-MIB: ultrix ::= { ucdSnmpAgent 5 }
Cannot adopt OID in UCD-SNMP-MIB: osf ::= { ucdSnmpAgent 4 }
Cannot adopt OID in UCD-SNMP-MIB: solaris ::= { ucdSnmpAgent 3 }
Cannot adopt OID in UCD-SNMP-MIB: sunos4 ::= { ucdSnmpAgent 2 }
Cannot adopt OID in UCD-SNMP-MIB: hpux9 ::= { ucdSnmpAgent 1 }
Cannot adopt OID in NET-SNMP-EXTEND-MIB: nsExtendOutputGroup ::= { nsExtendGroups 2 }
Cannot adopt OID in NET-SNMP-EXTEND-MIB: nsExtendConfigGroup ::= { nsExtendGroups 1 }
Cannot adopt OID in UCD-DISKIO-MIB: diskIOEntry ::= { diskIOTable 1 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsTransactionEntry ::= { nsTransactionTable 1 }
Cannot adopt OID in NET-SNMP-MIB: netSnmpGroups ::= { netSnmpConformance 2 }
Cannot adopt OID in NET-SNMP-MIB: netSnmpCompliances ::= { netSnmpConformance 1 }
Cannot adopt OID in UCD-SNMP-MIB: mrModuleName ::= { mrEntry 2 }
Cannot adopt OID in UCD-SNMP-MIB: mrIndex ::= { mrEntry 1 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsDebugTokenEntry ::= { nsDebugTokenTable 1 }
Cannot adopt OID in NET-SNMP-EXTEND-MIB: nsExtendStatus ::= { nsExtendConfigEntry 21 }
Cannot adopt OID in NET-SNMP-EXTEND-MIB: nsExtendStorage ::= { nsExtendConfigEntry 20 }
Cannot adopt OID in NET-SNMP-EXTEND-MIB: nsExtendRunType ::= { nsExtendConfigEntry 7 }
Cannot adopt OID in NET-SNMP-EXTEND-MIB: nsExtendExecType ::= { nsExtendConfigEntry 6 }
Cannot adopt OID in NET-SNMP-EXTEND-MIB: nsExtendCacheTime ::= { nsExtendConfigEntry 5 }
Cannot adopt OID in NET-SNMP-EXTEND-MIB: nsExtendInput ::= { nsExtendConfigEntry 4 }
Cannot adopt OID in NET-SNMP-EXTEND-MIB: nsExtendArgs ::= { nsExtendConfigEntry 3 }
Cannot adopt OID in NET-SNMP-EXTEND-MIB: nsExtendCommand ::= { nsExtendConfigEntry 2 }
Cannot adopt OID in NET-SNMP-EXTEND-MIB: nsExtendToken ::= { nsExtendConfigEntry 1 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsModuleTable ::= { nsMibRegistry 1 }
Cannot adopt OID in NET-SNMP-MIB: netSnmpPlaypen ::= { netSnmpExperimental 9999 }
Cannot adopt OID in NET-SNMP-EXAMPLES-MIB: netSnmpIETFWGEntry ::= { netSnmpIETFWGTable 1 }
Cannot adopt OID in UCD-SNMP-MIB: prErrFixCmd ::= { prEntry 103 }
Cannot adopt OID in UCD-SNMP-MIB: prErrFix ::= { prEntry 102 }
Cannot adopt OID in UCD-SNMP-MIB: prErrMessage ::= { prEntry 101 }
Cannot adopt OID in UCD-SNMP-MIB: prErrorFlag ::= { prEntry 100 }
Cannot adopt OID in UCD-SNMP-MIB: prCount ::= { prEntry 5 }
Cannot adopt OID in UCD-SNMP-MIB: prMax ::= { prEntry 4 }
Cannot adopt OID in UCD-SNMP-MIB: prMin ::= { prEntry 3 }
Cannot adopt OID in UCD-SNMP-MIB: prNames ::= { prEntry 2 }
Cannot adopt OID in UCD-SNMP-MIB: prIndex ::= { prEntry 1 }
Cannot adopt OID in UCD-DLMOD-MIB: dlmodEntry ::= { dlmodTable 1 }
Cannot adopt OID in UCD-SNMP-MIB: memSwapErrorMsg ::= { memory 101 }
Cannot adopt OID in UCD-SNMP-MIB: memSwapError ::= { memory 100 }
Cannot adopt OID in UCD-SNMP-MIB: memUsedRealTXT ::= { memory 17 }
Cannot adopt OID in UCD-SNMP-MIB: memUsedSwapTXT ::= { memory 16 }
Cannot adopt OID in UCD-SNMP-MIB: memCached ::= { memory 15 }
Cannot adopt OID in UCD-SNMP-MIB: memBuffer ::= { memory 14 }
Cannot adopt OID in UCD-SNMP-MIB: memShared ::= { memory 13 }
Cannot adopt OID in UCD-SNMP-MIB: memMinimumSwap ::= { memory 12 }
Cannot adopt OID in UCD-SNMP-MIB: memTotalFree ::= { memory 11 }
Cannot adopt OID in UCD-SNMP-MIB: memAvailRealTXT ::= { memory 10 }
Cannot adopt OID in UCD-SNMP-MIB: memTotalRealTXT ::= { memory 9 }
Cannot adopt OID in UCD-SNMP-MIB: memAvailSwapTXT ::= { memory 8 }
Cannot adopt OID in UCD-SNMP-MIB: memTotalSwapTXT ::= { memory 7 }
Cannot adopt OID in UCD-SNMP-MIB: memAvailReal ::= { memory 6 }
Cannot adopt OID in UCD-SNMP-MIB: memTotalReal ::= { memory 5 }
Cannot adopt OID in UCD-SNMP-MIB: memAvailSwap ::= { memory 4 }
Cannot adopt OID in UCD-SNMP-MIB: memTotalSwap ::= { memory 3 }
Cannot adopt OID in UCD-SNMP-MIB: memErrorName ::= { memory 2 }
Cannot adopt OID in UCD-SNMP-MIB: memIndex ::= { memory 1 }
Cannot adopt OID in UCD-DEMO-MIB: ucdDemoMIBObjects ::= { ucdDemoMIB 1 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsModuleTimeout ::= { nsModuleEntry 6 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsModuleModes ::= { nsModuleEntry 5 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsModuleName ::= { nsModuleEntry 4 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsmRegistrationPriority ::= { nsModuleEntry 3 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsmRegistrationPoint ::= { nsModuleEntry 2 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsmContextName ::= { nsModuleEntry 1 }
Cannot adopt OID in LM-SENSORS-MIB: lmMiscSensorsEntry ::= { lmMiscSensorsTable 1 }
Cannot adopt OID in NET-SNMP-MIB: netSnmpNotificationObjects ::= { netSnmpNotificationPrefix 1 }
Cannot adopt OID in NET-SNMP-MIB: netSnmpNotifications ::= { netSnmpNotificationPrefix 0 }
Cannot adopt OID in NET-SNMP-PASS-MIB: netSnmpPassTable ::= { netSnmpPassExamples 2 }
Cannot adopt OID in NET-SNMP-PASS-MIB: netSnmpPassOIDValue ::= { netSnmpPassExamples 99 }
Cannot adopt OID in NET-SNMP-PASS-MIB: netSnmpPassGauge ::= { netSnmpPassExamples 6 }
Cannot adopt OID in NET-SNMP-PASS-MIB: netSnmpPassCounter ::= { netSnmpPassExamples 5 }
Cannot adopt OID in NET-SNMP-PASS-MIB: netSnmpPassIpAddress ::= { netSnmpPassExamples 4 }
Cannot adopt OID in NET-SNMP-PASS-MIB: netSnmpPassTimeTicks ::= { netSnmpPassExamples 3 }
Cannot adopt OID in NET-SNMP-PASS-MIB: netSnmpPassString ::= { netSnmpPassExamples 1 }
Cannot adopt OID in NET-SNMP-MIB: netSnmpDomains ::= { netSnmpEnumerations 3 }
Cannot adopt OID in NET-SNMP-MIB: netSnmpAgentOIDs ::= { netSnmpEnumerations 2 }
Cannot adopt OID in NET-SNMP-MIB: netSnmpModuleIDs ::= { netSnmpEnumerations 1 }
Cannot adopt OID in LM-SENSORS-MIB: lmFanSensorsEntry ::= { lmFanSensorsTable 1 }
Cannot adopt OID in LM-SENSORS-MIB: lmTempSensorsEntry ::= { lmTempSensorsTable 1 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsModuleGroup ::= { netSnmpGroups 2 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsCacheGroup ::= { netSnmpGroups 4 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsConfigGroups ::= { netSnmpGroups 7 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsTransactionGroup ::= { netSnmpGroups 8 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsAgentNotifyGroup ::= { netSnmpGroups 9 }
Cannot adopt OID in UCD-SNMP-MIB: fileEntry ::= { fileTable 1 }
Cannot adopt OID in NET-SNMP-VACM-MIB: nsVacmStatus ::= { nsVacmAccessEntry 5 }
Cannot adopt OID in NET-SNMP-VACM-MIB: nsVacmStorageType ::= { nsVacmAccessEntry 4 }
Cannot adopt OID in NET-SNMP-VACM-MIB: nsVacmViewName ::= { nsVacmAccessEntry 3 }
Cannot adopt OID in NET-SNMP-VACM-MIB: nsVacmContextMatch ::= { nsVacmAccessEntry 2 }
Cannot adopt OID in NET-SNMP-VACM-MIB: nsVacmAuthType ::= { nsVacmAccessEntry 1 }
Cannot adopt OID in NET-SNMP-EXTEND-MIB: netSnmpExtendMIB ::= { nsExtensions 1 }
Cannot adopt OID in NET-SNMP-EXTEND-MIB: nsExtendObjects ::= { nsExtensions 2 }
Cannot adopt OID in NET-SNMP-EXTEND-MIB: nsExtendGroups ::= { nsExtensions 3 }
Cannot adopt OID in LM-SENSORS-MIB: lmVoltSensorsEntry ::= { lmVoltSensorsTable 1 }
Cannot adopt OID in NET-SNMP-MIB: netSnmp ::= { enterprises 8072 }
Cannot adopt OID in UCD-SNMP-MIB: ucdavis ::= { enterprises 2021 }
Cannot adopt OID in UCD-DISKIO-MIB: diskIONWrittenX ::= { diskIOEntry 13 }
Cannot adopt OID in UCD-DISKIO-MIB: diskIONReadX ::= { diskIOEntry 12 }
Cannot adopt OID in UCD-DISKIO-MIB: diskIOLA15 ::= { diskIOEntry 11 }
Cannot adopt OID in UCD-DISKIO-MIB: diskIOLA5 ::= { diskIOEntry 10 }
Cannot adopt OID in UCD-DISKIO-MIB: diskIOLA1 ::= { diskIOEntry 9 }
Cannot adopt OID in UCD-DISKIO-MIB: diskIOWrites ::= { diskIOEntry 6 }
Cannot adopt OID in UCD-DISKIO-MIB: diskIOReads ::= { diskIOEntry 5 }
Cannot adopt OID in UCD-DISKIO-MIB: diskIONWritten ::= { diskIOEntry 4 }
Cannot adopt OID in UCD-DISKIO-MIB: diskIONRead ::= { diskIOEntry 3 }
Cannot adopt OID in UCD-DISKIO-MIB: diskIODevice ::= { diskIOEntry 2 }
Cannot adopt OID in UCD-DISKIO-MIB: diskIOIndex ::= { diskIOEntry 1 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsTransactionMode ::= { nsTransactionEntry 2 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsTransactionID ::= { nsTransactionEntry 1 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsDebugTokenStatus ::= { nsDebugTokenEntry 4 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsDebugTokenPrefix ::= { nsDebugTokenEntry 2 }
Cannot adopt OID in NET-SNMP-EXAMPLES-MIB: nsIETFWGChair2 ::= { netSnmpIETFWGEntry 3 }
Cannot adopt OID in NET-SNMP-EXAMPLES-MIB: nsIETFWGChair1 ::= { netSnmpIETFWGEntry 2 }
Cannot adopt OID in NET-SNMP-EXAMPLES-MIB: nsIETFWGName ::= { netSnmpIETFWGEntry 1 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsLoggingTable ::= { nsConfigLogging 1 }
Cannot adopt OID in NET-SNMP-EXAMPLES-MIB: netSnmpHostsEntry ::= { netSnmpHostsTable 1 }
Cannot adopt OID in UCD-DLMOD-MIB: dlmodStatus ::= { dlmodEntry 5 }
Cannot adopt OID in UCD-DLMOD-MIB: dlmodError ::= { dlmodEntry 4 }
Cannot adopt OID in UCD-DLMOD-MIB: dlmodPath ::= { dlmodEntry 3 }
Cannot adopt OID in UCD-DLMOD-MIB: dlmodName ::= { dlmodEntry 2 }
Cannot adopt OID in UCD-DLMOD-MIB: dlmodIndex ::= { dlmodEntry 1 }
Cannot adopt OID in LM-SENSORS-MIB: lmMiscSensorsValue ::= { lmMiscSensorsEntry 3 }
Cannot adopt OID in LM-SENSORS-MIB: lmMiscSensorsDevice ::= { lmMiscSensorsEntry 2 }
Cannot adopt OID in LM-SENSORS-MIB: lmMiscSensorsIndex ::= { lmMiscSensorsEntry 1 }
Cannot adopt OID in NET-SNMP-PASS-MIB: netSnmpPassEntry ::= { netSnmpPassTable 1 }
Cannot adopt OID in LM-SENSORS-MIB: lmSensors ::= { ucdExperimental 16 }
Cannot adopt OID in UCD-DLMOD-MIB: ucdDlmodMIB ::= { ucdExperimental 14 }
Cannot adopt OID in UCD-DISKIO-MIB: ucdDiskIOMIB ::= { ucdExperimental 15 }
Cannot adopt OID in UCD-SNMP-MIB: dskEntry ::= { dskTable 1 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: netSnmpAgentMIB ::= { netSnmpModuleIDs 2 }
Cannot adopt OID in LM-SENSORS-MIB: lmFanSensorsValue ::= { lmFanSensorsEntry 3 }
Cannot adopt OID in LM-SENSORS-MIB: lmFanSensorsDevice ::= { lmFanSensorsEntry 2 }
Cannot adopt OID in LM-SENSORS-MIB: lmFanSensorsIndex ::= { lmFanSensorsEntry 1 }
Cannot adopt OID in LM-SENSORS-MIB: lmTempSensorsValue ::= { lmTempSensorsEntry 3 }
Cannot adopt OID in LM-SENSORS-MIB: lmTempSensorsDevice ::= { lmTempSensorsEntry 2 }
Cannot adopt OID in LM-SENSORS-MIB: lmTempSensorsIndex ::= { lmTempSensorsEntry 1 }
Cannot adopt OID in UCD-SNMP-MIB: logMatchTable ::= { logMatch 2 }
Cannot adopt OID in UCD-SNMP-MIB: logMatchMaxEntries ::= { logMatch 1 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsLoggingEntry ::= { nsLoggingTable 1 }
Cannot adopt OID in UCD-SNMP-MIB: fileErrorMsg ::= { fileEntry 101 }
Cannot adopt OID in UCD-SNMP-MIB: fileErrorFlag ::= { fileEntry 100 }
Cannot adopt OID in UCD-SNMP-MIB: fileMax ::= { fileEntry 4 }
Cannot adopt OID in UCD-SNMP-MIB: fileSize ::= { fileEntry 3 }
Cannot adopt OID in UCD-SNMP-MIB: fileName ::= { fileEntry 2 }
Cannot adopt OID in UCD-SNMP-MIB: fileIndex ::= { fileEntry 1 }
Cannot adopt OID in NET-SNMP-EXTEND-MIB: nsExtendOutput2Table ::= { nsExtendObjects 4 }
Cannot adopt OID in NET-SNMP-EXTEND-MIB: nsExtendOutput1Table ::= { nsExtendObjects 3 }
Cannot adopt OID in NET-SNMP-EXTEND-MIB: nsExtendConfigTable ::= { nsExtendObjects 2 }
Cannot adopt OID in NET-SNMP-EXTEND-MIB: nsExtendNumEntries ::= { nsExtendObjects 1 }
Cannot adopt OID in NET-SNMP-EXTEND-MIB: nsExtendOutput1Entry ::= { nsExtendOutput1Table 1 }
Cannot adopt OID in UCD-SNMP-MIB: ssCpuNumCpus ::= { systemStats 67 }
Cannot adopt OID in UCD-SNMP-MIB: ssCpuRawGuestNice ::= { systemStats 66 }
Cannot adopt OID in UCD-SNMP-MIB: ssCpuRawGuest ::= { systemStats 65 }
Cannot adopt OID in UCD-SNMP-MIB: ssCpuRawSteal ::= { systemStats 64 }
Cannot adopt OID in UCD-SNMP-MIB: ssRawSwapOut ::= { systemStats 63 }
Cannot adopt OID in UCD-SNMP-MIB: ssRawSwapIn ::= { systemStats 62 }
Cannot adopt OID in UCD-SNMP-MIB: ssCpuRawSoftIRQ ::= { systemStats 61 }
Cannot adopt OID in UCD-SNMP-MIB: ssRawContexts ::= { systemStats 60 }
Cannot adopt OID in UCD-SNMP-MIB: ssRawInterrupts ::= { systemStats 59 }
Cannot adopt OID in UCD-SNMP-MIB: ssIORawReceived ::= { systemStats 58 }
Cannot adopt OID in UCD-SNMP-MIB: ssIORawSent ::= { systemStats 57 }
Cannot adopt OID in UCD-SNMP-MIB: ssCpuRawInterrupt ::= { systemStats 56 }
Cannot adopt OID in UCD-SNMP-MIB: ssCpuRawKernel ::= { systemStats 55 }
Cannot adopt OID in UCD-SNMP-MIB: ssCpuRawWait ::= { systemStats 54 }
Cannot adopt OID in UCD-SNMP-MIB: ssCpuRawIdle ::= { systemStats 53 }
Cannot adopt OID in UCD-SNMP-MIB: ssCpuRawSystem ::= { systemStats 52 }
Cannot adopt OID in UCD-SNMP-MIB: ssCpuRawNice ::= { systemStats 51 }
Cannot adopt OID in UCD-SNMP-MIB: ssCpuRawUser ::= { systemStats 50 }
Cannot adopt OID in UCD-SNMP-MIB: ssCpuIdle ::= { systemStats 11 }
Cannot adopt OID in UCD-SNMP-MIB: ssCpuSystem ::= { systemStats 10 }
Cannot adopt OID in UCD-SNMP-MIB: ssCpuUser ::= { systemStats 9 }
Cannot adopt OID in UCD-SNMP-MIB: ssSysContext ::= { systemStats 8 }
Cannot adopt OID in UCD-SNMP-MIB: ssSysInterrupts ::= { systemStats 7 }
Cannot adopt OID in UCD-SNMP-MIB: ssIOReceive ::= { systemStats 6 }
Cannot adopt OID in UCD-SNMP-MIB: ssIOSent ::= { systemStats 5 }
Cannot adopt OID in UCD-SNMP-MIB: ssSwapOut ::= { systemStats 4 }
Cannot adopt OID in UCD-SNMP-MIB: ssSwapIn ::= { systemStats 3 }
Cannot adopt OID in UCD-SNMP-MIB: ssErrorName ::= { systemStats 2 }
Cannot adopt OID in UCD-SNMP-MIB: ssIndex ::= { systemStats 1 }
Cannot adopt OID in NET-SNMP-EXTEND-MIB: nsExtendOutput2Entry ::= { nsExtendOutput2Table 1 }
Cannot adopt OID in UCD-SNMP-MIB: laEntry ::= { laTable 1 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsCacheTable ::= { nsCache 3 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsCacheEnabled ::= { nsCache 2 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsCacheDefaultTimeout ::= { nsCache 1 }
Cannot adopt OID in UCD-SNMP-MIB: logMatchEntry ::= { logMatchTable 1 }
Cannot adopt OID in UCD-SNMP-MIB: extEntry ::= { extTable 1 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsConfigLogging ::= { nsConfiguration 2 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsConfigDebug ::= { nsConfiguration 1 }
Cannot adopt OID in NET-SNMP-EXAMPLES-MIB: netSnmpExampleString ::= { netSnmpExampleScalars 3 }
Cannot adopt OID in NET-SNMP-EXAMPLES-MIB: netSnmpExampleSleeper ::= { netSnmpExampleScalars 2 }
Cannot adopt OID in NET-SNMP-EXAMPLES-MIB: netSnmpExampleInteger ::= { netSnmpExampleScalars 1 }
Cannot adopt OID in LM-SENSORS-MIB: lmVoltSensorsValue ::= { lmVoltSensorsEntry 3 }
Cannot adopt OID in LM-SENSORS-MIB: lmVoltSensorsDevice ::= { lmVoltSensorsEntry 2 }
Cannot adopt OID in LM-SENSORS-MIB: lmVoltSensorsIndex ::= { lmVoltSensorsEntry 1 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsCacheEntry ::= { nsCacheTable 1 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsDebugTokenTable ::= { nsConfigDebug 4 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsDebugDumpPdu ::= { nsConfigDebug 3 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsDebugOutputAll ::= { nsConfigDebug 2 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsDebugEnabled ::= { nsConfigDebug 1 }
Cannot adopt OID in UCD-DEMO-MIB: ucdDemoPassphrase ::= { ucdDemoPublic 4 }
Cannot adopt OID in UCD-DEMO-MIB: ucdDemoUserList ::= { ucdDemoPublic 3 }
Cannot adopt OID in UCD-DEMO-MIB: ucdDemoPublicString ::= { ucdDemoPublic 2 }
Cannot adopt OID in UCD-DEMO-MIB: ucdDemoResetKeys ::= { ucdDemoPublic 1 }
Cannot adopt OID in NET-SNMP-EXAMPLES-MIB: netSnmpExampleHeartbeatName ::= { netSnmpExampleNotificationObjects 2 }
Cannot adopt OID in NET-SNMP-EXAMPLES-MIB: netSnmpExampleHeartbeatRate ::= { netSnmpExampleNotificationObjects 1 }
Cannot adopt OID in NET-SNMP-PASS-MIB: netSnmpPassExamples ::= { netSnmpExamples 255 }
Cannot adopt OID in NET-SNMP-EXAMPLES-MIB: netSnmpExampleNotifications ::= { netSnmpExamples 3 }
Cannot adopt OID in NET-SNMP-EXAMPLES-MIB: netSnmpExampleTables ::= { netSnmpExamples 2 }
Cannot adopt OID in NET-SNMP-EXAMPLES-MIB: netSnmpExampleScalars ::= { netSnmpExamples 1 }
Cannot adopt OID in NET-SNMP-VACM-MIB: nsVacmAccessTable ::= { netSnmpVacmMIB 1 }
Cannot adopt OID in UCD-SNMP-MIB: ucdShutdown ::= { ucdTraps 2 }
Cannot adopt OID in UCD-SNMP-MIB: ucdStart ::= { ucdTraps 1 }
Cannot adopt OID in LM-SENSORS-MIB: lmMiscSensorsTable ::= { lmSensors 5 }
Cannot adopt OID in LM-SENSORS-MIB: lmVoltSensorsTable ::= { lmSensors 4 }
Cannot adopt OID in LM-SENSORS-MIB: lmFanSensorsTable ::= { lmSensors 3 }
Cannot adopt OID in LM-SENSORS-MIB: lmTempSensorsTable ::= { lmSensors 2 }
Cannot adopt OID in LM-SENSORS-MIB: lmSensorsMIB ::= { lmSensors 1 }
Cannot adopt OID in UCD-SNMP-MIB: mrEntry ::= { mrTable 1 }
Cannot adopt OID in NET-SNMP-EXTEND-MIB: nsExtendConfigEntry ::= { nsExtendConfigTable 1 }
Cannot adopt OID in NET-SNMP-EXAMPLES-MIB: netSnmpHostRowStatus ::= { netSnmpHostsEntry 5 }
Cannot adopt OID in NET-SNMP-EXAMPLES-MIB: netSnmpHostStorage ::= { netSnmpHostsEntry 4 }
Cannot adopt OID in NET-SNMP-EXAMPLES-MIB: netSnmpHostAddress ::= { netSnmpHostsEntry 3 }
Cannot adopt OID in NET-SNMP-EXAMPLES-MIB: netSnmpHostAddressType ::= { netSnmpHostsEntry 2 }
Cannot adopt OID in NET-SNMP-EXAMPLES-MIB: netSnmpHostName ::= { netSnmpHostsEntry 1 }
Cannot adopt OID in UCD-SNMP-MIB: prEntry ::= { prTable 1 }
Cannot adopt OID in NET-SNMP-EXAMPLES-MIB: netSnmpExampleNotification ::= { netSnmpExampleNotifications 1 }
Cannot adopt OID in NET-SNMP-EXAMPLES-MIB: netSnmpExampleNotificationObjects ::= { netSnmpExampleNotifications 2 }
Cannot adopt OID in NET-SNMP-EXAMPLES-MIB: netSnmpExampleNotificationPrefix ::= { netSnmpExampleNotifications 0 }
Cannot adopt OID in NET-SNMP-EXAMPLES-MIB: netSnmpHostsTable ::= { netSnmpExampleTables 2 }
Cannot adopt OID in NET-SNMP-EXAMPLES-MIB: netSnmpIETFWGTable ::= { netSnmpExampleTables 1 }
Cannot adopt OID in NET-SNMP-PASS-MIB: netSnmpPassOID ::= { netSnmpPassEntry 3 }
Cannot adopt OID in NET-SNMP-PASS-MIB: netSnmpPassInteger ::= { netSnmpPassEntry 2 }
Cannot adopt OID in NET-SNMP-PASS-MIB: netSnmpPassIndex ::= { netSnmpPassEntry 1 }
Cannot adopt OID in NET-SNMP-VACM-MIB: netSnmpVacmMIB ::= { netSnmpObjects 9 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsVersion ::= { netSnmpObjects 1 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsMibRegistry ::= { netSnmpObjects 2 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsExtensions ::= { netSnmpObjects 3 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsDLMod ::= { netSnmpObjects 4 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsCache ::= { netSnmpObjects 5 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsErrorHistory ::= { netSnmpObjects 6 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsConfiguration ::= { netSnmpObjects 7 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsTransactions ::= { netSnmpObjects 8 }
Cannot adopt OID in UCD-DEMO-MIB: ucdDemoMIB ::= { ucdavis 14 }
Cannot adopt OID in UCD-SNMP-MIB: logMatch ::= { ucdavis 16 }
Cannot adopt OID in UCD-SNMP-MIB: fileTable ::= { ucdavis 15 }
Cannot adopt OID in UCD-SNMP-MIB: ucdTraps ::= { ucdavis 251 }
Cannot adopt OID in UCD-SNMP-MIB: systemStats ::= { ucdavis 11 }
Cannot adopt OID in UCD-SNMP-MIB: mrTable ::= { ucdavis 102 }
Cannot adopt OID in UCD-SNMP-MIB: snmperrs ::= { ucdavis 101 }
Cannot adopt OID in UCD-SNMP-MIB: version ::= { ucdavis 100 }
Cannot adopt OID in UCD-SNMP-MIB: laTable ::= { ucdavis 10 }
Cannot adopt OID in UCD-SNMP-MIB: dskTable ::= { ucdavis 9 }
Cannot adopt OID in UCD-SNMP-MIB: memory ::= { ucdavis 4 }
Cannot adopt OID in UCD-SNMP-MIB: extTable ::= { ucdavis 8 }
Cannot adopt OID in UCD-SNMP-MIB: prTable ::= { ucdavis 2 }
Cannot adopt OID in UCD-SNMP-MIB: ucdSnmpAgent ::= { ucdavis 250 }
Cannot adopt OID in UCD-SNMP-MIB: ucdExperimental ::= { ucdavis 13 }
Cannot adopt OID in UCD-SNMP-MIB: ucdInternal ::= { ucdavis 12 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsModuleEntry ::= { nsModuleTable 1 }
Cannot adopt OID in UCD-SNMP-MIB: dskErrorMsg ::= { dskEntry 101 }
Cannot adopt OID in UCD-SNMP-MIB: dskErrorFlag ::= { dskEntry 100 }
Cannot adopt OID in UCD-SNMP-MIB: dskUsedHigh ::= { dskEntry 16 }
Cannot adopt OID in UCD-SNMP-MIB: dskUsedLow ::= { dskEntry 15 }
Cannot adopt OID in UCD-SNMP-MIB: dskAvailHigh ::= { dskEntry 14 }
Cannot adopt OID in UCD-SNMP-MIB: dskAvailLow ::= { dskEntry 13 }
Cannot adopt OID in UCD-SNMP-MIB: dskTotalHigh ::= { dskEntry 12 }
Cannot adopt OID in UCD-SNMP-MIB: dskTotalLow ::= { dskEntry 11 }
Cannot adopt OID in UCD-SNMP-MIB: dskPercentNode ::= { dskEntry 10 }
Cannot adopt OID in UCD-SNMP-MIB: dskPercent ::= { dskEntry 9 }
Cannot adopt OID in UCD-SNMP-MIB: dskUsed ::= { dskEntry 8 }
Cannot adopt OID in UCD-SNMP-MIB: dskAvail ::= { dskEntry 7 }
Cannot adopt OID in UCD-SNMP-MIB: dskTotal ::= { dskEntry 6 }
Cannot adopt OID in UCD-SNMP-MIB: dskMinPercent ::= { dskEntry 5 }
Cannot adopt OID in UCD-SNMP-MIB: dskMinimum ::= { dskEntry 4 }
Cannot adopt OID in UCD-SNMP-MIB: dskDevice ::= { dskEntry 3 }
Cannot adopt OID in UCD-SNMP-MIB: dskPath ::= { dskEntry 2 }
Cannot adopt OID in UCD-SNMP-MIB: dskIndex ::= { dskEntry 1 }
Cannot adopt OID in UCD-DISKIO-MIB: diskIOTable ::= { ucdDiskIOMIB 1 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsLoggingGroup ::= { nsConfigGroups 2 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsDebugGroup ::= { nsConfigGroups 1 }
Cannot adopt OID in UCD-SNMP-MIB: snmperrErrMessage ::= { snmperrs 101 }
Cannot adopt OID in UCD-SNMP-MIB: snmperrErrorFlag ::= { snmperrs 100 }
Cannot adopt OID in UCD-SNMP-MIB: snmperrNames ::= { snmperrs 2 }
Cannot adopt OID in UCD-SNMP-MIB: snmperrIndex ::= { snmperrs 1 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsTransactionTable ::= { nsTransactions 1 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsLogStatus ::= { nsLoggingEntry 5 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsLogMaxLevel ::= { nsLoggingEntry 4 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsLogType ::= { nsLoggingEntry 3 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsLogToken ::= { nsLoggingEntry 2 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsLogLevel ::= { nsLoggingEntry 1 }
Cannot adopt OID in NET-SNMP-EXTEND-MIB: nsExtendResult ::= { nsExtendOutput1Entry 4 }
Cannot adopt OID in NET-SNMP-EXTEND-MIB: nsExtendOutNumLines ::= { nsExtendOutput1Entry 3 }
Cannot adopt OID in NET-SNMP-EXTEND-MIB: nsExtendOutputFull ::= { nsExtendOutput1Entry 2 }
Cannot adopt OID in NET-SNMP-EXTEND-MIB: nsExtendOutput1Line ::= { nsExtendOutput1Entry 1 }
Cannot adopt OID in NET-SNMP-EXTEND-MIB: nsExtendOutLine ::= { nsExtendOutput2Entry 2 }
Cannot adopt OID in NET-SNMP-EXTEND-MIB: nsExtendLineIndex ::= { nsExtendOutput2Entry 1 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsNotifyStart ::= { netSnmpNotifications 1 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsNotifyShutdown ::= { netSnmpNotifications 2 }
Cannot adopt OID in NET-SNMP-AGENT-MIB: nsNotifyRestart ::= { netSnmpNotifications 3 }
Cannot adopt OID in UCD-SNMP-MIB: laErrMessage ::= { laEntry 101 }
Cannot adopt OID in UCD-SNMP-MIB: laErrorFlag ::= { laEntry 100 }
Cannot adopt OID in UCD-SNMP-MIB: laLoadFloat ::= { laEntry 6 }
Cannot adopt OID in UCD-SNMP-MIB: laLoadInt ::= { laEntry 5 }
Cannot adopt OID in UCD-SNMP-MIB: laConfig ::= { laEntry 4 }
Cannot adopt OID in UCD-SNMP-MIB: laLoad ::= { laEntry 3 }
Cannot adopt OID in UCD-SNMP-MIB: laNames ::= { laEntry 2 }
Cannot adopt OID in UCD-SNMP-MIB: laIndex ::= { laEntry 1 }

```

---

### Post by brian_p on 2019-03-17
> **forteller2 said:**
> Thanks again! Tried adding it to pixma.conf also, but still nothing happening in Simple scan.

Here's the output you asked for:

```

+   eno1 IPv6 Canon TS8100 series                           _uscan._tcp          local
+   eno1 IPv4 Canon TS8100 series                           _uscan._tcp          local
=   eno1 IPv6 Canon TS8100 series                           _uscan._tcp          local
   hostname = [338D34000000.local]
   address = [192.168.10.104]
   port = [80]
   txt = ["duplex=F" "is=platen" "cs=grayscale,color" "rs=eSCL" "representation=http://338D34000000.local./icon/printer_icon.png" "vers=2.63" "UUID=00000000-0000-1000-8000-00182140f369" "adminurl=http://338D34000000.local./index.html?page=PAGE_AAP" "note=" "pdl=image/jpeg,application/pdf" "ty=Canon TS8100 series" "txtvers=1"]
=   eno1 IPv4 Canon TS8100 series                           _uscan._tcp          local
   hostname = [338D34000000.local]
   address = [192.168.10.104]
   port = [80]
   txt = ["duplex=F" "is=platen" "cs=grayscale,color" "rs=eSCL" "representation=http://338D34000000.local./icon/printer_icon.png" "vers=2.63" "UUID=00000000-0000-1000-8000-00182140f369" "adminurl=http://338D34000000.local./index.html?page=PAGE_AAP" "note=" "pdl=image/jpeg,application/pdf" "ty=Canon TS8100 series" "txtvers=1"]

```

Thanks for this. I just might make use of it later, if appropriate.

The *scanimage -L* output is something I've not seen before; it should say (or not say) what scanners have been found. Are you sure you typed the right thing?

Anyway, what is it that you want to do with scanning that scangearmp2 doesn't offer?

---

### Post by brian_p on 2019-03-17
Your *avahi-browse* output has come to be useful. It has

> ty=Canon TS8100 series

So not a TS8000 series. SANE has

> PIXMA TS8100 Series 	USB WiFi 	0x04a9/0x1821 	Untested 	Testers needed!

Your willingness to test is commendable. We need a **scanimage-L** output.

---

### Post by forteller2 on 2019-03-17
Thank you, Brian. I've double checked now and the scanimage -L output I posted above is correct. Please use anything I post that might help you make things better :)

I didn't think there was an 8100-series, because I found a SANE website that mentioned a 8000-series, but no 8100-series. Sorry about that.

What I want that scangearmp2 doesn't offer, except for a way to launch it without using the terminal (I've created a .desktop file now, but that's a pain), is a good user experience. In scangearmp2 you first have to select the scanner (but I only have one, so this step is just annoying), then you have to select where to save the file and name, and scan without any preview, and quite the bad GUI. And you only have the option of a jpg or a pdf. I also saw elsewhere online someone saying that the pdf is really just the jpg put into a pdf, so you cant search or copy the text or anything like that.

---

### Post by brian_p on 2019-03-17
> **forteller2 said:**
> Thank you, Brian. I've double checked now and the scanimage -L output I posted above is correct. Please use anything I post that might help you make things better :)

Thanks for doing that. It wasn't that I disbelieved you, just that the output was outside my experience. :)

> 
I didn't think there was an 8100-series, because I found a SANE website that mentioned a 8000-series, but no 8100-series. Sorry about that.

No problem. I'd never have known  it myself. Your avahi-browse output was most useful.

> 
What I want that scangearmp2 doesn't offer, except for a way to launch it without using the terminal (I've created a .desktop file now, but that's a pain), is a good user experience. In scangearmp2 you first have to select the scanner (but I only have one, so this step is just annoying), then you have to select where to save the file and name, and scan without any preview, and quite the bad GUI. And you only have the option of a jpg or a pdf. I also saw elsewhere online someone saying that the pdf is really just the jpg put into a pdf, so you cant search or copy the text or anything like that.

I understand your concern about a good user experience. I have one last idea about a way forward, but it may not lead to an instant solution. Let's see if we can get a sensible -scanimage -L first, though.

Remove scangearmp2. I think that

```
apt purge scangearmp2
```

should do it. Or use whatever you normally would use (synaptic?). What do you get for the command now?

---

### Post by forteller2 on 2019-03-18
Hey, brian. I was just at my parent's for the weekend, and I'm not sure when I'll be able to go back. Not going to ask my dad to do this ;) I'll update you here when I've been able to test it.

---

### Post by brian_p on 2019-03-18
> **forteller2 said:**
> Hey, brian. I was just at my parent's for the weekend, and I'm not sure when I'll be able to go back. Not going to ask my dad to do this ;) I'll update you here when I've been able to test it.

Purging what is already there would be good. Getting a normal **scanimage -L ** would be even better.

Some good news. I came across

[https://launchpad.net/~thierry-f/+archive/ubuntu/fork-michael-gruz/+packages](https://launchpad.net/~thierry-f/+archive/ubuntu/fork-michael-gruz/+packages)

The scangearmp2 packages are revamped Canon software which should allow simple-scan to be used. They might not be perfect because they still rely on some closed-source material. I think issues can be reported at

[https://github.com/Ordissimo/scangearmp2](https://github.com/Ordissimo/scangearmp2)

Either there or at

[https://alioth-lists.debian.net/cgi-bin/mailman/listinfo/sane-devel](https://alioth-lists.debian.net/cgi-bin/mailman/listinfo/sane-devel)

An update would be appreciated at some time. Good luck.

---

