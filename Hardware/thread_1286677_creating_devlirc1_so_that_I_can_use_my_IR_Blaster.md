---
title: "creating /dev/lirc1 so that I can use my IR Blaster"
date: 2009-10-09
forum: Hardware
---

### Post by markdavidoff on 2009-10-09
I have an IR Reciever that works great at my first serial port ttyS0

I just installed 2 more serial ports via PCI card. I have an IR Blaster installed at ttyS2

echo "TEST TEST" >> /dev/ttyS2

makes the IR LED light up, so It is confirmed working.

Now, for the problem...I need to get it to work with LIRC as an IR Blaster.

/dev/lirc0 exists, but /dev/lirc1 does not, which is the problem

I did dpkg-reconfigure lirc

and selected Homebrew Serial IR Reciever
and Custom as the IR Blaster

How can I get /dev/lirc1 to be created?

I will paste my hardware.conf below. My lircd.conf and lircd1.conf files just have the include "<remote config file>" lines, so I will not bother pasting them.

```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Home-brew (16x50 UART compatible serial port)"
REMOTE_MODULES="lirc_dev lirc_serial"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="/home/myth/WinfastTV2000DeluxeAus"
REMOTE_LIRCD_ARGS="/etc/lirc/lircd.conf"

#Chosen IR Transmitter
TRANSMITTER="Serial Port (UART)"
TRANSMITTER_MODULES="lirc_dev lirc_serial"
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE="/dev/lirc1"
TRANSMITTER_LIRCD_CONF="/home/myth/FoxtelDigital"
TRANSMITTER_LIRCD_ARGS="/etc/lirc/lircd1.conf"

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

I also noted that when I added the line
TRANSMITTER_DEVICE="/dev/lirc1

in the hardware.conf, it created /dev/lircd1 , which wasn't there before...but I still need /dev/lirc1 to be created

---

### Post by markdavidoff on 2009-10-11
Since I wasn't getting any help here, I decided to email the maintainer of LIRC. I got a reply quite fast. Kudos to him for that.

> "Because lirc_serial only supports one interface. It would require a major 
change to the driver to add support for multiple interfaces.
You can still make it work by compiling two different instances of 
lirc_serial with different MAJOR number settings and by renaming the 
second instance to e.g. lirc_serial2.
Currently there is no other easy setup option."

Perhaps this time, someone can help me out with this?

---

### Post by markdavidoff on 2009-10-13
Bump!
Come on...I know people have done this before!

---

### Post by Don Giovanni on 2009-10-25
Hi markdavidoff
Have you had any luck sorting this out? I am having a similar problem.

Currently on my machine only devices on /dev/lirc0 work (previously both lirc0 and lirc1 worked fine).

If I set my remote to /dev/lirc0 (using REMOTE_MODULES="lirc_dev lirc_i2c")
and my transmitter to /dev/lirc1 (using TRANSMITTER_MODULES="lirc_dev lirc_serial")

the remote on lirc0 with work but the ir transmitter won't.  If I go into to hardware.conf and switch them (remote is /dev/lirc1 and transmitter is /dev/lirc0) the transmitter will work but the remote will not.

So for some reason lirc1 isn't being created or isn't being looked at?
So I think the problem is greater than you just needing two instances of lirc_serial...

---

### Post by markdavidoff on 2009-10-26
No. I did not figure it out, but my problem is different to yours. My problem is that lirc will only work for ONE serial driver.

It seems you have a serial, and something else, so you should be getting two lirc devices

please paste your hardware.conf file and the output to ls /dev/lirc* and maybe i can help you out

---

### Post by Don Giovanni on 2009-10-26
I have my own thread open here [http://ubuntuforums.org/showthread.php?t=1301052](http://ubuntuforums.org/showthread.php?t=1301052) if you don't mind taking a look at it.
I'll keep the info there rather than hijack your thread.

---

### Post by sbradley07 on 2010-03-31
Sorry to resurrect this thread, but it describes the exact issue I am having, and I suspect it is the root of the problem I am having with my IR blaster.  

MD - did you ever resolve it?  I have the same issue with the missing device /dev/lirc1, though I am using a **USB** IR receiver and a IR Blaster that connects to the back of the receiver by a 1/8" jack.  It's a Hauppauge HVR-1600 tuner.  With this setup, there is technically only one device (the receiver) that connects to the PC.  After I configure the remote and blaster thru Myth Control Centre, the hardware.conf file defines the remote and transmitter as REMOTE_DEVICE="/dev/lirc0"
 and TRANSMITTER_DEVICE="/dev/lirc1".  However, "ls -l /dev/licr*" only gives:

crw-rw---- 1 root root 61, 0 date-time /dev/lirc0
lrwxrwxrwx 1 root root    19 date-time /dev/lircd -> /var/run/lirc/lircd
lrwxrwxrwx 1 root root    20 date-time /dev/lircd1 -> /var/run/lirc/lircd1

There's no /dev/lirc1.

The problem:  If I use irsend from a command line or a script, it works fine, but if I use the remote control, the signal does not fire the IR blaster, so I can't change channels on the set top box.  

Does anyone know if my problem has to do with the missing /dev/lirc1 or might it be something else entirely?

---

