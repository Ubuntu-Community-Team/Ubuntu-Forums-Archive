---
title: "Epson TM-T88V thermal printer"
date: 2010-05-18
forum: Hardware
---

### Post by jsoderba on 2010-05-18
I'm trying to get a TM-T88V thermal printer to work with CUPS. I'm using Ubuntu 9.10 64-bit (and it would be very good if I didn't have to upgrade 10.04 yet, I need this to work with several other machines I can't easily upgrade.) When I try to print via CUPS I get an error pop-up saying a com.apple.print.recoverable exception or something like that has occured.

I installed the printer driver from Epson ([here](https://www.epson-pos.com/cgi-bin/sdssm/main/prod.jsp?BV_SessionID=@@@@1531631478.1274179178@@@@&BV_EngineID=ccceadekheiidmfcefeceeedfhldfkl.0&ptn=1&oid1=13056&oid2=15341&sub_id=14141)) and the printer shows up when I try to add a printer in the CUPS web interface. 

In cups I choose

1. Administration
2. Add Printer
3. Local printers: Epson TM/BA/EU printer
4. In connection I put socket://localhost
5. I input a name for the printer
6. I pick the PPD that came with the driver package epson-tm-t88v-rastertotmt.ppd

This creates a printer in the cups interface, and I can send jobs to it and see them both via the Web UI and the ubuntu GUI tools and the command line tools. But jobs are stuck forever on "processing". 

I can get text from the printer by running "echo test > /dev/usblp0" so the USB connection seems to work.

---

### Post by jsoderba on 2010-05-18
OK, looks like I figured it out on my own.

This fixed it:

cupsctl FileDevice=Yes
lpadmin -p EpsonTM-T88V -E -v file:/dev/usb/lp0 

where EpsonTM-T88V is the name of my printer queue.

This makes the printer run in a direct mode that disables some of the filters and security checks, so think about what you are doing if you need to do this.

---

### Post by LuisC-SM on 2011-01-29
> **jsoderba said:**
> OK, looks like I figured it out on my own.

This fixed it:

cupsctl FileDevice=Yes
lpadmin -p EpsonTM-T88V -E -v file:/dev/usb/lp0 

where EpsonTM-T88V is the name of my printer queue.

This makes the printer run in a direct mode that disables some of the filters and security checks, so think about what you are doing if you need to do this.

Hi. Most probabily too late for this.
It's very strange I did not find something similar in opensuse 2 weeks before,  however, I wanted to post my experience trying to install the TM-U220PD in OS11.3.

1.- To install the linux driver (for tm-u220 series) the printer should be off.

2.- To make it work one should symlink the rastertotmu filter:
(as root).... ```
# cd /usr/lib/cups/filter
# ln -s /usr/lib64/cups/filter/rastertotmu rastertotmu . (including the dot)
```
That's all folks, enjoy your EPSON POS ticket PRINTER and ... CUPS ;)

Regards

Luis

PD. Ref [http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2250737.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2250737.html)
[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/569190](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/569190)
Linux Driver: tmu-cups-1.0.0.0.tar.gz 
DL Site: [https://www.epson-pos.com/cgi-bin/sdssm/main/down_soft.jsp?BV_SessionID=@@@@1272278980.1296426081@@@@&BV_EngineID=ccceademihemiehcefeceeedfhldfkl.0&ptn=0&cont_id=15863](https://www.epson-pos.com/cgi-bin/sdssm/main/down_soft.jsp?BV_SessionID=@@@@1272278980.1296426081@@@@&BV_EngineID=ccceademihemiehcefeceeedfhldfkl.0&ptn=0&cont_id=15863)
Site (on what's new section): [https://www.epson-pos.com/cgi-bin/sdssm/main/td_login.jsp](https://www.epson-pos.com/cgi-bin/sdssm/main/td_login.jsp)
User Manual: [https://www.epson-pos.com/1to1/sd/txtfiles/cups_UsersManual_V200.html](https://www.epson-pos.com/1to1/sd/txtfiles/cups_UsersManual_V200.html)
Linux Driver is for Ubuntu/Debian 32/64 and openSuSE 11.1 32/64 distros

---

### Post by arsya on 2011-04-01
@jsoderba: Thank you very much for sharing. I used your method with EPSON TM T81 and it worked great!
Previously, I had to send the raw data directly, and having a lot of trouble with buffer limitation of the device.
Now, what I need is simply write all the esc pos command to a file and send it to cups via lpr command.

About, the job stuck on the queue, it also happened to me, when using the 'official driver'. I got some error messages in /var/log/messages, like the following:
gs[8725]: segfault at 0 ip .... error 6 in libgs.so.8.71[b6ed8000+46e000]

Perhaps problem with ghostscript? I am not really sure, but I still prefer writing ESC/POS commands and send them to the printer via cups.

---

