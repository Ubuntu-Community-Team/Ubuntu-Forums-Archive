---
title: "The Remote Control does not start at boot"
date: 2016-03-31
forum: Hardware
---

### Post by choyin.wif on 2016-03-31
I have a problem with my Remote Control on Ubuntu. My problem is the next:

When you start the system and entered the desktop, the remote control does not work, lircd is loaded, IRW charge and is not recognized anything on the remote control.

Then I have to charge the terminal and load (*sudo dpkg-reconfigure lirc*) or too (*sudo /etc/init.d/lirc restart*) and when it starts to operate the remote control.

I do not know what's going on. How I can do to make the remote control work from the start of the system?

When I load (*sudo dpkg-reconfigure lirc*) or (*sudo /etc/init.d/lirc restart*) the terminal displays:
> ***@******:~$ *sudo /etc/init.d/lirc restart*
sh: echo: I/O error
sh: echo: I/O error
 * Stopping remote control daemon(s): LIRC 
 * Starting remote control daemon(s) : 


And then it works 

[B]My /etc/lirc/hardware.conf
[/B]> # /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Windows Media Center Transceivers/Remotes (all)"
REMOTE_MODULES="false"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="mceusb/lircd.conf.mceusb"
REMOTE_LIRCD_ARGS=""


#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""


#Disable kernel support.
#Typically, lirc will disable in-kernel support for ir devices in order to
#handle them internally.  Set to false to prevent lirc from disabling this
#in-kernel support. 
#DISABLE_KERNEL_SUPPORT="true"


#Enable lircd
START_LIRCD="true"


#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"


#Try to load appropriate kernel modules
LOAD_MODULES="true"


# Default configuration files for your hardware if any
LIRCMD_CONF="/etc/lirc/lircd.conf"


#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""

[B]my /etc/lirc/lircd.conf
[/B]> #This configuration has been automatically generated via
#the Ubuntu LIRC package maintainer scripts.
#
#It includes the default configuration for the remote and/or
#transmitter that you have selected during package installation.
#
#Feel free to add any custom remotes to the configuration
#via additional include directives or below the existing
#Ubuntu include directives from your selected remote and/or
#transmitter.


#Configuration for the Windows Media Center Transceivers/Remotes (all) remote:
include "/usr/share/lirc/remotes/mceusb/lircd.conf.mceusb"



Thank you

---

### Post by QDR06VV9 on 2016-03-31
I used this method: [http://ubuntuforums.org/showthread.php?t=1637530](http://ubuntuforums.org/showthread.php?t=1637530)
**But one thing is a must the kernel has to recognise your your IR sensor.**
but that dose not appear to be a problem for you.

---

### Post by choyin.wif on 2016-03-31
> **runrickus said:**
> I used this method: [http://ubuntuforums.org/showthread.php?t=1637530](http://ubuntuforums.org/showthread.php?t=1637530)
**But one thing is a must the kernel has to recognise your your IR sensor.**
but that dose not appear to be a problem for you.

It does not work, thanks for your help *runrickus*.

---

