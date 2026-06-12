---
title: "EPSON V100 Scanner not working on Ubuntu 14.04. Can't install drivers."
date: 2014-06-29
forum: Hardware
---

### Post by Paper Pusher on 2014-06-29
I have an Epson perfection V100.

The scanner used to work with Ubuntu 12.04-32bit LTS DTE.

I installed 14.04, and now the scanner will not work with the computer. I have downloaded the drivers from the Epson website. Isimple scan used to recongnize the Epson scanner, but now it doesn't.

I now don't know what to do!

---

### Post by pdc on 2014-06-30
you have this other thread? [http://ubuntuforums.org/showthread.php?t=2228342&highlight=epson](http://ubuntuforums.org/showthread.php?t=2228342&highlight=epson)

______________

When I look again at the Epson download site, I don't think you have the [COLOR="#EE82EE"]**plugin package**[/COLOR] installed: see the thumbnail; can I suggest you install that and see how you do after that?

you did have 32bit 12.04 and you don't say if you have 32bit 14.04 but if you do you will need the [COLOR="#008000"]iscan-plugin-gt-s600_2.1.2-1_i386.deb[/COLOR] available from here [http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=15835&DSCCHK=3028e98de6ebfd2725e648cc0613d4aa3425e1cd](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=15835&DSCCHK=3028e98de6ebfd2725e648cc0613d4aa3425e1cd)

---

### Post by Paper Pusher on 2014-06-30
Thank you for your help. I downloaded the package but after clicking on it, the software ceneter opens up but it doesn't start to install. Do you know what command I would use to install it through the terminal?

---

### Post by pdc on 2014-07-01
you seem sure it is not now installed; 

can you check that in software centre?

If you go back to Downloads folder; and right-click on package, are there options there to use to install it? (gdebi installer for example)

terminal commands would be 

cd Downloads

and then > ls ...........which will list the contents of the directory  

to install, commands are > sudo dpkg -i *whatever*.deb                where you substitute the correct name where I used *whatever*

---

### Post by Paper Pusher on 2014-07-05
I listed the downloads and this is what I got:

     axel@axel-O-E-M:~$ cd Downloads
     axel@axel-O-E-M:~/Downloads$ ls
     iscan_2.29.3-1~usb0.1.ltdl7_i386.deb  iscan-plugin-gt-s600_2.1.2-1_i386.deb
     iscan-data_1.28.0-2_all.deb

I then started by trying to install the iscan-plugin and this is what it game me:

axel@axel-O-E-M:~/Downloads$ sudo dpkg -i iscan-plugin-gt-s600_2.1.2-1_i386.deb
[sudo] password for axel: 
(Reading database ... 195303 files and directories currently installed.)
Preparing to unpack iscan-plugin-gt-s600_2.1.2-1_i386.deb ...
Unpacking iscan-plugin-gt-s600 (2.1.2-1) over (2.1.2-1) ...
dpkg: dependency problems prevent configuration of iscan-plugin-gt-s600:
 iscan-plugin-gt-s600 depends on iscan (>= 2.16.1); however:
  Package iscan is not configured yet.

dpkg: error processing package iscan-plugin-gt-s600 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 iscan-plugin-gt-s600
axel@axel-O-E-M:~/Downloads$ 

     When I tried the iscan-data I got this: 

axel@axel-O-E-M:~/Downloads$ sudo dpkg -i iscan-data_1.28.0-2_all.deb
(Reading database ... 195303 files and directories currently installed.)
Preparing to unpack iscan-data_1.28.0-2_all.deb ...
Unpacking iscan-data (1.28.0-2) over (1.28.0-2) ...
Setting up iscan-data (1.28.0-2) ...

    When I did iscan_2.29.3-1~usb I got this: 

axel@axel-O-E-M:~/Downloads$ sudo dpkg -i iscan_2.29.3-1~usb0.1.ltdl7_i386.deb 
(Reading database ... 195303 files and directories currently installed.)
Preparing to unpack iscan_2.29.3-1~usb0.1.ltdl7_i386.deb ...
Unpacking iscan (2.29.3-1~usb0.1.ltdl7) over (2.29.3-1~usb0.1.ltdl7) ...
dpkg: dependency problems prevent configuration of iscan:
 iscan depends on iscan-data.

dpkg: error processing package iscan (--install):
 dependency problems - leaving unconfigured
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.54ubuntu1) ...
Processing triggers for man-db (2.6.7.1-1) ...
Errors were encountered while processing:
 iscan

---

### Post by pdc on 2014-07-05
so Epson say you need 3 things:

1) DATA package
2) iscan package
3) plug-in

so we can see what is installed, 

what does > [COLOR="#FF0000"]dpkg -l | grep iscan[/COLOR] give please?

---

### Post by Paper Pusher on 2014-07-05
This is what I got

axel@axel-O-E-M:~/Downloads$ dpkg -l | grep iscan
rc  iscan                                                 2.29.3-1~usb0.1.ltdl7                               i386         simple, easy to use scanner utility for EPSON scanners
ii  iscan-data                                            1.28.0-2                                            all          Image Scan! for Linux data files
iU  iscan-plugin-gt-s600                                  2.1.2-1                                             i386         Image Scan! plugin for the Epson GT-S600 / Epson GT-F650 / Epson Perfection V10 / Epson Perfection V100 PHOTO
axel@axel-O-E-M:~/Downloads$

---

### Post by pdc on 2014-07-06
.........so you have the 3 needed packages installed it seems; 

what does 

> sane-find-scanner

and 

> scanimage -L

---

### Post by Paper Pusher on 2014-07-06
This is what I got 

       aregivers@axel-O-E-M:~$ sane-find-scanner 

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04b8 [EPSON], product=0x012d [EPSON Scanner]) at libusb:001:004
could not open USB device 0x0bda/0x0151 at 001:003: Access denied (insufficient permissions)
could not open USB device 0x04f9/0x0040 at 001:002: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0002 at 001:001: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0001 at 005:001: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0001 at 004:001: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0001 at 003:001: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0001 at 002:001: Access denied (insufficient permissions)
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.




caregivers@axel-O-E-M:~$ scanimage -L 


No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).


---The scanner is all plugged in, and when I try to scan something with simple scan, it said that it failed to scan and that no scanner is connected. This is new to 14.04

---

### Post by Paper Pusher on 2014-07-19
What does it mean when it says "Access denied (insufficient permissions)" ??

Any help would be appreciated.

---

### Post by pdc on 2014-07-19
> "Access denied (insufficient permissions)"


...........from your previous posting.................

> # You may want to run this program as root to find all devices. Once you
# found the scanner devices, be sure to adjust access permissions as
# necessary.

only root may have access to the machine: usually the install files create the necessary permissions to allow you as user to access the scanner; 

for their devices, [http://support.brother.com/g/s/id/linux/en/instruction_scn1c.html?c=us_ot&lang=en&redirect=on#u13.04](http://support.brother.com/g/s/id/linux/en/instruction_scn1c.html?c=us_ot&lang=en&redirect=on#u13.04)

Brother suggest editing /lib/udev/rules.d/40-libsane.rules and [COLOR="#800080"]Add the following two lines to the end of the device list. (Before the line "# The following rule will disable ..."):
If there is "LABEL="libsane_rules_end"", add the following 2 lines before "LABEL="libsane_rules_end"".[/COLOR]

we need to know the ID of your device: if you type > [COLOR="#FF0000"]lsusb[/COLOR] into a terminal; and it should give you the manufacturer's ID: 04b8 and then the device ID ......if you substititute those device ID values for [COLOR="#EE82EE"]@@@@[/COLOR] I have typed in the phrase below ..........

so can I suggest you issue the command > [COLOR="#FF0000"]gksudo gedit /lib/udev/rules.d/40-libsane.rules[/COLOR]     ...........you will be asked for your sudo password ....................

and then paste in; as two separate lines
> # Epson V100 
ATTRS{idVendor}=="04b8", ATTRS{idProduct}=="[COLOR="#EE82EE"]@@@@[/COLOR]", ENV{libsane_matched}="yes"                  .......*where @@@@ is changed for the device ID you see from the lusb command* ..............

save; close; reboot: any joy? you could re-run the sane-find-scanner commands and the scanimage -L commands ...........................

---

### Post by Paper Pusher on 2014-07-20
Thank you for the help, but it looks like I am stuck on the last step. This is what I got for everything:

axel@axel-O-E-M:~$ lsusb
Bus 001 Device 006: ID 04b8:012d Seiko Epson Corp. GT-F650 [GT-S600/Perfection V10/V100]
Bus 001 Device 010: ID 04f9:0040 Brother Industries, Ltd 
Bus 001 Device 008: ID 046d:082d Logitech, Inc. HD Pro Webcam C920
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
axel@axel-O-E-M:~$ gksudo gedit /lib/udev/rules.d/40-libsane.rules
The program 'gksudo' is currently not installed. You can install it by typing:
sudo apt-get install gksu
axel@axel-O-E-M:~$ sudo apt-get install gksu
[sudo] password for axel: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 gksu : Depends: libgksu2-0 (>= 2.0.8) but it is not going to be installed
 iscan-plugin-gt-s600:i386 : Depends: iscan:i386 (>= 2.16.1) but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
axel@axel-O-E-M:~$ # Epson V100
axel@axel-O-E-M:~$ ATTRS{idVendor}=="04b8", ATTRS{idProduct}=="012d", ENV{libsane_matched}="yes" 
ATTRS{idVendor}==04b8,: command not found

---

### Post by pdc on 2014-07-20
Hi Axel;

what I was suggesting in post #11 was that you edit the file that is called [COLOR="#EE82EE"]40-libsane.rules[/COLOR] and it is stored inside the directory [COLOR="#EE82EE"]rules.d[/COLOR] ......that is inside the directory called [COLOR="#EE82EE"]udev[/COLOR] ........that is inside the directory called [COLOR="#EE82EE"]lib[/COLOR] ............

so to edit files like that, you use the text editor called [COLOR="#0000FF"]gedit[/COLOR] (and I suspect its name comes from *g*nome and *edit*);

so if you just want to read a file the command is > gedit MY_FILE_WHATEVERITSNAMEIS ......but to CHANGE the file you need SUDO powers so the command is > gksudo gedit MY_FILE_WHATEVERITSNAMEIS

________________

so I was suggesting you try what Brother suggest; 

so to open the file; *and allow you to change it*; the command is > [COLOR="#FF0000"]gksudo gedit /lib/udev/rules.d/40-libsane.rules[/COLOR]

.......................that opens the file and then you need to paste 

>  # Epson V100
ATTRS{idVendor}=="04b8", ATTRS{idProduct}=="012d", ENV{libsane_matched}="yes" 


.............into the file.................that is opened in gedit..................at the place Brother suggest it .................................. and then SAVE and CLOSE ..................

____________

I see you getting warning messages about iscan but in a previous post it seems the 3 needed packages are installed

---

### Post by Paper Pusher on 2014-07-20
Hi pdc,

         I really appreciate your help! I edited the file by copying and pasting what you gave me. Afterwards I restarted the computer and I tried the scanner and it loaded forever so I restarted the iscan program and tried it again and it still says that there is no scanner connected. After this I re-opened the file with gedit and what I pasted was still in there.

---

