---
title: "Epson BX320 FW Scanner"
date: 2014-08-18
forum: Hardware
---

### Post by theo5 on 2014-08-18
Hello.

I have a problem with my office machine. I can print any document I want (although it says that ink level is not available), but ubuntu can't recognize its scanner.
By using Simple Scan I get a "No Scanners Detected" message.

I am using Ubuntu 14.04 LTS in Xfce Desktop Enviroment and I connect the BX via usb2.

Any ideas?

---

### Post by pdc on 2014-08-19
I wondered if you had the Epson drivers for ubuntu installed?

If one goes here [http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=28880&DSCCHK=ec6ec9b0ae7d86aeadf2c0b88252dbe4149a9831](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=28880&DSCCHK=ec6ec9b0ae7d86aeadf2c0b88252dbe4149a9831)

Epson would say: install the DATA package first ................. **[COLOR="#008000"]iscan-data_1.29.0-2_all.deb[/COLOR]**

then the ltd7 debian package for 32bit or 64bit as appropriate;

Epson also have a network plugin package [http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=24993&DSCCHK=fd5cb71b1b7dcca4b2eba38afa9631e914a5e10f](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=24993&DSCCHK=fd5cb71b1b7dcca4b2eba38afa9631e914a5e10f)

The iscan programme should appear in your menu; and with luck it will work and you can scan from that;

---

### Post by theo5 on 2014-08-19
Thank you very much! It works perfect - even the autofeeder.
When I installed the very first driver I thought it would be for both printing and scanning. Obviously I was wrong.

Btw, is there anything I can do for the Ink Level indicator? I go to Settings Manager -> Printers -> Epson BX -> right click -> Properties -> Ink Toner Levels, but "Marker levels are not reported for this printer".
I just installed the latest driver from here ```
http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=29017&DSCCHK=a4c2c08eb49b65cf152f57c3451257670c4b2d48
```

Thank you for your time.

---

### Post by pdc on 2014-08-19
glad it is working;

for ink levels, anything here that is of help to you? [http://forums.linuxmint.com/viewtopic.php?f=51&t=27806](http://forums.linuxmint.com/viewtopic.php?f=51&t=27806)

...........oh..................as initiator of this thread, you can go to thread tools on the top line; and add **SOLVED**

---

### Post by ski_phreak on 2014-08-20
One more bit for people struggling with scanners and AIO (all-in-one) or MFP (multi-function-printers.)
I'm running kubuntu 14.04 LTS and just barely bought an Epson WF-7620 (had to have the ADF and the 11"x17" scan sizes.)

**First, I set up the stuff that ubuntu repositories **could give me like so:[INDENT][FONT=arial narrow]sudo sudo apt-get install xsane gimp-help-en gimp-data-extras gocr geeqie sane-utils libsane-extras skanlite escputil libinklevel5 mtink gutenprint-locales mtink-doc[/FONT]
[/INDENT]


**Then, I added a repository for epson **printers to /etc/apt/sources.list.  Sadly, this only gave me a lot of older printers to choose from. WF-7510 was the closest and it didn't work at all....but it gave me nice ink level graphics!  Nothing else.  If you've got an older Epson you may want to try, though.[INDENT][FONT=arial narrow]sudo kate /etc/apt/sources.list[/FONT]
[/INDENT]
(switch kate for your favourite editor.)[FONT=arial narrow]
[/FONT]add this line.[INDENT][FONT=arial narrow]deb [http://download.ebz.epson.net/dsc/op/stable/debian/](http://download.ebz.epson.net/dsc/op/stable/debian/) lsb3.2 main
[/FONT][/INDENT]
Then
[INDENT][FONT=arial narrow]sudo apt-get update
apt-cache search epson (or 7510, or Stylus or whatever you're searching for.)
sudo apt-get install <whatever-your-printer-driver>
[/FONT][/INDENT]

When that didn't work (for me at least,) I put sources.list back, uninstalled the driver for WF-7510, and tried the following

I downloaded and installed the** files already mentioned from epson/seiko.**  In my case it was:[INDENT][FONT=arial narrow]dpkg -i epson-inkjet-printer-escpr_1.4.1-1lsb3.2_amd64.deb iscan_2.29.3-1~usb0.1.ltdl7_amd64.deb epson-pc-fax_1.0.0-1lsb3.2_amd64.deb iscan-data_1.29.0-2_all.deb[/FONT]
[/INDENT]

(replace your own architecture needs in the above, if you're following along...)

The **results were weird,** and unlike anything I've seen documented.
Printing, as mentioned, worked fine.
[LIST]
[*][FONT=arial narrow]> xsane iscan [/FONT]failed, saying "Failed to open device 'iscan'. Invalid argument." 
[*][FONT=arial narrow]> xsane epkowa[/FONT] failed with the same message. 
[*][FONT=arial narrow]> xsane epson [/FONT]worked, but it was low-quality, fax-like, not what I need. 
[*][FONT=arial narrow]> iscan launched the Epson/Seiko program, which worked[/FONT]. (I'm used to xsane; I like it's features best.) 
[/LIST]

I** KNOW** this ADF scanner worked fine under a previous installation of Kubuntu 14.04.  

Both **Xsane and GIMP pointed me in the right direction**, because they had two instances of my scanner to choose from.  
[LIST]
[*]Epson PID 08B9 flatbed scanner [epson2:net:192.168.1.127] 
[*]Epson WF-7610/7620 Ser flatbed scanner [epkowa:usb:001:006] 
[/LIST]

Yes, I've attached both the CAT network cable and the usb cable to this scanner.

**The solution to my (admittedly weird) problem** is simply to choose the one that includes the network address, rather than the epkowa:usb one.  Unreal.  Never would've guess this outcome.

I hope this helps someone who may be out there searching.  Heaven knows I couldn't find anything remotely like it posted when I looked these last 2 days.

---

### Post by theo5 on 2014-08-20
Marked as Solved.

I installed from synaptic Ink (tool for checking the ink level of your local printer) but had no luck.

```

theo@Utopia:~/Desktop/libinklevel-0.8.0$ ink -p usb
Could not access '/dev/usb/lp0' or '/dev/usblp0'.
Could not get ink level.
theo@Utopia:~/Desktop/libinklevel-0.8.0$ sudo ink -p usb
[sudo] password for theo: 
Unknown IEEE 1284.4 error number 80
An unknown error occured.
Could not get ink level.
theo@Utopia:~/Desktop/libinklevel-0.8.0$ sudo ink -p usb
No ink level found.
Could not get ink level.

```

Also tried Mtink, but when I run the program I get the following message:

No access to printer device file.
Please make sure that mtink has enough
right for accessing the device file.
On Debian Based Systems as Ubuntu you must 
be a member of the group lp. [???]

---

### Post by ski_phreak on 2014-08-21
I just tested mtink on my own printer.  After the power-save woke up, it reported fine about  my WF-7620.

Based on your message about "lp group," the system administrator (probably you) needs to add you (your username) to the group "lp."

Specificially, do this:

Open a terminal from your menus.  Then type
```
groups
```

What follows is the list of groups that your version of ubuntu automatically set you up with when you (or your admin) installed the system and/or created your account.

Mine shows the following (note that I am an admin of my system, so you may or may not have some of these.)
```

groups
scotsman adm lp cdrom sudo dip plugdev lpadmin sambashare

```

If you don't see "lp" in the list, add that group and then add  yourself to that group as follows:
```

sudo addgroup lp
sudo adduser <yourUsername> lp

```

If that's the only thing keeping mtink from working, you should be set.

---

### Post by ski_phreak on 2014-08-21
p.s.  I have no idea about synaptic and ink.  mtink was what came from Epson/Seiko.

---

### Post by theo5 on 2014-08-21
well... that's weird

```

theo@Utopia:~/Desktop$ groups
theo adm cdrom sudo dip plugdev lpadmin sambashare

```

so no lp group.

```

theo@Utopia:~/Desktop$ sudo addgroup lp
addgroup: The group `lp' already exists.
theo@Utopia:~/Desktop$ sudo adduser theo lp
The user `theo' is already a member of `lp'.

```

so there is a lp group... hidden.

I also found this 
[http://ubuntuforums.org/showthread.php?t=1871321](http://ubuntuforums.org/showthread.php?t=1871321)

```

theo@Utopia:~/Desktop$ sudo modprobe usblp
theo@Utopia:~/Desktop$ lsusb
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 013 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 012 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 011 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 010 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0409:005a NEC Corp. HighSpeed Hub
Bus 001 Device 003: ID 0409:005a NEC Corp. HighSpeed Hub
[COLOR=#ff0000]**Bus 001 Device 005: ID 04b8:085f Seiko Epson Corp. Stylus Office BX320FW/TX525FW Series**[/COLOR]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

run mtink

First window I see has a "Epson Stylus Office BX320FW" title and says "Port Choice:"
Only available port is "/dev/usb/lp0", so I select this and press next, which results the following error

"Problems with the printer communication,
please check the printer for errors:
Out of Paper, No Ink, Printer not Powered

Note that some printers block for a few seconds after
powering on."

Behind the error window is the mtink window, which has the same title as before, and no ink indication.

I installed mtink from synaptic manager, uninstalled it and reinstalled it from here : [https://apps.ubuntu.com/cat/applications/precise/mtink/](https://apps.ubuntu.com/cat/applications/precise/mtink/)

---

