---
title: "Can't get lirc working anymore."
date: 2009-04-15
forum: Hardware
---

### Post by Captain_Glen on 2009-04-15
Hi,

I have a DigitalNow TinyTwin tv recorder/ir reciever [http://www.digitalnow.com.au]("http://www.digitalnow.com.au")

I had it working using the GUI Infrared Remote Control program.  But it had an error saying the lirc daemon was not running even though the buttons worked.

Now it still has the error and the buttons don't work anymore.  I don't know what I did to change it.  The only major system changes I made was trying unsuccessfully to get my eye toy working.


When I try to start the lirc daemon I get:
```
glen@glen-desktop:~$ sudo /etc/init.d/lirc start
 * Loading LIRC modules                                                  [ OK ] 
 * Unable to load LIRC kernel modules. Verify your
 * selected kernel modules in /etc/lirc/hardware.conf
glen@glen-desktop:~$
```

Checking /etc/lirc/hardware.conf I get:
```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="None"
REMOTE_MODULES="lirc_serial"
REMOTE_DRIVER="devinput"
REMOTE_DEVICE="/dev/input/event2"
REMOTE_LIRCD_CONF=""
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD=true

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

# Receiver settings required by gnome-lirc-properties
RECEIVER_MODEL="Afatech DVB-T 2"
RECEIVER_VENDOR="Linux Input Device"

# Remote settings required by gnome-lirc-properties
REMOTE_MODEL="Linux Input Layer compatible Remote"
REMOTE_VENDOR="Generic"
```

And finally dmesg:
```
glen@glen-desktop:~$ dmesg | grep lirc
[   66.839927] lirc_dev: IR Remote Control driver registered, at major 61 
[   66.849795] lirc_serial: port 03f8 already in use
[   66.849801] lirc_serial: use 'setserial /dev/ttySX uart none'
[   66.849802] lirc_serial: or compile the serial port driver as module and
[   66.849804] lirc_serial: make sure this module is loaded first
[  188.720569] lirc_serial: port 03f8 already in use
[  188.720574] lirc_serial: use 'setserial /dev/ttySX uart none'
[  188.720576] lirc_serial: or compile the serial port driver as module and
[  188.720578] lirc_serial: make sure this module is loaded first
[  309.931919] lirc_serial: port 03f8 already in use
[  309.931925] lirc_serial: use 'setserial /dev/ttySX uart none'
[  309.931927] lirc_serial: or compile the serial port driver as module and
[  309.931928] lirc_serial: make sure this module is loaded first
[ 1102.588368] lirc_serial: port 03f8 already in use
[ 1102.588374] lirc_serial: use 'setserial /dev/ttySX uart none'
[ 1102.588375] lirc_serial: or compile the serial port driver as module and
[ 1102.588377] lirc_serial: make sure this module is loaded first
[ 1281.383826] lirc_serial: port 03f8 already in use
[ 1281.383831] lirc_serial: use 'setserial /dev/ttySX uart none'
[ 1281.383833] lirc_serial: or compile the serial port driver as module and
[ 1281.383834] lirc_serial: make sure this module is loaded first
[ 1448.196102] lirc_serial: port 03f8 already in use
[ 1448.196108] lirc_serial: use 'setserial /dev/ttySX uart none'
[ 1448.196109] lirc_serial: or compile the serial port driver as module and
[ 1448.196111] lirc_serial: make sure this module is loaded first

```

---

### Post by Captain_Glen on 2009-04-16
Arg!  Linux is really getting annoying.  For no apparent reason it is working again.  I wish I knew wheat I did!

---

### Post by Shig on 2009-07-31
Hi

The error you are getting loading lirc_serial is because the lirc_serial module tries to access a physical serial port, which in your case is apparently tied up already.

The TinyTwin seems to be USB, so you don't need lirc_serial, and could most likely change the line 
```
REMOTE_DRIVER="lirc_serial"
```...to...
```
REMOTE_DRIVER=""
```...and have it work just fine.

---

