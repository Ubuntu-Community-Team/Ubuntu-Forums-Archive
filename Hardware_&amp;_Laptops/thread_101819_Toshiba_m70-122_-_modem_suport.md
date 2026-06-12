---
title: "Toshiba m70-122 - modem suport"
date: 2005-12-10
forum: Hardware &amp; Laptops
---

### Post by linuxmad on 2005-12-10
Hi, 
just noticed that my modem is not working. Doing a lspci gave me these results:
"0000:00:1e.3 Modem: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)"
Where can i download drivers for it? I am using breezy with a 2.6.12-10-686 kernel in a toshiba sat. m70-122.
thanks in advance...
jose

---

### Post by towsonu2003 on 2005-12-10
Do you see your (assuming it is dial up modem) modem here: System>Administration>Networking? If yes, the driver is there and you need to set it up. 

I will assume you did not find your modem there. Then, it means you have a winmodem (most probably). go to linmodems.org , read the page, download scanModem tool using another machine and copy it to ubuntu machine -pereferably to ~/Desktop somehow. in the directory you copied scanModem.gz, do ```
gunzip scanModem.gz
chmod +x scanModem
./scanModem
```
scanmodem will NOT configure the modem. It will tell you how to configure it / find drivers / compile drivers...

read read1st.txt and modemdata.txt under the Modem folder created by scanModem (if you executed scanModem in ~/ then Modem is under ~/ ). If you cannot figure out what to do with this modemdata.txt, use the linmodems.org mailing list, following the instructions in modemdata.txt

good luck...

---

### Post by linuxmad on 2005-12-11
ok... this is my modemdata.txt
"DO use the following line as the email Subject Line, to alert cogent experts:
      scanModem, Ubuntu 5.10 "Breezy Badger"  kernel 2.6.12-10-686
 Occassionally reponses are blocked by an Internet Provider mail filters.
 So do in a day also check the Archived responses at [email]DISCUSS@linmodems.org[/email]
Code updated on:  2005_Oct_25
------------ --------------  System information ------------------------
 Ubuntu 5.10 "Breezy Badger" 
 on System with processor: i686
 currently under kernel:   2.6.12-10-686
 USB modem not detected.


 The kernel was assembled with compiler:  3.4.5
 with current System compiler GCC=4.0.2
    /usr/bin/gcc -> gcc-4.0
      
 The Major.Minor versions differ in the designated compiler 4.0.2 and the 3.4.5 used in kernel assembly!!"
But there must be a match on the target for driver installation, 
of gcc Major.Minor versions or kernel and drivers!!
Otherwise the drivers will fail to load with warning:
  Invalid module format!!"
See [http://linmodems.technion.ac.il/archive-fifth/msg04252.html](http://linmodems.technion.ac.il/archive-fifth/msg04252.html) 
 

Modem candidates are at PCI_buses:  0000:00:1e.3
    
Providing detail for device at  0000:00:1e.3
  with vendor-ID:device-ID
	    ----:----
Class 0703: 8086:266d   Modem: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03) (prog-if 00 [Generic])
  SubSystem 1179:0001  Toshiba America Info Systems: Unknown device 0001
	Flags: medium devsel, IRQ 20
 Checking for IRQ 20 sharing with modem.

  
                  -----PCI_IDs-------                    --CompilerVer- 
    Feature List:  Primary  Subsystem Distr  KernelVer   kernel default  CPU
 ./scanModem test 8086:266d 1179:0001 debian 2.6.12-10-686  3.4.5 4.0.2    i686
              From records, 1179:0001 has soft modem codec SIL27
 The Subsystem PCI id does not itself identify the modem Codec.
Checking for autoloaded ALSA modem drivers

  Driver snd-intel8x0m  may enable codec acquisition "

... Still i really don't know what driver to use...???
Please help:confused:

---

### Post by linuxmad on 2005-12-12
ok ... my modem uses slmodemd driver.. i installed it with apt... and still i am not able to connect ... this is my vwdial output...
"jt@ubuntu:~$ sudo wvdial
--> WvDial: Internet dialer version 1.54.0
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT679300000
--> Waiting for carrier.
ATDT679300000
CONNECT 50667
--> Carrier detected.  Waiting for prompt.
NAS6608
Proibido o acesso nao autorizado! / Unauthorized access prohibited!
login:
--> Looks like a login prompt.
--> Sending: x2091749
x2091749
Password:
--> Looks like a password prompt.
--> Sending: (password)
~~[7f]}#@!}!t} ,}"}&} }*} } }%}&[0b][19]};[1c]}'}"}(}"}1}$}%t}3}4}!novis-access-sgbp< ~
--> PPP negotiation detected.
--> Starting pppd at Sun Dec 11 21:30:25 2005
--> pid of pppd: 9346
--> Using interface ppp0
--> Using interface ppp0
--> Disconnecting at Sun Dec 11 21:30:31 2005
--> The PPP daemon has died: PPP negotiation failed (exit code = 10)
--> man pppd explains pppd error codes in more detail.
--> I guess that's it for now, exiting
--> The PPP daemon has died. (exit code = 10)
jt@ubuntu:~$

... can someone help please...

---

### Post by Ubuntuud on 2006-01-04
Hi, I'm planning on buying the same laptop. Would you recommend it or weren't you satisfied? The biggest thing that concerns me is that the laptop testers said that the sleep-function didn't work (the computer would freeze if you started it again). Is this true?

---

