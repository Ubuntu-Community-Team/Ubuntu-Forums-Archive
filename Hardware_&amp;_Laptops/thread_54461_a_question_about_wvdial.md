---
title: "a question about wvdial"
date: 2005-08-04
forum: Hardware &amp; Laptops
---

### Post by HasH on 2005-08-04
hallo guys, i'm a newbee in linux, now i'm trying to make my ibm integrated modem working, but after lots of tries, i can still not connect to the internet... 
i think i've correctly installed the driver (sl-modem-daemon_2.9.9a-1ubuntu4_i386.deb ;    sl-modem-source_2.9.9a-1ubuntu4_i386.deb ;  slmodem-2.9.10.tar.gz )

and this is the diagnose from scanmodem:

------------ --------------  System information ------------------------
 Ubuntu 5.04 "Hoary Hedgehog" 
 on System with processor: i686
 currently under kernel:   2.6.10-5-686

There are emerging complications under 2.6.10 and later kernels. 
Concerning Intel-536ep and 537
   [http://www.ubuntulinux.org/wiki/IntelFiveThreeSixEPModemHowto/](http://www.ubuntulinux.org/wiki/IntelFiveThreeSixEPModemHowto/) 
   [http://linmodems.technion.ac.il/archive-fifth/msg00280.html](http://linmodems.technion.ac.il/archive-fifth/msg00280.html)
   [http://linmodems.technion.ac.il/archive-fifth/msg00881.html](http://linmodems.technion.ac.il/archive-fifth/msg00881.html)
   
 The kernel was assembled with compiler:  3.3.5
 with current System compiler GCC=3.3.5
    /usr/bin/gcc -> gcc-3.3

A package kernel-kbuild-2.6-3 or later version must be installed to support compiling

Checking for kernel-headers needed for compiling.
The kernel-headers have base folder: 
/lib/modules/2.6.10-5-686/build -> /usr/src/linux-headers-2.6.10-5-686
/usr/src/linux -> linux-headers-2.6.10-5-686
/usr/src/linux-headers-2.6.10-5-686
Please install the package WVDIAL for modem testing and dialout.

 Modem symbolic link is:  /dev/modem -> ttySL0
 USB modem not detected.

0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)

Modem candidates are at PCI_buses:  0000:00:1f.6
    
Providing detail for device at  0000:00:1f.6
  with vendor-ID:device-ID
	    ----:----
Class 0703: 8086:24c6   Modem: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01) (prog-if 00 [Generic])
  SubSystem 1014:0559   IBM: Unknown device 0559
0000:00:1f.6 0703: 8086:24c6 (rev 01)
	Flags: bus master, medium devsel, latency 0, IRQ 11
  
                  -----PCI_IDs-------                    --CompilerVer- 
    Feature List:  Primary  Subsystem Distr  KernelVer   kernel default  CPU
 ./scanModem test 8086:24c6 1014:0559 debian 2.6.10-5-686  3.3.5 3.3.5    i686

       
 The soft modem Subsystem operates under a controller
   8086:24c6 82801DB ICH4 
 capable of supporting under Linux AT LEAST modem Subsystem chips from manufacturers:

	Broadcom
	AgereSystems
	Conexant
	Intel
	Smartlink
 The Subsystem PCI id does not itself identify the modem Codec.

	Smartlink software in ALSA mode may support this modem 

  Driver snd-intel8x0m  may enable codec acquisition 





i've run "sudo slmodemd --country=MY_COUNTRY  /dev/modem" and got this result

SmartLink Soft Modem: version 2.9.10 Aug  4 2005 18:32:34
symbolic link `/dev/ttySL0' -> `/dev/pts/3' created.
modem `modem' created. TTY is `/dev/pts/3'
Use `/dev/ttySL0' as modem device, Ctrl+C for termination.



then the link "/dev/modem" just disapeared... ](*,)  ](*,)  ](*,)  
but after reboot, it will exist again and with a "X" symbol.




i've run "sudo wvdialconf /etc/wvdial.conf" and this is my wvdial.conf

[Dialer Defaults]
Modem = /dev/modem
Baud = 460800
Init1 = ATX3
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem
Phone = 01920786
Username = arcor
Password = internet
~


the result from "sudo wvdial":

--> WvDial: Internet dialer version 1.54.0
--> Initializing modem.
--> Sending: ATX3
ATX3
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT01920786
--> Waiting for carrier.
ATDT01920786
NO ANSWER
--> Unknown dial response string.
--> Disconnecting at Fri Aug  5 00:52:00 2005



i must thank a lot of people here, i can't go this far without their help, but i will be more appreciate when you give me any suggestion . O:)

---

### Post by HasH on 2005-08-05
anybody......HELP.......

---

### Post by yyagol on 2005-08-05
i had the same prob with fedora and now with ubuntu
did you :
$sudo ln -s /dev/ttySL0 /dev/modem

in fedora i got it to ring but not more then that
it could not conect to the internet or send a fax
this winmodem sucks!!!! 
```
root@localhost ~]# dmesg | grep slamr
slamr: SmartLink AMRMO modem.
slamr: probe 163c:3052 SL1900 card...
slamr: slamr0 is SL1900 card. 
``` 
then i did:
```
[root@localhost ~]# modprobe slamr
[root@localhost ~]# slmodemd -c ISRAEL
SmartLink Soft Modem: version 2.9.10 Jul  4 2005 21:11:27
symbolic link `/dev/ttySL0' -> `/dev/pts/3' created.
modem `slamr0' created. TTY is `/dev/pts/3'
Use `/dev/ttySL0' as modem device, Ctrl+C for termination. 
``` 

then this :
```
[root@localhost ~]# ln -n /dev/ttySL0 /dev/modem
[root@localhost ~]# wvdial
--> WvDial: Internet dialer version 1.54.0
--> Warning: section [Dialer Defaults] does not exist in wvdial.conf.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Modem initialized.
--> Configuration does not specify a valid phone number.
--> Configuration does not specify a valid login name.
--> Configuration does not specify a valid password.
[root@localhost ~]# 
``` 

ok so the modem is fine but i could not get it to work with
efax .....no modem was detected.
i just rty one with ubuntu but gave up on it couse it just cant work!!!!! ](*,)

---

### Post by mingus on 2005-08-15
HasH -

In the wvdial.conf file change the modem device to /dev/ttySL0 and the baud to 115200.  Try using gnome-ppp which calls wvdial but which allows you to add more dialer options; try "stupid mode".  Also try pppconfig, and then in a terminal pon to dial (poff to hang-up).  And for the /dev/modem "x" issue, run Nautilus as sudo or su, find that file, and check the permissions; give "Other" read and write access; do the same for device /dev/ttySL0.  Note the following.

yyagol -

You have an entirely different problem.  Your modem is based on the smartlink chipset.  The sl-modem module actually has 2 drivers, slamr for proprietary smartlink and Alsa also for this chipset but works with some AC97 modems (the traffic is being piped thru the sound card).

Your wvdial.conf file doesn't have the necessary dialing info, to use wvdial you have to add that or use gnome-ppp and enter it there.

There is a known bug in the smartlink driver for some systems.  At the scanmodem website find ungrab-winmodem, download and compile it.  Then add ungrab-winmodem and slamr to the end of file /etc/modules.  Reboot.

If /dev/modem is still not recognized, try using /dev/ttySL0 in the dialer instead.  Also try pppconfig if wvdial doesn't work.

EDIT:  If using wvdial, sometimes the line "Carrier check = no" in /etc/wvdial.conf is required.

---

### Post by yyagol on 2005-08-17
i will try it thanks

---

### Post by joshpelkey on 2005-08-17
> At the scanmodem website find ungrab-winmodem, download and compile it You both will not need to do this since the modprobe and slmodemd command you issued worked correctly.  Definitely add "Carrier check = no" [without quotes] to the end of wvdail.conf.  And check to make sure the phone number you are providing is correct!  :grin:  

**yyagol**  If you've never really used wvdial before, make sure you've run this command:

wvdialconf /etc/wvdial.conf

Then edit the file...adding your username, password, ISP phone number, and add Carrier Check no!  Post your wvdail.conf for further analysis if wvdial still won't work. [you can edit out your username and pass if you need].

Don't give up!  You are so close.  I just went through this about 2 weeks ago.

---

### Post by mingus on 2005-08-18
[QUOTE=joshpelkey]Definitely add "Carrier check = no" [without quotes] to the end of wvdail.conf.[/QUOTE]

Just checking . . . do they need to do this if they are using the slamr driver rather than the Alsa alternative?

---

### Post by joshpelkey on 2005-08-18
To be honest, I'm not 100% sure that it is absolutely neccessary.  I use the slamr drivers, and I use Carrier Check = no, so I just assumed it was.  From what I've read through ./scanModem => Testing.txt, "For systems using the SmartLink slmodem drivers, the following line should be added to its /etc/wvdial.conf Carrier Check = no"     I'd have to go check it out on my home computer, but I think that includes the slamr drivers.  As far as HasH's problem, it looks as if the number he's dialing isn't working.  yyagol needs to confingure his wvdial first, before he attempts to run it.

---

### Post by blastus on 2005-08-19
[QUOTE=yyagol
```
[root@localhost ~]# ln -n /dev/ttySL0 /dev/modem
[root@localhost ~]# wvdial
--> WvDial: Internet dialer version 1.54.0
--> Warning: section [Dialer Defaults] does not exist in wvdial.conf.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Modem initialized.
--> Configuration does not specify a valid phone number.
--> Configuration does not specify a valid login name.
--> Configuration does not specify a valid password.
[root@localhost ~]# 
``` 

ok so the modem is fine but i could not get it to work with
efax .....no modem was detected.
i just rty one with ubuntu but gave up on it couse it just cant work!!!!! ](*,)[/QUOTE]

This looks like your /etc/wvdial.conf file does not exist or is invalid. You need to enter:

```
sudo wvdialconf /etc/wvdial.conf
```

to create the /etc/wvdial.conf file. Then you need to put in your connection information (phone number, username, and password.) Remember to take out the semicolons and the angle brackets <>!

---

### Post by mingus on 2005-08-22
fwiw, I've discovered that there are underlying diffs in the dialers (pon/poff, wvdial, gnome-ppp, Networking from the menu).  I've had good luck with pppconfig/pon/poff and gnome-ppp, but not Networking.  Strangely, given that gnome-ppp uses wvdial, I've had the former work but the latter not.  In any event, try the different dialers.

---

### Post by Rumpty on 2005-09-18
I managed to get wvdial going with my external serial 56k modem

Here is my wvdial.conf

[Dialer Defaults]
Modem = /dev/ttyS0
Baud = 115200
Init1 = ATZ
Init2 = AT&FE0V1&C1&D2S95=45S0=0S7=60S30=0L1M1\N3%C3&K3BN1X4
ISDN = 0
Modem Type = Analog Modem
Phone =086727234
Username =********
Password =******

There was a problem having the password recognised, but careful attention to the password entry (spaces, or the lack of them) seemed to sort it out

I also had to free up permissions in wvdial.conf to allow running it as a user, and not root

---

