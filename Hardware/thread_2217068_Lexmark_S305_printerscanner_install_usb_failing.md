---
title: "Lexmark S305 printer/scanner install usb failing"
date: 2014-04-15
forum: Hardware
---

### Post by medusa569 on 2014-04-15
After changing pcs completely and upgrading from Lxde based on ubuntu 10.10 to Lxle based on ubuntu 12.04.   I cannot install my all in one printer. 
It is not recognized by the usb connection. I have downloaded the 64 bit drivers and the firmware ( which would not installed because of not finding the printer). Driver software was installed by gdebi so I know it's installed and I don't have to compile.  I am utterly stuck.  I don't know why the simple usb doesn't see the printer. is there a way to install with debug options to see what the problem may be. I'm getting no error messages.

---

### Post by pdc on 2014-04-15
> It is not recognized by the usb connection

so you are saying that the command > [COLOR="#FF0000"]lsusb[/COLOR] does not report a printer .........

what does > [COLOR="#FF0000"]/usr/sbin/lpinfo -v[/COLOR] give..............can you do the copy and paste back here please?

and what does > [COLOR="#FF0000"]dpkg -l | grep lexmark[/COLOR] give please?

---

### Post by medusa569 on 2014-04-15
PDC:  the output of the 3 queries are below....

medusa@ethers:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 005 Device 002: ID 1532:0007 Razer USA, Ltd DeathAdder Mouse
Bus 005 Device 003: ID 13ba:0018 Unknown 
 
medusa@ethers:~$ /usr/sbin/lpinfo -v
WARNING: gnome-keyring:: couldn't connect to: /tmp/keyring-4Iv73B/pkcs11: No such file or directory
network lpd
network http
network socket
network ipp14
direct hp
network ipps
network beh
network ipp
network https
network smb

medusa@ethers:~$ dpkg -l | grep lexmark
ii  lexmark-inkjet-legacy                     1.0-1                                               This package contains the lexmark-inkjet-legacy. 
ii  lexmark-printer-utility                   1.0-1                                               This package contains the lexmark-printer-utility. 
ii  lexmark-scan-legacy                       1.1-1                                               This package contains the lexmark-scan-legacy. 


Hope this tells you something.

---

### Post by pdc on 2014-04-15
well; when did it last work; your computer (to me) is not seeing the lexmark device; so many possible reasons: not turned on; broken; not connected; all usb ports are broken; .............I find it hard to believe that is just because of a newer version of lubuntu

an ID on an lsusb command for lexmark should show something like > Bus 003 Device 007: ID [COLOR="#EE82EE"]043d:007b[/COLOR] Lexmark International, Inc. InkJet Color Printer 

and if it were connected, one would hope to see > [COLOR="#EE82EE"]direct parallel:/dev/lp0[/COLOR] appear in the command > /usr/sbin/lpinfo -v

______________________________________

(and you have a set of lexmark drivers installed)

---

### Post by medusa569 on 2014-04-16
[QUOTE=pdc;12988935]well; when did it last work; your computer (to me) is not seeing the lexmark device; so many possible reasons: not turned on; broken; not connected; all usb ports are broken; .............I find it hard to believe that is just because of a newer version of lubuntu

as I mentioned this installation is new ( not an overwrite) on a new mobo(C7z87-oce)  and new version (12.04) of ubuntu). The usb ports are not broken as I have been using them daily. 


I know what I "should"  have in the lsusb query and I do have the drivers installed ( by gdebi) but as I said the usb connection recognition by the program is just not there.  I've checked the permissions of the usb ports thinking that might have been blocking it....but maybe somehow during the install process something wasn't allowed....is there a way to run these installers in a debug mode to see errors?

---

### Post by medusa569 on 2014-04-16
Update notice:  I finally got it recognized....I don't know how but it is seen now.  I thank pdc for attempting to help.

---

