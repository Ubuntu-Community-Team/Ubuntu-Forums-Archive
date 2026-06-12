---
title: "HP network duplex printer doesn't print duplex for auto discovered printer"
date: 2022-04-28
forum: Hardware
---

### Post by mark-16288 on 2022-04-28
This is a strange issue I've found. I have an HP M252dw printer connected to my network. 

Without any action on my part, in "Printer" (under Settings in the menu), it will automatically detect my printer and put it in as "HP_Color_LaserJet_Pro_M252dw_A38503_". 
For this discovered printer, in properties, the "Printer Options" tab shows an entry for "2-Sided Printing", with "On (Portrait)" selected. While this looks good, selecting this printer will always print single-sided, regardless of the printer settings used in the print dialog. You can see the dialog with the printer options in the attached images, it's the one with 7 options shown, the fourth option in the list is the relevant option for duplex printing.

To see if there was a work around, I manually added the same printer in the "Printer" app. There were three printers in the "Network Printer" section that automatically displayed. 
1- HP Color LaserJet Pro M252dw(nnn.nnn.nnn.204)  - where the "n"s are my internal IP network
2- HP Color LaserJet Pro M252dw(HP%20Color%20LaserJet%20Pro%20M252dw%20(A38503)._ipp._tcp.local)
3- HP Color LaserJet Pro M252dw(NPIA38503.local,xxxxxxxxxx:8503) - I've substituted "x"s for the address
  
During the add, if I select the first printer with the IP address, it  highlights the Connection for "HP Linux Imaging and Printing (HPLIP)",  then offers a page showing "Installable Option" with "Duplex Unit",  which I check and then continue forward. See the third attached image for that dialog. After the install, when I go  into properties and the printer options tab, I see a different set of  options. See the first attached image. It shows more options. The second option in the tab  is "Two-Sided", I picked "Long-Edge Binding" (other options are "None"  and "Short-Edge Binding"). Printing with this gives me duplex printing,  unless I select to turn it off in the printing dialog.

If I select the second choice (with the "_ipp" in the description, it picks a Connection of "Driverless IPP". After the install, the printer options look exactly like the options from the auto discovered printer (the second attached image) and regardless of the printer options selected while printing a document, only single-sided pages are printed.

During the add, if I select the third printer containing "NPIA", it shows no option for Connection, but if I continue forward, it will show the dialog for Installable Option" where I can check the box for duplex unit. Once I continue forward it completes. Once installed, this printer will also have a printer options tab identical to the first printer (with the IP address). Printing with this will print duplex too.

Based on this, it would appear that the auto discover is picking the "Driverless IPP" option, which seems to have a bug that doesn't detect or allow setting the duplex installable option, rendering the duplex settings in the printer options tab in properties invalid.

What needs to be done to have someone address this issue, so that the "Driverless IPP" will allow use of duplex printing?

---

### Post by brian_p on 2022-04-28
> **mark-16288 said:**
> This is a strange issue I've found. I have an HP M252dw printer connected to my network. 

A puzzler indeed!

Please give

```
avahi-browse -rt _ipp._tcp
```

```
avahi-browse -rt _uscan._tcp
```
```
driverless
```

---

### Post by mark-16288 on 2022-04-29
Here are the outputs you requested:

===
$ sudo avahi-browse -rt _ipp._tcp
+   eth0 IPv6 HP Color LaserJet Pro M252dw (A38503)         Internet Printer     local
+   eth0 IPv4 HP Color LaserJet Pro M252dw (A38503)         Internet Printer     local
=   eth0 IPv6 HP Color LaserJet Pro M252dw (A38503)         Internet Printer     local
   hostname = [NPIA38503.local]
   address = [fe80::725a:fff:fea3:8503]
   port = [631]
   txt = ["mopria_certified=1.2" "mac=70:5a:0f:a3:85:03" "usb_MDL=HP Color LaserJet Pro M252dw" "usb_MFG=Hewlett-Packard" "TLS=1.2" "PaperMax=legal-A4" "kind=document,envelope,photo" "UUID=564e4233-4235-3233-3931-705a0fa38503" "Fax=F" "Scan=F" "Duplex=T" "Color=T" "note=" "adminurl=http://NPIA38503.local./hp/device/info_config_AirPrint.html?tab=Networking&menu=AirPrintStatus" "priority=10" "product=(HP Color LaserJet Pro M252dw)" "ty=HP Color LaserJet Pro M252dw" "URF=V1.4,CP99,W8,OB10,PQ3-4-5,ADOBERGB24,DEVRGB24,DEVW8,SRGB24,DM1,IS1,MT1-2-3-5-12,RS600" "rp=ipp/print" "pdl=image/urf,application/pdf,application/postscript,application/vnd.hp-PCL,application/vnd.hp-PCLXL,application/PCLm,application/octet-stream,image/jpeg" "qtotal=1" "txtvers=1"]
=   eth0 IPv4 HP Color LaserJet Pro M252dw (A38503)         Internet Printer     local
   hostname = [NPIA38503.local]
   address = [10.8.8.204]
   port = [631]
   txt = ["mopria_certified=1.2" "mac=70:5a:0f:a3:85:03" "usb_MDL=HP Color LaserJet Pro M252dw" "usb_MFG=Hewlett-Packard" "TLS=1.2" "PaperMax=legal-A4" "kind=document,envelope,photo" "UUID=564e4233-4235-3233-3931-705a0fa38503" "Fax=F" "Scan=F" "Duplex=T" "Color=T" "note=" "adminurl=http://NPIA38503.local./hp/device/info_config_AirPrint.html?tab=Networking&menu=AirPrintStatus" "priority=10" "product=(HP Color LaserJet Pro M252dw)" "ty=HP Color LaserJet Pro M252dw" "URF=V1.4,CP99,W8,OB10,PQ3-4-5,ADOBERGB24,DEVRGB24,DEVW8,SRGB24,DM1,IS1,MT1-2-3-5-12,RS600" "rp=ipp/print" "pdl=image/urf,application/pdf,application/postscript,application/vnd.hp-PCL,application/vnd.hp-PCLXL,application/PCLm,application/octet-stream,image/jpeg" "qtotal=1" "txtvers=1"]

===
$ avahi-browse -rt _uscan._tcp
<no output, even if using sudo>

===
$ driverless
ipp://HP%20Color%20LaserJet%20Pro%20M252dw%20(A38503)._ipp._tcp.local/

===
Don't know if this is helpful, but I also ran this:

$ avahi-browse -rt _pdl-datastream._tcp
+   eth0 IPv4 HP Color LaserJet Pro M252dw (A38503)         PDL Printer          local
+   eth0 IPv6 HP Color LaserJet Pro M252dw (A38503)         PDL Printer          local
=   eth0 IPv4 HP Color LaserJet Pro M252dw (A38503)         PDL Printer          local
   hostname = [NPIA38503.local]
   address = [10.8.8.204]
   port = [9100]
   txt = ["TBCP=T" "Binary=T" "Transparent=T" "note=" "adminurl=http://NPIA38503.local." "priority=40" "product=(HP Color LaserJet Pro M252dw)" "ty=HP Color LaserJet Pro M252dw" "qtotal=1" "txtvers=1" "UUID=564e4233-4235-3233-3931-705a0fa38503"]
=   eth0 IPv6 HP Color LaserJet Pro M252dw (A38503)         PDL Printer          local
   hostname = [NPIA38503.local]
   address = [fe80::725a:fff:fea3:8503]
   port = [9100]
   txt = ["TBCP=T" "Binary=T" "Transparent=T" "note=" "adminurl=http://NPIA38503.local." "priority=40" "product=(HP Color LaserJet Pro M252dw)" "ty=HP Color LaserJet Pro M252dw" "qtotal=1" "txtvers=1" "UUID=564e4233-4235-3233-3931-705a0fa38503"]

---

### Post by brian_p on 2022-04-30
The info looks OK. Try setting up this print queue:

```
lpadmin -p LaserJetM252 -v "ipp://HP%20Color%20LaserJet%20Pro%20M252dw%20(A38503)._i pp._tcp.local/" -E -m everywhere
```

Then print:

```
lp -d LaserJetM252 -o sides=two-sided-long-edge /etc/services
```

---

### Post by mark-16288 on 2022-05-01
When I ran the lpadmin command, it created a new printer, "LaserJetM252". When I printed using the second command, I get dual-sided printout.

Interestingly, when I look at the Printer Properties "Printer Options" tab, I get a new set of options shown. I've attached the file "2022-05-01_Printer-Options_from-lpadmin-cmd.png" showing the new options. I can also print duplex from a browser, PDF reader, etc., using the new Printer.

While this is another work around similar to what I did using the GUI, it still doesn't fix the automatically generated printer. If I delete the automatic one named "HP_Color_LaserJet_Pro_M252dw_A38503_", it will regenerate and still only print 1-sided.

===
Here are the commands I ran, with the results;

```
$ lpadmin -p LaserJetM252 -v "ipp://HP%20Color%20LaserJet%20Pro%20M252dw%20(A38503)._ipp._tcp.local/" -E -m everywhere
```
```
$ lpinfo -v
network https
file cups-brf:/
network beh
network lpd
network socket
network ipp
direct hp
network http
network ipps
direct xpraforwarder
network smb
direct hpfax
network dnssd://HP%20Color%20LaserJet%20Pro%20M252dw%20(A38503)._ipp._tcp.local/?uuid=564e4233-4235-3233-3931-705a0fa38503
network ipp://HP%20Color%20LaserJet%20Pro%20M252dw%20(A38503)._ipp._tcp.local/
```
```
$ lp -d LaserJetM252 -o sides=two-sided-long-edge /etc/services
request id is LaserJetM252-556 (1 file(s))
```

---

### Post by brian_p on 2022-05-03
> **mark-16288 said:**
> When I ran the lpadmin command, it created a new printer, "LaserJetM252". When I printed using the second command, I get dual-sided printout.

That's a win in my book :D.

> 
Interestingly, when I look at the Printer Properties "Printer Options" tab, I get a new set of options shown. I've attached the file "2022-05-01_Printer-Options_from-lpadmin-cmd.png" showing the new options. I can also print duplex from a browser, PDF reader, etc., using the new Printer.

If you want the previous set of options, do

```
lpadmin -p LaserJetM252 -v "URI" -E -m driverless:"URI"
```

URI is

```
ipp://HP%20Color%20LaserJet%20Pro%20M252dw%20(A38503)._ipp._tcp.local
```

> 
While this is another work around similar to what I did using the GUI, it still doesn't fix the automatically generated printer. If I delete the automatic one named "HP_Color_LaserJet_Pro_M252dw_A38503_", it will regenerate and still only print 1-sided.

I haven't any idea why the auto-setup by cups-browsed does not give duplex printing. To remove the printer entry

```
sudo apt purge cups-browsed
```

---

### Post by him610 on 2022-05-03
> does not give duplex printing
While reading all of the posts in this thread I discovered another printer setup method that I was unaware of. I have not figured it all out yet, but I will trust someone else to do that. Try this - it shows an option to setup 2-sided printing.
```
ippeveprinter -v

```

---

### Post by bekzclz11 on 2022-05-04
Right-click the printer icon ( ) for your HP product. Click Printing Preferences, and then click the Features tab. In the Paper Saving Options area, select Automatic from the Two-sided printing drop-down list.












[COLOR=#000000][FONT=Arial][krnt.run]("https://krnl.run")
[myindigocard app]("https://indigocard.ltd")

[/FONT][/COLOR]

---

### Post by mark-16288 on 2022-05-07
For the auto-detected printer, that option will not work.

---

### Post by mark-16288 on 2022-05-07
So far, no one has really answered my question. I already know how to work around the problem. No additional work around suggestions are needed.

My original question was and is:
**What needs to be done to have someone address this issue, so that the "Driverless IPP" will allow use of duplex printing?**

---

### Post by brian_p on 2022-05-07
```
lpadmin -p LaserJetM252 -v "ipp://HP%20Color%20LaserJet%20Pro%20M252dw%20(A38503)._i pp._tcp.local/" -E -m driverless:"ipp://HP%20Color%20LaserJet%20Pro%20M252dw%20(A38503)._i pp._tcp.local/"
```

---

