---
title: "Lexmark x2480"
date: 2007-11-30
forum: Hardware &amp; Laptops
---

### Post by bigscotty20 on 2007-11-30
Hello. I am trying to get my lexmark x2480 inkjet working. How do I do this.

---

### Post by jcsteele on 2007-11-30
have you plugged it in?  Is it USB?  Does anything appear on your screen when you plug it in (usb)?  If USB, can you post the output of "lsusb" to us...

What version of ubuntu are you on?  Please provide some specific information so we can help.

//jcs

---

### Post by bigscotty20 on 2007-12-01
Sorry. I use Ubuntu 7.04. The (USB) printer is plugged in and turned on. LSUSB gives this output:
```
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 006: ID 043d:00e9 Lexmark International, Inc. 
Bus 001 Device 001: ID 0000:0000  
``` Nothing happens immediately when I connect the printer; when I go to Administration > Printing > New Printer, the first screen lists it 3 times: Lexmark 2400 Series (Lexmark 2400 Series USB #1), Lexmark 2400 Series (Lexmark Printer), and Lexmark 2400 Series (Lexmark Printer). When I select any of them and go to the next screen, NOTHING in the 2400 series is listed.
Thx.
Scott

---

### Post by jcsteele on 2007-12-01
can you take a screenshot of the printer selection screen where it lists the lexmark models??

//jcs

---

### Post by bigscotty20 on 2007-12-01
Screenshot attached. I also have the terminal output I get when I manually invoke gnome-cups-add:
```
scott@scott-laptop:~$ gnome-cups-add

** (gnome-cups-add:6022): WARNING **: Two ppds have driver == 'pbm2lwxl (recommended)'
        ->foomatic:Avery-Personal_Label_Printerplus-pbm2lwxl.ppd (Avery Personal Label Printer+ Foomatic/pbm2lwxl (recommended)[1]) and
        ->foomatic:Avery-Personal_Label_Printer-pbm2lwxl.ppd (Avery Personal Label Printer Foomatic/pbm2lwxl (recommended))[1]

** (gnome-cups-add:6022): WARNING **: model named 'Designjet 800PS (recommended)' doesn't have a recognized structure

** (gnome-cups-add:6022): WARNING **: model named 'DesignJet 5000PS (recommended)' doesn't have a recognized structure

** (gnome-cups-add:6022): WARNING **: model named 'designjet 5500ps (recommended)' doesn't have a recognized structure

** (gnome-cups-add:6022): WARNING **: Two ppds have driver == 'High Quality Image (Gutenprint CUPS) (expert)'
        ->gutenprint.5.0://hp-cij_cp1700/expert/C (HP Color Inkjet Printer CP1700 - CUPS+Gutenprint v5.0.0.99.1[0]) and
        ->gutenprint.5.0://hp-cij_cp1160/expert/C (HP Color Inkjet Printer CP1160 - CUPS+Gutenprint v5.0.0.99.1)[0]

** (gnome-cups-add:6022): WARNING **: Two ppds have driver == 'High Quality Image (Gutenprint CUPS) (simple)'
        ->gutenprint.5.0://hp-cij_cp1700/simple/C (HP Color Inkjet Printer CP1700 - CUPS+Gutenprint v5.0.0.99.1 Simplified[0]) and
        ->gutenprint.5.0://hp-cij_cp1160/simple/C (HP Color Inkjet Printer CP1160 - CUPS+Gutenprint v5.0.0.99.1 Simplified)[0]

** (gnome-cups-add:6022): WARNING **: Two ppds have driver == 'hpijs (recommended)'
        ->foomatic:HP-Color_Inkjet_Printer_CP1700-hpijs.ppd (HP Color Inkjet Printer CP1700 Foomatic/hpijs (recommended)[1]) and
        ->foomatic:HP-Color_Inkjet_Printer_CP1160-hpijs.ppd (HP Color Inkjet Printer CP1160 Foomatic/hpijs (recommended))[1]

** (gnome-cups-add:6022): WARNING **: Two ppds have driver == 'Postscript (recommended)'
        ->foomatic:HP-LaserJet_9000_MFP-Postscript.ppd (HP LaserJet 9000 MFP Foomatic/Postscript (recommended)[1]) and
        ->openprinting/HP/mono_laser/HP_LaserJet_9000_MFP.ppd.gz (HP LaserJet 9000 MFP  Postscript (recommended))[1]

** (gnome-cups-add:6022): WARNING **: Two ppds have driver == 'PS3'
        ->openprinting/Oce/Others/OC8445_3.ppd.gz (Oce 8445 PS3[0]) and
        ->openprinting/Oce/Oce-8445PS/1/OC8445_3.ppd.gz (Oce 8445 PS3)[0]

** (gnome-cups-add:6022): WARNING **: Two ppds have driver == 'PS3'
        ->openprinting/Oce/Others/OC8465_3.ppd.gz (Oce 8465 PS3[0]) and
        ->openprinting/Oce/Oce-8465PS/1/OC8465_3.ppd.gz (Oce 8465 PS3)[0]

** (gnome-cups-add:6022): WARNING **: Two ppds have driver == 'PS3'
        ->openprinting/Oce/Others/OC3145_3.ppd.gz (Oce NC3145 PS3[0]) and
        ->openprinting/Oce/Oce-3145PS/1/OC3145_3.ppd.gz (Oce NC3145 PS3)[0]

** (gnome-cups-add:6022): WARNING **: Two ppds have driver == 'PS3'
        ->openprinting/Oce/Others/OC3155_3.ppd.gz (Oce NC3155 PS3[0]) and
        ->openprinting/Oce/Oce-3155PS/1/OC3155_3.ppd.gz (Oce NC3155 PS3)[0]

** (gnome-cups-add:6022): WARNING **: Two ppds have driver == 'PS3'
        ->openprinting/Oce/Others/OC3165_3.ppd.gz (Oce NC3165 PS3[0]) and
        ->openprinting/Oce/Oce-3165PS/1/OC3165_3.ppd.gz (Oce NC3165 PS3)[0]

** (gnome-cups-add:6022): WARNING **: Two ppds have driver == 'PS3'
        ->openprinting/Oce/Others/OCVP2105.ppd.gz (Oce VarioPrint 2105 PS3[0]) and
        ->openprinting/Oce/Oce-VarioPrint_2105PS/1/OCVP2105.ppd.gz (Oce VarioPrint 2105 PS3)[0]

** (gnome-cups-add:6022): WARNING **: Two ppds have driver == 'PS3'
        ->openprinting/Oce/Others/OCVP2090.ppd.gz (Océ VarioPrint 2090 PS3[0]) and
        ->openprinting/Oce/Oce-VarioPrint_2090PS/1/OCVP2090.ppd.gz (Oce VarioPrint 2090 PS3)[0]

** (gnome-cups-add:6022): WARNING **: Two ppds have driver == 'PS, 1.2'
        ->openprinting/Sharp/shc260mj.ppd.gz (Sharp AR-C260M PS, 1.2[0]) and
        ->openprinting/Sharp/shac260m.ppd.gz (Sharp AR-C260M PS, 1.2)[0]

** (gnome-cups-add:6022): WARNING **: Two ppds have driver == 'PS, 1.1'
        ->openprinting/Sharp/Sharp-MX-2300G-ps.ppd.gz (Sharp MX-2300G PS, 1.1[0]) and
        ->openprinting/Sharp/Sharp-MX-2300G-ps-jp.ppd.gz (Sharp MX-2300G PS, 1.1)[0]

** (gnome-cups-add:6022): WARNING **: Two ppds have driver == 'PS, 1.1'
        ->openprinting/Sharp/Sharp-MX-2700G-ps.ppd.gz (Sharp MX-2700G PS, 1.1[0]) and
        ->openprinting/Sharp/Sharp-MX-2700G-ps-jp.ppd.gz (Sharp MX-2700G PS, 1.1)[0]

** (gnome-cups-add:6022): WARNING **: Two ppds have driver == 'PS, 1.1'
        ->openprinting/Sharp/Sharp-MX-3500N-ps.ppd.gz (Sharp MX-3500N PS, 1.1[0]) and
        ->openprinting/Sharp/Sharp-MX-3500N-ps-jp.ppd.gz (Sharp MX-3500N PS, 1.1)[0]

** (gnome-cups-add:6022): WARNING **: Two ppds have driver == 'PS, 1.1'
        ->openprinting/Sharp/Sharp-MX-3501N-ps.ppd.gz (Sharp MX-3501N PS, 1.1[0]) and
        ->openprinting/Sharp/Sharp-MX-3501N-ps-jp.ppd.gz (Sharp MX-3501N PS, 1.1)[0]

** (gnome-cups-add:6022): WARNING **: Two ppds have driver == 'PS, 1.1'
        ->openprinting/Sharp/Sharp-MX-4500N-ps.ppd.gz (Sharp MX-4500N PS, 1.1[0]) and
        ->openprinting/Sharp/Sharp-MX-4500N-ps-jp.ppd.gz (Sharp MX-4500N PS, 1.1)[0]

** (gnome-cups-add:6022): WARNING **: Two ppds have driver == 'PS, 1.1'
        ->openprinting/Sharp/Sharp-MX-4501N-ps.ppd.gz (Sharp MX-4501N PS, 1.1[0]) and
        ->openprinting/Sharp/Sharp-MX-4501N-ps-jp.ppd.gz (Sharp MX-4501N PS, 1.1)[0]
scott@scott-laptop:~$ 


```
Lucky coincidence we were online at the same time.
Scott

---

### Post by rare HERO on 2008-02-25
This link should reveal some info, isn't good news though:

[http://www.linuxprinting.org/show_printer.cgi?recnum=Lexmark-X2480]("http://www.linuxprinting.org/show_printer.cgi?recnum=Lexmark-X2480")

---

### Post by K.Morgan on 2008-06-06
I've been trying to find out if this printer will work and stumbled across this thread.  

So is the final conclusion that there's absolutely no way of getting this printer to work with Ubuntu? not even Hardy?

I'm surprised that there isn't some sort of wrapper available like there is for wireless cards with Ndsiwrapper?

---

