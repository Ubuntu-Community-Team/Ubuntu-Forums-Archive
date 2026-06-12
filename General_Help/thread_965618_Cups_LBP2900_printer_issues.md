---
title: "Cups: LBP2900 printer issues"
date: 2008-10-31
forum: General Help
---

### Post by ba0bab on 2008-10-31
Hi,

I recently upgraded to 8.10 Intrepid. The release is great, however my printer doesn't work. For 8.04 I used this guide:

[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900)

However, things have changed. firstly, cupsys is now cups instead. Even while taking that into consideration, there are problems. At step 7, I get this 

```

emil@zeptobuntu:~$ sudo update-rc.d ccpd defaults 20
update-rc.d: warning: /etc/init.d/ccpd missing LSB style header
 System startup links for /etc/init.d/ccpd already exist.

```

"/etc/init.d/ccpd missing LSB style header" - mysterious.

However everything *seems* fine, when I get to step 9 then this is what it looks like:

```

emil@zeptobuntu:~$ sudo ccpdadmin

 CUPS_ConfigPath = /etc/cups/
 LOG Path        = None
 UI Port         = 59787

 Entry Num  : Spooler	: Backend	: FIFO path		: Device Path 	: Status 
 ----------------------------------------------------------------------------
     [0]    : LBP2900 	: ccp 		: /var/ccpd/fifo0 	: /dev/usblp0 	

```

The printer doesn't respond, though. I restarted my computer and tried this:

```

captstatusui -P LBP2900

```

I get this message:
```

:Check the <Printer ***> of /etc/ccpd.conf

```

Another complication is that I tried this once before and it didn't work. Now I have two printers under main menu>System>admin>printing. I have LBP2900 and LBP2900. I tried "captstatusui" with both of them and nothing happened.

I don't have any idea what's wrong though, and help would be very much appreciated.

Thanks in advance,
Emile

---

