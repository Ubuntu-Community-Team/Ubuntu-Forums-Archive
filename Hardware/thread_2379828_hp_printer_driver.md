---
title: "hp printer driver"
date: 2017-12-10
forum: Hardware
---

### Post by jimr1 on 2017-12-10
has anyone gotten an HP color laserjet pro mfp m180nw to work?  running 16.04 LTS.  I have the latest HP library installed.  when I try to install the printer, it suggests "generic postscript" which works fine for printing, but the scanner can't be found.  I've tried a couple of HP drivers for similar sounding MFPs but they either don't work at all, or I get the same thing, printer works but not the scanner.

the m180nw is a small cheap MFP for home use, maybe there's an HP that's similar?
               thanks.

---

### Post by DuckHook on 2017-12-10
Welcome to the forums, jimr1.

If the printer is a very recent model, then the version of hplip that you have in Xenial may not have the proper config files. You say, "I have the latest HP library installed", but did you do so from the [HPLIP website]("https://developers.hp.com/hp-linux-imaging-and-printing")?

---

### Post by jimr1 on 2017-12-10
> **DuckHook said:**
> Welcome to the forums, jimr1.

If the printer is a very recent model, then the version of hplip that you have in Xenial may not have the proper config files. You say, "I have the latest HP library installed", but did you do so from the [HPLIP website]("https://developers.hp.com/hp-linux-imaging-and-printing")?

HPLIP-3.17.11 version was installed on 07-12-2017. (that's from the HP setup screen)
I believe that's the latest.

---

### Post by DuckHook on 2017-12-10
[LIST=1]
[*]Is MFP connected through USB or network?
[*]What method did you use to install HPLIP? apt? synaptic? Something else?
[*]Did you use *sudo*?
[/LIST]
Please post back to this thread the output of:```
hp-check
``````
hp-scan -g
``````
ls -alF /var/lib/hp
``````
ls -alF /usr/share/hplip/scan/plugins
```
It's best to copy and paste from the terminal output so that nothing is lost. And please post your output between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar.

PS You may also wish to have a look at [this]("https://answers.launchpad.net/hplip/+question/242504") launchpad report.

---

### Post by jimr1 on 2017-12-11
I installed using the "run" script that I downloaded from the hp site.  it uses apt and uses sudo to install.  the printer is on the network.
but, there does not seem to be anything in the /var/lib/hp directory at all.  here's the output of commands.
```


jr@jr-Inspiron-560:/var/lib/hp$ hp-scan -g


HP Linux Imaging and Printing System (ver. 3.17.11)
Scan Utility ver. 2.2


Copyright (c) 2001-15 HP Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.


hp-scan[2760]: debug: getDeviceUri(None, None, ['hpaio'], {'scan-type': (<built-in function gt>, 0)}, , True)
hp-scan[2760]: debug: Mode=0
error: No device selected/specified or that supports this functionality.
jr@jr-Inspiron-560:/var/lib/hp$ ls -alF /.usr/share/hplip/scan/plugins
ls: cannot access '/.usr/share/hplip/scan/plugins': No such file or directory
jr@jr-Inspiron-560:/var/lib/hp$ ls -alF /var/lib/hp
total 8
drwxr-xr-x  2 root root 4096 Dec  7 13:56 ./
drwxr-xr-x 70 root root 4096 Dec  7 13:56 ../
jr@jr-Inspiron-560:/var/lib/hp$ hp-check
Saving output in log file: /var/lib/hp/hp-check.log


HP Linux Imaging and Printing System (ver. 3.17.11)
Dependency/Version Check Utility ver. 15.1


Copyright (c) 2001-15 HP Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.


Note: hp-check can be run in three modes:
1. Compile-time check mode (-c or --compile): Use this mode before compiling the
HPLIP supplied tarball (.tar.gz or .run) to determine if the proper dependencies
are installed to successfully compile HPLIP.                                    
2. Run-time check mode (-r or --run): Use this mode to determine if a distro    
supplied package (.deb, .rpm, etc) or an already built HPLIP supplied tarball   
has the proper dependencies installed to successfully run.                      
3. Both compile- and run-time check mode (-b or --both) (Default): This mode    
will check both of the above cases (both compile- and run-time dependencies).   


Check types:                                                                    
a. EXTERNALDEP - External Dependencies                                          
b. GENERALDEP - General Dependencies (required both at compile and run time)    
c. COMPILEDEP - Compile time Dependencies                                       
d. [All are run-time checks]                                                    
PYEXT SCANCONF QUEUES PERMISSION                                                


Status Types:
    OK
    MISSING       - Missing Dependency or Permission or Plug-in
    INCOMPAT      - Incompatible dependency-version or Plugin-version


 
---------------
| SYSTEM INFO |
---------------


 Kernel: 4.10.0-42-generic #46~16.04.1-Ubuntu SMP Mon Dec 4 15:57:59 UTC 2017 GNU/Linux
 Host: jr-Inspiron-560
 Proc: 4.10.0-42-generic #46~16.04.1-Ubuntu SMP Mon Dec 4 15:57:59 UTC 2017 GNU/Linux
 Distribution: 12 16.04
 Bitness: 64 bit




-----------------------
| HPLIP CONFIGURATION |
-----------------------


HPLIP-Version: HPLIP 3.17.11
HPLIP-Home: /usr/share/hplip
HPLIP-Installation: Auto installation is supported for ubuntu distro  16.04 version 


Current contents of '/etc/hp/hplip.conf' file:
# hplip.conf.  Generated from hplip.conf.in by configure.


[hplip]
version=3.17.11


[dirs]
home=/usr/share/hplip
run=/var/run
ppd=/usr/share/ppd/HP
ppdbase=/usr/share/ppd
doc=/usr/share/doc/hplip-3.17.11
html=/usr/share/doc/hplip-3.17.11
icon=/usr/share/applications
cupsbackend=/usr/lib/cups/backend
cupsfilter=/usr/lib/cups/filter
drv=/usr/share/cups/drv/hp
bin=/usr/bin
apparmor=/etc/apparmor.d
# Following values are determined at configure time and cannot be changed.
[configure]
network-build=yes
libusb01-build=no
pp-build=no
gui-build=yes
scanner-build=yes
fax-build=yes
dbus-build=yes
cups11-build=no
doc-build=yes
shadow-build=no
hpijs-install=no
foomatic-drv-install=no
foomatic-ppd-install=no
foomatic-rip-hplip-install=no
hpcups-install=yes
cups-drv-install=yes
cups-ppd-install=no
internal-tag=3.17.11
restricted-build=no
ui-toolkit=qt4
qt3=no
qt4=yes
qt5=no
policy-kit=no
lite-build=no
udev_sysfs_rules=no
hpcups-only-build=no
hpijs-only-build=no
apparmor_build=yes
class-driver=no




Current contents of '/var/lib/hp/hplip.state' file:
Plugins are not installed. Could not access file: No such file or directory


Current contents of '~/.hplip/hplip.conf' file:
[upgrade]
notify_upgrade = true
last_upgraded_time = 1513001672
pending_upgrade_time = 0
latest_available_version = 3.17.10


[installation]
date_time = 12/11/2017 09:30:00
version = 3.17.11




 <Package-name>        <Package-Desc>      <Required/Optional> <Min-Version> <Installed-Version> <Status>   <Comment>


--------------
| COMPILEDEP |
--------------


 gcc                  gcc - GNU Project C and C++ Compiler                         REQUIRED        -               5.4.0           OK         -
 make                 make - GNU make utility to maintain groups of programs       REQUIRED        3.0             4.1             OK         -
 libtool              libtool - Library building support services                  REQUIRED        -               2.4.6           OK         -


------------------------
| General Dependencies |
------------------------


 libcrypto            libcrypto - OpenSSL cryptographic library                    REQUIRED        -               1.0.2           OK         -
 python-xml           Python XML libraries                                         REQUIRED        -               2.1.0           OK         -
 libnetsnmp-devel     libnetsnmp-devel - SNMP networking library development files REQUIRED        5.0.9           5.7.3           OK         -
 sane-devel           SANE - Scanning library development files                    REQUIRED        -               1.0.25          OK         -
 pil                  PIL - Python Imaging Library (required for commandline scanning with hp-scan) OPTIONAL        -               1.1.7           OK         -
 pyqt4-dbus           PyQt 4 DBus - DBus Support for PyQt4                         REQUIRED        4.0             4.11.4          OK         -
 libpthread           libpthread - POSIX threads library                           REQUIRED        -               2.23            OK         -
 python-devel         Python devel - Python development files                      REQUIRED        2.2             2.7.12          OK         -
 cups-devel           CUPS devel- Common Unix Printing System development files    REQUIRED        -               2.1.3           OK         -
 python-dbus          Python DBus - Python bindings for DBus                       REQUIRED        0.80.0          1.2.0           OK         -
 cups-ddk             CUPS DDK - CUPS driver development kit                       OPTIONAL        -               -               OK         -
 reportlab            Reportlab - PDF library for Python                           OPTIONAL        2.0             3.3.0           OK         -
 pyqt4                PyQt 4- Qt interface for Python (for Qt version 4.x)         REQUIRED        4.0             4.11.4          OK         -
 libusb               libusb - USB library                                         REQUIRED        -               1.0             OK         -
 cups-image           CUPS image - CUPS image development files                    REQUIRED        -               2.1.3           OK         -
 python2X             Python 2.2 or greater - Python programming language          REQUIRED        2.2             2.7.12          OK         -
 python-notify        Python libnotify - Python bindings for the libnotify Desktop notifications OPTIONAL        -               -               OK         -
 libjpeg              libjpeg - JPEG library                                       REQUIRED        -               -               OK         -
 sane                 SANE - Scanning library                                      REQUIRED        -               1.0.25          OK         -


----------------------
| Scan Configuration |
----------------------


 scanext              Scan-SANE-Extension                                          REQUIRED        -               3.17.11         OK         -
 hpaio                HPLIP-SANE-Backend                                           REQUIRED        -               3.17.11         OK         'hpaio found in /etc/sane.d/dll.conf'


-------------------------
| External Dependencies |
-------------------------


 gs                   GhostScript - PostScript and PDF language interpreter and previewer REQUIRED        7.05            9.18            OK         -
 scanimage            scanimage - Shell scanning program                           OPTIONAL        1.0             1.0.25          OK         -
 cups                 CUPS - Common Unix Printing System                           REQUIRED        1.1             2.1.3           OK         'CUPS Scheduler is running'
 network              network -wget                                                OPTIONAL        -               1.17.1          OK         -
 policykit            PolicyKit - Administrative policy framework                  OPTIONAL        -               0.105           OK         -
 xsane                xsane - Graphical scanner frontend for SANE                  OPTIONAL        0.9             0.999           OK         -
 dbus                 DBus - Message bus system                                    REQUIRED        -               1.10.6          OK         -
 avahi-utils          avahi-utils                                                  OPTIONAL        -               0.6.32          OK         -


---------------------
| Python Extentions |
---------------------


 hpmudext             IO-Extension                                                 REQUIRED        -               3.17.11         OK         -
 cupsext              CUPS-Extension                                               REQUIRED        -               3.17.11         OK         -


------------------------------
| DISCOVERED SCANNER DEVICES |
------------------------------


No Scanner found.


--------------------------
| DISCOVERED USB DEVICES |
--------------------------


No devices found.


---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------


 
HP-Color-LaserJet-Pro-MFP-M477
------------------------------
Type: Unknown
Device URI: socket://192.168.0.101:9100
PPD: /etc/cups/ppd/HP-Color-LaserJet-Pro-MFP-M477.ppd
warning: Failed to read /etc/cups/ppd/HP-Color-LaserJet-Pro-MFP-M477.ppd ppd file
PPD Description: 
Printer status: printer HP-Color-LaserJet-Pro-MFP-M477 is idle.  enabled since Thu 07 Dec 2017 02:23:33 PM EST
warning: Printer is not HPLIP installed. Printers must use the hp: or hpfax: CUPS backend for HP-Devices.




--------------
| PERMISSION |
--------------


 
-----------
| SUMMARY |
-----------


Missing Required Dependencies
-----------------------------
None


Missing Optional Dependencies
-----------------------------
None




Total Errors: 0
Total Warnings: 1




Done.
jr@jr-Inspiron-560:/var/lib/hp$ 

```

hope I did that right.

thanks for your help.

---

### Post by pdc on 2017-12-11
I hope DuckHook doesn't mind me commenting here: my take is the hp-check looks ok but the phrase "plug-in" is mentioned; and I see the hp-check seems to see your device as an MFP m477 that needs a plug-in

this page [https://developers.hp.com/hp-linux-imaging-and-printing/binaary_plugin.html](https://developers.hp.com/hp-linux-imaging-and-printing/binaary_plugin.html) talks about how to do it: basically type ```
hp-setup
``` in a terminal and authorise a plug-in to be installed

(I think you must have an icon in your PRINTERS folder; I would suggest right-click and delete it .... if it is not working ...... HP say the command above gets the plug-in installed; and that sets up a printer registration; so a clean slate to do that sounds right ..)

---

### Post by jimr1 on 2017-12-11
```
hp-setup


HP Linux Imaging and Printing System (ver. 3.17.11)
Printer/Fax Setup Utility ver. 9.0


Copyright (c) 2001-15 HP Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.


Searching... (bus=net, timeout=5, ttl=4, search=(None) desc=0, method=slp)
error: No devices found on bus: net
warning:  HPLIP cannot detect printers in your network.  This may be due to existing firewall settings blocking the required ports.
                When you are in a trusted network environment, you may open the ports for network services like mdns and slp in the firewall. For detailed steps follow the link.
                 http://hplipopensource.com/node/375
``` 
when I try to go to that page it isn't found.  and that doesn't make sense anyway, does it, if when I boot to windows, it finds both the printer and the scanner fine.  

the printer I have currently installed was an attempt to use something similar to my printer, which does not seem to be supported...but again while the print functions work, no scanner can be found.

---

### Post by DuckHook on 2017-12-11
> **pdc said:**
> I hope DuckHook doesn't mind me commenting here…
@pdc  I am more than happy to see you diving in. Your participation is an example of Ubuntu Forums working at its best! ;)
> **jimr1 said:**
> …here's the output of commands.
hope I did that right.

One of the outputs is the result of an invalid command because you made a typo and have an extra . (dot) before *usr*:```
ls -alF /.usr/share/hplip/scan/plugins     #incorrect
ls -alF /usr/share/hplip/scan/plugins     #correct
```The extra dot will point to a nonexistent directory. It's probably best to copy and paste my command line into your terminal session to avoid such typos. Please repost.
> **jimr1 said:**
> …when I boot to windows, it finds both the printer and the scanner fine.  
What Windows will find won't have any bearing on what Ubuntu will find. Every printer sold is tested exhaustively to ensure compatibility with Windows. To be fair, HP is usually very good with Linux too, so this one is a head scratcher.
> the printer I have currently installed was an attempt to use something similar to my printer, which does not seem to be supported...but again while the print functions work, no scanner can be found.A similar driver will often do the job. However, in Linux, scanning uses a completely different subsystem.

I would suggest trying the workaround at the bottom of the page that *pdc* linked to:> Do the following:

1.  Launch a command-line window and enter:

                       ```
hp-plugin
```

2. Follow the directions above for navigating the GUI but remember that the printer que will not be installed through this process.

 *Note: you may need to run hp-plugin as root or super user depending on your distro.

---

### Post by jimr1 on 2017-12-12
before running hp-plugin:

```
jr@jr-Inspiron-560:/usr/lib$ ls -alF /usr/share/hplip/scan/plugins
ls: cannot access '/usr/share/hplip/scan/plugins': No such file or directory
```

after:
```
jr@jr-Inspiron-560:/usr/share/hplip/scan$ ls -alF /usr/share/hplip/scan/pluginstotal 200
drwxr-xr-x 2 root root  4096 Dec 12 16:55 ./
drwxr-xr-x 3 root root  4096 Dec 12 16:55 ../
lrwxrwxrwx 1 root root    47 Dec 12 16:55 bb_escl.so -> /usr/share/hplip/scan/plugins/bb_escl-x86_64.so*
-rwxr-xr-x 1 root root 43832 Dec 12 16:55 bb_escl-x86_64.so*
lrwxrwxrwx 1 root root    50 Dec 12 16:55 bb_marvell.so -> /usr/share/hplip/scan/plugins/bb_marvell-x86_64.so*
-rwxr-xr-x 1 root root 37957 Dec 12 16:55 bb_marvell-x86_64.so*
lrwxrwxrwx 1 root root    49 Dec 12 16:55 bb_soapht.so -> /usr/share/hplip/scan/plugins/bb_soapht-x86_64.so*
-rwxr-xr-x 1 root root 59314 Dec 12 16:55 bb_soapht-x86_64.so*
lrwxrwxrwx 1 root root    47 Dec 12 16:55 bb_soap.so -> /usr/share/hplip/scan/plugins/bb_soap-x86_64.so*
-rwxr-xr-x 1 root root 48353 Dec 12 16:55 bb_soap-x86_64.so*
```


now what?

---

### Post by DuckHook on 2017-12-12
> **jimr1 said:**
> before running hp-plugin:

```
jr@jr-Inspiron-560:/usr/lib$ ls -alF /usr/share/hplip/scan/plugins
ls: cannot access '/usr/share/hplip/scan/plugins': No such file or directory
```

after:
```
jr@jr-Inspiron-560:/usr/share/hplip/scan$ ls -alF /usr/share/hplip/scan/pluginstotal 200
drwxr-xr-x 2 root root  4096 Dec 12 16:55 ./
drwxr-xr-x 3 root root  4096 Dec 12 16:55 ../
lrwxrwxrwx 1 root root    47 Dec 12 16:55 bb_escl.so -> /usr/share/hplip/scan/plugins/bb_escl-x86_64.so*
-rwxr-xr-x 1 root root 43832 Dec 12 16:55 bb_escl-x86_64.so*
lrwxrwxrwx 1 root root    50 Dec 12 16:55 bb_marvell.so -> /usr/share/hplip/scan/plugins/bb_marvell-x86_64.so*
-rwxr-xr-x 1 root root 37957 Dec 12 16:55 bb_marvell-x86_64.so*
lrwxrwxrwx 1 root root    49 Dec 12 16:55 bb_soapht.so -> /usr/share/hplip/scan/plugins/bb_soapht-x86_64.so*
-rwxr-xr-x 1 root root 59314 Dec 12 16:55 bb_soapht-x86_64.so*
lrwxrwxrwx 1 root root    47 Dec 12 16:55 bb_soap.so -> /usr/share/hplip/scan/plugins/bb_soap-x86_64.so*
-rwxr-xr-x 1 root root 48353 Dec 12 16:55 bb_soap-x86_64.so*
```


now what?
This command does not make sense:```
jr@jr-Inspiron-560:/usr/share/hplip/scan$ ls -alF /usr/share/hplip/scan/pluginstotal 200
```However, I suspect that you actually typed:```
jr@jr-Inspiron-560:/usr/share/hplip/scan$ ls -alF /usr/share/hplip/scan/plugins
```If so, then the output you posted is as expected.

Now please run:```
hp-setup
```…and follow the instructions that come up to install your printer. Let's see if things work better now.

---

### Post by jimr1 on 2017-12-12
```

jr@jr-Inspiron-560:/usr/share/hplip/scan$ hp-setup


HP Linux Imaging and Printing System (ver. 3.17.11)
Printer/Fax Setup Utility ver. 9.0


Copyright (c) 2001-15 HP Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.


Searching... (bus=net, timeout=5, ttl=4, search=(None) desc=0, method=slp)
error: No devices found on bus: net
warning:  HPLIP cannot detect printers in your network.  This may be due to existing firewall settings blocking the required ports.
                When you are in a trusted network environment, you may open the ports for network services like mdns and slp in the firewall. For detailed steps follow the link.
                 http://hplipopensource.com/node/375  


Done.

```

---

### Post by DuckHook on 2017-12-12
Do you have a firewall like UFW set up on your computer?
Please post results of:```
sudo apt install nmap && nmap -sn 192.168.0.0/24
```
I think an explanation would help at this point:
You are able to print because you are going directly through *CUPS* and bypassing HPLIP. This is stated in the last sentence of following output from your hp-check report:```
HP-Color-LaserJet-Pro-MFP-M477
------------------------------
Type: Unknown
Device URI: socket://192.168.0.101:9100
PPD: /etc/cups/ppd/HP-Color-LaserJet-Pro-MFP-M477.ppd
warning: Failed to read /etc/cups/ppd/HP-Color-LaserJet-Pro-MFP-M477.ppd ppd file
PPD Description: 
Printer status: printer HP-Color-LaserJet-Pro-MFP-M477 is idle.  enabled since Thu 07 Dec 2017 02:23:33 PM EST
warning: Printer is not HPLIP installed. Printers must use the hp: or hpfax: CUPS backend for HP-Devices.
```
In other words, you are not using HPLIP at all. For some reason, HPLIP cannot find your printer on the network, but CUPS can. Therefore, HPLIP installed the printer using a sort of fallback mode. The problem is that while you can print using CUPS, HPLIP cannot manage the printer, and this includes installing the needed scanning module.

I will have to do some research on this one.

The latest commands are to download *nmap* so that we can have a look at your network layout. If you feel this to be too intrusive, please feel free to describe your network instead (will need IP info).

---

### Post by DuckHook on 2017-12-13
Okay, let's try the following:
[LIST=1]
[*]```
sudo apt install hplip-gui
```This will install the desktop GUI frontend for hp-setup. This is easier to work with for general users.
[*]Launch the gui hp toolbox that should now show up in your list of apps.
[*]Install a printer.
[*]If / when it finds nothing on the network, select manual setup and enter the IP address of your printer.
[/LIST]
Hopefully, HPLIP will now find your printer and download the appropriate printer and scanner drivers.

---

### Post by jimr1 on 2017-12-13
```
hp-setup


HP Linux Imaging and Printing System (ver. 3.17.11)
Printer/Fax Setup Utility ver. 9.0


Copyright (c) 2001-15 HP Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.


Searching... (bus=net, timeout=5, ttl=4, search=(None) desc=0, method=slp)
error: No devices found on bus: net
warning:  HPLIP cannot detect printers in your network.  This may be due to existing firewall settings blocking the required ports.
                When you are in a trusted network environment, you may open the ports for network services like mdns and slp in the firewall. For detailed steps follow the link.
                 [http://hplipopensource.com/node/375](http://hplipopensource.com/node/375)  


Done.
```

---

### Post by DuckHook on 2017-12-13
:confused:
This is not the result from what I asked you to do in #13 above. Those would be GUI steps with GUI results. Please follow those instructions and *describe* to us what happens.

---

### Post by jimr1 on 2017-12-13
sorry, I'm being stupid, didn't realize there was a second page.
```

jr@jr-Inspiron-560:/usr/share/hplip/scan$ sudo ufw status
[sudo] password for jr: 
Status: inactive
jr@jr-Inspiron-560:/usr/share/hplip/scan$ sudo apt install nmap && nmap -sn 192.168.0.0/24
[sudo] password for jr: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  fonts-roboto fonts-roboto-hinted libcec-platform1v5 libcec3 libfstrcmp0
  libhdhomerun2 libjs-iscroll libplatform2 linux-headers-4.10.0-35
  linux-headers-4.10.0-35-generic linux-headers-4.10.0-37
  linux-headers-4.10.0-37-generic linux-headers-4.10.0-38
  linux-headers-4.10.0-38-generic linux-image-4.10.0-35-generic
  linux-image-4.10.0-37-generic linux-image-4.10.0-38-generic
  linux-image-extra-4.10.0-35-generic linux-image-extra-4.10.0-37-generic
  linux-image-extra-4.10.0-38-generic python-psutil python3-notify2
  python3-pyqt4 python3-sip
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  liblinear3 lua-lpeg ndiff python-bs4 python-chardet python-html5lib
  python-lxml python-pkg-resources
Suggested packages:
  liblinear-tools liblinear-dev python-genshi python-lxml-dbg python-lxml-doc
  python-setuptools
The following NEW packages will be installed:
  liblinear3 lua-lpeg ndiff nmap python-bs4 python-chardet python-html5lib
  python-lxml python-pkg-resources
0 upgraded, 9 newly installed, 0 to remove and 13 not upgraded.
Need to get 5,897 kB of archives.
After this operation, 26.6 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 liblinear3 amd64 2.1.0+dfsg-1 [39.3 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 lua-lpeg amd64 0.12.2-1 [28.3 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 python-bs4 all 4.4.1-1 [64.2 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 python-pkg-resources all 20.7.0-1 [108 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 python-chardet all 2.3.0-2 [96.3 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 python-html5lib all 0.999-4 [83.1 kB]
Get:7 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 python-lxml amd64 3.5.0-1build1 [819 kB]
Get:8 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 ndiff all 7.01-2ubuntu2 [20.1 kB]
Get:9 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 nmap amd64 7.01-2ubuntu2 [4,638 kB]
Fetched 5,897 kB in 0s (13.5 MB/s)
Selecting previously unselected package liblinear3:amd64.
(Reading database ... 332841 files and directories currently installed.)
Preparing to unpack .../liblinear3_2.1.0+dfsg-1_amd64.deb ...
Unpacking liblinear3:amd64 (2.1.0+dfsg-1) ...
Selecting previously unselected package lua-lpeg:amd64.
Preparing to unpack .../lua-lpeg_0.12.2-1_amd64.deb ...
Unpacking lua-lpeg:amd64 (0.12.2-1) ...
Selecting previously unselected package python-bs4.
Preparing to unpack .../python-bs4_4.4.1-1_all.deb ...
Unpacking python-bs4 (4.4.1-1) ...
Selecting previously unselected package python-pkg-resources.
Preparing to unpack .../python-pkg-resources_20.7.0-1_all.deb ...
Unpacking python-pkg-resources (20.7.0-1) ...
Selecting previously unselected package python-chardet.
Preparing to unpack .../python-chardet_2.3.0-2_all.deb ...
Unpacking python-chardet (2.3.0-2) ...
Selecting previously unselected package python-html5lib.
Preparing to unpack .../python-html5lib_0.999-4_all.deb ...
Unpacking python-html5lib (0.999-4) ...
Selecting previously unselected package python-lxml.
Preparing to unpack .../python-lxml_3.5.0-1build1_amd64.deb ...
Unpacking python-lxml (3.5.0-1build1) ...
Selecting previously unselected package ndiff.
Preparing to unpack .../ndiff_7.01-2ubuntu2_all.deb ...
Unpacking ndiff (7.01-2ubuntu2) ...
Selecting previously unselected package nmap.
Preparing to unpack .../nmap_7.01-2ubuntu2_amd64.deb ...
Unpacking nmap (7.01-2ubuntu2) ...
Processing triggers for libc-bin (2.23-0ubuntu9) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up liblinear3:amd64 (2.1.0+dfsg-1) ...
Setting up lua-lpeg:amd64 (0.12.2-1) ...
Setting up python-bs4 (4.4.1-1) ...
Setting up python-pkg-resources (20.7.0-1) ...
Setting up python-chardet (2.3.0-2) ...
Setting up python-html5lib (0.999-4) ...
Setting up python-lxml (3.5.0-1build1) ...
Setting up ndiff (7.01-2ubuntu2) ...
Setting up nmap (7.01-2ubuntu2) ...
Processing triggers for libc-bin (2.23-0ubuntu9) ...


Starting Nmap 7.01 ( https://nmap.org ) at 2017-12-13 23:22 EST
Nmap scan report for 192.168.0.1
Host is up (0.00030s latency).
Nmap scan report for 192.168.0.101
Host is up (0.00024s latency).
Nmap scan report for 192.168.0.103
Host is up (0.046s latency).
Nmap scan report for 192.168.0.106
Host is up (0.0030s latency).
Nmap scan report for 192.168.0.110
Host is up (0.00050s latency).
Nmap done: 256 IP addresses (5 hosts up) scanned in 2.44 seconds
jr@jr-Inspiron-560:/usr/share/hplip/scan$ sudo apt install hplip-gui
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  fonts-roboto fonts-roboto-hinted libcec-platform1v5 libcec3 libfstrcmp0
  libhdhomerun2 libjs-iscroll libplatform2 linux-headers-4.10.0-35
  linux-headers-4.10.0-35-generic linux-headers-4.10.0-37
  linux-headers-4.10.0-37-generic linux-headers-4.10.0-38
  linux-headers-4.10.0-38-generic linux-image-4.10.0-35-generic
  linux-image-4.10.0-37-generic linux-image-4.10.0-38-generic
  linux-image-extra-4.10.0-35-generic linux-image-extra-4.10.0-37-generic
  linux-image-extra-4.10.0-38-generic python-psutil
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  hplip hplip-data libhpmud0 libsane-hpaio printer-driver-hpcups
  printer-driver-postscript-hp
Suggested packages:
  hplip-doc system-config-printer
The following NEW packages will be installed:
  hplip hplip-data hplip-gui libhpmud0 libsane-hpaio printer-driver-hpcups
  printer-driver-postscript-hp
0 upgraded, 7 newly installed, 0 to remove and 13 not upgraded.
Need to get 7,940 kB/7,956 kB of archives.
After this operation, 15.6 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 hplip-data all 3.16.3+repack0-1 [6,393 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 libhpmud0 amd64 3.16.3+repack0-1 [107 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 libsane-hpaio amd64 3.16.3+repack0-1 [114 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 printer-driver-hpcups amd64 3.16.3+repack0-1 [252 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 hplip amd64 3.16.3+repack0-1 [65.6 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 printer-driver-postscript-hp all 3.16.3+repack0-1 [1,009 kB]
Fetched 7,940 kB in 0s (14.0 MB/s)                      
Selecting previously unselected package hplip-data.
(Reading database ... 333836 files and directories currently installed.)
Preparing to unpack .../hplip-data_3.16.3+repack0-1_all.deb ...
Unpacking hplip-data (3.16.3+repack0-1) ...
Selecting previously unselected package libhpmud0:amd64.
Preparing to unpack .../libhpmud0_3.16.3+repack0-1_amd64.deb ...
Unpacking libhpmud0:amd64 (3.16.3+repack0-1) ...
Selecting previously unselected package libsane-hpaio:amd64.
Preparing to unpack .../libsane-hpaio_3.16.3+repack0-1_amd64.deb ...
Unpacking libsane-hpaio:amd64 (3.16.3+repack0-1) ...
Selecting previously unselected package printer-driver-hpcups.
Preparing to unpack .../printer-driver-hpcups_3.16.3+repack0-1_amd64.deb ...
Unpacking printer-driver-hpcups (3.16.3+repack0-1) ...
Selecting previously unselected package hplip.
Preparing to unpack .../hplip_3.16.3+repack0-1_amd64.deb ...
Unpacking hplip (3.16.3+repack0-1) ...
Selecting previously unselected package hplip-gui.
Preparing to unpack .../hplip-gui_3.16.3+repack0-1_all.deb ...
Unpacking hplip-gui (3.16.3+repack0-1) ...
Selecting previously unselected package printer-driver-postscript-hp.
Preparing to unpack .../printer-driver-postscript-hp_3.16.3+repack0-1_all.deb ...
Unpacking printer-driver-postscript-hp (3.16.3+repack0-1) ...
Processing triggers for libc-bin (2.23-0ubuntu9) ...
Processing triggers for cups (2.1.3-4ubuntu0.3) ...
Processing triggers for dbus (1.10.6-1ubuntu3.3) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5.1) ...
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20160824-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.59ubuntu1) ...
Setting up hplip-data (3.16.3+repack0-1) ...
Setting up libhpmud0:amd64 (3.16.3+repack0-1) ...
Setting up libsane-hpaio:amd64 (3.16.3+repack0-1) ...
Setting up printer-driver-hpcups (3.16.3+repack0-1) ...
Setting up hplip (3.16.3+repack0-1) ...
Creating/updating hplip user account...
Setting up hplip-gui (3.16.3+repack0-1) ...
Setting up printer-driver-postscript-hp (3.16.3+repack0-1) ...
Processing triggers for libc-bin (2.23-0ubuntu9) ...

```

---

### Post by jimr1 on 2017-12-13
when I run the GUI hp tool, it still can't find the printer.  tried the manual method, same thing.

---

### Post by DuckHook on 2017-12-13
I'm running out of ideas. A search shows this bug from Launchpad: [https://bugs.launchpad.net/ubuntu/+source/hplip/+bug/1697958](https://bugs.launchpad.net/ubuntu/+source/hplip/+bug/1697958) which sounds like your issue.

So let's try a few more things:

[LIST=1]
[*]On your physical printer, in its settings, make sure that SNMP is turned on. Then try manual discovery again.
[*]Also, try using mDNS/Bonjour to probe for printer.
[/LIST]
If all of this fails, then I surmise that your problem may be similar to that of Dror Cohen's in the Launchpad thread, and isn't found in the models.dat file (it's a large monster file containing all of the models and their settings that HPLIP can process)

I suppose for curiosity's sake, you could run:```
hp-setup -g
```…which runs the setup app in debug mode, just as Dror did. But even if this confirms his findings, it won't do you any good. You will just know that HPLIP cannot find your printer because it is so new or so unusual that no settings have been defined for it in HPLIP.

I am not sufficiently knowledgeable to help you set up scanning independently of HPLIP. So, assuming that above guess is accurate (a big assumption), you may have no choice but to wait for newer versions of HPLIP to come out that recognize your MFP.

---

### Post by agillator on 2017-12-14
You might try contacting the HPLIP folks at [https://developers.hp.com/hp-linux-imaging-and-printing/support](https://developers.hp.com/hp-linux-imaging-and-printing/support) unless I missed that one of the above is from them. And apparently there is other support from HP directly but I think the HPLIP folks would be the place to start and they should direct you elsewhere if they need to. Once you are talking to the right people at HP the support is quite good. For some reason the wrong people don't seem to want to admit they support Linux, so be persistent.

---

### Post by jimr1 on 2017-12-14
```
jr@jr-Inspiron-560:/usr/share/hplip/scan$ hp-setup -g


HP Linux Imaging and Printing System (ver. 3.17.11)
Printer/Fax Setup Utility ver. 9.0


Copyright (c) 2001-15 HP Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.


hp-setup[4460]: debug: param=
hp-setup[4460]: debug: selected_device_name=None
hp-setup[4460]: debug: Sys.argv=['/usr/bin/hp-setup', '-g'] printer_name=None param= jd_port=1 device_uri=None remove=False
hp-setup[4460]: debug: Starting GUI loop...
Searching... (bus=net, timeout=5, ttl=4, search=(None) desc=0, method=slp)
hp-setup[4460]: debug: 0000:  01 07 01 eb 00 00 65 6e 00 03 2c 0a 00 00 01 db 28 78 2d 68 70 2d 76 65 72 3d 30 31 29 28 78 2d  ......en..,.....(x-hp-ver=01)(x-
hp-setup[4460]: debug: 0020:  68 70 2d 70 72 6f 64 5f 69 64 3d 54 36 42 37 34 41 29 28 78 2d 68 70 2d 6d 61 63 3d 31 38 36 30  hp-prod_id=T6B74A)(x-hp-mac=1860
hp-setup[4460]: debug: 0040:  32 34 43 42 43 43 31 43 29 28 78 2d 68 70 2d 67 75 69 64 3d 31 38 36 30 32 34 43 42 43 43 31 43  24CBCC1C)(x-hp-guid=186024CBCC1C
hp-setup[4460]: debug: 0060:  29 28 78 2d 68 70 2d 6e 75 6d 5f 70 6f 72 74 3d 30 31 29 28 78 2d 68 70 2d 69 70 3d 31 39 32 2e  )(x-hp-num_port=01)(x-hp-ip=192.
hp-setup[4460]: debug: 0080:  31 36 38 2e 30 30 30 2e 31 30 31 29 28 78 2d 68 70 2d 68 6e 3d 4e 50 49 43 42 43 43 31 43 29 28  168.000.101)(x-hp-hn=NPICBCC1C)(
hp-setup[4460]: debug: 00a0:  78 2d 68 70 2d 70 31 3d 4d 46 47 3a 48 50 3b 43 4d 44 3a 50 4a 4c 2c 50 4d 4c 2c 50 43 4c 58 4c  x-hp-p1=MFG:HP;CMD:PJL,PML,PCLXL
hp-setup[4460]: debug: 00c0:  2c 50 57 47 5f 52 41 53 54 45 52 2c 55 52 50 2c 50 43 4c 2c 50 44 46 2c 50 4f 53 54 53 43 52 49  ,PWG_RASTER,URP,PCL,PDF,POSTSCRI
hp-setup[4460]: debug: 00e0:  50 54 3b 4d 44 4c 3a 48 50 20 43 6f 6c 6f 72 4c 61 73 65 72 4a 65 74 20 4d 46 50 20 4d 31 37 38  PT;MDL:HP ColorLaserJet MFP M178
hp-setup[4460]: debug: 0100:  2d 4d 31 38 31 3b 43 4c 53 3a 50 52 49 4e 54 45 52 3b 44 45 53 3a 48 50 20 43 6f 6c 6f 72 20 4c  -M181;CLS:PRINTER;DES:HP Color L
hp-setup[4460]: debug: 0120:  61 73 65 72 4a 65 74 20 4d 46 50 20 4d 31 38 30 6e 77 3b 4d 45 4d 3a 4d 45 4d 3d 32 32 38 4d 42  aserJet MFP M180nw;MEM:MEM=228MB
hp-setup[4460]: debug: 0140:  3b 50 52 4e 3a 54 36 42 37 34 41 3b 43 4f 4d 4d 45 4e 54 3a 52 45 53 3d 36 30 30 78 38 3b 4c 45  ;PRN:T6B74A;COMMENT:RES=600x8;LE
hp-setup[4460]: debug: 0160:  44 4d 44 49 53 3a 55 53 42 23 66 66 23 30 34 23 30 31 3b 43 49 44 3a 48 50 4c 4a 50 44 4c 56 31  DMDIS:USB#ff#04#01;CID:HPLJPDLV1
hp-setup[4460]: debug: 0180:  3b 49 50 50 2d 45 3a 46 46 2d 30 34 2d 30 31 2c 46 46 2d 30 34 2d 30 31 2c 46 46 2d 30 39 2d 30  ;IPP-E:FF-04-01,FF-04-01,FF-09-0
hp-setup[4460]: debug: 01a0:  31 2c 46 46 2d 30 39 2d 30 31 3b 65 53 43 4c 3a 46 46 2d 30 34 2d 30 31 2c 46 46 2d 30 34 2d 30  1,FF-09-01;eSCL:FF-04-01,FF-04-0
hp-setup[4460]: debug: 01c0:  31 2c 46 46 2d 30 39 2d 30 31 2c 46 46 2d 30 39 2d 30 31 3b 4d 43 54 3a 4d 46 3b 4d 43 4c 3a 46  1,FF-09-01,FF-09-01;MCT:MF;MCL:F
hp-setup[4460]: debug: 01e0:  4c 3b 4d 43 56 3a 32 2e 30 3b 29                                                                 L;MCV:2.0;)
hp-setup[4460]: debug: Found device: {'device3': '0', 'mac': '186024CBCC1C', 'device2': '0', 'ip': '192.168.000.101', 'num_devices': 1, 'device1': 'MFG:HP;CMD:PJL,PML,PCLXL,PWG_RASTER,URP,PCL,PDF,POSTSCRIPT;MDL:HP ColorLaserJet MFP M178-M181;CLS:PRINTER;DES:HP Color LaserJet MFP M180nw;MEM:MEM=228MB;PRN:T6B74A;COMMENT:RES=600x8;LEDMDIS:USB#ff#04#01;CID:HPLJPDLV1;IPP-E:FF-04-01,FF-04-01,FF-09-01,FF-09-01;eSCL:FF-04-01,FF-04-01,FF-09-01,FF-09-01;MCT:MF;MCL:FL;MCV:2.0;', 'note': '', 'hn': 'NPICBCC1C', 'status_code': 0, 'product_id': 'T6B74A', 'num_ports': 1}
hp-setup[4460]: debug: Cache miss: hp_colorlaserjet_mfp_m178-m181
hp-setup[4460]: debug: Reading file: /usr/share/hplip/data/models/models.dat
hp-setup[4460]: debug: Searching for section [hp_colorlaserjet_mfp_m178-m181] in file /usr/share/hplip/data/models/models.dat
error: No devices found on bus: net
warning:  HPLIP cannot detect printers in your network.  This may be due to existing firewall settings blocking the required ports.
                When you are in a trusted network environment, you may open the ports for network services like mdns and slp in the firewall. For detailed steps follow the link.
                 http://hplipopensource.com/node/375  



```

so yes, it looks similar to that reported bug, in that the printer is being seen, but since it's not in the models.dat file, not recognized.  the bug was reported against 17.04 thought, and I'm running 16.04 LTS, for what it's worth.

tried those other two options in advanced mode, nothing different there either, same with using the direct method.

I couldn't figure out how to set that option on the physical printer, went all through the menu, didn't find it.  I'll dig into the manual tomorrow when I'm more awake and see if I can find that.  

thanks for all your help, appreciate it.  but I'm about ready to give up here, and just boot to windows (yuck!) when I need to scan something.  that'll teach me to buy something without checking the compat list first.

---

### Post by DuckHook on 2017-12-14
> **jimr1 said:**
> …it looks similar to that reported bug, in that the printer is being seen, but since it's not in the models.dat file, not recognized.
That's my conclusion as well.
> the bug was reported against 17.04 thought, and I'm running 16.04 LTS, for what it's worth.It won't work on any version because the bug is not, in fact, in the OS, it's in HPLIP. That won't change until a new version of HPLIP comes out.
> I couldn't figure out how to set that option on the physical printer, went all through the menu, didn't find it.  I'll dig into the manual tomorrow when I'm more awake and see if I can find that.
I suspect that you will only be wasting your time. HPLIP sees the printer. It just doesn't know what to do with it.
> thanks for all your help, appreciate it.  but I'm about ready to give up here, and just boot to windows (yuck!) when I need to scan something.  that'll teach me to buy something without checking the compat list first.
I'm rather cheesed off, truth be told. I don't like going down in defeat this way, no matter how high we hold our heads. But I suspect that my feelings aren't going to get you any closer to a solution. At least you can print, which you made happen by yourself (to your credit!).

FWIW, I ran into a similar issue a few years ago: bought a printer too new for HPLIP. The HPLIP developers are a fine bunch of people, but they are largely community-based volunteers and it understandably takes them some time to build new drivers and settings for all of the printers that HP introduces.

I suspect that you won't have to wait too long. In the meantime, firing up Windows is a good workaround.

Good Luck and Happy Ubuntu-ing!

---

### Post by jimr1 on 2017-12-14
thanks for the advice.  I did try the HP folk, had a fellow on the phone for about an hour before I realized he knew nothing about unix and was just wasting my time.  I will try again.

---

