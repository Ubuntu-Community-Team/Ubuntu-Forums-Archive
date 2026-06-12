---
title: "Remote Control for Lenovo Y530, driver module is OK now"
date: 2010-08-06
forum: Hardware
---

### Post by jackallen0714 on 2010-08-06
I followed the steps some HP owners did, changed some lines in lirc_it87.h and lirc_it97.c and now it seems ITE8708 is working on Lenovo Y530 laptop !

1. Recompile the driver for ITE8708 and install it
The first attachment includes 
            1. source code ( lirc_it87.h, lirc_it87.c ) for Y530( I hope Lenovo only have only one version of the hardware, for me in Windows the IOs range from 0x300 to 0x307 and IRQ is 4, if yours is not, you must edit the corresponding lines in lirc_it87.h and recompile the driver ) 
            2.compiled module ( lirc_it87.ko ,you can just copy it to /lib/modules/2.6.32-24-generic/kernel/ubuntu/lirc/lirc_it87/ and replace the one already exists) 

Then 

sudo modprobe lirc_it87
dmesg | grep lirc 
If it is right, you will see something like this 

> [   21.263985] lirc_dev: IR Remote Control driver registered, major 61 
[   21.266742] lirc_dev: lirc_register_driver: sample_rate: 0
[   21.267115] lirc_it87: set default io 0x300
[   21.267128] lirc_it87: set default irq 0x4
[   21.267163] lirc_it87: I/O port 0x0300, IRQ 4.
[   21.267205] lirc_it87: Installed.


2. Make sure that your /etc/lirc/hardware.conf seems like this :

> # /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="ITE8708 CIR port"
REMOTE_MODULES="lirc_dev lirc_it87"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF=""
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="Custom"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_SOCKET=""
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

3. Now grab a Remote control and create the configure file ( I failed on the one Lenovo provides but succeeded by using my TV's Remote Control )

Restart the computer if it is necessary  or you can just
sudo /etc/init.d/lirc restart

Then
sudo  xmode2 -t 1 -d /dev/lirc0

Press one button and see if there are some waveform 

The graph seems clearer if you use 
sudo  xmode2 -m  -t 1 -d /dev/lirc0

Then follow the instruction after you
sudo irrecord -d /dev/lirc0 /etc/lirc/lircd.conf

if it requires key name,  you can find them by 
irrecord -l

After create the config file
sudo irw 
press a button of Remote control, you should get something like this

> 0000000000000005 00 KEY_PLAYPAUSE /etc/lirc/lircd.conf

4. Enable it in Totem, Mplayer ... 

sudo apt-get install mythbuntu-lirc-generator 
mythbuntu-lirc-generator  
mythbuntu-lircrc-generator 

Then press a button to see if it works

---

### Post by jackallen0714 on 2010-08-06
The problem is using the Remote Control Lenovo provides I always get this

Hope someone familiar with LIRC can offer some help !

> sudo irrecord -d /dev/lirc0 /home/jack/lenovo

irrecord -  application for recording IR-codes for usage with lirc

Copyright (C) 1998,1999 Christoph Bartelmus(lirc@bartelmus.de)

This program will record the signals from your remote control
and create a config file for lircd.


A proper config file for lircd is maybe the most vital part of this
package, so you should invest some time to create a working config
file. Although I put a good deal of effort in this program it is often
not possible to automatically recognize all features of a remote
control. Often short-comings of the receiver hardware make it nearly
impossible. If you have problems to create a config file READ THE
DOCUMENTATION of this package, especially section "Adding new remote
controls" for how to get help.

If there already is a remote control of the same brand available at
[http://www.lirc.org/remotes/](http://www.lirc.org/remotes/) you might also want to try using such a
remote as a template. The config files already contain all
parameters of the protocol used by remotes of a certain brand and
knowing these parameters makes the job of this program much
easier. There are also template files for the most common protocols
available in the remotes/generic/ directory of the source
distribution of this package. You can use a template files by
providing the path of the file as command line parameter.

Please send the finished config files to <lirc@bartelmus.de> so that I
can make them available to others. Don't forget to put all information
that you can get about the remote control in the header of the file.

Press RETURN to continue.


Now start pressing buttons on your remote control.

It is very important that you press many different buttons and hold them
down for approximately one second. Each button should generate at least one
dot but in no case more than ten dots of output.
Don't stop pressing buttons until two lines of dots (2x80) have been
generated.

Press RETURN now to start recording.
................................................................................
Found const length: 75776
Please keep on pressing buttons like described above.
................................................................................
RC-6 remote control found.
No header data.
No repeat code found.
Signals are biphase encoded.
Signal length is 41
Checking for toggle bit mask.
Please press an arbitrary button repeatedly as fast as possible.
Make sure you keep pressing the SAME button and that you DON'T HOLD
the button down!.
If you can't see any dots appear, then wait a bit between button presses.

Press RETURN to continue.

No toggle bit mask found.
But I know for sure that RC6 has a toggle bit!

---

### Post by jackallen0714 on 2010-08-06
Some graph I get by xmode2

---

### Post by jackallen0714 on 2010-08-06
Finally , it's all working !

I tried to irrecord with file mceusb.conf(in lirc source code) and now everything works !

just cp the following text to  lircd.conf file( /etc/lirc/lircd.conf)
> 
# Please make this file available to others
# by sending it to <lirc@bartelmus.de>
#
# this config file was automatically generated
# using lirc-0.8.6(default) on Fri Aug  6 17:18:47 2010
#
# contributed by 
#
# brand:                       Y530
# model no. of remote control: 
# devices being controlled by this remote:
#

begin remote

  name  Y530
  bits            8
  flags RC6|CONST_LENGTH
  eps            30
  aeps          100

  header       2667   889
  one           444   444
  zero          444   444
  pre_data_bits   29
  pre_data       0x37FBA7B
  gap          105000
  toggle_bit_mask 0x8000
  rc6_mask    0x100000000

      begin codes
          KEY_MUTE                 0xF2
          KEY_DOWN                 0xA6
          KEY_UP                   0xA7
          KEY_RIGHT                0xA4
          KEY_LEFT                 0xA5
          KEY_BACK                 0x7C
          KEY_VOLUMEDOWN           0xEE
          KEY_VOLUMEUP             0xEF
          KEY_CHANNELDOWN          0xE0
          KEY_CHANNELUP            0xE1
          KEY_RECORD               0xC8
          KEY_PAUSE                0xCF
          KEY_STOP                 0xCE
          KEY_PLAY                 0xD3
          KEY_REWIND               0xD6
          KEY_FORWARD              0xD7
          KEY_NEXT            0xDF
          KEY_PREVIOUS        0xDE
          KEY_DVD                  0xAB
          KEY_HOME                 0xA2
          KEY_INFO                 0x34
          KEY_EXIT                0xF3
          KEY_LIST                 0xC1
          KEY_PVR                  0x64
          KEY_TV                   0xD1
          KEY_ENTER                0xA3
      end codes

end remote


Tested on Lenovo Remote Control RC2292601/01

---

### Post by jackallen0714 on 2010-08-07
Newest Version, include config file for Totem, Mplayer ...

---

### Post by jackallen0714 on 2010-11-16
updated for 10.10

---

### Post by jackallen0714 on 2010-11-16
Forget the source code in previous package

---

### Post by kazayoshi on 2010-11-30
Driver working great with standard rc6 remote in y530. Reinstalling lirc and compiling with sources solve all errors like: "Invalid module format", irrecord: "Sorry, something went wrong, try again" etc.

---

### Post by nusch on 2012-04-18
Did you send your solution (source code and configs) to launchpad/ubuntu kernel team or lirc itself ?  Because only then there is a chance in future releases of ubuntu we would have Irda working out of the box.

---

### Post by jackallen0714 on 2012-04-22
This driver has been merged into ite-cir driver before kernel 3.0

Now only need to set the hardware.conf with ite-cir

Other configuration files still works. Just tried on Ubuntu 12.04

:)

---

