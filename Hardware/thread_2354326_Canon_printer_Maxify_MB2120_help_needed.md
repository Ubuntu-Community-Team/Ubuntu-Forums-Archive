---
title: "Canon printer Maxify MB2120 help needed"
date: 2017-03-01
forum: Hardware
---

### Post by rickrodriguez1971 on 2017-03-01
I have been looking all around this place and the internet
I desperately want to install my printer, the default recommendation it to use the "generic drivers" and "text" only
but even that will not work

any help would be appreciated

---

### Post by Autodave on 2017-03-01
Not sure where you were looking, but I seem to have found it at Canon's website:  [http://www.canonsdrivers.com/2016/08/canon-maxify-mb2120-driver-download.html](http://www.canonsdrivers.com/2016/08/canon-maxify-mb2120-driver-download.html)

You may want to start there and report back.

---

### Post by slickymaster on 2017-03-01
*Thread moved to **Hardware**.*

---

### Post by rickrodriguez1971 on 2017-03-01
I already have tried this 3 days ago, but that "download link" just leads to nothing useful
it only goes to other model of printers made by Canon
I tried emailing them, with no response

---

### Post by pdc on 2017-03-02
so I went to the USA Canon website; as the MB2120 seems to be sold there and I got to here [https://www.usa.canon.com/internet/portal/us/home/support/details/printers/small-office-home-office-printers/mb2120?tab=drivers#Z7_MQH8HIC0L88RB0AMD0F1Q42K25](https://www.usa.canon.com/internet/portal/us/home/support/details/printers/small-office-home-office-printers/mb2120?tab=drivers#Z7_MQH8HIC0L88RB0AMD0F1Q42K25)

so you need the debian package which is listed there as

"[COLOR="#008000"]IJ Printer Driver Ver. 5.40 for Linux (debian Packagearchive)[/COLOR]"

comes down as [COLOR="#0000FF"]cnijfilter2-5.40-1-deb.tar.gz[/COLOR] so click to download and select to **SAVE** and it should end up in your [COLOR="#0000FF"]Downloads[/COLOR] folder;

assuming that happens, the commands that you need to paste into a terminal are:

```
cd Downloads
```        (right-click in the terminal at the prompt spacing, and PASTE should appear as an option .....and hit the ENTER key after each paste ..........)
```
tar -zxvf cnijfilter2-5.40-1-deb.tar.gz
```
```
cd cnijfilter2-5.40-1-deb
```
```
sudo ./install.sh
```and this last command runs the automated INSTALL SCRIPT but maybe open your terminal up to full screen at this point: (+ sign at the top right of the terminal .......) and watch as the script may ask you questions and tell you to do things like turn the printer on etc ......

..... the above should work

---

### Post by rickrodriguez1971 on 2017-03-02
almost...
I answered all the questions
when it said enter a value I entered "1" (hope that was correct)
it said it installed correctly
It will do a self-test print (it didnt before), but nothing else
I tried test print
and a test LibreOffice page
neither work

---

### Post by rickrodriguez1971 on 2017-03-02
I have tried it again and didn't change anything, just answered yes to all questions (values were already there)
but nothing is different from earlier, it will only "self-test print"
not "test print"
nor print off LibreOffice

---

### Post by pdc on 2017-03-02
thanks Rick;

so is this a usb connection? 

If so, can you type ```
lsusb
``` in your terminal please; and copy and paste back what you get; and can you also type or copy ```
lpinfo -v
``` and copy the result and paste it back here please;

........... do you already have any other printers connected to your computer? I ask because linux would call the first printer ```
lp0
``` ...... ie lp zero ........ and a second printer (which would then be your MB2120would be thought of as ```
lp1
```

.... the Canon script would assume the MB2120 is the first usb printer; and would assign it to lp0 .............. and maybe another printer has that hot-spot already?

---

### Post by rickrodriguez1971 on 2017-03-04
```
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 006: ID 1c4f:0003 SiGma Micro HID controller
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 04a9:1793 Canon, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 046d:0a1f Logitech, Inc. G930
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 011 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 010 Device 004: ID 04d9:1605 Holtek Semiconductor, Inc. 
Bus 010 Device 003: ID 046d:c408 Logitech, Inc. Marble Mouse (4-button)
Bus 010 Device 002: ID 0409:005a NEC Corp. HighSpeed Hub
Bus 010 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

```

network ipps
network beh
network lpd
network http
network ipp
network ipp14
network socket
direct hp
serial serial:/dev/ttyS0?baud=115200
network https
direct cnijusb:/dev/usb/lp1
direct cnijusb:/dev/usb/lp2
direct hpfax
direct cnijbe2://Canon/?port=usb&serial=108928
direct cnijbe2://Canon/?port=usb&serial=108928

```


no I do not have any other printers connected to my computer

---

### Post by pdc on 2017-03-04
thanks;

so when I run the "lpinfo -v" on our system, I get .... amongst other things .... "[COLOR="#008000"]direct cnijusb:/dev/usb/lp0[/COLOR]"

whereas; interestingly; your printout says 

> [COLOR="#0000FF"]direct cnijusb:/dev/usb/lp1[/COLOR]
direct cnijusb:/dev/usb/lp2

so my suggestion would be that ...... for some reason ..... your system is allocating lp1 and lp2 to linux printers; ........ whereas mine starts at lp0 (lp zero)

so what about .... deleting any icons in the PRINTERS folder; re-running the install script; see if it mentions lp0 as the site of a printer: (as that will likely be what it assumes): see if you can edit that to tell it about lp1 ...... and we see how things go ........

______________________

when anyone runs an install script, behind the scenes what is happening is that the script installs the drivers; and then tell lp admin where to look and where to allocate things, so the format of the command is 

[COLOR="#0000FF"]sudo /usr/sbin/lpadmin -p [Printer Name] -P [PPD file path] -v usb:// [device &#65350;ile path] -E[/COLOR]

so it is telling lpadmin that if the print command says to use .. ***[Printer Name]*** ........ then use this PPD file ***[PPD file path]*** and send the message to this device to print it ***usb:// [device &#65350;ile path]***   ...and in your case, the default in the Canon script is probably is probably cnijusb:/dev/usb/lp0 and you would need cnijusb:/dev/usb/lp1 I think

---

### Post by rickrodriguez1971 on 2017-03-04
can I just change this?

---

### Post by pdc on 2017-03-04
"can I just change this? "

yes indeed you can ....... but when you say "*can I just change this*"     ....... what do you plan to change?

(I suggested running the install script again ....... as I thought it would be easiest to do .....................)

---

### Post by rickrodriguez1971 on 2017-03-05
i did run it again, about 5 more times, and I get the same result

but you suggested it might be that it says lp1 and lp2...not lp0

can I change it to lp0?

---

### Post by pdc on 2017-03-05
I was saying: it is likely the Canon script thinks your computer will call its printer port lp0 (ie lp zero); and so the Canon script will use lp0

however it seemed to me when you asked your computer what it called its printer port; it told us lp1 and lp2 and that was a surprise;

perhaps you just run ```
lpinfo -v
``` again please and we see what it is telling us today: 

so you just have a standard desktop; standalone; with the printer connected by usb cable; and it is all standalone .......

______________

**I see you have a high-speed hub listed;** *I wonder if you have plugged the printer into that?* 

If so, please plug the printer directly into a usb port on your computer; and then run the above command

---

### Post by rickrodriguez1971 on 2017-03-05
yes it is just a stand alone computer and printer

this is what I got 

```
network beh
network ipps
network lpd
network http
network socket
direct hp
network ipp14
serial serial:/dev/ttyS0?baud=115200
network ipp
network https
direct cnijusb:/dev/usb/lp1
direct cnijusb:/dev/usb/lp2
direct usb://Canon/MB2100%20series%20FAX?serial=108928&interface=2
direct hpfax



```

---

### Post by pdc on 2017-03-05
so looks like it wants lp2 to be the point for the printer; 

options that I see:

1) delete any existing entries in PRINTERS folder; re-run the install script; look to see if it says to you it wants to use lp0 and see if you can edit it to lp2 ....... seems to me easiest ... if it will work .......

2) delete existing entries; go to **ADD** in the PRINTERS folder (top-left corner); see if it will spot the MB2120 and offer to install it: we can only hope it picks up the Canon drivers; and finds the correct ppd ...........

3) have a look in the folder that is called model that sits inside /usr/share/cups/ and see if you can identify the exact name of the ppd file that would be for your MB2120 ....... my hunch would be it might be something like canonmb2100.ppd ......... if you get the name exact ..

then we can try a direct print registration from the terminal with the command ...... something like ........... 

                                    the format is /usr/sbin/lpadmin -p [Printer Name] -P [PPD file path] -v usb:// [device &#65350;ile path] -E

and we would do something like sudo /usr/sbin/lpadmin -p MB2120 -P /usr/share/cups/model/canon2100.ppd -v direct cnijusb:/dev/usb/lp2 -E

---

