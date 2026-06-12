---
title: "How to: Xbox DVD remote 11.04"
date: 2011-07-20
forum: Hardware
---

### Post by TrenTech on 2011-07-20
Haven't found any consistant instructions on how to do this so here it is. This is not my work it's the combination of other threads I've come across that seemed to work for me.

[LIST=1]
[*]Blacklist xpad
```
sudo nano /etc/modprobe.d/blacklist.conf
```
add:
```
blacklist xpad
```

[*]Install lirc - config menu will pop up. select none.
```
sudo apt-get install lirc
```

[*]Install lirc source modules
```
sudo apt-get install lirc-modules-source
```

[*]Configure hardware.conf
```
sudo nano /etc/lirc/hardware.conf
```
replace all and add:
```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="None"
REMOTE_MODULES="lirc_atiusb lirc_dev"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF=""
REMOTE_LIRCD_ARGS="-r"

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
LIRCMD_CONF="lircd.conf"

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="true"
START_LIRCMD=""
```
[*]configure lircd.conf
```
sudo nano /etc/lirc/lircd.conf
```
replace and add:
```
# LIRCD configuration file for Xbox DVD Kit
#
# Marko Friedemann <mfr@bmx-chemnitz.de>
#
#
# brand:             Microsoft
# model:             Xbox DVD Remote
# supported devices: Xbox DVD Remote via xpad-ir driver
#
# comment:           EXPERIMENTAL
#
begin remote

    name  XboxDVDDongle
    bits           8

    begin codes

        SELECT          0x0b
        UP              0xa6
        DOWN            0xa7
        RIGHT           0xa8
        LEFT            0xa9
        INFO            0xc3

        9               0xc6
        8               0xc7
        7               0xc8
        6               0xc9
        5               0xca
        4               0xcb
        3               0xcc
        2               0xcd
        1               0xce
        0               0xcf

        DISPLAY         0xd5
        BACK            0xd8
        SKIP+           0xdd
        SKIP-           0xdf
        STOP            0xe0
        REVERSE         0xe2
        FORWARD         0xe3
        TITLE           0xe5
        PAUSE           0xe6
        PLAY            0xea
        MENU            0xf7

      end codes

end remote
```
[*]configure modules to load at startup
```
sudo nano /etc/modules
```
add:
```
lirc_dev
lirc_atiusb
```
[*]edit lirc_dev.h
```
sudo nano /usr/src/lirc-0.8.7/drivers/lirc_dev/lirc_dev.h
```
change the line "#define LIRC_HAVE_KFIFO" to "#undef LIRC_HAVE_KFIFO"

[*]reconfigure lirc source modules
```
sudo dpkg-reconfigure lirc-modules-source
```
[*]reboot
[*]test
```
irw
```
press a button on the remote.should see something like this:
```
00000000000000a7 00 DOWN XboxDVDDongle
00000000000000a7 01 DOWN XboxDVDDongle
00000000000000a7 00 DOWN_UP XboxDVDDongle
00000000000000a7 00 DOWN XboxDVDDongle
00000000000000a7 00 DOWN_UP XboxDVDDongle
00000000000000a7 00 DOWN XboxDVDDongle
00000000000000a7 00 DOWN_UP XboxDVDDongle
00000000000000a9 00 LEFT XboxDVDDongle
00000000000000a9 00 LEFT_UP XboxDVDDongle
```

That it!

[/LIST]

---

### Post by solouko on 2011-08-02
Thanks this has been a lot of help, I've been trying to get my remote working all week, it's the only thing stopping me from installing ubuntu on my primary system.  Although, It's still not working, I've now installed and got the lirc_dev.h files and the hardwar.conf files there and set up but some things didn't work for me.  "sudo nano /etc/modprobe.d/blacklist.conf" did nothing but open up a blank file.  "sudo dpkg-recofigure lirc-modules-source" this said no such file or command  and "irw" did nothing.  Any ideas what i've done wrong? It's probably something very stupid because i've only been using ubuntu since Monday and... yes it's just turned Wednesday.

---

### Post by TrenTech on 2011-08-05
> **solouko said:**
> Thanks this has been a lot of help, I've been trying to get my remote working all week, it's the only thing stopping me from installing ubuntu on my primary system.  Although, It's still not working, I've now installed and got the lirc_dev.h files and the hardwar.conf files there and set up but some things didn't work for me.  "sudo nano /etc/modprobe.d/blacklist.conf" did nothing but open up a blank file.  "sudo dpkg-recofigure lirc-modules-source" this said no such file or command  and "irw" did nothing.  Any ideas what i've done wrong? It's probably something very stupid because i've only been using ubuntu since Monday and... yes it's just turned Wednesday.

I'm not sure why you don't see blacklist.conf. check your spelling. real easy to make small mistakes. Open file manager and navigate to /etc/modprobe.d/ or use the command: 

CODE: cd /etc/modprobe.d

make sure blacklist.conf is there. Also are you using 11.04?

Your second problem, I misspelled the command. Sorry about that

EDIT: sudo dpkg-reconfigure lirc-modules-source

If all goes well when you run command irw it will appear to do nothing, but if you press buttons on the remote you should see the results posted in this thread. took me a long time to get this working. also tested this procedure on 10.04 and 10.10 and it worked just as well.

---

### Post by cianof on 2011-10-20
Does anyone know to do this in 11.11?

I haven't been able to figure out the solution yet.

lirc-modules-source is no longer available. 

I found a few xbox patches for lirc 0.9 but could them to work.

---

### Post by BuddyLee13 on 2011-12-20
> **cianof said:**
> Does anyone know to do this in 11.11?

I haven't been able to figure out the solution yet.

lirc-modules-source is no longer available. 

I found a few xbox patches for lirc 0.9 but could them to work.

For people still looking for a solution to this in 11.10 (Oneiric), I followed the steps [here]("https://bbs.archlinux.org/viewtopic.php?id=122502") to get this working.  In a nutshell, you obtain the lirc source code, apply a patch, build a new lirc_xbox module and set your hardware.conf file to the new driver.

---

### Post by www.rzr.online.fr on 2012-05-13
related thread :

[http://ubuntuforums.org/showthread.php?p=11933104#post11933104#](http://ubuntuforums.org/showthread.php?p=11933104#post11933104#) XBoX

---

