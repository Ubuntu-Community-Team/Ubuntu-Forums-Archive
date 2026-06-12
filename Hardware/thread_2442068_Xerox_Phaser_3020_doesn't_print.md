---
title: "Xerox Phaser 3020 doesn't print"
date: 2020-04-29
forum: Hardware
---

### Post by aregnando on 2020-04-29
Hi everybody, I've installed Ubuntu 20.04 on my Dell 15 Inspiron 3581 I3-7020U, recently I've got a Xerox Phaser 3020 printer and when the printer was connected to the computer immediately was recognized and the OS suggested a driver (Xerox phaser 3010). The computer and the printer has communication but when I send a print, the printer receive the job but doesn't print it. 
Someone has experience about this printer. Thanks.

---

### Post by brian_p on 2020-04-29
With the Xerox connected to the network, gibe what you get for ```
avahi-browse -rt _ipp._tcp
``` ```
avahi-browse -rt _uscan._tcp
``` ```
driverless
```

---

### Post by aregnando on 2020-05-17
Good morning everybody, sorry for my delay.

1)```
aaaa@A-Inspiron-3581:~$ avahi-browse -rt _ipp._tcp
```
```
+ wlp2s0 IPv4 Xerox Phaser 3020 (XRX9C934E362E8A)           Internet Printer     local
= wlp2s0 IPv4 Xerox Phaser 3020 (XRX9C934E362E8A)           Internet Printer     local
   hostname = [XRX9C934E362E8A.local]
   address = [192.168.0.124]
   port = [631]
   txt = ["Staple=F" "Sort=F" "Fax=F" "Scan=F" "Punch=0" "PaperMax=legal-A4" "PaperCustom=T" "Duplex=F" "Copies=T" "Color=F" "Collate=F" "Bind=F" "URF=W8,RS600,IS1,CP1,IFU0,PQ4,OB10,V1.3" "kind=document,envelope,label" "UUID=16a65700-007c-1000-bb49-9c934e362e8a" "MDL=Phaser 3020" "MFG=Xerox" "usb_CMD=MFG:Xerox;CMD:SPL,URF,FWV,EXT;MDL:Phaser 3020;CLSPRINTER;CID:XR_GDI3_Class01_Mono;MODE:SPL3,R000105;" "usb_MDL:Phaser 3020" "usb_MFG=Xerox" "adminurl=http://XRX9C934E362E8A.local./sws/index.html?link=/sws/app/settings/network/AirPrint/AirPrint.html" "pdl=application/octet-stream,application/x-QPDL,image/urf" "product=(Xerox Phaser 3020)" "ty=Xerox Phaser 3020" "priority=51" "qtotal=1" "note=" "rp=ipp/print" "txtvers=1"]
```

2)```
avahi-browse -rt _ipp._tcp
```…doesn't return anything

3)```
driverless
```…doesn't return anything.

---

### Post by forkedaway on 2020-05-19
Hi! Got the same problem today with my brand new printer.

The point is the recommended Xerox phaser 3010 is a wrong one. To make the things work you probably need to install the proper one.

1) Go to the Xerox driver dowloads: [https://www.support.xerox.com/support/phaser-3020/downloads/enus.html?operatingSystem=linux](https://www.support.xerox.com/support/phaser-3020/downloads/enus.html?operatingSystem=linux)

2) Download and unpack the driver.

3) Run 'install-printer.sh' via the terminal.

4) Go to the System Properties => Printers => Additional printer settings...

5) Double click your printer in the opened window.

6) You should see the Xerox phaser 3010 as the printer model. Click 'Change..' button.

7) Pick the Xerox manufacturer from the list, hit the 'Next' button and you should see the proper 'Xerox Phaser 3020' driver in the list. If you haven't installed the Xerox Linux driver yet you have just the current 'Xerox phaser 3010' there.

8) Click 'Apply' and try to print the test page.

9) Have fun.

At least this one worked for me.

---

### Post by aregnando on 2020-05-19
So many thanks, it was so clear. The printer works perfectly now.
Thanks again.

---

### Post by cristyma on 2020-11-13
Hello, need some help please, the same problem. I am new to linux.
Downloaded the 2 drivers from xerox website. 
I cannot intall any of them.
The printer is autodetected and installed as 3010, but does not print (only recieves comanad ).
how do I manualy install drivers that I downloaded from xerox website?

---

### Post by aregnando on 2020-11-13
Hello, I follow step by step the indications from  forkedaway and it were perfectly fine.

1) Go to the Xerox driver dowloads: [https://www.support.xerox.com/suppor...ngSystem=linux](https://www.support.xerox.com/suppor...ngSystem=linux)

2) Download and unpack the driver.

3) Run 'install-printer.sh' via the terminal.   In this line I need to clarify that you need to open the terminal in the folder where is the file: /Downloads/uld
next verify there is a file called "install.sh" , the you run on the terminal: "sh install-printer.sh" without quotes.

4) Go to the System Properties => Printers => Additional printer settings...

5) Double click your printer in the opened window.

6) You should see the Xerox phaser 3010 as the printer model. Click 'Change..' button.

7) Pick the Xerox manufacturer from the list, hit the 'Next' button and you should see the proper 'Xerox Phaser 3020' driver in the list. If you haven't installed the Xerox Linux driver yet you have just the current 'Xerox phaser 3010' there.

8) Click 'Apply' and try to print the test page.

9) Have fun.

It works fine for me and thanks to Forkedaway.

---

### Post by cristyma on 2020-11-14
I used this link [https://www.support.xerox.com/en-za/product/phaser-3020/downloads?platform=linux&language=en](https://www.support.xerox.com/en-za/product/phaser-3020/downloads?platform=linux&language=en) and downloaded the first driver, extracted in curent folder (downloads)
In UHL folder right click open in terminal and I ran "install-printer.sh"   says comand not found
I ran "sh install-printer.sh" and that command worked an installed driver I think
Powered on the printer and conected it via usb, ubuntu installed it (as xerox Phaser3020  this time), and still said that it required aditional drivers, but IT WORKS IT PRINTED A TEST PAGE.
MANY THANKS :p

---

