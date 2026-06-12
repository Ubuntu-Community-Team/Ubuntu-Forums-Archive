---
title: "Can't find network printer (IPv4 address exists)"
date: 2016-12-30
forum: Hardware
---

### Post by andyru on 2016-12-30
I just bought a new Canon PIXMA MX922 printer and my linux machine is not finding the printer on the network. The printer is wired into the network with an ethernet cable and displays an IPv4 address (do I need an IPv6 address too...? I had to diable it on the printer to get it to connect). A mac that I have is able to connect and print without a problem but my linux comp cannot. When I type the IP into "Find network printer" it displays "No printer was found at that address". Any help is really appreciated!

---

### Post by Bucky Ball on 2017-01-14
Welcome. As above. You need to [go here and download and install the drivers]("https://www.usa.canon.com/internet/portal/us/home/support/details/printers/inkjet-multifunction/mx-series-inkjet/mx922") (click the 'Downloads and Drivers' button and choose your architecture). Once that's done, open 'Printers', delete any printers you've created to avoid confusion, 'Add Printer' and 'Network Printer' and give it a few seconds to find the network printer. From there, follow your nose. You will be asked to select a driver. Select the one you downloaded and installed.

Note: no, you don't need IPv6 on. Leave it off or 'Ignore'.

---

### Post by slickymaster on 2017-01-15
*Thread moved to **Hardware**.*

---

### Post by pdc on 2017-01-15
sadly, the US Canon site very frequently lacks links to the extensive linux support that Canon provide; what a shame

so if one goes to the Canon Asia site, [http://support-asia.canon-asia.com/?personal](http://support-asia.canon-asia.com/?personal) and moves to the MX922 one gets to here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100517002.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100517002.html)

(Canon supply 3 flavours of linux driver; rpm, debian and source code); from the link above if you download [COLOR="#008000"]cnijfilter-mx920series-3.90-1-deb.tar.gz[/COLOR] and save to your Downloads folder, the terminal commands to install would be:

```
cd Downloads
```

```
tar -zxvf cnijfilter-mx920series-3.90-1-deb.tar.gz
```

```
cd cnijfilter-mx920series-3.90-1-deb
```

then run the install script ```
./install.sh
```           .......one would hope that detects your printer and does the necessary.

it is the 922 in the US, but the 927 in Asia; but the driver is of the 920 series ..............

Canon also supply scanner (linux) drivers from here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100518302.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100518302.html)

so if one closes the terminal; and re-opens it, the format of the commands is the same, except one is installing **scangearmp-mx920series-2.10-1-deb.tar.gz**

the crucial thing is one is installing ScanGearMP, that is COMPLETELY SEPARATE to Simple Scan etc; so you run it initially from the terminal with ```
scangearmp
``` .......if it works, we can point you to a shortcut

---

