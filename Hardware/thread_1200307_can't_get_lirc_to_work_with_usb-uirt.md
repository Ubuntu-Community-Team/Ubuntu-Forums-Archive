---
title: "can't get lirc to work with usb-uirt"
date: 2009-06-29
forum: Hardware
---

### Post by ToddW7 on 2009-06-29
I have a usb-uirt receiver plugged in, running 9.04 and I can't get lirc to work.  The model of the usb-uirt is usbuirt0038z.  It worked as a plug and play device under linuxmce, so I know it works.  I have followed the guide at [https://help.ubuntu.com/community/Lirc_USB-UIRT](https://help.ubuntu.com/community/Lirc_USB-UIRT) but no success.  When I type irw at the command line, it waits for my input.  I use various remotes and press buttons on them and the red light on the usb-uirt lights up at each button press, but nothing shows up in the terminal.

Here is what I have done:
installed lirc with synapatic package manager
at command line I typed: dmesg | grep -i usb which gave me:
[    0.458589] usbcore: registered new interface driver usbfs
[    0.458589] usbcore: registered new interface driver hub
[    0.458589] usbcore: registered new device driver usb
[    4.909256] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    4.909652] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 1
[    4.920018] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00
[    4.920077] usb usb1: configuration #1 chosen from 1 choice
[    4.920100] hub 1-0:1.0: USB hub found
[    4.920196] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    4.920541] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2
[    4.978045] usb usb2: configuration #1 chosen from 1 choice
[    4.978066] hub 2-0:1.0: USB hub found
[    4.978147] uhci_hcd: USB Universal Host Controller Interface driver
[    5.608028] usb 2-3: new full speed USB device using ohci_hcd and address 2
[    5.831102] usb 2-3: configuration #1 chosen from 1 choice
[   10.477906] usbcore: registered new interface driver usbserial
[   10.477941] USB Serial support registered for generic
[   10.477977] usbcore: registered new interface driver usbserial_generic
[   10.477979] usbserial: USB Serial Driver core
[   10.600480] USB Serial support registered for FTDI USB Serial Device
[   10.600522] ftdi_sio 2-3:1.0: FTDI USB Serial Device converter detected
[   10.600548] usb 2-3: Detected FT232RL
[   10.600589] usb 2-3: FTDI USB Serial Device converter now attached to ttyUSB0
[   10.600600] usbcore: registered new interface driver ftdi_sio
[   10.600603] ftdi_sio: v1.4.3:USB FTDI Serial Converters Driver

I edited my hardware conf (gksudo gedit /etc/lirc/hardware.conf)
my hardware.conf is as follows:
# /etc/lirc/hardware.conf

#
# Arguments which will be used when launching lircd
LIRCD_ARGS="-d /dev/ttyUSB0"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD=false

#Try to load appropriate kernel modules
LOAD_MODULES=false

# Run "lircd --driver=help" for a list of supported drivers.
DRIVER="uirt2_raw"
# If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
# automatically used instead
DEVICE=""
MODULES=""

# Default configuration files for your hardware if any
LIRCD_CONF=""
LIRCMD_CONF=""
#Chosen Remote Control
REMOTE="USB-UIRT"
REMOTE_MODULES=""
REMOTE_DRIVER="usb_uirt_raw"
REMOTE_DEVICE=""
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
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"
LIRCD_ARGS="-d /dev/ttyUSB0"

#Try to load appropriate kernel modules
LOAD_MODULES="false"

DRIVER="usb_uirt_raw"

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

at the termina irw gives me nothing when I press the remote buttons.  What should I try next?  Thanks in advance.

---

### Post by ToddW7 on 2009-07-01
Update:
when I do this, and press an ir remote I get the following:
$ cat /dev/ttyUSB0
#
D&#4097;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;#
T&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;#

But, the command "irw" has no responses

Any suggestions on what to do next?

---

### Post by tsx_5 on 2009-09-09
Hi,

I wanted to find out if this problem was ever resolved....  I have similar hardware and overall situation -- Only difference is that I don't get any characters when I try cat /dev/ttyUSB0.

TSX-5

---

### Post by robgue on 2009-09-13
same problem here. bump.

---

### Post by tsx_5 on 2009-09-24
](*,)

---

### Post by robgue on 2009-11-05
this is what finally got it working. in case some one can use it.this using an old hauppauge config. (my remote) Hopefully get it to transmit one day...:

```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Hauppauge TV card"
REMOTE_MODULES="lirc_dev lirc_i2c"
REMOTE_DRIVER="usb_uirt_raw"
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="hauppauge/lircd.conf.hauppauge"
REMOTE_LIRCD_ARGS="-d /dev/ttyUSB0"

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS="-d /dev/ttyUSB0"

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

### Post by Gh0stface on 2011-01-20
FYI this is how I got transmitting to work, I haven't tried receiving yet but I will see if I can get something working using the stuff you posted. If so I will post a complete hardware.conf. 

```

#Chosen IR Transmitter
TRANSMITTER="USB-UIRT2 : Direct TV Receiver"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER="usb_uirt_raw"
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF="directtv/general.conf"
TRANSMITTER_LIRCD_ARGS="-l -d /dev/ttyUSB0"

```

---

### Post by santhony on 2011-03-30
I've gotten my two USB-UIRTS to work with the following files in Ubuntu Maverick 10.10 amd64 (64 bit).

/etc/lirc/hardware.conf
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="USB-UIRT"
REMOTE_MODULES=""
REMOTE_DRIVER="usb_uirt_raw"
REMOTE_DEVICE=""
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF=""
REMOTE_LIRCD_ARGS="-d /dev/ttyUSB0"

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

I used the Hauppauge_350 remote, here's the lircd.conf:

#
# this config file was automatically generated
# using lirc-0.5.5pre8 on Sun Apr 18 11:43:45 1999
#
# contributed by Jens Leuschner <leuschner@gmx.net>
#
# brand:             Hauppauge
# model:             
# supported devices: WinTV primo; WinTV pci; WinTV radio
#
# This config file will work with both homebrew receivers and 
# original Hauppauge TV cards !!!
#

begin remote

  name  Hauppauge
  bits           13
  flags SHIFT_ENC
  eps            30
  aeps          100

  one           950   830
  zero          950   830
  plead         960
  gap          89584
  repeat_bit      2

      begin codes
          TV                       0x000000000000100F
          RADIO                    0x000000000000100C
          FULL_SCREEN              0x000000000000102E
          CH+                      0x0000000000001020
          CH-                      0x0000000000001021
          VOL-                     0x0000000000001011
          VOL+                     0x0000000000001010
          MUTE                     0x000000000000100D
          SOURCE                   0x0000000000001022
          1                        0x0000000000001001
          2                        0x0000000000001002
          3                        0x0000000000001003
          4                        0x0000000000001004
          5                        0x0000000000001005
          6                        0x0000000000001006
          7                        0x0000000000001007
          8                        0x0000000000001008
          9                        0x0000000000001009
          0                        0x0000000000001000
          RESERVED                 0x000000000000101E
          MINIMIZE                 0x0000000000001026
      end codes

end remote


#
# this config file was automatically generated
# using lirc-0.6.6(animax) on Tue Apr 15 19:50:27 2003
#
# contributed by 
#
# brand: 				Hauppauge
# model no. of remote control: 
# devices being controlled by this remote: PVR 2/350
#

begin remote

  name  hauppauge_pvr
  bits           13
  flags RC5|CONST_LENGTH
  eps            30
  aeps          100

  one           969   811
  zero          969   811
  plead        1097
  gap          114605
  toggle_bit      2


      begin codes
          Power                    0x00000000000017FD
          Go                       0x00000000000017FB
          1                        0x00000000000017C1
          2                        0x00000000000017C2
          3                        0x00000000000017C3
          4                        0x00000000000017C4
          5                        0x00000000000017C5
          6                        0x00000000000017C6
          7                        0x00000000000017C7
          8                        0x00000000000017C8
          9                        0x00000000000017C9
          Back/Exit                0x00000000000017DF
          0                        0x00000000000017C0
          Menu                     0x00000000000017CD
          Red                      0x00000000000017CB
          Green                    0x00000000000017EE
          Yellow                   0x00000000000017F8
          Blue                     0x00000000000017E9
          Ch+                      0x00000000000017E0
          Ch-                      0x00000000000017E1
          Vol-                     0x00000000000017D1
          Vol+                     0x00000000000017D0
          Ok                       0x00000000000017E5
          Mute                     0x00000000000017CF
          Blank                    0x00000000000017CC
          Full                     0x00000000000017FC
          Rewind                   0x00000000000017F2
          Play                     0x00000000000017F5
          Forward                  0x00000000000017F4
          Record                   0x00000000000017F7
          Stop                     0x00000000000017F6
          Pause                    0x00000000000017F0
          Replay                   0x00000000000017E4
          Skip                     0x00000000000017DE
      end codes

end remote


#
# this config file was automatically generated
# using lirc-0.7.0(any) on Sun Nov 28 20:25:09 2004
#
# contributed by 
#
# brand:   Hauppauge 350
# Created: G.J. Werler (The Netherlands)
# Project: Mythtv Fedora Pundit-R [www.mythtvportal.com](www.mythtvportal.com)
# Date:    2004/11/28
# model no. of remote control: Hauppauge A415-HPG
# devices being controlled by this remote: PVR-350
#

begin remote

  name  Hauppauge_350
  bits           13
  flags RC5|CONST_LENGTH
  eps            30
  aeps          100

  one           969   811
  zero          969   811
  plead        1097
  gap          114605
  toggle_bit      2


      begin codes
          Go                       0x00000000000017BB
          Power                    0x00000000000017BD
          TV                       0x000000000000179C
          Videos                   0x0000000000001798
          Music                    0x0000000000001799
          Pictures                 0x000000000000179A
          Guide                    0x000000000000179B
          Radio                    0x000000000000178C
          Up                       0x0000000000001794
          Left                     0x0000000000001796
          Right                    0x0000000000001797
          Down                     0x0000000000001795
          OK                       0x00000000000017A5
          Back/Exit                0x000000000000179F
          Menu/i                   0x000000000000178D
          Vol+                     0x0000000000001790
          Vol-                     0x0000000000001791
          Prev.Ch                  0x0000000000001792
          Mute                     0x000000000000178F
          Ch+                      0x00000000000017A0
          Ch-                      0x00000000000017A1
          Record                   0x00000000000017B7
          Stop                     0x00000000000017B6
          Rewind                   0x00000000000017B2
          Play                     0x00000000000017B5
          Forward                  0x00000000000017B4
          Replay/SkipBackward      0x00000000000017A4
          Pause                    0x00000000000017B0
          SkipForward              0x000000000000179E
          1                        0x0000000000001781
          2                        0x0000000000001782
          3                        0x0000000000001783
          4                        0x0000000000001784
          5                        0x0000000000001785
          6                        0x0000000000001786
          7                        0x0000000000001787
          8                        0x0000000000001788
          9                        0x0000000000001789
          Asterix                  0x000000000000178A
          0                        0x0000000000001780
          #                        0x000000000000178E
          Red                      0x000000000000178B
          Green                    0x00000000000017AE
          Yellow                   0x00000000000017B8
          Blue                     0x00000000000017A9
      end codes

end remote
#
# this config file was automatically generated
# using lirc-0.7.0pre4(serial) on Sun Oct  2 00:24:32 2005
#
# contributed by anton|ganthaler.at and juergen.wilhelm|aon.at
# members of linux user group Vorarlberg [www.lugv.at](www.lugv.at)
# 
# for ir remote controler from Hauppauge WinTV Nexus-S
# most of the keys are supported
#
# brand:                       Hauppauge
# model no. of remote control: WinTV Nexus-S
# devices being controlled by this remote:
#

begin remote

  name  Hauppauge_WinTV_Nexus-S
  bits           13
  flags RC5|CONST_LENGTH
  eps            30
  aeps          100

  one           944   828
  zero          944   828
  plead         980
  gap          113932
  min_repeat      1
  toggle_bit      2


      begin codes
          Up                       0x0000000000001794
          Down                     0x0000000000001795
          Left                     0x0000000000001796
          Right                    0x0000000000001797
          Power                    0x00000000000017BD
          Ok                       0x00000000000017A5
          Menu                     0x000000000000178D
          Back                     0x000000000000179F
          Red                      0x000000000000178B
          Green                    0x00000000000017AE
          Yellow                   0x00000000000017B8
          Blue                     0x00000000000017A9
          0                        0x0000000000001780
          1                        0x0000000000001781
          2                        0x0000000000001782
          3                        0x0000000000001783
          4                        0x0000000000001784
          5                        0x0000000000001785
          6                        0x0000000000001786
          7                        0x0000000000001787
          8                        0x0000000000001788
          9                        0x0000000000001789
          Play                     0x00000000000017B5
          Pause                    0x00000000000017B0
          Stop                     0x00000000000017B6
          Record                   0x00000000000017B7
          FastFwd                  0x00000000000017B4
          FastRwd                  0x00000000000017B2
          Channel+                 0x00000000000017A0
          Channel-                 0x00000000000017A1
          Volume+                  0x0000000000001790
          Volume-                  0x0000000000001791
          Mute                     0x000000000000178F
          Timers                   0x000000000000178A
          Recordings               0x000000000000178E
          Back                     0x000000000000179F
          Record                   0x00000000000017B7
          Pause                    0x00000000000017B0
      end codes

end remote


#
# this config file was automatically generated
# using lirc-0.8.3pre1(default) on Sat Jun 21 12:36:46 2008
#
# contributed by Matthew Wright
#
# brand:  Hauppauge (HRV-1600 RT Remote)
# model no. of remote control: A415-HPG-A
# devices being controlled by this remote:
#

begin remote

  name  Hauppauge
  bits           13
  flags RC5|CONST_LENGTH
  eps            30
  aeps          100

  one           919   852
  zero          919   852
  plead         930
  gap          112908
  toggle_bit_mask 0x800

      begin codes
          power                    0x17BD
          go                       0x17BB
          tv                       0x179C
          videos                   0x1798
          music                    0x1799
          pictures                 0x179A
          guide                    0x179B
          radio                    0x178C
          exit                     0x179F
          menu                     0x178D
          prevch                   0x1792
          mute                     0x178F
          up                       0x1794
          down                     0x1795
          left                     0x1796
          right                    0x1797
          ok                       0x17A5
          volup                    0x1790
          voldown                  0x1791
          chup                     0x17A0
          chdown                   0x17A1
          record                   0x17B7
          stop                     0x17B6
          rewind                   0x17B2
          fastfwd                  0x17B4
          play                     0x17B5
          replay                   0x17A4
          skip                     0x179E
          pause                    0x17B0
          1                        0x1781
          2                        0x1782
          3                        0x1783
          4                        0x1784
          5                        0x1785
          6                        0x1786
          7                        0x1787
          8                        0x1788
          9                        0x1789
          *                        0x178A
          0                        0x1780
          #                        0x178E
          red                      0x178B
          green                    0x17AE
          yellow                   0x17B8
          blue                     0x17A9
          sub/cc                   0x178E
          text                     0x178A
          home                     0x17BB
      end codes

end remote


#
# this config file was automatically generated
# using lirc-0.8.5(default) on Wed Dec 30 21:52:35 2009
#
# contributed by 
#
# brand:                       Hauppauge
# model no. of remote control: 
# devices being controlled by this remote: MVP
#

begin remote

  name  Hauppauge_MVP
  bits           13
  flags RC5|CONST_LENGTH
  eps            30
  aeps          100

  one           912   857
  zero          912   857
  plead         937
  gap          113935
  toggle_bit_mask 0x800

      begin codes
          KEY_1                    0x10C1
          KEY_2                    0x10C2
          KEY_3                    0x10C3
          KEY_4                    0x10C4
          KEY_5                    0x10C5
          KEY_6                    0x10C6
          KEY_7                    0x10C7
          KEY_8                    0x10C8
          KEY_9                    0x10C9
          KEY_0                    0x10C0
          KEY_POWER                0x10FD
          KEY_GOTO                 0x10FB
          KEY_BACK                 0x10DF
          KEY_MENU                 0x10CD
          KEY_RED                  0x10CB
          KEY_GREEN                0x10EE
          KEY_YELLOW               0x10F8
          KEY_BLUE                 0x10E9
          KEY_UP                   0x10E0
          KEY_DOWN                 0x10E1
          KEY_LEFT                 0x10D1
          KEY_RIGHT                0x10D0
          KEY_MUTE                 0x10CF
          KEY_FN_1                 0x10CC
          KEY_FN_2                 0x10FC
          KEY_OK                   0x10E5
          KEY_REWIND               0x10F2
          KEY_FASTFORWARD          0x10F4
          KEY_PLAY                 0x10F5
          KEY_RECORD               0x10F7
          KEY_STOP                 0x10F6
          KEY_PAUSE                0x10F0
          KEY_PREVIOUS             0x10E4
          KEY_NEXT                 0x10DE
      end codes

end remote

---

### Post by santhony on 2011-03-30
For irrecord to work with USB-UIRT, you have to:

1. specify the actual device, /dev/ttyUSB0, 
2. the driver, uirt2_raw,
3. the file to save the results too, usb_uirt.conf.

not doing so will have irrecord use the defaults and will give errors such as:

irrecord: could not get file information for /dev/lirc
irrecord: could not get hardware features
irrecord: this device driver does not support the LIRC ioctl interface
irrecord: major number of /dev/ttyUSB0 is 188
irrecord: LIRC major number is 61
irrecord: check if /dev/ttyUSB0 is a LIRC device
irrecord: could not init hardware (lircd running ?

Here's what I typed to have irrecord work with my USB-UIRT:

irrecord -d /dev/ttyUSB0 -H uirt2_raw test.conf

-d -provides the device, which you should see under your /dev folder, /dev/ttyUSB0
-H -tells irrecord which driver to use, uirt2_raw
    To see available drivers, type: irrecord --driver=help
    This will list available drivers and you should be using one of them.

test.conf - specifies a file to save the results too.

---

