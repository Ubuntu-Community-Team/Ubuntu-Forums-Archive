---
title: "Pinnacle PCTV 73e LIRC Support"
date: 2009-09-12
forum: Hardware
---

### Post by adammw on 2009-09-12
Hi.
I've recently bought a USB PCTV 73e, and getting it to work as a normal DVB-T tuner on Ubuntu was mildly successful.
I was trying to use the remote with LIRC, but I cannot seem to be able to get any data from the builtin IR receiver.
I have looked in dmesg and /proc/bus/input/devices, both report that the IR reciever has been detected and works, but I cannot get LIRC, irrecord or even cat to read any data from the /dev/input/eventX .


Futher details about the output of /proc/bus/input/devices:
```
I: Bus=0003 Vendor=2304 Product=0237 Version=0100
N: Name="IR-receiver inside an USB DVB receiver"
P: Phys=usb-0000:00:1d.7-8/ir0
S: Sysfs=/devices/pci0000:00/0000:00:1d.7/usb5/5-8/input/input12
U: Uniq=
H: Handlers=kbd event10 
B: EV=3
B: KEY=14afc336 284284d00000000 0 480058000 219040000801 9e96c000000000 90020000000ffd

```

I am sure that somewhere in Ubuntu the remote is working, as if I press any of the number buttons, they appear as if i typed them with the keyboard, and the volume up/down buttons work as if i pressed volume up/down on the keyboard.

Please help to try and resolve this issue.
Thanks.

---

### Post by tulpie on 2009-12-14
[IMG]http://www2.pic-upload.de/15.12.09/pscs7h1zlhuo.png[/IMG]

Hier ist my /etc/lirc/lircd.conf
which is work with the pinnacle remote and a Haupauge remote
but the code for the ?-Button and Window-resize-Button i cann't find.

```
begin remote
  name  Hauppauge-DSR-0112
  bits           32
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  gap          249808
  toggle_bit      1

      begin codes
          back                     0x0001009E
          up                       0x00010067
          tv                       0x00010179
          go                       0x00010162
          home                     0x00010066
          power                    0x00010074
          left                     0x00010069
          ok                       0x00010160
          right                    0x0001006A
          prev                     0x00010195
          next                     0x00010197
          rec                      0x000100A7
          down                     0x0001006C
          stop                     0x00010080
          pause                    0x00010077
          play                     0x000100CF
          1                        0x00010002
          2                        0x00010003
          3                        0x00010004
          4                        0x00010005
          5                        0x00010006
          6                        0x00010007
          7                        0x00010008
          8                        0x00010009
          9                        0x0001000A
          0                        0x0001000B
          txt                      0x00010184
          menu                     0x0001008B
          rew                      0x000100A8
          fwd                      0x000100D0
          ch+                      0x00010192
          ch-                      0x00010193
          vol+                     0x00010073
          vol-                     0x00010072
          ch-back                  0x0001016B
          mute                     0x00010071

#### another Bottons at bigger remotes

          Pictures                 0x000100E2
          Guide                    0x0001016D
          Radio                    0x00010181
          Videos                   0x00010189
          Music                    0x00010188
          Red                      0x0001018E
          Green                    0x0001018F
          Yellow                   0x00010190
          Blue                     0x00010191
          #                        0x00010029
          *                        0x00010037
     end codes
end remote
```

```

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Linux input layer (/dev/input/eventX)"
REMOTE_MODULES=""
REMOTE_DRIVER="dev/input"
REMOTE_DEVICE="/dev/input/event9"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="/etc/lirc/lircd.conf"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

Driver="devinput"

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
```

The line
**REMOTE_DEVICE="/dev/input/event9"**
must be ubdated by hand after eatch restart.
The right DEV can be found with.

sudo ls -l /dev/input/by-path

example output 0000:00:1d.7-**event-ir** -> ../**event9**

---

### Post by tulpie on 2009-12-14
if you want to test it ((((the /etc/lirc/lircd.conf above)))).

You must must open tow Terminals at the same time.
In the first terminal typ in:

> sudo lircd --nodaemon -H devinput -d /dev/input/event9 #####
(device shoud be the same as in /etc/lirc/hardware.conf as seted above )

perhaps you shold kill lirc before trying it an if gave errors.

> sudo killall lircd

the first command shold be loaded in first terminal. #####

In the second open terminal typ in 

> sudo irw

and enjoy the output in this terminal when you are playing with the remote.
:popcorn:

if you are chancing the /etc/lirc/lircd.conf you should restart lirc, with 
sudo /etc/init.d/lirc restart 
to make shur lirc know about the changings.

oh my english is woderful, greats from Germany :D :D :D :D :D

---

### Post by tulpie on 2009-12-14
Before i forgot it, you shoud look if the lirc modul is loaded

> lsmod | grep lirc

in the output must be

**lirc_dev**

If not type in
> 
sudo modprobe lirc_dev

but the hardware.conf above must autoloaded at restart your machine.
I can't say if this modul is loaded after reboot, becaus my machine is ""always"" up and doing some misterious things. :D:D:D

---

### Post by tulpie on 2009-12-14
> **adammw said:**
> Hi.
I've recently bought a USB PCTV 73e, and getting it to work as a normal DVB-T tuner on Ubuntu was mildly successful.
I was trying to use the remote with LIRC, but I cannot seem to be able to get any data from the builtin IR receiver.
I have looked in dmesg and /proc/bus/input/devices, both report that the IR reciever has been detected and works, but I cannot get LIRC, irrecord or even cat to read any data from the /dev/input/eventX .


Futher details about the output of /proc/bus/input/devices:
```
I: Bus=0003 Vendor=2304 Product=0237 Version=0100
N: Name="IR-receiver inside an USB DVB receiver"
P: Phys=usb-0000:00:1d.7-8/ir0
S: Sysfs=/devices/pci0000:00/0000:00:1d.7/usb5/5-8/input/input12
U: Uniq=
H: Handlers=kbd event10 
B: EV=3
B: KEY=14afc336 284284d00000000 0 480058000 219040000801 9e96c000000000 90020000000ffd

```

I am sure that somewhere in Ubuntu the remote is working, as if I press any of the number buttons, they appear as if i typed them with the keyboard, and the volume up/down buttons work as if i pressed volume up/down on the keyboard.

Please help to try and resolve this issue.
Thanks.

if you download an compile the newest
v4l-dvb all remotes are patch in the drivers.
I hab also downlaodet the newest v4l-dvb drivers:popcorn:

---

### Post by tulpie on 2009-12-15
[IMG]http://www2.pic-upload.de/15.12.09/4b4ob5wdrqa.png[/IMG]

the lirc.conf in the 2nd Post funktion also for this remote :P
(Haupauge DSR-0112 )

After reboot my  machine no lirc-modul was loaded.

> lsmod | grep lirc
gave no output

I have now edited my /etc/moduls and insert the line

> sudo gedit /etc/modules
---> **lirc_dev**

this line make's it shure that the modul is loaded after reboot.

you must also update 

> sudo gedit /etc/rc.local 
--->**irexec -d**
exit 0


that the lirc-Programm irexec is loaded at startup, becaus you can use a 
.lircrc

> gedit ~/.lircrc

and copy the next box in it, to use toetm
heer ist a .lircrc which work with totem (i testet :D :D)

```
# LIRCRC Auto Generated by Mythbuntu Lirc Generator
# Author(s): Mario Limonciello, Nick Fox
# Created for use with Mythbuntu
begin
    remote = Hauppauge-DSR-0112
    prog = totem
    button = up
    config = up
end

begin
    remote = Hauppauge-DSR-0112
    prog = totem
    button = power
    config = quit
end

begin
    remote = Hauppauge-DSR-0112
    prog = totem
    button = left
    config = left
end

begin
    remote = Hauppauge-DSR-0112
    prog = totem
    button = right
    config = right
end

begin
    remote = Hauppauge-DSR-0112
    prog = totem
    button = down
    config = down
end

begin
    remote = Hauppauge-DSR-0112
    prog = totem
    button = pause
    config = pause
end

begin
    remote = Hauppauge-DSR-0112
    prog = totem
    button = play
    config = play_pause
end

begin
    remote = Hauppauge-DSR-0112
    prog = totem
    button = menu
    config = menu
end

begin
    remote = Hauppauge-DSR-0112
    prog = totem
    button = fwd
    config = seek_forward
end

begin
    remote = Hauppauge-DSR-0112
    prog = totem
    button = vol+
    config = volume_up
end

begin
    remote = Hauppauge-DSR-0112
    prog = totem
    button = vol-
    config = volume_down
end

begin
    remote = Hauppauge-DSR-0112
    prog = totem
    button = mute
    config = mute
end

```

the hardware.conf must be updatet in anyway because the /dev/input/eventxxx is changing in some time. :popcorn:

On linuxtv.org i found a way to set always a right /dev/input/eventxxx,
but by now it does not function right.

[http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T-Stick](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T-Stick)
this howto must always function, becaus it make no matter if i stick in the Pinnacle or the haupauge :popcorn:

---

