---
title: "How do I get lircmd to work?"
date: 2010-07-26
forum: Hardware
---

### Post by regneva on 2010-07-26
I've installed lirc and it works fine. However, when I start the service lircmd does not get started.

```

neo@matrix:~$ sudo service lirc restart
 * Stopping remote control daemon(s): LIRC                               [ OK ] 
 * Loading LIRC modules                                                  [ OK ] 
 * Starting remote control daemon(s) : LIRC                              [ OK ] 
neo@matrix:~$ 

```

lircd starts up on boot time and works fine, but lircmd and irexec are never started.

```

neo@matrix:~$ ps -ef | grep lirc
root      4717     1  0 13:53 ?        00:00:00 /usr/sbin/lircd --output=/var/run/lirc/lircd --device=/dev/lirc0
neo    4876  4457  0 14:01 pts/0    00:00:00 grep --color=auto lirc
neo@matrix:~$
ps -ef | grep irexec
neo    4878  4457  0 14:02 pts/0    00:00:00 grep --color=auto irexec
neo@matrix:~$

```

Furthermore, if I start lircmd separately, and run cat /dev/lircm it is getting the keypresses on my remote. But even if I restart gdm, the mouse never works.

I've created symlink /dev/lircm as follows:

```

neo@matrix:~$ ls -al /dev/lirc*
crw-rw---- 1 root root 61, 0 2010-07-26 12:49 /dev/lirc0
lrwxrwxrwx 1 root root    19 2010-07-26 13:53 /dev/lircd -> /var/run/lirc/lircd
lrwxrwxrwx 1 root root    19 2010-07-26 13:16 /dev/lircm -> /var/run/lirc/lircm

```

My lircd.conf is as follows:

```

begin remote

    name  XboxDVDDongle
    bits           8

    begin codes

        SELECT         0x0b
        UP             0xa6
        DOWN           0xa7
        RIGHT          0xa8
        LEFT           0xa9
        INFO           0xc3
        9              0xc6
        8              0xc7
        7              0xc8
        6              0xc9
        5              0xca
        4              0xcb
        3              0xcc
        2              0xcd
        1              0xce
        0              0xcf
        DISPLAY        0xd5
        BACK           0xd8
        SKIP-          0xdd
        SKIP+          0xdf
        STOP           0xe0
        REVERSE        0xe2
        FORWARD        0xe3
        TITLE          0xe5
        PAUSE          0xe6
        PLAY           0xea
        MENU           0xf7

    end codes
end remote

```

Hardware.conf is:

```

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="XBOX DVD PLayback Kit"
REMOTE_MODULES="lirc_dev lirc_atiusb"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="/etc/lirc/lircd.conf"
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

#Enable irexec
START_IREXEC="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="true"

# Default configuration files for your hardware if any
LIRCMD_CONF="/etc/lirc/lircmd.conf"

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD="true"
REMOTE_SOCKET=""
TRANSMITTER_SOCKET=""

```

lircmd.conf is:

```

#UNCONFIGURED
#
# To find out how to get a proper configuration file please read:
# 
#	/usr/share/doc/lirc/README.Debian

# lircmd config file
#

PROTOCOL IntelliMouse

# ACCELERATOR start max multiplier

ACCELERATOR 2 30 5

MOVE_N XboxDVDDongle 2
MOVE_S XboxDVDDongle 5
MOVE_E XboxDVDDongle 3
MOVE_W XboxDVDDongle 1

BUTTON1_CLICK XboxDVDDongle 4
BUTTON2_CLICK XboxDVDDongle 6
# BUTTONx_CLICK, BUTTONx_UP, BUTTONx_DOWN are also possible

# add to xorg.conf and uncomment

```

xorg.conf is as follows:

```

Section "ServerLayout"
Identifier "MyLayout"
screen "Default Screen"
InputDevice "LIRC-Mouse" "CorePointer"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

Section "InputDevice"
	Identifier	"LIRC-Mouse"
    Driver "mouse"
    Option "Device" "/dev/lircm"
    Option "Protocol" "IntelliMouse"
    Option "SendCoreEvents"
    Option "Buttons" "5"
    Option "ZAxisMapping" "4 5"
EndSection

```

What am I doing wrong? Any help is greatly appreciated!

---

### Post by regneva on 2010-07-27
Bump!

---

### Post by regneva on 2010-07-27
I isolated the lircmd not starting to "#UNCONFIGURED" line on lircmd.conf. The init script specifically checks for this line and if it is present it does not start the lircmd.

Now lircmd is started normally when the computer boots. But the /dev/lircm is still not created and even if manually create it as ln -s /var/run/lirc/lircm /dev the mouse still doesn't work. 

Any pointers, ideas?

Thanks in advance..

**Update:**

Tried solution here: [http://ubuntuforums.org/showthread.php?t=1329662&page=2]("http://ubuntuforums.org/showthread.php?t=1329662&page=2"). It did not work. cat /var/run/lirc/lircm shows some activity when I press the right buttons, but I still can't get the mouse pointer to move on X :(

Now I am using xautomation as a kludge. More here: [http://flavor8.com/index.php/2010/02/24/how-to-control-the-mouse-pointer-with-a-remote-control/]("http://flavor8.com/index.php/2010/02/24/how-to-control-the-mouse-pointer-with-a-remote-control/")

If anyone knows a proper way to solve lircm issue, it's greatly appreciated.

---

