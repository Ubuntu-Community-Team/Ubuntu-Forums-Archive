---
title: "Issue with HP printer"
date: 2014-07-24
forum: Hardware
---

### Post by hojjat on 2014-07-24
I have two HP printers accessible via network; one is LaserJet 4100 and one is LaserJet 4200. I can successfully install and use the 4200 using HP Device Management (hplip), but not the other one. Here is the result of running *snmp* for both printers:

```

$ /usr/lib/cups/backend/snmp does.not.work.com
$ /usr/lib/cups/backend/snmp does.work.com
network socket://10.11.12.13 "HP LaserJet 4200" "hp LaserJet 4200" "MFG:Hewlett-Packard;CMD:PJL,MLC,POSTSCRIPT,PJL,PCLXL,PCL;1284.4DL:4d,4e,1;MDL:hp LaserJet 4200;CLS:PRINTER;DES:Hewlett-Packard LaserJet 4200;" ""

```

As you can see, the one printer that I cannot install doesn't return anything on snmp. What does that mean? The result of nmap is pasted below for reference:

```

$ namp does.not.work.com
80/tcp   open  http
280/tcp  open  http-mgmt
443/tcp  open  https
515/tcp  open  printer
631/tcp  open  ipp
1782/tcp open  hp-hcip
9100/tcp open  jetdirect

$ nmap does.work.com
PORT     STATE SERVICE
21/tcp   open  ftp
23/tcp   open  telnet
80/tcp   open  http
280/tcp  open  http-mgmt
443/tcp  open  https
515/tcp  open  printer
631/tcp  open  ipp
9100/tcp open  jetdirect

```

---

### Post by hojjat on 2014-07-28
Bump?

---

