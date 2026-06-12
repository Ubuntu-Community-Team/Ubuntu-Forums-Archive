---
title: "ASUS USB-N13 adaptor"
date: 2010-08-28
forum: Hardware
---

### Post by M_Mynaardt on 2010-08-28
Hi!

I have an ASUS USB-N13 wireless adaptor and I have no clue how to install it on my computer.  I sort of stumbled on making my wireless mobile to work (a Novatel MC950D).  But that doesn't do me much good in this case.

Any suggestions?  I tried following the various posts on the USB-N13 and got totally befuddled.

I'm not entirely dim; I did find the compressed driver files and all that.  But it's been clueless-ville since that point.  Can anyone give me step-by-step directions on how to get this toy to work with Ubuntu on my desktop?  Under the assumption I know virutually nothing about Linux terminal commands (which wouldn't be too far off the mark)...

I _think_ from the posts I read, the driver archive [COLOR="DarkGreen"]2009_1110_RT3070_Linux_STA_v2.1.2.0.tar[/COLOR] is the best choice.  Apart from that; I'm lost!  :confused:

Thanks in advance...

---

### Post by M_Mynaardt on 2010-08-28
[SIZE=3]**[COLOR=Red]My USB-N13 Works in UBUNTU now!!!   WOOO-HOO![/COLOR]**[/SIZE]


I guess I shouldn't get _that_ excited, but still...

I followed post #17 of chili555 trying to help someone else with the very same 'toy'.

And his advice worked!  And there was much rejoicing!

Here's what I did, if this could be any help of anyone else.

[SIZE=2][COLOR=Indigo]I would like to emphasize that this is due to chili555's Linux know how; no way could I have thought this up on my own![/COLOR][/SIZE]
[FONT=Courier New]
[/FONT][INDENT]
[LIST=1]
[*][FONT=Courier New]Downloaded the file chili555 recommended  -->  2009_1110_RT3070_Linux_STA_v2.1.2.0.tar.bz2[/FONT]
[*][FONT=Courier New]Extracted to the Desktop.[/FONT]
[*][FONT=Courier New]Changed the name of the folder to RT3070, so I couldn't screw up the "cd" command (much).
[/FONT]
[*][FONT=Courier New]Went into the command line thingamajig.[/FONT]
[*][FONT=Courier New]Used the following commands:[/FONT]
[LIST=1]
[*][FONT=Courier New]...$ sudo su[/FONT]
[*][FONT=Courier New]...# make uninstall   [/FONT][FONT=Courier New][COLOR=Blue]*(I had one dud before this)*[/COLOR][/FONT][FONT=Courier New]
[/FONT]
[*][FONT=Courier New][COLOR=RoyalBlue][COLOR=Black]...# make[/COLOR][/COLOR][/FONT]
[*][FONT=Courier New][COLOR=RoyalBlue][COLOR=Black]...# make install
[/COLOR][/COLOR][/FONT]
[*][FONT=Courier New][COLOR=RoyalBlue][COLOR=Black]...# modprobe rt3070sta[/COLOR][/COLOR][/FONT]
[*][FONT=Courier New][COLOR=RoyalBlue][COLOR=Black]...# iwconfig[/COLOR][/COLOR][/FONT]
[/LIST]
 
[/LIST]
[/INDENT]And as soon as I typed on  iwconfig, the LED started flashing on the USB-N13 and the terminal showed:[INDENT][FONT=Courier New]lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2870 Wireless  ESSID:"208-thomson"  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr : off   Fragment thr : off
          Encryption key : off
          Link Quality=10/100  Signal level : 0 dBm  Noise level:-95 dBm
          Rx invalid nwid:0  Rx invalid crypt : 0  Rx invalid frag : 0
          Tx excessive retries:0  Invalid misc : 0   Missed beacon : 0[/FONT]
[/INDENT]I can't pretend to actually _understand_ any of that, but all I know is that after many hours of getting nowhere fast, this actually worked!

---

### Post by roxxar on 2011-02-03
I just bought my self an ASUS USB-N13 adpator in order to use it for aircrack-ng because my current wireless chip (broadcom 4313 working with the STA Wireless driver) does not support aircrack-ng. 

It's really weird because the asus usb can detect network around my house but only a few, but it won't connect correctly. I try to connect to my network, and it worked once but disconnects... I'm suspecting its due to incorrect wireless driver.

So i'm trying to install the correct driver for the asus USB...


I tried this but I get an error after make install: 

ut argument 3 has type ‘ULONG’
  CC [M]  /home/tyler/Desktop/RT3070/os/linux/../../os/linux/rt_usb.o
  CC [M]  /home/tyler/Desktop/RT3070/os/linux/../../common/cmm_mac_usb.o
/home/tyler/Desktop/RT3070/os/linux/../../common/cmm_mac_usb.c: In function ‘NICInitRecv’:
/home/tyler/Desktop/RT3070/os/linux/../../common/cmm_mac_usb.c:83: error: implicit declaration of function ‘usb_buffer_alloc’
/home/tyler/Desktop/RT3070/os/linux/../../common/cmm_mac_usb.c:83: warning: assignment makes pointer from integer without a cast
/home/tyler/Desktop/RT3070/os/linux/../../common/cmm_mac_usb.c:112: error: implicit declaration of function ‘usb_buffer_free’
make[2]: *** [/home/tyler/Desktop/RT3070/os/linux/../../common/cmm_mac_usb.o] Error 1
make[1]: *** [_module_/home/tyler/Desktop/RT3070/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-25-generic'
make: *** [LINUX] Error 2

When I try the command airmon-ng I get this :

Interface    Chipset        Driver

eth1        Unknown         wl
wlan0        Unknown         usb

the second i believe is the asus USB...

---

### Post by milocat on 2011-02-07
roxxar, I am getting the exact same error messages as well.....:confused:

---

### Post by ltrls on 2011-02-17
hi I am having the same error coming up as well. Please help I am a linoob have tried everything the great chilli555 requested, my computer is kind of recognising the device but fails to connect. any help greatly appreciated. its a bit of a con that it says 'linux compatible' on the box and raves about it on amazon but getting the drivers etc. to get the bloody thing to work is a nightmare!

---

### Post by noraaj on 2011-04-12
i am having the same error as well it keeps giving me linux error 2 and linux error 1 i don't know what it means please help

---

