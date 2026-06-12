---
title: "Brother HL 2140 on Dell Optiplex 330 just prints non-stop blanks"
date: 2015-01-19
forum: Hardware
---

### Post by mostlybob2 on 2015-01-19
I have an install of Lubuntu 14.04 64 bit on a Dell Optiplex 330. I have it connected to a Brother HL-2140 via USB. It's a fresh install on a new SSD. I went through the printer control panel and did a standard install. It saw and correctly identified the printer, however when I try to print a test page, the printer starts spitting out blank pages and does not stop until the tray is empty or you shut off the printer. Even then, when you start the printer back up, it starts putting out blanks again. The only way I found to stop it was to shut off the printer and reboot the computer. My own machine is running Ubunt MATE 14.04 64 bit connecting to a Brother HL-2280DW via network with no issues, so this behavior was unexpected. Any ideas where to start looking would be appreciated. Thanks!

---

### Post by pdc on 2015-01-20
Hi Bob

Brother offer what they call a "Driver Install Tool": can I suggest you let that do the work for you?

If what you have doesn't work, can I suggest you delete the current Brother setting so go to Menu/Administration/Printing or however it is set up in Lubuntu; delete any setting; leave the HL-2140 turned off for now

______________________

to get the Brother install tool, go here [http://support.brother.com/g/b/downloadend.aspx?c=au&lang=en&prod=hl2140_all&os=128&dlid=dlf006893_000&flang=4&type3=625](http://support.brother.com/g/b/downloadend.aspx?c=au&lang=en&prod=hl2140_all&os=128&dlid=dlf006893_000&flang=4&type3=625)

and click to DOWNLOAD and SAVE and the assumption will be that downloads are by default saved to your Downloads directory

_____________________

if you open a terminal, and copy these commands; and paste them into the terminal; line by line

```
cd Downloads
```

```
gunzip linux-brprinter-installer-2.0.0-1.gz
```

```
sudo bash linux-brprinter-installer-2.0.0-1 HL-2140
```

___________

that should activate the installer script; it should ask you to confirm the machine  and it should do all for you

____________

any joy?

---

### Post by mostlybob2 on 2015-01-20
It's a church computer, so I can't get to it immediately, but I will try that at my first opportunity. Thanks for the quick response!

---

### Post by birdy62 on 2015-11-13
I am not the OP but this worked for me despite the process throwing up several errors. Also I was installing for a HL-2142 on a generic Intel® Core™ i5-4570 CPU @ 3.20GHz × 4 running 14.04 LTS Ubuntu Gnome. At the end I was presented with the following dialogue ```
Errors were encountered while processing:
 cupswrapperHL2140-2.0.2-1a.i386.deb
################################

0: cups-pdf:/
1: ipps
2: ipp
3: nx
4: socket
5: nxprint
6: usb://Brother/HL-2140%20series?serial=F0J731627
7: https
8: serial:/dev/ttyS0?baud=115200
9: smb
10: ipp14
11: lpd
12: http
13 (I): Specify IP address.
14 (A): Auto. (usb://Brother/HL-2140%20series?serial=F0J731627)

select the number of destination Device URI. ->14

lpadmin -p HL2140 -v usb://Brother/HL-2140%20series?serial=F0J731627 -E -P /usr/share/cups/model/HL2140.ppd
Test Print? [y/N] ->y

wait 5s.
lpr -P HL2140 /usr/share/cups/data/testprint
```
As you can see I chose "14" and this worked for me. 
Note: Despite clearing all printers in "system settings" once I turned on the printer Ubuntu automatically installed "HL2040-series" drivers as the default printer as well as "HL2140" . Producing the same problem as mentioned by the OP. Setting "HL2140" to default solved the problem.

---

