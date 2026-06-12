---
title: "SANE can't see my Epson XP -205 scanner"
date: 2014-07-05
forum: Hardware
---

### Post by mattinker on 2014-07-05
SANE can't see my Epson XP -205 scanner. I can find messages that tell me how to solve this problem, but I'm too much of a newbie to make it work. I'm afraid I'm generating files in duplicate and messing things up!! I can cut and paste into the terminal, but then I get different answers to those that I should! I need to find the IP adress for my scanner, but I don't know how!I tried all the skanlite, sane-pygtk, Scanner utility, simplescan and xsane Image scanning program. I am using Ubuntu Studio 14.04 . If somebody could help me get my scanner running I would be very grateful!
Regards, Matthew

---

### Post by jp734 on 2014-07-05
read the **epson.conf** and **epson2.conf** files under** /etc/sane.d**. Might help you out.

---

### Post by mattinker on 2014-07-05
Thanks for your reply, but where are these files? I find that nobody seems to imagine that a newbie knows nothing at all, maybe enough to get himself into trouble, but that is it!

---

### Post by pdc on 2014-07-05
wireless to the scanner side of these devices just seems a little tricky; 

with a usb cable, it all seems fine;

Epson provide their own programme that you can use if you wish; instead of the sane family; to start iscan (Epson's programme) it should be called ImageScan for Linux and can also be started from the terminal with > iscan

_____________

you have installed the iscan files have you? 

If you start here [http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX](http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX) and type in xp-205 it takes you to here [http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=28880&DSCCHK=ec6ec9b0ae7d86aeadf2c0b88252dbe4149a9831](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=28880&DSCCHK=ec6ec9b0ae7d86aeadf2c0b88252dbe4149a9831)

and Epson say:

1) DATA package first so for ubuntu; that uses debian packages; you need iscan-data_1.29.0-2_all.deb

2) then iscan_2.29.3-1~usb0.1.ltdl7_i386.deb or iscan_2.29.3-1~usb0.1.ltdl7_amd64.deb depending on whether you have 32bit or 64bit

3) go here [http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=24993&DSCCHK=fd5cb71b1b7dcca4b2eba38afa9631e914a5e10f](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=24993&DSCCHK=fd5cb71b1b7dcca4b2eba38afa9631e914a5e10f) for network-plugin package 

___________

to read the files that jp734 points you to: paste 

> [COLOR="#FF0000"]gedit /etc/sane.d/epson.conf[/COLOR] into a terminal and it should use the text editor gedit to open the epson.conf file that is inside the directory sane.d that is inside the /etc directory

__________

did you install the epson printer driver package?

________

If you google on > support.epson.ru/upload/library_file/11/scanner_linux.pdf or > How to install Epson scanner on linux you should find the pdf and it goes through how set up iscan; I suspect folks may win where they assign a static IP to their device; and they have a stationary target to aim at each time

---

### Post by mattinker on 2014-07-05
Thanks, I opened epson.conf, but I don't understand how to configure usb /dev/usbscanner0 or usb /dev/usb/scanner0

[http://download.ebz.epson.net/dsc/du...52dbe4149a9831](http://download.ebz.epson.net/dsc/du...52dbe4149a9831) I downloaded as instructed, Status : Error: Dependency is not satisfiable: iscan-data

Where now?

---

### Post by jp734 on 2014-07-05
Open terminal. With your scanner plugged in and turned on, type 'lsusb'. This will display what usb devices you have plugged in on your pc. It will also show you the Bus, Device and ID numbers. I believe these are the numbers you need to enter on your config file. Just do some research online how to enter them as I'm not quite sure how to enter it myself.

Another thing you could try if above method doesn't work. This worked for me but I don't have an Epson scanner (just keep that in mind)
--------------------------
Download a firmware for your scanner from epson website. Edit the [COLOR=#0000ff]snapscan.conf[/COLOR] file
 - [COLOR=#0000ff]sudo gedit /etc/sane.d/snapscan.conf[/COLOR]
sudo command will ask for an admin password as you need privilege to edit the file.

Find a line similar to this: '[COLOR=#0000ff]firmware /home/rudy/Documents/620u/u96v121.bin[/COLOR]' (this is the path to my scanner's firmware to get it to work so it would be different from what you will see). This line should be at the very top of the page. Simply edit the path and direct it to the folder where you saved your downloaded firmware. After that, save the file and test your scanner.

Good luck.

---

### Post by mattinker on 2014-07-05
thanks jp734,
sudo lsusb opened the Device list, Bus 002 Device 008: ID 04b8:0896 Seiko Epson Corp, the ID 04b8:0896 corresponds with what I found on  epson.conf. I still haven't found out how to enter it on the config file. I feel like I'm maybe getting somwhere!

Regards, Matthew

---

### Post by mattinker on 2014-07-05
OK, I did a $ sudo sane-find-scanner results, could not fetch string descriptor: Pipe error, no scanner!

---

### Post by pdc on 2014-07-05
so you started off by saying wireless; but do I take it now you have a usb cable?

The iscan files; if installed; should do all the configuration for you:

Epson say: most important: install the data file first; I am not clear: did you install the data package first?

___________

so I think one needs:
1) data package
2) iscan package
3)network plugin

____________________________

Epson uses their own "backend" called epkowa; and when iscan is installed, it creates a file called epkowa.conf and configures various things

I understand the iscan configuration should enter the id of your device in that file: 

so if you read the file with > gedit /etc/sane.d/epkowa.conf      and you want to use usb I wonder if there is an entry > [COLOR="#0000FF"]usb 0x04b8 0x0896[/COLOR]

.........it it isn't you can edit the file by closing it and then > gksudo gedit /etc/sane.d/epkowa.conf and the sudo allows you to save changes

__________________

for the network the file epkowa.conf says as a help

> # Network attached devices may be made to work by first installing the
# (non-free) iscan-network-nt package and then adding configuration lines
# as per information below.
#
# For each network attached device, you must add an entry as follows:
#
#   net <IP-address|hostname> [port-number]
#
# Ask your network administrator for the device's IP address or check
# for yourself on the panel (if it has one).  The port-number is very
# optional and defaults to 1865.
# Note that network attached devices are not queried unless configured
# in this file.
#
# Examples:
#
net 192.168.1.102:515
#net 10.0.0.1
#net scanner.mydomain.com


---

### Post by mattinker on 2014-07-05
pdc,

at no time did I mention Wifi, I'm all hard wired, I avoid Wifi!

I tried what you said, I don't know what to make of the results apart from the scanner still doesn't work! Thank you for your thoughts, I hope this makes sense to someone! Regards, Matthew.

~$ sudo gedit /etc/sane.d/dll.conf

(gedit:2848): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

(gedit:2848): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
mattinker@Bureau:~$ ^C
mattinker@Bureau:~$ ^C
mattinker@Bureau:~$ ^C
mattinker@Bureau:~$ gedit /etc/sane.d/epkowa.conf 

(gedit:3007): Gtk-WARNING **: Attempting to read the recently used resources file at `/home/mattinker/.local/share/recently-used.xbel', but the parser failed: Failed to open file '/home/mattinker/.local/share/recently-used.xbel': Permission denied.

(gedit:3007): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
sudo gedit /etc/sane.d/epkowa.conf 
gksudo gedit /etc/sane.d/epkowa.conf

---

### Post by pdc on 2014-07-05
> at no time did I mention Wifi, I'm all hard wired,

that's great: I think I interpreted > I need to find the IP adress for my scanner,  as you being wireless;

........so it's usb: excellent

________________

I am not clear about the error messages you get:

if one first sees if one can read the files with > [COLOR="#FF0000"]gedit /etc/sane.d/epkowa.con[/COLOR]f 

_________________

can you open the file using the command above please?

---

### Post by jp734 on 2014-07-05
Ok, I've been doing some readiing myself on how to do this. So, lsusb gives you [COLOR="#0000FF"]"Bus 002 Device 008: ID 04b8:0896 Seiko Epson Corp"[/COLOR].

entering this command in terminal [COLOR="#0000FF"]"lsusb -D /dev/bus/usb/002/008"[/COLOR] will show you more info about your device and I think, basing from the output of this command, you will enter [COLOR="#0000FF"]usb 0x04b8 0x0896[/COLOR] on epson.conf file. Make sure you remove the # character.

You should have the following by the time you're done.
# For libusb support for unknown scanners use the following command
# usb <product ID> <device ID>
# e.g.:
[COLOR="#0000FF"]usb 0x04b8 0x0896[/COLOR]

Also, I'm not sure what configuration file it will look for so I suggest you do the same thing with the epson2.conf file

---

### Post by mattinker on 2014-07-06
> **pdc said:**
> that's great: I think I interpreted  as you being wireless;

........so it's usb: excellent

My bas, I got mixed up with the Wifi instructions!

if one first sees if one can read the files with 

_________________

can you open the file using the command above please?
Yes I can open gedit /etc/sane.d/epkowa.conf, It has  usb 0x04b8 0x0896 that I typed in previously. 

Regards, Matthew

---

### Post by mattinker on 2014-07-06
> **jp734 said:**
> Ok, I've been doing some readiing myself on how to do this. So, lsusb gives you [COLOR="#0000FF"]"Bus 002 Device 008: ID 04b8:0896 Seiko Epson Corp"[/COLOR].

entering this command in terminal [COLOR="#0000FF"]"lsusb -D /dev/bus/usb/002/008"[/COLOR] will show you more info about your device and I think, basing from the output of this command, you will enter [COLOR="#0000FF"]usb 0x04b8 0x0896[/COLOR] on epson.conf file. Make sure you remove the # character.

You should have the following by the time you're done.
# For libusb support for unknown scanners use the following command
# usb <product ID> <device ID>
# e.g.:
[COLOR="#0000FF"]usb 0x04b8 0x0896[/COLOR]

Also, I'm not sure what configuration file it will look for so I suggest you do the same thing with the epson2.conf file

I tried "sudo lsusb -D /dev/bus/usb/002/008"
I got "Cannot open /dev/bus/usb/002/008"l

So I'm stuck! Regards, Matthew.

---

### Post by jp734 on 2014-07-06
Hmm, that's strange. I tried that command on two of my usb devices and it worked both times. Double check your Bus and Device numbers and make sure scanner is on. If that really doesn't work, I'd try the other method I mentioned last time, downloading the firmware.

---

### Post by mattinker on 2014-07-06
OK I tried it again to make sure, I still can't get it to work and I'm having no luck with the firmware either!

Regards, Matthew

---

### Post by jp734 on 2014-07-06
Well, I'm not sure at this point. I would start doing what @pdc is suggesting sine you can't find the firmware. you could go ahead and edit and save the epson.conf files since you have the id numbers you need and see if it works. I don't see why you can't try.

---

### Post by mattinker on 2014-07-07
I've been trying both your and @pdc's sugestions.

Thank you both for trying! Regards, Matthew.

---

