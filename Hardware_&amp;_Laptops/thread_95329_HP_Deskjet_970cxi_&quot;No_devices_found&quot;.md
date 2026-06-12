---
title: "HP Deskjet 970cxi &quot;No devices found&quot;"
date: 2005-11-26
forum: Hardware &amp; Laptops
---

### Post by panka43 on 2005-11-26
(first of all i'm sorry for my bad english)  
 
Hi folks,  
 
i'm writing to signal the problem i had with the hplip toolbox program.  
 
i had succesfully installed my HP Deskjet 970 cxi with the Gnome->System->Administration->Printers utility (in my Ubuntu 5.10), but i've found a lot of problems when i printed (blank pages, unknowed strings printed on parts of pages..)  
 
When i discovered the HPLIP project i read the installation instructions and i discovered that the HPLIP was already installed on my machine. ;-(  
When i tried to make the hplip GUI work (the hplip toolbox or Device Manager), i received this message:  
 
"No installed HP devices found. To install a device, use the CUPS web interface ([http://localhost:631](http://localhost:631)) or the printer installation utility that came with your operating system. After setting up a printer, you must press F6 or chose Device | Refresh All for the printer to appear in the HP Device Manager.  
 
Note: Only devices installed with the hp:CUPS backend will appear in the Hp Device Manager"  
 
I pressed the button "CUPS Web Interface" and after some problems i succeeded in installing my printer with the web interface, but the Hp Device Manager spotted the same error.  
 
I tried with the console command  
 
hp-probe  
 
and  
 
hp-makeuri parallel:/dev/lp0  
 
but the first answered:  
 
[ERROR]: No devices found.  
[ERROR]: Error occured during interactive mode. Exiting.  
 
and the second:  
 
[ERROR]: parallel:/dev/lp0: Failed. Please check device node of device and try again.  
 
Now, i've no idea about to do.  
 
Someone can help me please? where i do mistaken?  
 
thanks..  
 
panka43

---

### Post by abstauber on 2006-01-13
Hi,

after lots of searching google, I may have found a solution for this.
I think there's a problem with the device URI in /etc/cups/printers.conf

If you have hplip installed, launch the following command in the shell
```
hp-info |fgrep device-uri
```
It returned me this line:
```
device-uri                    hp:/usb/DESKJET_990C?serial=ES08G1C0G5LG 
```

Now you've to change the device URI in /etc/cups/printers.conf: ```
### Old value
#DeviceURI usb://HP/DeskJet%20990C?serial=ES08G1C0G5LG

### New value from hp-info
DeviceURI hp:/usb/DESKJET_990C?serial=ES08G1C0G5LG
```

The HP-Toolbox should work now, but for me it didn't give me any improvements over gnome printing.

---

### Post by coaxx on 2006-01-15
[QUOTE=abstauber]Hi,

after lots of searching google, I may have found a solution for this.
I think there's a problem with the device URI in /etc/cups/printers.conf

If you have hplip installed, launch the following command in the shell
```
hp-info |fgrep device-uri
```
It returned me this line:
```
device-uri                    hp:/usb/DESKJET_990C?serial=ES08G1C0G5LG 
```

Now you've to change the device URI in /etc/cups/printers.conf: ```
### Old value
#DeviceURI usb://HP/DeskJet%20990C?serial=ES08G1C0G5LG

### New value from hp-info
DeviceURI hp:/usb/DESKJET_990C?serial=ES08G1C0G5LG
```

The HP-Toolbox should work now, but for me it didn't give me any improvements over gnome printing.[/QUOTE]

For me this does not work, because "hp-info" / "hp-probe" etc dont work, they just tell that there is no hp device. But there is, its a HP 1220 connected to /dev/lp0 and its set in cups. I dont have the needed uri with the serial in /etc/cups/printer.conf.

Printing is fine. As far as I know there is no other way to clean the tank by another way.

Maybe I shouldt boot from a Suse Live Cd and check the hp:/<   > uri and use that in /etc/cups/printer.conf. This shouldt work then...

---

### Post by pjbgravely on 2006-01-26
Same problem for me, I am guessing that "hp" the cups backend is not installing properly. also sane cannot find the scanner on the hp photo-smart 2600, so that back end must not be installed either. I hope to be able to spend more time on this soon. Both printers do print fine, I just cannot run the Hplip toolbox.

Update: [On this page]("http://hpinkjet.sourceforge.net/hplip_readme.html") near the bottom I found some troubleshooting. It didn't help get Hplip tool box working but I can now scan from the HP PhotoSmart 2600 printer/scanner.

---

### Post by kewl1uk on 2006-02-04
Worked for me with the HP PSC1410. Thank you:
```
#DeviceURI usb://HP/PSC%201400%20series?serial=******
DeviceURI hp:/usb/PSC_1400_series?serial=******
```
btw I censored the serial :)

Previous ppl who couldn't get
```
hp-info |fgrep device-uri
```
to work. Did you install the printer first: System > Administration > Printing > New Printer.

---

### Post by sundman on 2006-02-06
This fix works for me, too, with an DeskJet 5150.

[QUOTE=abstauber]
The HP-Toolbox should work now, but for me it didn't give me any improvements over gnome printing.[/QUOTE]

My only reason is to use the hplip toolbox is to figure out the ink levels. Or is there some other way to show them?

---

