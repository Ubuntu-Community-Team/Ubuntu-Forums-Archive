---
title: "Epson Stylus Color 670 not detected"
date: 2005-05-25
forum: Hardware &amp; Laptops
---

### Post by Vurdak829 on 2005-05-25
I have a very big problem with this printer...i've searched the web, the forum, but i can't use this printer...
The printer is perfectly working on linux, i have used it on suse, mandrake and fedora, but in ubuntu (x86)  it doesn't work..
I've tried with lsmod
> vurdak@zeus:~$ lsmod | grep parport
parport_pc             34372  0
parport                33480  2 parport_pc,lp 

and

> vurdak@zeus:~$ dmesg | grep parport
vurdak@zeus:~$ 

The second one it's very scaring me.. :D

Any one can help me? I have no idea..

---

### Post by cdhotfire on 2005-05-25
[http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-Stylus_Color_670](http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-Stylus_Color_670)

seems it should work perfectly.
```

$ sudo apt-get install cupsys-driver-gimpprint cupsys-driver-gimpprint-data

```

System -> Administration -> Printing

New Printer

Select Local Printer, if it is not detected, choose what type of cable your used(USB or Parallel).  Then click Foward.

Choose your Printer. Then press Apply.

Ez as Pie. Yum!;-)

---

### Post by David Haas on 2005-05-25
After selecting your Epson printer model in the Printers application, you should select the PPD file for it in that application. Click through the directories to your PPD file, which is in Hoary. It's escp2-670.ppd.gz and its located in the directory /usr/share/cups/model/gimp-print/4.2. When you select it with the "Open" button, an unzipped copy of it will be placed in etc/cups/ppd. Then, your printer should work.
David

---

### Post by Vurdak829 on 2005-05-26
Nothing...the printers is not detected yet... :neutral:

---

### Post by cdhotfire on 2005-05-26
[QUOTE=cdhotfire][http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-Stylus_Color_670]("http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-Stylus_Color_670")

seems it should work perfectly.
```

$ sudo apt-get install cupsys-driver-gimpprint cupsys-driver-gimpprint-data

```

System -> Administration -> Printing

New Printer

Select Local Printer, if it is not detected, choose what type of cable your used(USB or Parallel).  Then click Foward.

Choose your Printer. Then press Apply.

Ez as Pie. Yum!;-)[/QUOTE]

Did you do this?

I said if it is not detected choose "Select Local Printer" and then select the cable you used.:???:

---

### Post by Vurdak829 on 2005-05-26
[QUOTE=cdhotfire]Did you do this?

I said if it is not detected choose "Select Local Printer" and then select the cable you used.:???:[/QUOTE]

It doesn't see the parralel port..only usb's...

---

### Post by cdhotfire on 2005-05-27
hmmm, i dont know.:|

I think the parallel port drivers are not working. :?

Edit: I found this:
  **Make**  

     **Model**  

     **PPD/Driver**  

     **Supported**  

     **Works?**  

     **Comments**  

     **Last Updated**  

  

           Epson  

     Stylus C60  

     ??  

     No  

     Yes  

     Needs cupsys-driver-gimpprint from universe. Does not seem to work over parallel port connection but does work over USB  

     21-Oct-2004

---

### Post by Vurdak829 on 2005-05-29
Uhm, it doesn't work yet..it's a kernel problem i suppose..now i'll try with 2.6.11

---

