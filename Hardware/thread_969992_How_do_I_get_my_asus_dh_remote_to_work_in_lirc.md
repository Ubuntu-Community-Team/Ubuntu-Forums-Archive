---
title: "How do I get my asus dh remote to work in lirc?"
date: 2008-11-03
forum: Hardware
---

### Post by Hyper Tails on 2008-11-03
Hi I run Interpid ibex and I want to get my remote that came with my mother board and I have installed lirc and I don't know how to get it working.

I tried all i could and still no luck.

---

### Post by Hyper Tails on 2008-11-04
helllllllo? anyone?

---

### Post by Hyper Tails on 2008-11-04
:confused:please:confused:

---

### Post by Hyper Tails on 2008-11-05
Please I really, really, really want this to work

---

### Post by anamorgan on 2008-11-05
If you have got your software installed, it should give some signs of working, contact the vendor if any hardware problems.

---

### Post by Hyper Tails on 2008-11-06
no one knows?

---

### Post by Hyper Tails on 2008-11-07
fine I don't care

---

### Post by paulo.bartos on 2011-10-05
I know this is a dead post, but I as I came here looking for the answers, I will post what I did to make the asus dh remote work with ubuntu server 11.04.


1) the latest lirc does not need kernel module for this remote ( as stated in the link below) 

[http://www.lirc.org/html/table.html](http://www.lirc.org/html/table.html)

2) plugin the receiver and make sure the command lsusb comes with the line below (witch is the remote) (in my case didn´t need to do anything)

Bus 004 Device 002: ID 1130:cc00 Tenx Technology, Inc. 

3) cat the devices /dev/usb/hiddevX (were X is the numbers you have, try the bigger ones) and press the remote buttons and check for response.

cat /dev/usb/hiddev1

&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;
                  &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;      &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;^C

theese question marks appeared after pressing the remote buttons.


4) put the device you discovered in the /etc/lirc/hardware.conf file 

```

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Asus DH USB Remote"
REMOTE_MODULES=""
REMOTE_DRIVER="asusdh"
REMOTE_DEVICE="/dev/usb/hiddev1"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="asus/lircd.conf.asusdh"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="true"

# Default configuration files for your hardware if any
LIRCMD_CONF=""

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""


```

5) restart the lirc daemon and test it with the irw

/etc/init.d/lirc restart
 * Stopping remote control daemon(s): LIRC             [ OK ] 
 * Loading LIRC modules                                [ OK ] 
 * Starting remote control daemon(s) : LIRC            [ OK ] 




/etc/lirc# irw 
ff00000000000007 00 PLUS AsusDH
ff00000000000009 00 PLAY/PAUSE AsusDH
ff0000000000000a 00 FWD AsusDH
ff00000000000008 00 REV AsusDH

---

### Post by max78 on 2012-12-27
Thanks a lot, it works! :)

---

### Post by overdrank on 2012-12-27
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

