---
title: "Help with Soundgraph VFD/IR (Model #0036) infrared receiver in Mythbuntu 10.4"
date: 2010-05-16
forum: Hardware
---

### Post by Modem Mercenary on 2010-05-16
Greetings,


    I've built an HTPC using a Silverstone LC16M case that includes the  Soundgraph iMon IR/VFD (model #0036) usb display.  The VFD display works  with no problem, but I'm having trouble getting LIRC working with the  VFD's on board IR receiver.

  Lirc creates /dev/lirc0, which accepts input from the knob on the  front of the case. From what I understand, the Soundgraph iMon driver  should have two devices; lirc0 and lirc1,  with lirc1 receiving input  from the remote control.

   Other posts suggest that the IR receiver is getting grabbed by usbhid  and needs to be freed up so it can function normally.

   I tried solutions given in other posts that should free the receiver  from usbhid, but it seems that 10.4 does things differently than  previous versions. For example, the path given in this **_[COLOR=Red][post]("http://ubuntuforums.org/showthread.php?t=1041258")[/COLOR]_**:

```
mount -t usbfs none /proc/bus/usb

cat /proc/bus/usb/devices...

``` doesn't exist in Lucid Lynx.

  Also, trying to insert a **_[udev  rule for lirc]("http://ubuntuforums.org/showthread.php?t=1175001")_** (msg #6):

```
sudo gedit /etc/udev/rules.d/10-lirc.rules 

ATTRS{idVendor}=="15c2", ATTRS{idProduct}=="0036",  OPTIONS=="ignore_device"
```had no effect.

  Nor did manually loading modules in /etc/rc.local as suggested in the  same thread (msg #10):

```

modprobe -r usbhid lirc_imon
modprobe lirc_imon
modprobe usbhid
``` My question is:

  Has anyone been able to get the Soundgraph's IR receiver working in  Mythbuntu 10.4, and if so, could you help me get mine going?

Thanks in advance for your help!!

Mod_Merc

---------------------------------------------------------------------------------------------------
System specs:

Processor:      AMD Athlon 64 X2 4200+ 2.2GHz
motherboard:  Asus M3N78-VM
Memory:        2GB Corsair DDR667
Case:            Silverstone LC16M HTPC Case w/Soundgraph IR/VFD display  (Model #0036)

I have 64-bit Mythbuntu 10.4 installed with the latest updates as of May   15th, 2010.

The current kernel is 2.6.32-22-generic and lirc version   0.8.6-0ubuntu4.1.


```
ls -la /dev/li*

/dev/lirc0
/dev/lircd
``````
ls -la /dev/hid*

/dev/hidraw0
/dev/hidraw1
/dev/hidraw2
``````
dmesg | grep imon

[    6.708723] lirc_dev: IR Remote Control driver registered, major 61
[    6.783259] lirc_imon: Driver for SoundGraph iMON MultiMedia  IR/Display, v0.6
[    6.783295] lirc_dev: lirc_register_driver: sample_rate: 0
[    6.783450] lirc_imon: Registered iMON driver (lirc minor: 0)
[    6.788040] lirc_imon: iMON device (15c2:0036, intf0) on  usb<3:2> initialized
[    6.791035] lirc_imon: iMON device (15c2:0036, intf1) on  usb<3:2> initialized
[    6.791080] usbcore: registered new interface driver  lirc_imon
``````
lsusb

Bus 004 Device 007: ID 046d:c404 Logitech, Inc. TrackMan Wheel
Bus 004 Device 003: ID 0b38:0003 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 15c2:0036 SoundGraph Inc.
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0bda:0151 Realtek Semiconductor Corp. Mass  Storage Device
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root  hub
``````
System Information - hwinfo

-Input Devices-
 
Name         : iMON PAD IR Mouse (15c2:0036)
Type         : Mouse
Bus          : 0x3
Vendor       : 15c2
Product      : 0x36
Version      : 0x2
Connected to : usb-0000:00:02.0.-4/input0

```

---

### Post by Modem Mercenary on 2010-06-03
I have an update:


I'm not sure how it happened, but the iMON's IR receiver is now responding to the remote via irrecord.  The only thing I have done between now and my original post is made sure my system has all the current updates.

If anyone else is still experiencing this problem, make sure your system is fully updated and try using irrecord again.

Only problem now is, the pad is acting like a mouse (as it normally should) and the only buttons that work as key commands are the channel up and down buttons.

Now that the remote and receiver are working, I'll try to figure out how to get it to issue keyboard commands instead of mouse controls... :)

For those of you who are new to lirc configuration, I have included the steps I used to capture the button IR codes from the remote.

```
sudo /etc/init.d/lirc stop

sudo irrecord --disable-namespace -d /dev/lirc0 imon
```and follow irrecord's instructions.  

Make sure you don't hold down the buttons unless irrecord tells you to do so. I got some different codes when I accidentally held down a button instead of pressing it once.

Afterwards, I copied the resulting imon file to /etc/lirc/ directory and renamed it as imon.conf:

```
sudo cp imon /etc/lirc/imon.conf
```I edited my /etc/lirc/lircd.conf to include the path of the new imon.conf file (see below)

Finally, I restarted lircd

```
sudo /etc/init.d/lirc restart
```I hope this info helps out others who have this same problem.

Take care!

Mod_Merc

-------------------------------------------------

Here's my lirc configuration files for reference:

/etc/lirc/hardware.conf

**Note:**  As I was composing this post, I noticed the line marked in red below.  It's referring to a default imon pad remote control configuration file.  I'll have it point to the /etc/lirc/lircd.conf file tomorrow.  Hopefully this will make the remote behave as a keyboard.

**Edit:**  Changing the line didn't seem to work either.  

```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
#REMOTE="Soundgraph iMON PAD IR/VFD"
REMOTE="iMON-PAD"
REMOTE_MODULES="lirc_dev lirc_imon"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lircd"
REMOTE_SOCKET=""
[COLOR=Red]REMOTE_LIRCD_CONF="imon/lircd.conf.imon-pad"[/COLOR]
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
```I named the button directly under the "Enter" button, "Main".  Numbered "18" in [COLOR=Black]the [/COLOR][COLOR=Black]picture[/COLOR] shown [COLOR=Blue]**[here]("http://www.soundgraph.com/pad-remote-feature-en/")**[/COLOR].

/etc/lirc/imon.conf

```
# Please make this file available to others
# by sending it to <lirc@bartelmus.de>
#
# this config file was automatically generated
# using lirc-0.8.6(default) on Thu Jun  3 04:01:16 2010
#
# contributed by 
#
# brand:                       imon.conf
# model no. of remote control: 
# devices being controlled by this remote:
#

begin remote

  name  imon.conf
  bits           64
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  gap          95989
  toggle_bit_mask 0x400000000000

      begin codes
          App_Exit                 0x288195B700000201
          Power                    0x289115B700000201
          Record                   0x298115B700000201
          Play                     0x2A8115B700000201
          Eject                    0x29B195B700000201
          Rewind                   0x2A8195B700000201
          Pause                    0x2A9115B700000201
          FastFoward               0x2B8115B700000201
          Prev_Track               0x2B9115B700000201
          Stop                     0x2B9715B700000201
          Next_Track               0x298195B700000201
          BackSpace                0x0200002A00000000
          Select_Space             0x0200002C00000000
          Menu                     0x0280000000000000
          Context_Menu             0x0200006500000000
          Left_Click               0x0101000000000000
          Enter                    0x0200002800000000
          Right_Click              0x0102000000000000
          Escape                   0x0200002900000000
          Eject                    0x299395B700000201
          App_Launch               0x29B715B700000201
          Task_Switcher            0x2A9395B700000201
          Main                     0x2AB195B700000201
          Mute                     0x2B9595B700000201
          Vol_Up                   0x28A395B700000201
          Vol_Down                 0x28A595B700000201
          Ch_Up                    0x289395B700000201
          Ch_Down                  0x288795B700000201
          Timer                    0x2B8395B700000201
          1                        0x0200001E00000000
          2                        0x0200001F00000000
          3                        0x0200002000000000
          4                        0x0200002100000000
          5                        0x0200002200000000
          6                        0x0200002300000000
          7                        0x0220002500000000
          8                        0x0200002500000000
          9                        0x0200002600000000
          *                        0x0220002500000000
          0                        0x0200002700000000
          #                        0x0220002000000000
          Red_Video                0x2B8515B700000201
          Green_Music              0x299195B700000201
          Blue_Picture             0x2BA115B700000201
          Yellow_TV                0x28A515B700000201
          BookMark                 0x288515B700000201
          Thumbnail                0x2AB715B700000201
          Zoom                     0x29A595B700000201
          FullScreen               0x2AA395B700000201
          DVD                      0x29A395B700000201
          DVD_Menu                 0x2BA395B700000201
          DVD_Subtitle             0x298595B700000201
          DVD_Audio                0x2B8595B700000201
          Left                     0x0100008000000000
          Up                       0x0100800000000000
          Right                    0x0100007F00000000
          Down                     0x01003F0000000000
          Push                     0x0100008000000000
      end codes

end remote
```I edited this file to include the path of the imon.conf file.

/etc/lirc/lircd.conf:

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

#Configuration for the Soundgraph iMON PAD IR/VFD remote:

include "/etc/lirc/imon.conf"

```Lastly, here's an example of irrecord capturing input from the knob on the front 
of the Silverstone LC16M case:


```
# Please make this file available to others
# by sending it to <lirc@bartelmus.de>
#
# this config file was automatically generated
# using lirc-0.8.6(default) on Thu Jun  3 02:11:10 2010
#
# contributed by 
#
# brand:                       imon_knob
# model no. of remote control: 
# devices being controlled by this remote:
#

begin remote

  name  imon_knob
  bits           40
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  post_data_bits  24
  post_data      0x2EE
  gap          23990
  min_repeat      8
  toggle_bit_mask 0x100000001000000

      begin codes
          Knob_Push                0x0000000001
          Knob_ClckWse             0x0001000000
          Knob_Counter             0x0100000000
      end codes

end remote

```

---

### Post by seppl82 on 2010-06-10
Hi Modem Mercenary,

is it still working with your Infrared device?
I've tried all those funny things but the remote control still interacts as a mouse and i can only press channel up and channel down and use the mouse.

Kind Regards
/Seppl

---

### Post by Modem Mercenary on 2010-06-13
Hi seppl82.

Mine is still doing the exact same thing as yours.  I'm working on it right now.  I have also
posted a reply to your [[COLOR=Blue]thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1506214&highlight=seppl82") with info of what I've found so far and a link back to here
so others can reference my lirc config files.

---

### Post by Modem Mercenary on 2010-06-13
So far, I have found that the lirc_imon module can take a parameter  called "nomouse". I'm trying the directions found [[COLOR=Blue]here[/COLOR]]("https://help.ubuntu.com/community/IMON_VFD_and_LCD_Karmic_9.10") but they don't seem  to be working for 10.4 as far as I can tell. 

The article says to create a file in /etc/modprobe.d called lirc.conf 

```
/etc/modprobe.d/lirc.conf
```with the following line:

```
options lirc_imon debug=1 nomouse=1 display_type=1  pad_thresh=5
```I tried the following line in my own system:

```
options lirc_imon nomouse=1
```but it didn't seem to work.  I  don't know if it because 10.4 does things different from previous  versions or if I'm just doing something wrong.

I hope to solve this problem soon... until then, Take care all!!

Mod_Merc

---

### Post by seppl82 on 2010-06-13
Hi Mod_Mec,

i've found a solution, hopefully it will help you too.
I have the Antec Fusion Micro 350 case.

ist i've added an udev rule like this

vi /etc/udev/rules/90-lirc.conf

```
ATTRS{idVendor}=="15c2", ATTRS{idProduct}=="0038", OPTIONS=="ignore_device"
```

next i've did was going to the Mythbuntu Control Centrer
Go to Infrared and selct 

**"Soundgraph iMon Antec Veris"**

Now the Mouse event was away and i can use it properly.
Please check if it works for you and report it so that others have a benefit of it.

---

### Post by kanka on 2010-10-03
I had a crazy mouse problem with my iMon Pad: even without batteries, the mouse was behaving randomly, choosing items in menus by itself, really annoying.

seppl82, your trick fixed that problem, thank you very much!

---

