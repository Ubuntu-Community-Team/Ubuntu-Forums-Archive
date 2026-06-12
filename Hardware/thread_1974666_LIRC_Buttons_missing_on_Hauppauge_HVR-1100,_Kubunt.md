---
title: "LIRC: Buttons missing on Hauppauge HVR-1100, Kubuntu 12.04"
date: 2012-05-06
forum: Hardware
---

### Post by lvancleef on 2012-05-06
Hi Ubuntu Forum,

I am trying to use my remote Hauppauge HVR-1100 with lirc on Kubuntu 12.04. Testing with irw is fine, except that three buttons are not recognised:

  - power,
  - Pictures,
  - Ok.

```

$ irw
000000008001006c 00 Down HVR-1100
0000000080010067 00 Up HVR-1100
0000000080010069 00 Left HVR-1100
000000008001006a 00 Right HVR-1100
...

```Here is my configuration:

```

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Hauppauge HVR-1100"
REMOTE_MODULES="devinput"
REMOTE_DRIVER="devinput"
REMOTE_DEVICE="/dev/input/by-path/pci-0000:05:01.0-event-ir"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="hauppauge/lircd.conf.hauppauge"
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
LOAD_MODULES="false"

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

```And /etc/lirc/lircd.conf:

```

#This configuration has been automatically generated via
#the Ubuntu LIRC package maintainer scripts.
#
#It includes the default configuration for the remote and/or
#transmitter that you have selected during package installation.
#
#Feel free to add any custom remotes to the configuration
#via additional include directives or below the existing
#Ubuntu include directives from your selected remote and/or
#transmitter.

#Configuration for the Hauppauge HVR-1100 remote:
include "/usr/share/lirc/extras/more_remotes/hauppauge/lircd.conf.hauppauge"

```How can I make the missing three buttons work?

Thanks for your help!

---

### Post by lvancleef on 2012-05-06
All buttons of the remote control can be used if this /etc/lirc/lircd.conf is used:

```

#This configuration has been automatically generated via
#the Ubuntu LIRC package maintainer scripts.
#
#It includes the default configuration for the remote and/or
#transmitter that you have selected during package installation.
#
#Feel free to add any custom remotes to the configuration
#via additional include directives or below the existing
#Ubuntu include directives from your selected remote and/or
#transmitter.

#Configuration for the Hauppauge HVR-1100 remote:
#include "/usr/share/lirc/extras/more_remotes/hauppauge/lircd.conf.hauppauge"
include "/usr/share/lirc/remotes/devinput/lircd.conf.devinput"

```

---

