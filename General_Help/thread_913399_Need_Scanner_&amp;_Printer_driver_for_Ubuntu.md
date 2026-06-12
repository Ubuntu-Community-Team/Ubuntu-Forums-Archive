---
title: "Need Scanner &amp; Printer driver for Ubuntu"
date: 2008-09-07
forum: General Help
---

### Post by kokkus on 2008-09-07
Hi everyone.
I am new here, and I changed from Windows to Ubuntu yesterday.
I think it's perfect, and MUCH better then windows what so ever.
Btw, I need to install my printer/scannner but I can't find any linux driver for it so I hoped that you guys could help me.

It's an EPSON Stylus DX600
(Scann, print and copy in 1)

And I have the windows installation CD for it if that helps.

I would be more then happy if you could help me solve this problem.

Thanks in advance :)

---

### Post by lintoon on 2008-09-07
For your scanner install Xsane and give that a try.  I have an epson all in one (an older rx425) and it worked first time.

I don't know about your printer because I checked and could not find it in my list.   Having said that it should work.  It may work with another epson driver.  Drivers are also available from a link on the Epson site.

[http://www.business-solutions.epson.co.uk/Compatible.htm](http://www.business-solutions.epson.co.uk/Compatible.htm)

Hopefully someone here can clarify things for you better than me.

---

### Post by plucky on 2008-09-07
> It's an EPSON Stylus DX600
(Scann, print and copy in 1)


Do you mean epson stylus DX6000? 

There is no DX600 on the [open printing website]( http://openprinting.org/printer_list.cgi)

Have you tried adding the printer in **System > Administration > Printing**?

Good Luck

---

### Post by lintoon on 2008-09-07
If it's the DX6000, I've read that the DX4800 driver works.

---

### Post by kokkus on 2008-09-07
Yup that's right. DX6000 that is.
Thanks alot you guys :)

---

### Post by kokkus on 2008-09-07
Ok I found it on "printers" but xsane won't recognize it.
It says that it can't find device, and I don't know any other scanning programs. Do you?

---

### Post by plucky on 2008-09-07
> It says that it can't find device, and I don't know any other scanning programs. Do you? 

You need to edit some files to get xsane to recognize your scanner.

See the openprinting website page [here](http://www.openprinting.org/show_printer.cgi?recnum=Epson-Stylus_DX6000)


Good Luck

---

### Post by lintoon on 2008-09-07
If no-one comes up with an easier answer check this out and change any  values to match yours.

[http://www.linuxmint.com/forum/viewtopic.php?highlight=dx6000+epson&t=5453](http://www.linuxmint.com/forum/viewtopic.php?highlight=dx6000+epson&t=5453)

---

### Post by kokkus on 2008-09-07
Thank you guys.

---

### Post by kokkus on 2008-09-07
Here's what I did so far.
Created 45-libsane.rules: sudo gedit /etc/udev/rules.d/45-libsane.rules
Pasted:  SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="082e", MODE="664", GROUP="scanner"
Opened /etc/sane.d/epson.conf
At the end of the page, I pasted: usb 0x4b8 0x082e

I've done everything in the guide. and it still won't work.

Any solution?

---

### Post by kokkus on 2008-09-07
Here's the error I get when I open xsane now:
Error durring CMS conversation.
Couldn't open ICM profile.

Please help me here. Thanks.

---

### Post by kokkus on 2008-09-08
Bump.
I do not like to bump but plz help me with this.

---

### Post by kokkus on 2008-09-08
Ok I think i've done it now, but not sure about the epson conf file if someone could take a look and correct it plz:)

# epson.conf
#
# here are some examples for how to configure the EPSON backend
#
# SCSI scanner:
scsi EPSON
# for the GT-6500:
scsi "EPSON SC"
#
# Parallel port scanner:
#pio 0x278
#pio 0x378
#pio 0x3BC
#
# USB scanner:
# There are two different methods of configuring a USB scanner: libusb and the kernel module
# For any system with libusb support (which is pretty much any recent Linux distribution) the
# following line is sufficient. This however assumes that the connected scanner (or to be more
# accurate, it's device ID) is known to the backend. 
usb
# For libusb support for unknown scanners use the following command
# usb <product ID> <device ID>
# e.g.:
# usb 0x4b8 0x110
# And for the scanner module, use the following configuration:
#usb /dev/usbscanner0
#usb /dev/usb/scanner0
usb 0x4b8 0x082e
usb 0x? 0x?

---

### Post by Sef on 2008-09-08
> Bump.

Please don't bump your thread unless 24 hours has gone by.  Thank you.

---

### Post by plucky on 2008-09-08
Remove this line ```
usb 0x? 0x?
```from epson.conf and reboot.

Please post terminal output of ```
lsusb
scanimage -L
```

---

### Post by kokkus on 2008-09-08
Thank you:) The output is:

Bus 007 Device 004: ID 04b4:6830 Cypress Semiconductor Corp. USB-2.0 IDE Adapter
Bus 007 Device 002: ID 04b8:082e Seiko Epson Corp. 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 0aec:3260 Neodio Technologies Corp. 7-in-1 Card Reader
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 046d:c312 Logitech, Inc. 
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 004: ID 046d:c024 Logitech, Inc. 
Bus 002 Device 001: ID 0000:0000  
chris@chris-desktop:~$ scanimage -L
device `epson:libusb:007:002' is a Epson CX6000 flatbed scanner
device `epkowa:libusb:007:002' is a Epson Stylus CX5900/CX6000/DX6000 flatbed scanner

---

### Post by plucky on 2008-09-08
> chris@chris-desktop:~$ scanimage -L
device `epson:libusb:007:002' is a Epson CX6000 flatbed scanner
device `epkowa:libusb:007:002' is a Epson Stylus CX5900/CX6000/DX6000 flatbed scanner 


Well your scanner is there,what happens when you start Xsane?

If that doesn't work,open a terminal and try to start xsane with super user mode ```
gksudo xsane
```.

If that works,see this [thread](http://ubuntuforums.org/showthread.php?t=599673&highlight=epson+scanner+dx6000) for how to get it to work from the menus.

Good Luck

---

### Post by kokkus on 2008-09-08
You know that running Xsane from root is dangerous, and I don't think I will get any support if something happends then.

EDIT: I started xsane in normal mode and got the same error as before.
The error goes something like this:

Error durring CMS conversation. Couldn't open scanner ICM profile.

---

### Post by plucky on 2008-09-08
> You know that running Xsane from root is dangerous, and I don't think I will get any support if something happends then.



Why? All you are doing is seeing if Xsane has a permissions issue,and if it does,using super user mode will show it if it works.I am not saying you should use super user mode all the time.

Did You read the link in my last post?

---

### Post by kokkus on 2008-09-08
Wow the error didnt come up when I ren it in root. Why. how and how can I get it to work in normal mode ?
I guess the thread link you sent me can help but that is a long guide with much to read and I am not sure what I am looking for there to fix this.

EDIT: I followed the guide but it doesn't seem to work.

In that guide he says: If it works in root, there's a promission issue. Do the following 
sudo chmod a+w /dev/bus/usb/005/003

I tried that but there no such file or directory is the message I got then.

Besice, that guide was for version DX6050. I have a DX6000. 
I don't know but maybe that's the reason?.

---

### Post by plucky on 2008-09-08
> In that guide he says: If it works in root, there's a promission issue. Do the following
sudo chmod a+w /dev/bus/usb/005/003

I tried that but there no such file or directory is the message I got then.

Besice, that guide was for version DX6050. I have a DX6000.
I don't know but maybe that's the reason?. 


You have to do it for the specific location of your scanner.

```
sudo chmod a+w /dev/bus/usb/007/002
``` Then reboot and it should work.

Also can you check that your user is able to use the scanner. **System > Administration > Users and Groups > Unlock > Select User > Properties > User Privileges** and see if you are allowed to use scanner.


Good Luck

---

### Post by kokkus on 2008-09-08
Thanks but nothing happenn when I insert that into terminal. and when I reboot it won't work.

---

### Post by kokkus on 2008-09-08
I tried again in root mode and got the same error about the cms thing when I tried to do something. Like e.g Enable color management.

---

### Post by plucky on 2008-09-09
> **kokkus said:**
> I tried again in root mode and got the same error about the cms thing when I tried to do something. Like e.g Enable color management.

Try to remove the .sane hidden folder in your /home partition to let xsane create a new one.

Do you have the right to access the scanner? Open a terminal and input ```
id
``` and you should see "105(scanner)".

I am very fast running out of ideas here as every indication says to me that it should be working.Perhaps retrace your steps and make sure the changes you made are actually correct.

Good Luck

---

### Post by kokkus on 2008-09-09
Nope I can't find anything with 105. How can I add it? btw, heres the list I got:

uid=1000(chris) gid=1000(chris) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),107(fuse),109(lpadmin),115(admin),1000(chris)

---

### Post by plucky on 2008-09-09
**System > Administration > Users and Groups > Unlock > Select User > Properties > User Privileges** and tick "Use scanner" box.

Logout and log back in and you should then have the user privilege.

Also delete the .sane folder in your home directory.

Run "xsane epson" from a terminal window and see what messages you get.

---

### Post by kokkus on 2008-09-09
OK I did what u say but it still won't work. The scanner has been added to the id list now btw.

uid=1000(chris) gid=1000(chris) groups=4(adm),20(dialout),24(cdrom),25(floppy),26(tape),29(audio),30(dip),44(video),46(plugdev),105(scanner),107(fuse),109(lpadmin),115(admin),1000(chris)

---

### Post by plucky on 2008-09-09
Can you post output of ```
cat /etc/sane.d/dll.conf
```

as I think you have two drivers installed for the same scanner as the optput of "scanimage -L is ```
device `epson:libusb:007:002' is a Epson CX6000 flatbed scanner
device `epkowa:libusb:007:002' is a Epson Stylus CX5900/CX6000/DX6000 flatbed scanner
```

Have you installed libsane-extras?

---

### Post by kokkus on 2008-09-09
Here's the output. and I don't know what I have installed. JUst followed guides to get it to work. 

chris@chris-desktop:~$ cat /etc/sane.d/dll.conf
# /etc/sane.d/dll.conf - Configuration file for the SANE dynamic backend loader
#
# On Debian systems, the dll backend will also look for pieces of configuration
# in the /etc/sane.d/dll.d directory -- packages providing backends should drop
# a config file similar to dll.conf in this directory.
#

# enable the next line if you want to allow access through the network:
net
abaton
agfafocus
apple
avision
artec
artec_eplus48u
as6e
bh
canon
canon630u
#canon_pp
cardscan
coolscan
coolscan2
#dc25
#dc210
#dc240
dell1600n_net
dmc
epjitsu
epson

#epson2
fujitsu
#gphoto2
genesys
gt68xx
hp
hp3900
hpsj5s
hp3500
hp4200
hp5400
hp5590
hpljm1005
hs2p
ibm
leo
lexmark
ma1509
matsushita
microtek
microtek2
mustek
#mustek_pp
mustek_usb
mustek_usb2
nec
niash
pie
pixma
plustek
#plustek_pp
#pnm
qcam
ricoh
s9036
sceptre
sharp
sm3600
sm3840
snapscan
sp15c
#st400
#stv680
tamarack
teco1
teco2
teco3
#test
u12
umax
#umax_pp
umax1220u
v4l




EDIT: I searched for libsane-extras, and found 4 scores.

libsane
libsane-extras
libsane-extras-dbg
libsane-extras-dev

---

### Post by plucky on 2008-09-09
Try this ```
gksudo gedit /etc/sane.d/dll.conf
```


Put a # in front epson and remove the space between epson and epson2 as ```
#epson
#epson2
```

And then I think you might have to reboot.

After you reboot do a ```
scanimage -L
``` from a terminal and see how many scanners it finds.


Also open synaptic package manager and search for libsane-extras and see if it is installed.I think that is what installs the epkowa driver shown by the "scanimage -L" command.

---

### Post by kokkus on 2008-09-09
here's the output from terminal now:

device `epson:libusb:002:002' is a Epson CX6000 flatbed scanner
device `epkowa:libusb:002:002' is a Epson Stylus CX5900/CX6000/DX6000 flatbed scanner

seems like it won't turn off the wrong driver for some reason.

EDIT: I uninstalled the extra package with epkowa as u told me to but now both the scanners are gone (checked scanimage -L), and it still won't work in xsane.

As i said in my last post I have all the 3 extras packages. should I just remove them all then?

---

### Post by plucky on 2008-09-09
> As i said in my last post I have all the 3 extras packages. should I just remove them all then? 


I don't think you need those packages,so remove them and go back into the ```
/etc/sane.d/dll.conf
``` and remove the # from the epson2 line and reboot.I think the epson2 file is the one the sane website says is the one that has the driver for your scanner.

If that doesn't work,comment out the epson2 and un-comment the epson line and try to access the scanner again.


I am wondering if it might be worth you re-installing the whole system to start from a clean install,and then follow this [thread to install the dx6000](http://ubuntuforums.org/showthread.php?t=599673&highlight=epson+dx6000) as that seems to work.

---

### Post by kokkus on 2008-09-09
Thanks but it won't work. Scanimage won't find any of them 2 epson drivers now. and as u can see here I still have the same problem.

[IMG]http://scumbox.com/1.png[/IMG]

BUt I got an idea. What if I post the output of the files I have to edit and you fix them? I think I maybe could have done something wrong in 1 of the files.
Besice, I have only made changes to 3 files in this epson case, so what could possibly go wrong?

---

### Post by kokkus on 2008-09-10
Ok I guess Epson is never ment for Ubuntu since I have to go thru all these problem fixing stuff.
Is there any scanner/printer that will work for Ubuntu from the very first time u plug it in and where u don't have to fix things?

---

### Post by kokkus on 2008-09-11
Bump.
Since I havn't solve this problem yet, reinstalled ubuntu to do it al from start again. And it still won't work.
Is there any scanner/printers out there I can just plug in to my PC and it will be auto-detected by ubuntu and work with no problem?

Or back to the epson dx6000, maybe I've followed the wrong guide.
Just in case, gimme the right guide link plz.

Thank you, and sorry for bumping but I am desperate.

---

