---
title: "Remote control for laptop HP nx9010 ALI FIR5123"
date: 2010-03-24
forum: Hardware
---

### Post by kmedioman on 2010-03-24
I'm trying to use the remote Humax RS-101P for my laptop HP nx9010 to build a media center; the on board hardware should be ALI FIR 5123 (windows xp says), it works under windows for file transfer, never tried with a remote control. I have installed Jaunty, lirc setserial, this is the log:
```

luca@Hyppo:~$ dmesg | grep lirc
[   29.082140] lirc_dev: IR Remote Control driver registered, major 61 
[   29.127188] lirc_dev: lirc_register_plugin: sample_rate: 0
[   29.127420] lirc_sir: I/O port 0x03e8, IRQ 4.
[   29.127450] lirc_sir: Installed.

```This is /etc/lirc/hardware.conf
```

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="SIR IrDA (built-in IR ports)"
REMOTE_MODULES="lirc_dev lirc_sir"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
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

```This is /etc/lirc/lircd.conf for the remote Hmax RS-101P from lirc website.

```

#
# this config file was automatically generated
# using lirc-0.6.5(serial) on Mon Apr  8 21:22:22 2002
#
# contributed by 
#
# brand:                       Humax
# model no. of remote control: RS-101P
# devices being controlled by this remote: HUMAX DVB
#

begin remote

  name  lircd.conf
  bits           16
  flags SPACE_ENC|CONST_LENGTH
  eps            30
  aeps          100

  header       9090  4417
  one           605  1647
  zero          605   514
  ptrail        606
  repeat       9091  2185
  pre_data_bits   16
  pre_data       0x8
  gap          107916
  toggle_bit      0


      begin codes
          1                        0x000000000000C03F
          2                        0x00000000000020DF
          3                        0x000000000000A05F
          4                        0x000000000000609F
          5                        0x000000000000E01F
          6                        0x00000000000010EF
          7                        0x000000000000906F
          8                        0x00000000000050AF
          9                        0x000000000000D02F
          0                        0x00000000000030CF
          power                    0x00000000000000FF
          tv/sat                   0x00000000000040BF
          ton                      0x000000000000B04F
          mute                     0x00000000000018E7
          red                      0x00000000000038C7
          green                    0x000000000000B847
          yellow                   0x00000000000058A7
          blue                     0x0000000000007887
          white                    0x0000000000009867
          gray                     0x0000000000006897
          menu                     0x000000000000708F
          up                       0x0000000000008877
          down                     0x000000000000A857
          right                    0x00000000000028D7
          left                     0x00000000000048B7
          ok                       0x000000000000C837
          v+                       0x000000000000F807
          v-                       0x00000000000002FD
          p+                       0x00000000000008F7
          p-                       0x000000000000F00F
          ?                        0x000000000000E817
          rcl                      0x000000000000827D
          epg                      0x000000000000D827
      end codes

end remote

```Serial ports:
```

luca@Hyppo:~$ /bin/setserial /dev/ttyS0
/dev/ttyS0, UART: unknown, Port: 0x03f8, IRQ: 4
luca@Hyppo:~$ /bin/setserial /dev/ttyS1
/dev/ttyS1, UART: 16550A, Port: 0x02f8, IRQ: 3

```No error restarting lirc
```
luca@Hyppo:~$ sudo /etc/init.d/lirc restart
[sudo] password for luca: 
 * Stopping remote control daemon(s): LIRC                               [ OK ] 
 * Loading LIRC modules                                                  [ OK ] 
 * Starting remote control daemon(s) : LIRC                              [ OK ] 

```Unfortunately I have no signal with irw or irrecord or mode2. The peripheral seems recognised and initialized by the system but doesn't receive any signal.

Any idea? Thanks.

---

### Post by kmedioman on 2010-03-25
Anybody?!?!

---

### Post by kmedioman on 2010-03-27
No way??? :cry:
[LEFT]Thanks
[/LEFT]

---

### Post by devsh on 2010-07-05
FIXED!!!!

here is some info

> **devsh]works!!!! thanks btw if you intend on making a tutorial or summink, the guyz from thinkpad got the lirc.conf wrong... its not code 0x2f8 but 0x02f8 

AND you need to create that file before you install lirc because of setserial claiming the resources.

[QUOTE=kmedioman]Hi, I reinstalled on my lucid laptop, actually irw doesn't seem to work. 
There is another instruction to set remote which is ```
sudo irrecord -d /dev/lirc0 foo 
```[COLOR=Black]
as you can see at the end of this page, "Testing LIRC" paragraph:[/COLOR]
[http://www.thinkwiki.org/wiki/How_to_make_use_of_IrDA#Configuring_lirc_sir](http://www.thinkwiki.org/wiki/How_to_make_use_of_IrDA#Configuring_lirc_sir)
I have a signal from remote with that command.
Please post your serial config by:
```
dmesg | grep lirc
setserial /dev/ttyS1
```[QUOTE=devsh]Maybe it's lucid's fault, I had irda-utils working on 8.04 but then I got lirc on it and it froze my system. I thought I had to reinstall

omg, ****, kernel downgrade or a 8.04 install :(


[QUOTE=kmedioman]I'm not giving you the right procedure, I'm telling you what worked for me.
```
dmesg | grep lirc
```[QUOTE=devsh]irw still blank... are you sure you given me the right procedure

[QUOTE=kmedioman]Correct, setserial should be required, irda-utils should not. When I tried, it blocked my computer. Try installing setserial only, and proceed with steps below. If you are using a different distro than Jaunty (where I tested the procedure), maybe the serial association is correct. Try dmesg | grep lirc at the end of step 1 just to doublecheck, maybe step 2 is not required.

[QUOTE=devsh]Wait a sec you didnt tell me I had to install setserial, but you listed it in the file. So is there anything else you havent told me to install, "I'm mostly thinking of irda-utils"

[QUOTE=kmedioman]

Ok, I'll try to go into details as much as I can. I had it working in Jaunty, not tried with Lucid yet. There are 3 fundamental steps:
1. Install lirc and make sure hardware is initializated
2. Associate serial port correctly
3. Configure remote reading irw codes

1. Install lirc from repository (synaptic or apt-get install). You'll be asked for hardware type, select "SIR IrDA" or similar from hardware list, and leave blank the transmitter related question
2. Restart the laptop, and make sure the hardware has been initializated (dmesg | grep lirc)
3. Create the file /etc/modprobe.d/lirc.conf [COLOR=Black]copy paste following text[/COLOR]
# prevent nsc_ircc from loading (blacklist might not be enough)
blacklist nsc_ircc
install nsc_ircc /bin/true
# pass options to lirc_sir to load it on ttyS1
options lirc_sir io=0x2f8 irq=3
# ensure serial resources are cleared before loading lirc_sir
# not doing so can result in a device busy error, or can even hang your system
install lirc_sir /bin/setserial /dev/ttyS1 uart none port 0 irq 0 said:**
> [/QUOTE][/QUOTE][/QUOTE][/QUOTE][/QUOTE][/QUOTE]

---

