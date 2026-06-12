---
title: "I need rt2500 help please..."
date: 2007-08-18
forum: Hardware &amp; Laptops
---

### Post by Oliazk on 2007-08-18
Ok I have been trying and trying and trying for the past couple of days to get the pain in the but rt2500 mini pci card I have to work nothing seems to work it will show it up but not connect unless I am trying to connect the wrong way.  I have tried ndiswrapper but it refuses to work, and I have tried the ubuntu drivers but they don't seem to be doing much better.

I would like to be able to use the supplied ubuntu drivers but like I said I can't get them to work correctly and I have tried almost every thing I have been able to find on the forums here.

I really want to get this working so I don't always have to use windows when I go places because I can't use this card I thought would be great to have because it is linux supported. "grumbles"......

So any links to what people have done to get it to work or other thing I could try. ... besides buying a new card I don't have the money. 

Thanks
Oliazk

---

### Post by defconoii on 2007-08-18
hey u might want to try loading up the serialmonkey drivers at [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com) or wget [http://rt2x00.serialmonkey.com/rt2500-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt2500-cvs-daily.tar.gz)
Installation instructions for the rt2500 Module

======================================================================
Build Instructions:
====================
For 2.4 or 2.6 series kernel:
a. $tar -xvzf rt2500-x.x.x.tar.gz
    go to "./rt2500-x.x.x/Module" directory.

b. $make                # compile driver source code

c. $make install        # installs kernel module driver

(read end of file for FedoraCore3 specific information)

======================================================================
To BUILD UTILITY
====================

a.  go to the "./Utility" directory

b.  run 'qmake -o Makefile raconfig2500.pro'
    If qmake command is not found in your system, you can download
    the QT tool 'qt-x11-free-3.2.1' or later at
    [http://www.trolltech.com/](http://www.trolltech.com/)

    (qmake comes with RedHat 7.3 or later QT Package)

c.  run 'make" to compile the utility source code.

d.  After all, an execution file would be generated "RaConfig2500"
    run "RaConfig2500" to config the driver as you want

======================================================================
INVOCATION
====================
Load the driver:

        $modprobe rt2500 [ifname=<name>] [debug=<mask>]

        <name> is the name of the device and defaults to "ra%d".
        If more than one adapter is installed, specify <name> in
        sprintf format (e.g. "wlan%d" - without the quotes).
        Successive devices will then be named ra0, ra1, etc., or
        (using the example) wlan0, wlan1, etc. If there are already
        wired ethernet devices named eth0 and eth1, then specifying
        <name> as "eth%d" gives the adapter the name "eth2".

        <mask> is a decimal or hex number. See TESTING file. Ignored
        if driver compiled without debug support.

Start it up:

        $ifup ra0        # If using Debian

======================================================================
CONFIGURATION:
====================
RT2500 driver can be configured via following interfaces,
i.e. (i)"iwconfig" command, (ii)"iwpriv" command, (iii) configuration
     file, (iv) RaConfig2500

i)  iwconfig comes with kernel.
ii) iwpriv usage, please refer to file "iwpriv_usage.txt" for details.
iii)copy configuration file "RT2500STA.dat" to
    /etc/Wireless/RT2500STA/RT2500STA.dat.
    Please refer to syntax descriptions below for details.
iv) RT2500 provides API : RaConfig2500, please go to directory
    ./Utility and refer to how-to-compile.txt


Configuration File : RT2500STA.dat

# Copy this file to /etc/Wireless/RT2500STA/RT2500STA.dat
# This file is a binary file and will be read on loading rt2500.o
# module.
#
# Use "vi -b RT2500STA.dat" to modify settings according to your need.
#
# 1.) set NetworkType to "Adhoc" for using Adhoc-mode, otherwise
#     using as Infrastructure-mode.
# 2.) set Channel to "0" for auto-select on Infrastructure mode.
# 3.) set SSID for connecting to your Accss-point.
# 4.) AuthMode can be "OPEN", "SHARED", "AUTO", "WPAPSK", "WPANONE".
# 5.) EncrypType can be "NONE", "WEP", "TKIP", "AES".
#
# When editing the file, make sure the filesize does not exceed 1024
# Bytes (1kb).
# Anything stored beyond the 1024 bte limit will be ignored by the
# driver.
#
[Default]
CountryRegion=0
WirelessMode=0
SSID=AP350
NetworkType=Infra
Channel=0
AuthMode=OPEN
EncrypType=NONE
DefaultKeyID=1
Key1=0123456789
Key2=
Key3=
Key4=
WPANONE=abcdefghijklmnopqrstuvwxyz
WPAPSK=abcdefghijklmnopqrstuvwxyz
TXBurst=0
TurboRate=0
BGProtection=0
ShortSlot=0
TxPreamble=2
TxRate=0
RTSThreshold=2312
FragThreshold=2312
PSMode=CAM
-----------------------------------------------
syntax is 'Param'='Value' and described below.

1.  CountryRegion=value
    value
        0:      for use channel 1-11
        1:      for use channel 1-11
        2:      for use channel 1-13
        3:      for use channel 10-11
        4:      for use channel 10-13
        5:      for use channel 14
        6:      for use channel 1-14
        7:      for use channel 3-9
2.  WirelessMode=value
    value
        0:      802.11 B/G mixed
        1:      802.11 B only
3.  SSID=value
    value
         1~32 ascii characters.
4.  NetworkType=Infra
    value
       Infra : infrastructure mode
       Adhoc : adhoc mode
5.  Channel=value
    value
        1~14 depends on  CountryRegion
6.  AuthMode=value
    value
        OPEN      For Open System
        SHARED    For Shared key system
        AUTO
        WPANONE   For pre-shared key in adhoc mode
        WPAPSK    For pre-shared key in infrastructure mode
7.  EncrypType=value
    value
        NONE      :For AuthMode=OPEN
        WEP       :For AuthMode=OPEN or AuthMode=SHARED
        TKIP      :For AuthMode=WPAPSK or AuthMode=WPANONE
        AES       :For AuthMode=WPAPSK or AuthMode=WPANONE
8.  DefaultKeyID=value
    value
        1 ~ 4
9.  Key1=value
    value
        10 or 26 hexadecimal characters eg: 012345678
        5 or 13 ascii characters eg: passd
10. Key2=value
    value
        10 or 26 hexadecimal characters eg: 012345678
        5 or 13 ascii characters eg: passd
11. Key3=value
    value
        10 or 26 hexadecimal characters eg: 012345678
        5 or 13 ascii characters eg: passd
12. Key4=value
    value
        10 or 26 hexadecimal characters eg: 012345678
        5 or 13 ascii characters eg: passd
13. WPANONE=value - use for adhoc mode
    value
        8 ~ 63 characters
          or
        64 hexadecimal characters
13. WPAPSK=value - use for infrastructure mode
    value
        8 ~ 63 characters
          or
        64 hexadecimal characters
14. TxBurst=value
    value
        0:        Disable
        1:        Enable
15. TurboRate=value
    value
        0:        Disable
        1:        Enable
16. BGProtection=value
   value
        0:        Auto
        1:        Always On
        2:        Always Off
17. ShortSlot=value
    value
        0:        Disable
        1:        Enable
18. TxPreamble=value
    value
         0:     Long
         1:     Short
         2:     Auto
19. TxRate=value
    value
         0:     Auto
         1:     1 Mbps
         2:     2 Mbps
         3:     5.5 Mbps
         4:     11 Mbps
         5:     6  Mbps  //WirelessMode must be 0
         6:     9  Mbps  //WirelessMode must be 0
         7:     12 Mbps  //WirelessMode must be 0
         8:     18 Mbps  //WirelessMode must be 0
         9:     24 Mbps  //WirelessMode must be 0
        10:     36 Mbps  //WirelessMode must be 0
        11:     48 Mbps  //WirelessMode must be 0
        12:     54 Mbps  //WirelessMode must be 0
20. RTSThreshold=value
    value
        1 ~ 2312
21. FragThreshold=value
    value
        256 ~ 2312
22. PSMode=value
    value
    MAX_PSP   Power Saving Mode

23. AdhocOfdm=value
    value
         0:     Tx MAX rate will be 11Mbps in Adhoc mode.
         1:     Tx MAX rate will be 54Mbps in Adhoc mode.

24. StaWithEtherBridge=value
    value
         0:     Disable sta with ethernet to wireless bridge.
         1:     Enable sta with ethernet to wireless bridge.


MORE INFORMATION
======================================================================
If you want for rt2500 driver to auto-load at boot time:
A) choose ra0 for first RT2500 WLAN card, ra1 for second RT2500 WLAN
   card, etc.

B) create(edit) 'ifcfg-ra0' file in /etc/sysconfig/network-scripts/,
   edit( or add the line) in /etc/modules.conf:
       alias ra0 rt2500

C) edit(create) the file /etc/sysconfig/network-scripts/ifcfg-ra0
   DEVICE='ra0'
   ONBOOT='yes'


NOTE:
   if you use dhcp, add this line too .
    BOOTPROTO='dhcp'

*D) To ease the Default Gateway setting,
    add the line
    GATEWAY=x.x.x.x
    in /etc/sysconfig/network

INFORMATION FOR FEDORA CORE 3 USERS (USE AT YOUR OWN RISK !!!)
======================================================================
While this information is directed to Fedora Core 3 users, there is no
harm in trying some hints and clues in other distros.

Before starting, make sure you don't have any ifcfg-ra* or ifcfg-eth*
that has information about Ralink wireless cards. Check also
/etc/modprobe.conf for additional 'alias' definitions.

If you have any of the files above and/or entries in modprobe.conf,
please delete them now.

Compile the module as you would do normally with:

a) $make

and as root do:

b) $make install-fedora

The module should be installed to the correct location and the rt2500
alias added to modprobe.conf (2.6 kernels) or modules.conf
(2.4 kernels).

Start 'system-config-network',
New->Wireless connection,
Select 'RaLink Ralink RT2500 802.11 Cardbus Reference Card (wlan0)'
If it does not appear, well then it didn't work for you :)

But if it did appear then configure the rest of the parameters and
activate the card in the end.

Save configuration and enjoy your new wireless device.

---

### Post by Oliazk on 2007-08-18
strangely enough it worked once *grr grumble* now I cant get it to get and ip address and that was typing commands on the command line so not quite sure how I did that. None of the programs like wifi-radar helps or seems to work with rt2500..... this is probably the most frustrating thing about my stupid wireless card ... getting it to work right and all the time simply .... not to mention the stupid way ralink makes it work grr stupid dat file is use less and yes I messed with it didn't help......



all i want is to have one less wire 


thanks for the help

---

### Post by Oliazk on 2007-08-18
hmm probalby not good to do it like this but I think its good 

I got it to work but for some reason I can not connect to my network I ca to another one thats open and if i remove  the wep key from mine so its open i can connect to mine also but not with it secure very strange

oh and what I was

I need the linux headers build up properly which i got help from this topic [http://ubuntuforums.org/showthread.php?t=400236&highlight=serialmonkey]("http://ubuntuforums.org/showthread.php?t=400236&highlight=serialmonkey")
 and I had to find the gtk+  development package and build it and its needs 

1. started out clean system
2. updated system
3. downloaded the rt2500 files from [HERE]("http://rt2x00.serialmonkey.com/wiki/index.php/Downloads")
4. went and built the drivers and installed them
5. also downloaded the RutilT from a link on that same page
6. had to add the gtk development packages
7. build the RutilT 
8. and used it to connect

I don't know if it works any other ways I am going to check but so far its working just not on my network with it secured. *** grumbles some more and wonders why it can not communicate with the dhcp server****(gentoo router modified good deal ) :)

Edit:
I am still haveing trouble conneting to my home network which is secured using WEP . . . It does not want to communitcate with the router for some reason when secured

Edit 2:
Ok  It works now using the wicd for some reason this time through. but I am having heavy packet loss and I do not know why has anyone else experienced this before I mean come on my laptop is like 3ft from the attena for my router.. please if anyone knows possibly why this is happening please please let me know a way to fix it cause it don't happen in damned windows xpshit

---

### Post by Oliazk on 2007-08-18
poke bump

sorry i had to

---

### Post by fredj on 2007-08-19
I have successfully configured a rt2500 card to connect to my wireless network using WPA
security. However to do this I installed the windows XP drivers using ndiswrapper and I 
uninstalled network-manager and replaced it with wicd.
The version of ndiswrapper in the Ubuntu repositories is faulty and doesn't work for this card.
Open a terminal and type sudo ndiswrapper -v and post the output from that here.

---

### Post by Oliazk on 2007-08-20
Well I have gotten it to work with the serial monkey drivers using wicd to connect but i get really bad packet loss for some reason has anyone else experienced this problem.

---

