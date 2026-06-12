---
title: "Epson Printer not printing correctly"
date: 2017-04-18
forum: Hardware
---

### Post by heroquestelf on 2017-04-18
First off, I'm running Ubuntu Mate 16.04.1 LTS on a Toshiba Satellite  with a 2x Intel Core2 Duo CPU (T550 @ 1.83GHz) with 3071MB of memory.

Secondly, I have an Epson printer (Workforce WF-3640) which is installed as a network printer. On my two Windows 10 desktop PC's it prints fine, but when I try to print from my Ubuntu MATE laptop, the printouts come out looking funny. Everything I send to the printer **DOES** actually print, but it prints really light. Instead of my text documents printing in black it prints in gray. Anybody got any idea how to fix this?

---

### Post by pdc on 2017-04-18
Hi Hero; if you go to the PRINTERS folder; find the icon there for your Epson; right-click; look in MAKE & MODEL: 

eg for our Epson XP-410 I see ```
Epson XP-410 Series - epson-inkjet-printer 1.0.0-1lsb3.2 (Seiko Epson Corporation LSB 3.2)
```

_____________

If one were starting at the Epson website, to download their driver; best delete the existing Epson config in your PRINTERS folder .. start afresh ..

The Epson website would take you here [http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=55539&DSCCHK=5ef6ec128765534a989152269045f12fc58077f2](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=55539&DSCCHK=5ef6ec128765534a989152269045f12fc58077f2)

for a 64bit install??, that would be epson-inkjet-printer-escpr_1.6.13-1lsb3.2_amd64.deb ...... click to download; select OPEN as the option, and hopefully software manager will install it; and trigger a new registration and config

---

### Post by heroquestelf on 2017-04-19
I deleted the printer, then re-downloaded and re-installed the driver, and now it works fine. Ubuntu support forums for the win!!

---

### Post by pdc on 2017-04-19
great! Pleased to hear it is all working for you: enjoy!

---

