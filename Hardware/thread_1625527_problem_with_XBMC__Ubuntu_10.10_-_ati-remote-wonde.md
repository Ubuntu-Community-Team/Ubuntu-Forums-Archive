---
title: "problem with XBMC  Ubuntu 10.10 - ati-remote-wonder"
date: 2010-11-19
forum: Hardware
---

### Post by juanalvarez9 on 2010-11-19
hi everybody, I'm having this problem with Lirc and a x10 remote on Ubuntu 10.10. So maybe u can help me because I have like three weeks trying to get this to work.

So here is the thing, I've installed lirc and when it ask me for my remote I choose ATI/NVidia/X10 RF Remote (userspace), and I can see the output on irw. THE PROBLEM is that any button I press generate 4 entries in the irw output, something like this:

```
00000014d10c0000 00 chdown ati_remote_wonder_rf
00000014d10c0000 01 chdown ati_remote_wonder_rf
00000014d10c0000 02 chdown ati_remote_wonder_rf
00000014d10c0000 03 chdown ati_remote_wonder_rf
00000014d10c0000 04 chdown ati_remote_wonder_rf
```

So, when I go to XBMC (The principal reason for this) every action its performed twice, so I can't do almost anything. I have read Like 1000 post, but a i'm almost Linux-noob so I don't now what i'm doing with all the post I've read.

OK that's it! Please Excuse me for interrupt you guys and for my poor-english so I hope maybe you could help me.

for the matters my specs:
ubuntu 10.10
my remote is a UR88A but the ati_remote_wonder_rf just recognize all the keys except for two so no problem,

ok this is it, thx for reading (if you do so xD) and any help will be greatly appreciated!

PS: Here are my config files:

```

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="ATI/NVidia/X10 RF Remote (userspace)"
REMOTE_MODULES=""
REMOTE_DRIVER="atilibusb"
REMOTE_DEVICE=""
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="atiusb/lircd.conf.atilibusb"
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

#Configuration for the ATI/NVidia/X10 RF Remote (userspace) remote:
include "/usr/share/lirc/remotes/atiusb/lircd.conf.atilibusb"

```

The Lircmap.xsl and remote.xsl (XBMC) I don't think u need them beacuse every key I press it's recognized. Every thing u need please tell me, thank you for the help!

---

### Post by kaburliic on 2010-11-19
Hi

I have exactly the same problem.

I solved it only for XBMC :
I create the following file ~/.xbmc/userdata/advancedsettings.xml.

The content :
```

<advancedsettings>
    <remotedelay>5</remotedelay>
    <remoterepeat>650</remoterepeat>
</advancedsettings>

```

Hope it can help you.

---

### Post by juanalvarez9 on 2010-11-19
It Works! I'm very pleased with your response! thank you, now I can enjoy my home-made HTPC xD... 

thanks again!

---

