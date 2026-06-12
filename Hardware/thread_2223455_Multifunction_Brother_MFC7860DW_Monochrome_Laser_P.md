---
title: "Multifunction Brother MFC7860DW Monochrome Laser Printer"
date: 2014-05-11
forum: Hardware
---

### Post by rickm1945 on 2014-05-11
I have a Brother Multifunction Printer MFC7860DW Brother has the driver for fax,scan and printer. It uses cups, which I know nothing about. Here is a link to Brother if anyone wants to take a look. [http://support.brother.com/g/s/id/linux/en/index.html?c=us&lang=en&prod=mfc7860dw_all&redirect=on](http://support.brother.com/g/s/id/linux/en/index.html?c=us&lang=en&prod=mfc7860dw_all&redirect=on) I am having a difficult time understanding it all. Any help will be greatly appreciated. I'm using Ubuntu 14.04.

---

### Post by pdc on 2014-05-11
Brother offer an install script; so it should ..........do everything for you

go here [http://support.brother.com/g/b/downloadlist.aspx?c=gb&lang=en&prod=mfc7860dw_all&os=128](http://support.brother.com/g/b/downloadlist.aspx?c=gb&lang=en&prod=mfc7860dw_all&os=128)  and click to download the Driver Install Tool           ........elect to **SAVE** it (and it will go to your Downloads directory)

if you can open a terminal [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal) .........see the paragraph **[COLOR="#800000"]Starting a Terminal[/COLOR]**

if you paste these commands: use the mouse and top line of the terminal and *hit the enter key after each paste* .........

> [COLOR="#FF0000"]cd Downloads[/COLOR]

> [COLOR="#FF0000"]gunzip linux-brprinter-installer-2.0.0-1.gz[/COLOR]

> [COLOR="#FF0000"]sudo bash linux-brprinter-installer-2.0.0-1 MFC-7860DW[/COLOR]     ..........and you will be asked for your sudo password, so have it ready ..................

and that should install the printer driver ,...........and the scanner I understand.................

____________________--

If we see how you get along with all that ...................if you subscribe to a thread, you can follow it ......subscribe options a few lines down .....................

---

### Post by rickm1945 on 2014-05-12
I did the install and it doen't pint,error message says check printer configuration. The package went smoothly through install. I will call Brother later this morning and I will provde a post as to status. I thank you fro you help. I have subsribed to this thread.

---

### Post by gifford on 2014-05-12
Sometimes the installation script does not work right. Brother has instructions on their site to do the install by command line. 
I have always used the instructions found there and have never had a problem.

---

### Post by rickm1945 on 2014-05-12
I called Brother, and they said they didn't do phone support for Linux. So, I'm back to square one. The printer is set as default and it says it is connected to host. I try to print and nothing happens. I keep at it.

---

### Post by gifford on 2014-05-12
Do the command line installation. Just follow the instructions on the Brother site. It works.

---

### Post by pdc on 2014-05-12
so this printer is connected by usb cable to a standalone computer?

and it is the only printer connected to the computer?

What does > [COLOR="#FF0000"]/usr/sbin/lpinfo -v[/COLOR] give if you copy and paste it into a terminal; and can you paste back what you get please............best to use the top line of the terminal for copy and paste; ie Menu along to Edit and down to paste ...

_____________________________________________________________________________________________________________________

I wonder what CUPS show: CUPS=common unix printing system

[http://localhost:631/printers/](http://localhost:631/printers/)           ........if you click on that; or paste it into a spare browser window; it opens your local printer admin page: I show a screenshot when I click on one of our printers: 

you can see my screenshot lists **Driver** and **Connection**: can you tell us what you get please?

if you also paste this > [COLOR="#FF0000"]dpkg -l | grep Brother[/COLOR] and paste back what you get: it asks your package install system dpkg (dpkg=debian package) to list what it has named Brother

_________________________________________________________________--

and a final bit of sleuthing; if you type or paste > [COLOR="#FF0000"]system-config-printer[/COLOR] into a terminal; it opens the printer dialogue box: if you go the menu items on the top line; go to HELP and down to troubleshoot: follow that........does anything helpful emerge there?

---

### Post by rickm1945 on 2014-05-13
I looked in printers folder and decided to try to the add printer. I added the printer and the cups selection came up and I choose that and the printer installed and it worked. So this thread has been solved.

---

### Post by davidtrounce on 2014-08-14
Thanks PDc, Gotta love Brothers work. Too easy. The only issue was where it asked for the URI. What it wants here is your Printers IP address which you will find under menu/network/TCPIP.

---

