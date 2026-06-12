---
title: "[SOLVED] Ubuntu 18.04 vs -- cp210x issues with usb ports (multiple devices)"
date: 2019-04-17
forum: Hardware
---

### Post by mstrozier on 2019-04-17
Good morning all.  I am currently using Ubuntu 18.04.02 LTS release.   The problem I am running into is using multiple usb devices that uses the cp210x.  It seems to disconnect from one usb port and connect to the other then back again over and over when I put them to use.  I have a futurebit moonlander 2 and a gekkoscience newpac for crypto mining. (for tinkering mainly).   I am fairly new to using linux and still in the process of learning.   I also have a 3rd device, an Arduino Uno that I will be connecting soon for other electronic projects.  And I have a concern that this issue will possibly affect it as well.  And sadly I do not know enough to correct this.   

So testing this out and showing the output after a reboot.   When I do a lsusb I have the below info:

```
lsusb
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 10c4:ea60 Cygnal Integrated Products, Inc. CP210x UART Bridge / myAVR mySmartUSB light
Bus 001 Device 003: ID 1a40:0101 Terminus Technology Inc. Hub
Bus 001 Device 002: ID 1a40:0201 Terminus Technology Inc. FE 2.1 7-port Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 011 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 010 Device 003: ID 0403:6015 Future Technology Devices International, Ltd Bridge(I2C/SPI/UART/FIFO)
Bus 010 Device 002: ID 2109:3431 VIA Labs, Inc. Hub
Bus 010 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 002: ID 2109:3431 VIA Labs, Inc. Hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

Moonlander is on Device 004.   Gekko Newpac is on Device03


Next I run the following command:  dmesg | grep ttyUSB 

```
$ dmesg | grep ttyUSB 
[   18.831492] usb 1-5.7.4: cp210x converter now attached to ttyUSB0
[ 1467.234808] usb 10-1.1: FTDI USB Serial Device converter now attached to ttyUSB1
```

Again so far this looks correct.  ttyUSB0 is the Moonlander and ttyUSB1 is the Gekko.

Now when I launch the mining software on the moonlander with the gekko newpac not being used but plugged in, I get the following when I run the dmesg command again:

```
$ dmesg | grep ttyUSB 
[   18.831492] usb 1-5.7.4: cp210x converter now attached to ttyUSB0
[ 1467.234808] usb 10-1.1: FTDI USB Serial Device converter now attached to ttyUSB1
[ 2031.856874] ftdi_sio ttyUSB1: failed to set flow control: -110
[ 2031.857228] ftdi_sio ttyUSB1: FTDI USB Serial Device converter now disconnected from ttyUSB1
```



Next if I launch the gekko miner it will crash the moonlander as this cp210x will then alternate between the two ttyusb0 and ttyusb1 and disconnecting from each other.   I sadly do not know enough on how to correct this?  Any help is appreciated as I believe running any Arduino IDE uploads to my uno on this same machine while these are attemping to run will also create problems.   So trying to fix this before I attach and start the next.   Right now I'm switching the Arduino over to my windows 10 machine.  But would prefer to use Ubuntu as it'll also help getting me used to operating off Linux.

Thanks for any help.

```
dmesg | grep ttyUSB 
[   18.831492] usb 1-5.7.4: cp210x converter now attached to ttyUSB0
[ 1467.234808] usb 10-1.1: FTDI USB Serial Device converter now attached to ttyUSB1
[ 2031.856874] ftdi_sio ttyUSB1: failed to set flow control: -110
[ 2031.857228] ftdi_sio ttyUSB1: FTDI USB Serial Device converter now disconnected from ttyUSB1
[ 2370.645128] cp210x ttyUSB0: cp210x converter now disconnected from ttyUSB0
[ 2370.656469] usb 1-5.7.4: cp210x converter now attached to ttyUSB1
[ 2370.656717] cp210x ttyUSB1: cp210x converter now disconnected from ttyUSB1
[ 2370.666930] usb 1-5.7.4: cp210x converter now attached to ttyUSB1
[ 2370.667142] cp210x ttyUSB1: cp210x converter now disconnected from ttyUSB1
[ 2370.679542] usb 1-5.7.4: cp210x converter now attached to ttyUSB1
[ 2370.679730] cp210x ttyUSB1: cp210x converter now disconnected from ttyUSB1
[ 2370.688799] usb 1-5.7.4: cp210x converter now attached to ttyUSB1
[ 2370.688996] cp210x ttyUSB1: cp210x converter now disconnected from ttyUSB1
[ 2370.698726] usb 1-5.7.4: cp210x converter now attached to ttyUSB1
[ 2370.698898] cp210x ttyUSB1: cp210x converter now disconnected from ttyUSB1
[ 2370.708106] usb 1-5.7.4: cp210x converter now attached to ttyUSB1
[ 2375.933671] cp210x ttyUSB1: cp210x converter now disconnected from ttyUSB1
[ 2375.943977] usb 1-5.7.4: cp210x converter now attached to ttyUSB2
[ 2375.944487] cp210x ttyUSB2: cp210x converter now disconnected from ttyUSB2
[ 2375.954261] usb 1-5.7.4: cp210x converter now attached to ttyUSB2
[ 2375.954632] cp210x ttyUSB2: cp210x converter now disconnected from ttyUSB2
[ 2375.964397] usb 1-5.7.4: cp210x converter now attached to ttyUSB2
[ 2375.964632] cp210x ttyUSB2: cp210x converter now disconnected from ttyUSB2
[ 2375.973780] usb 1-5.7.4: cp210x converter now attached to ttyUSB2
[ 2375.973936] cp210x ttyUSB2: cp210x converter now disconnected from ttyUSB2
[ 2375.984056] usb 1-5.7.4: cp210x converter now attached to ttyUSB2
[ 2375.984237] cp210x ttyUSB2: cp210x converter now disconnected from ttyUSB2
[ 2375.993478] usb 1-5.7.4: cp210x converter now attached to ttyUSB2
```

---

### Post by mstrozier on 2019-04-17
Actually thinking this possibly can't be done.  As the driver attaches to one usb port.   Same occurs in windows :/   So I may have to break these projects out among multiple boxes.

---

### Post by mstrozier on 2019-04-17
Disregard, solved my issue with some help.

---

### Post by mstrozier on 2019-04-24
Wanted to post up some notes in case it will benefit anyone else.  I updated my notes in bitcointalk forums however forgot to update it here.   Basic summary, if you are running multiple usb devices as in my case Futurebit Moonlander 2's and GekkoScience newpac's, you have to specific the actual device.  Don't let the system/miner attempt to auto find them as they will end up crossing each other and then disabling the port.  Below is what I did for one of each device.   Hope it helps:

[COLOR=#000000][FONT=verdana]

I'm posting up the below in case it helps any of the others using both Gekko Newpac's and Moonlanders on the same ubuntu  system.[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]First run the following command:  dmesg | grep ttyUSB[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]I have currently only 1 gekkoscience newpac and 1 moonlander on this system tinkering with.  They are on the same USB hub (a 10 port powered hub) and are shown attached to the following USB ports:[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]dmesg | grep ttyUSB[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana][   18.635808] usb 1-5.5: FTDI USB Serial Device converter now attached to ttyUSB0[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana][   19.749267] usb 1-5.7.4: cp210x converter now attached to ttyUSB1[/FONT][/COLOR]


[COLOR=#000000][FONT=verdana]So based on above, the cp210x (moonlander using) is on USB1.  The Newpac is on USB0.[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]Now, inside the folder where I installed the moonlander mining software I created a miner_verge.sh file to run the following command:[/FONT][/COLOR]


[COLOR=#000000][FONT=verdana]./bfgminer --scrypt -o stratum+tcp://xvg.mastermining.net:3181#skipcbcheck -u username.workername -p x -S /dev/ttyUSB1 --set MLD:clock=700[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]Listed above I have bfgminer pointed to pool mastermining mining Verge coin.   You would insert your username.worker to whatever pool you are connected to  add -S /dev/ttyUSB1 in this example as the Moonlander Miner is on USB1.   After saved and made the .sh executable just type sudo ./miner.verge.sh and now it is mining.[/FONT][/COLOR]


[COLOR=#000000][FONT=verdana]Next is to configure the gekko newpac miner.  Right now I have a script in it's directory called miner_prohashing.sh that I was using as a testing pool.  Below is the code in the script:[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]./cgminer -o stratum+tcp://prohashing.com:3335 -u username -p x --usb 1:3 --gekko-newpac-freq 200 --gekko-newpac-boost[/FONT][/COLOR]


[COLOR=#000000][FONT=verdana]For the gekko miners, you will need to add   --usb  bus address : device address.    So to get this information I run lsusb:[/FONT][/COLOR]


[COLOR=#000000][FONT=verdana]lsusb[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]Bus 001 Device 005: ID 10c4:ea60 Cygnal Integrated Products, Inc. CP210x UART Bridge / myAVR mySmartUSB light[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]Bus 001 Device 004: ID 1a40:0101 Terminus Technology Inc. Hub[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]Bus 001 Device 003: ID 0403:6015 Future Technology Devices International, Ltd Bridge(I2C/SPI/UART/FIFO)[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]Bus 001 Device 002: ID 1a40:0201 Terminus Technology Inc. FE 2.1 7-port Hub[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]Bus 011 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]Bus 010 Device 002: ID 2109:3431 VIA Labs, Inc. Hub[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]Bus 010 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]Bus 008 Device 002: ID 2109:3431 VIA Labs, Inc. Hub[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]Here I am looking for the ltd bridge(I2C/SPI/UART/FIFO) as this one is the Gekko Miner.  It is on Bus 001 and Device 003.  So in my miner statement above, I keyed --usb 1:3 so that it will know which of the usb sticks to use for cgminer.[/FONT][/COLOR]



[COLOR=#000000][FONT=verdana]If you are running multiple sticks say 4 moonlanders and 4 gekko's you may have to tweak a little more with this.  I believe with the Gekko's you would extend the --usb command so if I had 2 more in usb 4 and 5 and they were all on Bus 1 then I would have --usb 1:3,1:4,1:5 if I am understanding the readme file correctly.[/FONT][/COLOR]

---

