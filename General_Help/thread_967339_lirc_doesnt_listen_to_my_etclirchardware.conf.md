---
title: "lirc doesnt listen to my /etc/lirc/hardware.conf"
date: 2008-11-01
forum: General Help
---

### Post by Keithamus on 2008-11-01
Lirc has been a big pain in the *** for me, in reinstalling my mythbuntu box. It worked fine beforehand, after a bit of hacking with the events, but its not working so great now.

Running sudo lircd -n, or lircd -n /etc/lirc/hardware.conf, then irw gives me this

```
lircd-0.8.3[9389]: lircd(userspace) ready
lircd-0.8.3[9389]: accepted new client on /dev/lircd
lircd-0.8.3[9389]: could not get hardware features
lircd-0.8.3[9389]: this device driver does not support the new LIRC interface
lircd-0.8.3[9389]: major number of /dev/lirc is 13
lircd-0.8.3[9389]: LIRC major number is 61
lircd-0.8.3[9389]: check if /dev/lirc is a LIRC device
lircd-0.8.3[9389]: caught signal
Terminated

```

If I manually specify my driver/device like so:
sudo lircd -n --device=/dev/lirc --driver=dev/input
then it works perfectly.

Below is my hardware.conf
```

# /etc/lirc/hardware.conf                     
#                                             
#Chosen Remote Control                        
REMOTE="Hauppauge Nova-T 500"                 
REMOTE_MODULES=""                             
REMOTE_DRIVER="devinput"                      
REMOTE_DEVICE="/dev/lirc"                     
REMOTE_LIRCD_CONF="hauppauge/lircd.conf.hauppauge_novat500"
REMOTE_LIRCD_ARGS=""                                       

#Chosen IR Transmitter
TRANSMITTER="None"    
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER="" 
TRANSMITTER_DEVICE="" 
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

---

### Post by rich86 on 2008-11-02
I'm having a similar problem after reinstalling Intrepid LIRC doesn't seem to be working properly. It is not reconsing my .lircrc file in home directory and no applications are reconising commands. The only button that does work is the power-off button which goes and shuts down my computer.

Any help would be much appreciated also.

---

### Post by Keithamus on 2008-11-02
You can debug whats happening with your remote by doing the following:

1. Open up 2 terminal windows (Applications -> Accessories -> Terminal)
2. In one, type the following:
```
sudo /etc/init.d/lirc stop
sudo lircd -n /etc/lirc/hardware.conf
```
3. If all goes well, it should stay open (i.e you wont be put back to :~$) now, in the second terminal, type "irw" and press enter.
4. Look at the first terminal, is it still running? Has it crashed? If it has crashed, paste the log output here.
5. If it hasnt crashed, start pressing buttons on your remote. do you see buttons comming up in the 2nd terminal winodw (the one with irw)?

---

### Post by rich86 on 2008-11-03
Sorry to hi-jack this thread but this is my output:
```
:~$ sudo lircd -n /etc/lirc/hardware.conf
lircd-0.8.3[9220]: error in configfile line 3
lircd-0.8.3[9220]: reading of config file failed
lircd-0.8.3[9220]: lircd(userspace) ready
lircd-0.8.3[9220]: accepted new client on /dev/lircd
lircd-0.8.3[9220]: could not get file information for /dev/lirc
lircd-0.8.3[9220]: default_init(): No such file or directory
lircd-0.8.3[9220]: caught signal
Terminated

```

I don't think there is an error in my hardware.conf file but here it is:
```
:~$ cat /etc/lirc/hardware.conf
# /etc/lirc/hardware.conf
#Chosen Remote Control
REMOTE="MSI"
REMOTE_MODULES=""
REMOTE_DRIVER="dev/input"
REMOTE_DEVICE="/dev/input/by-path/pci-1-5--event-ir"
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
RECEIVER_MODEL="AT Translated Set 2 keyboard"
RECEIVER_VENDOR="Linux Input Device"

# Remote settings required by gnome-lirc-properties
REMOTE_MODEL="Linux Input Layer compatible Remote"
REMOTE_VENDOR="Generic"

```
Thanks for any help in advance

---

### Post by Keithamus on 2008-11-03
Try running this command:

```
sudo lircd -n --device=/dev/input/by-path/pci-1-5--event-ir --driver=dev/input
```

If this doesnt spit any errors, try typing irw in a new terminal and testing your remote. If lircd doesnt crash, then your setup works fine, its just your configfile. If it does work fine, then try running the actual daemon that runs on starup:

```
sudo /etc/init.d/lirc start
```

Try running irw after this, and if it works youre fine. As Ive found out, since writing the original post, theres something dodgy with running lircd manually - I get errors in my configfile, and it wont work at all, but running the daemon (sudo /etc/init.d/lirc start) works fine.

---

### Post by rich86 on 2008-11-03
both these commands work fine but when running irw i get no signals. I have also noticed that running: ```
sudo evtest /dev/input/by-path/pci-1-5--event-ir 

Input driver version is 1.0.0
Input device ID: bus 0x3 vendor 0xdb0 product 0x5580 version 0x95
Input device name: "IR-receiver inside an USB DVB receiver"
Supported events:
  Event type 0 (Reset)
    Event code 0 (Reset)
    Event code 1 (Key)
  Event type 1 (Key)
    Event code 113 (Mute)
    Event code 114 (VolumeDown)
    Event code 115 (VolumeUp)
    Event code 116 (Power)
    Event code 119 (Pause)
    Event code 128 (Stop)
    Event code 139 (Menu)
    Event code 152 (Coffee)
    Event code 154 (CycleWindows)
    Event code 167 (Record)
    Event code 168 (Rewind)
    Event code 208 (?)
    Event code 212 (?)
    Event code 352 (Ok)
    Event code 402 (ChannelUp)
    Event code 403 (ChannelDown)
Testing ... (interrupt to exit)


``` 

and pressing remote buttons does not result in any signals. Also with the mouse and keyboard running:
```

richard@richards:~$ sudo evtest /dev/input/by-path/platform-i8042-serio-1-event-mouse 
Input driver version is 1.0.0
Input device ID: bus 0x11 vendor 0x2 product 0x6 version 0x0
Input device name: "ImExPS/2 Generic Explorer Mouse"
Supported events:
  Event type 0 (Reset)
    Event code 0 (Reset)
    Event code 1 (Key)
    Event code 2 (Relative)
  Event type 1 (Key)
    Event code 272 (LeftBtn)
    Event code 273 (RightBtn)
    Event code 274 (MiddleBtn)
    Event code 275 (SideBtn)
    Event code 276 (ExtraBtn)
  Event type 2 (Relative)
    Event code 0 (X)
    Event code 1 (Y)
    Event code 6 (HWheel)
    Event code 8 (Wheel)
Testing ... (interrupt to exit)

```
results in no signals so its looking more like an event problem.

Any thoughts?

---

### Post by Hyper Tails on 2008-11-04
I need help with my asus digital home remote too in ubuntu

I select the correct setting and still don't work

---

### Post by rich86 on 2008-11-14
It apears the problem is related to this bug: [https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/164627](https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/164627)
Whether this will get fixed for Intrepid i have no idea, anyone else any the wiser when the new version of LIRC will be released?

---

