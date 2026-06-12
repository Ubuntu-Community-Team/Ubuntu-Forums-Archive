---
title: "Networked Brother MFC6490CW..Issues with connection?"
date: 2018-11-07
forum: Hardware
---

### Post by nussmier on 2018-11-07
I am pretty new to the Ubuntu/Linux stuff but so far have had little to no issues except for this networked Brother MFC6490CW.  It is currently set up as a network printer with a static IP address(192.168.127.2).  It is connected to other windows based operating system computers and prints fine.  I started by going to the Brother site and downloaded/installed the drivers(LPr and cupswrapper).  I went through the settings/printer/add printer dialogue and added the printer.  Really it was no issue getting the printer to install.  I can ping the printer from the terminal and like I said connect to it shows up in the add network printer dialogue.  I have the device URL in the printer properties set to lpd://192.168.127.2/BINARY_P1.  The problem is when I go to print it says it is printing and also says it is complete but never actually prints.  I don't get any errors displayed in the printer print pop-ups.  I tried to uninstall drivers, stop cups, restart cups, and reinstall drivers with no success. Along with a handful of other things but can't get anything to print.  Any help would be appreciated.
Thanks

Mike

---

### Post by plucky on 2018-11-08
>  I have the device URL in the printer properties set to lpd://192.168.127.2/BINARY_P1

My Brother Network printer (DCP-1610W) has the URL as ```
socket://192.168.0.100:9100
```

The port is set as 9100

You might have to reboot after changing the URL

Good Luck

---

### Post by him610 on 2018-11-08
My Brother MFC-7360n has a URL of ```
socket://10.0.0.197
```

---

### Post by nussmier on 2018-11-08
Thanks for the responses.  I tried socket://192.168.127.2 and rebooted. Unfortunately the problem is exactly the same.

I also ran nmap on the IP address and got the following:

Starting Nmap 7.60 ( [https://nmap.org](https://nmap.org) ) at 2018-11-08 16:28 EST
Nmap scan report for BRW78E4000C3558.lan (192.168.127.2)
Host is up (0.035s latency).
Not shown: 994 closed ports
PORT     STATE SERVICE
21/tcp   open  ftp
23/tcp   open  telnet
25/tcp   open  smtp
80/tcp   open  http
515/tcp  open  printer
9100/tcp open  jetdirect

Nmap done: 1 IP address (1 host up) scanned in 4.62 seconds

If I understand this right port 515 is used for LDP and 9100 is used for jetdirect.  I tried the following changes to the URL rebooting after each change:

I used URL LPD://192.168.127.2:515 and then socket://192.168.127.2:9100.

The results were still the same where it tells me the printing is complete with no errors but it never prints:

---

### Post by him610 on 2018-11-08
Did you personally set your browser to maneuver to the printer URL, 192.168.127.2 administrative setup page? You would have needed a logon and password to change either Admin or User modifiable settings.

Somehow, I can't help thinking something simple escapes us. Your machine is very similar to mine. This is my Brother installed software:
```
$ dpkg -l | grep Brother
ii  brmfcfaxlpd:i386                      1.0.0-2                                     i386         Brother MFC-FAX LPD driver
ii  brscan-skey                           0.2.4-1                                     amd64        Brother Linux scanner S-KEY tool
ii  brscan4                               0.4.6-1                                     amd64        Brother Scanner Driver
ii  cupswrappermfc7360n:i386              2.0.4-2                                     i386         Brother MFC7360N CUPS wrapper driver
ii  mfc7360nlpr:i386                      2.1.0-1                                     i386         Brother MFC-7360N LPR driver
ii  printer-driver-brlaser                4-1                                         amd64        printer driver for (some) Brother laser printers
ii  printer-driver-ptouch                 1.4.2-3                                     amd64        printer driver Brother P-touch label printers

```

Another thought, did you download and run the *Driver Install Tool * (vers 2.2.1.1 released 09/13/2018) to install your drivers?

---

### Post by him610 on 2018-11-08
I just ran *nmap* on mine, here 's what the results look like...
```
$ nmap -A 10.0.0.197

Starting Nmap 7.60 ( https://nmap.org ) at 2018-11-08 16:53 EST
Nmap scan report for 10.0.0.197
Host is up (0.048s latency).
Not shown: 993 closed ports
PORT     STATE SERVICE    VERSION
21/tcp   open  ftp        Brother/HP printer ftpd 1.13
23/tcp   open  telnet     Brother/HP printer telnetd
25/tcp   open  smtp       Brother printer smtpd
|_smtp-commands: SMTP: EHLO 500 Syntax error \x0D
80/tcp   open  http       Debut embedded httpd 1.20 (Brother/HP printer http admin)
|_http-server-header: debut/1.20
| http-title: Brother MFC-7360N
|_Requested resource was /main/main.html
515/tcp  open  printer
631/tcp  open  ipp?
9100/tcp open  jetdirect?
Service Info: Device: printer
 
```
I am running out of ideas. By the way, my network is also mixed Ubuntu-Windows. I have never encountered any issues, though.

---

### Post by nussmier on 2018-11-08
That dirver install tool was it.  It installed the 6490CN driver vs the CW driver but its working so for now I am going to leave it and will finish troubleshooting it later.  Thanks a bunch.

---

### Post by him610 on 2018-11-08
Oh, it's working now? Great! Please share with us how you got it working. All the Hardware Forum readers want to know. :)

---

### Post by nussmier on 2018-11-09
All I did to solve it was uninstall printer/drivers and then downloaded the Brother driver tool you mentioned above.  I ran the tool and it asked a bunch of questions about network, printer type, etc. I answered them and it installed the printer and driver and it worked.  The only strange thing is that it installed the drivers for Brother MFC6490CN and I have MFC6490CW but like I said its working so I am not going to mess with it until I have some free time.  Thanks again for your help.

---

