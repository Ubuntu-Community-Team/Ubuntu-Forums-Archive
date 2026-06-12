---
title: "Install HP LJ 5L into Ubuntu 12.04 LTS"
date: 2013-11-22
forum: Hardware
---

### Post by shestero on 2013-11-22
I want to install my parallel-port printer HP LJ 5L through DKU cable through USB and then share it through LAN.
I connect the printer and it is seen as /dev/usb/lp0 and can even print a plain text if I copy it into the file.

Then using CUPS http interface I added the printer:
[TABLE]
[TR]
[TH]Description:[/TH]
[TD]HPLJ5L at fit-PC3[/TD]
[/TR]
[TR]
[TH]Driver:[/TH]
[TD]HP LaserJet 5L Foomatic/ljet4 (recommended) (grayscale, 2-sided printing)[/TD]
[/TR]
[TR]
[TH]Connection:[/TH]
[TD]usb:/dev/usb/lp0[/TD]
[/TR]
[TR]
[TH]Defaults:[/TH]
[TD]job-sheets=none, none media=iso_a4_210x297mm sides=one-sided
[/TD]
[/TR]
[/TABLE]


But it cannot print (*"Waiting for printer to become available."*).
What shall I do?

---

### Post by shestero on 2013-11-22
I tried [COLOR=#000000][FONT=lucida grande]file:///dev/usb/lp0[/FONT][/COLOR]  insted of [COLOR=#000000]usb:/dev/usb/lp0[/COLOR]
[COLOR=#333333]Add into [/COLOR][COLOR=#000000][FONT=lucida grande]/etc/cups/cupsd.conf:[/FONT][/COLOR][COLOR=#333333]
FileDevice yes
and make sudo service cups restart
Still see: [/COLOR][COLOR=#000000][FONT=lucida grande]File device URIs have been disabled. To enable, see the FileDevice directive in "/etc/cups/cupsd.conf".[/FONT][/COLOR][COLOR=#333333]
in CUPS interface (cannot add new printer).

[/COLOR]

---

### Post by shestero on 2013-11-22
root@fitpc3-shestero:~# lpadmin -p HPLJ5L  -E -v file:///dev/usb/lp0
lpadmin: File device URIs have been disabled. To enable, see the FileDevice directive in "/etc/cups/cupsd.conf".
root@fitpc3-shestero:~# cat /etc/cups/cupsd.conf | grep FileDevice
FileDevice yes
root@fitpc3-shestero:~# cupsctl | grep FileDevice
FileDevice=yes

---

### Post by Bucky Ball on 2013-11-22
You need to have HPLip installed and that will install the printer drivers. Then delete and add the printer in Printing.

HPLip is in the repositories. Install from there.

---

### Post by shestero on 2013-11-22
hplip was installed before I began.

NB Now I eventually mentioned that I cannot print plain text copying it into /dev/usb/lp0 any more.

---

### Post by shestero on 2013-11-22
Update:
In error log I mentioned:
> [COLOR=#000000]W [23/Nov/2013:07:53:39 +0400] Please move "FileDevice yes" on line 2 of /etc/cups/cupsd.conf to the /etc/cups/cups-files.conf file; this will become an error in a future release.
[/COLOR]W [23/Nov/2013:07:53:39 +0400] Please move "User lp" on line 3 of /etc/cups/cupsd.conf to the /etc/cups/cups-files.conf file; this will become an error in a future release.
W [23/Nov/2013:07:53:39 +0400] Please move "Group lp" on line 4 of /etc/cups/cupsd.conf to the /etc/cups/cups-files.conf file; this will become an error in a future release. [COLOR=#000000]E [23/Nov/2013:07:53:39 +0400] Unknown directive SystemGroup on line 7 of /etc/cups/cupsd.conf.[/COLOR]So I do.
After restarting cups I manage to add the printer fith URI file:///dev/usb/lp0
But it still not working!
> [COLOR=#000000]E [23/Nov/2013:08:35:36 +0400] [Job 11] Stopping job because the scheduler could not open the output file.[/COLOR]

---

