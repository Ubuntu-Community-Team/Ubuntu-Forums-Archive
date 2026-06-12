---
title: "lirc problems with iMon"
date: 2008-11-15
forum: Hardware
---

### Post by damien_d on 2008-11-15
Hello all,

I have been attempting to install lirc for Ubuntu 8.04.  I am attempting to install it for a Silverstone LC16M case, which has the combined imon pad and vfd.

I can install lirc (sudo apt-get install lirc), and have configured it for "Soundgraph iMON PAD IR/VFD".  The following is my /etc/lirc/hardware.conf file:

```

damien@mediabox:~$ cat /etc/lirc/hardware.conf
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Soundgraph iMON PAD IR/VFD"
REMOTE_MODULES="lirc_dev lirc_imon"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="imon/lircd.conf.imon-pad"
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

Which, as I understand it, is the correct driver for the remote that I have:

```

Bus 004 Device 004: ID 15c2:ffdc SoundGraph Inc. iMON PAD Remote Controller
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x15c2 SoundGraph Inc.
  idProduct          0xffdc iMON PAD Remote Controller
  bcdDevice            0.00
  iManufacturer           0 
  iProduct                0 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           41
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         0 (Defined at Interface level)
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      ** UNRECOGNIZED:  09 21 00 01 00 01 22 25 00
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
Device Status:     0x0000
  (Bus Powered)

```

but when I attempt to run irw to test the interface, I get the following error:

```

damien@mediabox:~$ sudo irw /dev/lirc0
connect: Connection refused

```

After which, it looks like the daemon is no longer running (actually, I can't reproduce that again below....).  Let's try this again:
```

damien@mediabox:~$ sudo /etc/init.d/lirc restart
 * Stopping remote control daemon(s): LIRC                               [ OK ] 
 * Loading LIRC modules                                                  [ OK ] 
 * Starting remote control daemon(s) : LIRC                              [ OK ] 
damien@mediabox:~$ sudo irw /dev/lirc0
connect: Connection refused
damien@mediabox:~$ ps aux | grep lirc
root     15290  0.0  0.0  15828   592 ?        Ss   13:46   0:00 /usr/sbin/lircd --device=/dev/lirc0
damien   15301  0.0  0.0   5168   848 pts/5    S+   13:46   0:00 grep lirc
damien@mediabox:~$ 

```

This is the only hint I am getting from dmesg:
```

[1278225.619481] /var/lib/dkms/lirc/0.8.3~pre1/build/drivers/lirc_imon/lirc_imon.c: IR port opened
[1278225.619859] /var/lib/dkms/lirc/0.8.3~pre1/build/drivers/lirc_imon/lirc_imon.c: IR port closed
[1278245.247894] /var/lib/dkms/lirc/0.8.3~pre1/build/drivers/lirc_imon/lirc_imon.c: IR port opened
[1278245.248260] /var/lib/dkms/lirc/0.8.3~pre1/build/drivers/lirc_imon/lirc_imon.c: IR port closed

```

Now, the only complicating factor is that I have been trying a bunch of things, have have also loaded:
```

sudo apt-get install lirc-modules-source

```

and also

```

sudo apt-get install module-assistant

```

Just asking if someone else has any success... without compiling from source (because I really don't want to every time I do a kernel update....)

Edit: Just to make life even stranger, the imon driver appears to be loading fine on boot:
```

[   63.327316] lirc_dev: IR Remote Control driver registered, major 61 
[   63.527930] lirc_imon: no version for "lirc_unregister_plugin" found: kernel tainted.
[   63.528388] /var/lib/dkms/lirc/0.8.3~pre1/build/drivers/lirc_imon/lirc_imon.c: Driver for Soundgraph iMON MultiMedia IR/VFD, v0.3
[   63.528391] /var/lib/dkms/lirc/0.8.3~pre1/build/drivers/lirc_imon/lirc_imon.c: Venky Raju <dev@venky.ws>
[   63.528417] /var/lib/dkms/lirc/0.8.3~pre1/build/drivers/lirc_imon/lirc_imon.c: imon_probe: found IMON device
[   63.528423] lirc_dev: lirc_register_plugin: sample_rate: 0
[   63.528441] /var/lib/dkms/lirc/0.8.3~pre1/build/drivers/lirc_imon/lirc_imon.c: imon_probe: Registered iMON plugin(minor:0)
[   63.528467] /var/lib/dkms/lirc/0.8.3~pre1/build/drivers/lirc_imon/lirc_imon.c: imon_probe: iMON device on usb<4:2> initialized
[   63.528481] usbcore: registered new interface driver lirc_imon

```

However, I still have the same problems as before.

Edit2:

It looks like mode2 yields something when buttons are pressed:
```

damien@mediabox:~$ sudo mode2 -d /dev/lirc0
code: 0x146313ff
code: 0x14631bff
code: 0x28b595b7
code: 0x28b5d5b7
code: 0x2bb195b7
code: 0x2bb1d5b7
code: 0x28b195b7
code: 0x28b1d5b7
code: 0x2a8595b7
code: 0x2a85d5b7
code: 0x299595b7
code: 0x2995d5b7
code: 0x2aa595b7
code: 0x2aa115b7
code: 0x2aa155b7
code: 0x2aa5d5b7
code: 0x2b9395b7
code: 0x2b93d5b7
code: 0x2a8515b7
code: 0x2a8555b7
code: 0x2aa115b7
code: 0x2aa155b7
code: 0x2ba595b7
code: 0x2ba5d5b7

```

Clearly **something** is getting into the receiver, but why would irw refuse to listen to anything?

This thread seems to be related, but there are no answers there either...
[http://ubuntuforums.org/showthread.php?t=729680](http://ubuntuforums.org/showthread.php?t=729680)

---

### Post by cleatus99 on 2008-12-05
I too am running MYTHBUNTU 8.10 I have two systems on is installed in a LC16M with the Knob & IR/VFD

I also have a iMon Soundgraph IR/VFD with remote installed in another system I can not get either to work in Myth.

Any Luck anyone?

---

### Post by damien_d on 2008-12-05
> **cleatus99 said:**
> 

Any Luck anyone?

Cleatus99,

Are you able to reproduce the above on your system?  If so, we can think about filing a bug.

Cheers
Damien

---

### Post by damien_d on 2008-12-06
> **damien_d said:**
> 

Clearly **something** is getting into the receiver, but why would irw refuse to listen to anything?



I may finally be able to answer my own question.   I have recently upgraded to 8.10, and then tried:

```

sudo irw

```

which, to my surprise, worked perfectly.

So, I had figured that the upgrade fixed it, but I tried re-running my old steps:

```

sudo irw /dev/lirc0

```

Which came up with "connection refused" again, as before.   When reading the man page, it connects to a socket by default **/dev/lircd**, NOT **/dev/lirc0**

Therefore, I think all along it was an rtfm problem.

So, in short, when testing:
```

sudo irw /dev/lirc0 # <-- WRONG
sudo irw # <-- correct
sudo irw /dev/lircd # <- correct

```

---

### Post by cleatus99 on 2008-12-13
ok so I've runlsusb and I get
```

Bus 002 Device 008: ID 03f0:0024 Hewlett-Packard KU-0316 Keyboard
Bus 002 Device 003: ID 15c2:ffdc SoundGraph Inc. iMON PAD Remote Controller
Bus 002 Device 002: ID 046d:c018 Logitech, Inc. Optical Wheel Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
with irw 0.8.3 on Mythbuntu 8.10 

I run irw and it just sits there, never returns shell to me...

---

### Post by cleatus99 on 2008-12-13
sudo irw /dev/lircd

Nothing happens 

sudo irw /dev/lirc0
connect: Connection refused


```

lsusb -v returns

Bus 002 Device 003: ID 15c2:ffdc SoundGraph Inc. iMON PAD Remote Controller
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x15c2 SoundGraph Inc.
  idProduct          0xffdc iMON PAD Remote Controller
  bcdDevice            0.00
  iManufacturer           0 
  iProduct                0 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           41
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         0 (Defined at Interface level)
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      ** UNRECOGNIZED:  09 21 00 01 00 01 22 25 00
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
Device Status:     0x0000
  (Bus Powered)


```


No display funtions, No remote functions
:confused:

---

### Post by cleatus99 on 2008-12-13
This is the display in one system 

[IMG]http://www.mythtv.org/wiki/images/a/ac/Imon_lcd.png[/IMG]

My other system has the knob & VFD in the LC16M

---

### Post by damien_d on 2008-12-13
> **cleatus99 said:**
> sudo irw /dev/lircd

Nothing happens 


when you command irw, can you post the last 20 or so lines of dmesg? 

Also try:

```

sudo mode2 -d /dev/lirc0

```

And press random buttons on the remote.  You should see something like I have in an above post in this thread

---

### Post by cleatus99 on 2008-12-17
ok after typing irw & sudo mode2 -d /dev/lirc0
when I push the buttons on the remote it gives me feed back...
```

@MythTv:~$ irw
000000002b9595b7 00 Mute iMON-PAD
0000000028a595b7 00 Vol- iMON-PAD
000000002a8595b7 00 4 iMON-PAD
000000002aa115b7 00 9 iMON-PAD
000000002a8595b7 00 4 iMON-PAD
000000002aa595b7 00 6 iMON-PAD
00000000299595b7 00 5 iMON-PAD
0000000028b195b7 00 3 iMON-PAD
000000002b8395b7 00 Timer iMON-PAD
000000002ab195b7 00 MultiMon iMON-PAD
000000002b8395b7 00 Timer iMON-PAD
0000000029b715b7 00 AppLauncher iMON-PAD
000000002ab195b7 00 MultiMon iMON-PAD
000000002a9395b7 00 TaskSwitcher iMON-PAD
00000000299395b7 00 Eject iMON-PAD
000000002bb715b7 00 Esc iMON-PAD
00000000299395b7 00 Eject iMON-PAD
000000002b9115b7 00 PrevChapter iMON-PAD
000000002a8195b7 00 Rewind iMON-PAD
00000000298115b7 00 Record iMON-PAD
000000002b9715b7 00 Stop iMON-PAD
000000002a9115b7 00 Pause iMON-PAD
000000002a8115b7 00 Play iMON-PAD
00000000288195b7 00 AppExit iMON-PAD
0000000029b195b7 00 SlowMotion iMON-PAD
000000002b8115b7 00 FastForward iMON-PAD
00000000298195b7 00 NextChapter iMON-PAD
000000002a9115b7 00 Pause iMON-PAD
00000000298195b7 00 NextChapter iMON-PAD
0000000028a115b7 00 Backspace iMON-PAD
00000000299115b7 00 MouseKeyboard iMON-PAD
000000002a9315b7 00 SelectSpace iMON-PAD
0000000028b715b7 00 MouseMenu iMON-PAD
00000000688481b7 00 MouseRightClick iMON-PAD
0000000028a195b7 00 Enter iMON-PAD
00000000688301b7 00 MouseLeftClick iMON-PAD
000000002b8195b7 00 WindowsKey iMON-PAD
0000000028a115b7 00 Backspace iMON-PAD
000000002bb715b7 00 Esc iMON-PAD
0000000029b715b7 00 AppLauncher iMON-PAD
00000000299395b7 00 Eject iMON-PAD
000000002a9395b7 00 TaskSwitcher iMON-PAD
000000002aa115b7 00 9 iMON-PAD
0000000028b515b7 00 ShiftTab iMON-PAD
000000002ba595b7 00 0 iMON-PAD
0000000029a115b7 00 Tab iMON-PAD
000000002b8515b7 00 MyMovie iMON-PAD
00000000299195b7 00 MyMusic iMON-PAD
000000002ba115b7 00 MyPhoto iMON-PAD
00000000299195b7 00 MyMusic iMON-PAD
000000002ab715b7 00 Thumbnail iMON-PAD
000000002ba115b7 00 MyPhoto iMON-PAD
0000000029a595b7 00 AspectRatio iMON-PAD

```

ok so the pc see is getting commands, now how do I get them to work on mythtv frontend?
also the mouse pad on the remote doesn't show up on irw nor does DVD or Power......

---

### Post by damien_d on 2008-12-17
Does the DVD and power buttons come up with nothing in mode2, or just in irw?

The pad, I have no idea about.  I remember vaguely somewhere about it being implemented somewhere as a mouse, but don't trust that statement.  As for mythTV integration, I haven't yet started that project... still got a keyboard on the couch :P

---

### Post by cleatus99 on 2008-12-17
Ok I'm starting from scratch cause All i've done is make things worse....

I'm going focus on getting my my LC16M to work Remote & Display 1st then tackle the LCD display...

ok 1st I run 
```

root@mythtv2:/# lsusb
Bus 002 Device 004: ID 05e3:070e Genesys Logic, Inc. X-PRO CR20xA USB 2.0 Internal Card Reader
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 046d:c016 Logitech, Inc. M-UV69a/HP M-UV96 Optical Wheel Mouse
Bus 001 Device 004: ID 0b38:0003  
Bus 001 Device 003: ID 15c2:0036 SoundGraph Inc. 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

2nd I run
```

root@mythtv2:/# irw
connect: Connection refused

```

3rd I run
```

root@mythtv2:/# dmesg | grep lirc
[   31.339297] lirc_dev: IR Remote Control driver registered, major 61 
[   31.343977] lirc_imon: Driver for Soundgraph iMON MultiMedia IR/VFD w/imon pad2keys patch, v0.3p2k
[   31.343984] lirc_imon: Venky Raju <dev@venky.ws>
[   31.344025] usbcore: registered new interface driver lirc_imon

```

4th I try
```

root@mythtv2:/# LCDd
sock_create_inet_socket: Could not bind to port 13666 at address 127.0.0.1 - Address already in use
sock_init: Error creating socket - Address already in use
Critical error while initializing, abort.

```

Your Help is greatly appreciated.

---

### Post by damien_d on 2008-12-17
> **cleatus99 said:**
> 
```

root@mythtv2:/# LCDd
sock_create_inet_socket: Could not bind to port 13666 at address 127.0.0.1 - Address already in use
sock_init: Error creating socket - Address already in use
Critical error while initializing, abort.

```



Is there an LCD server already running?  If you have it installed, it probably starts as a daemon on boot.

---

### Post by membuntu on 2008-12-27
I have a very similar issue:

> ii  lirc                                       0.8.3-0ubuntu2                              Linux Infra-red Remote Control support
ii  lirc-modules-source                        0.8.3-0ubuntu2                              Linux Infra-red Remote Control support (kern


> root@mediapc:~# lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 15c2:0038 SoundGraph Inc.
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 05e3:070e Genesys Logic, Inc. X-PRO CR20xA USB 2.0 Internal Card Reader
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


> root@mediapc:~# dmesg | grep imon
[  334.839718] lirc_imon: Driver for Soundgraph iMON MultiMedia IR/VFD w/imon pad2keys patch, v0.3p2k
[  334.839733] lirc_imon: Venky Raju <dev@venky.ws>
[  334.841034] usbcore: registered new interface driver lirc_imon


> root@mediapc:~# lsmod | grep lirc
lirc_imon              23052  0
lirc_dev               20020  1 lirc_imon
usbcore               148848  7 lirc_imon,usbhid,usb_storage,libusual,ohci_hcd,ehci_hcd


When I run irw it simply exits the 1st time without any message, the second time it errors and the lirc daemon crashes.

> root@mediapc:~# /etc/init.d/lirc restart
 * Stopping remote control daemon(s): LIRC                                                              [ OK ]
 * Loading LIRC modules                                                                                 [ OK ]
 * Starting remote control daemon(s) : LIRC                                                             [ OK ]
root@mediapc:~# irw
root@mediapc:~# irw
connect: Connection refused
root@mediapc:~# /etc/init.d/lirc restart
 * Stopping remote control daemon(s): LIRC                                                              [fail]
 * Loading LIRC modules                                                                                 [ OK ]
 * Starting remote control daemon(s) : LIRC                                                             [ OK ]


I do not have a /dev/lirc0 but I do have /dev/lircd.
Running irw /dev/lircd does not help.

Mode 2 errors:
> root@mediapc:~# mode2
mode2: error opening /dev/lirc
mode2: No such file or directory


my /etc/lircd.conf (comments ommited)
> include /usr/share/lirc/remotes/imon/lircd.conf.imon
The file lirdd.conf points to does exist, its the one provided by the ubuntu package.

Kernel2.6.27-9-generic
ubuntu intrepid.

Case: SILVERSTONE ML02 [http://www.phoronix.com/scan.php?page=article&item=796&num=6](http://www.phoronix.com/scan.php?page=article&item=796&num=6)

Any help would be greatly appreciated. I have read similar threads and the issue was solved by compiling the latest lirc. I would prefer to use ubuntu packages as this is a HTPC im building for a friend.

---

### Post by damien_d on 2008-12-27
I'm not exactly an expert, but what does dmesg say after your irw fails?  If it crashes, then hopefully it barfs out something useful.

does 
```

ps aux | grep lirc

```

spit out anything after the first irw fun?

I have this vague recollection that it looked at the lirc conf file, then died because it couldn't find what it wanted.  Maybe post:

```

cat /etc/lircd.conf
cat /etc/lirc/hardware.conf

```

any anything else around that that we could possibly use for debugging.


And let's see what it says.

---

### Post by membuntu on 2008-12-28
Checked dmesg (and var/log/messages) for any info and nothing comes up.

> root@mediapc:~# /etc/init.d/lirc restart
 * Stopping remote control daemon(s): LIRC                                                              [ OK ]
 * Loading LIRC modules                                                                                 [ OK ]
 * Starting remote control daemon(s) : LIRC                                                             [ OK ]
root@mediapc:~# dmesg > 1.txt
root@mediapc:~# irw
root@mediapc:~# irw
connect: Connection refused
root@mediapc:~# /etc/init.d/lirc restart
 * Stopping remote control daemon(s): LIRC                                                              [fail]
 * Loading LIRC modules                                                                                 [ OK ]
 * Starting remote control daemon(s) : LIRC                                                             [ OK ]
root@mediapc:~# dmesg > 2.txt
root@mediapc:~# diff 1.txt 2.txt


dmesg doesnt say anything.



The lirc daemon does indeed crash:> root@mediapc:~# ps -ef | grep lirc
root     22748     1  0 16:19 ?        00:00:00 /usr/sbin/lircd --device=/dev/lirc0
root     23022  9124  0 16:20 pts/0    00:00:00 grep lirc
root@mediapc:~# irw
root@mediapc:~# irw
connect: Connection refused
root@mediapc:~# ps -ef | grep lirc
root     23026  9124  0 16:20 pts/0    00:00:00 grep lirc



**/etc/lircd.conf**
> #This configuration has been automatically generated via
#the Ubuntu LIRC package maintainer scripts.
#
#It includes the default configuration for the remote and/or
#transmitter that you have selected during package installation.
#
#Feel free to add any custom remotes to the configuration
#via additional include directives or below the existing
#Ubuntu include directives from your selected remote and/or
#transmitter.

#Configuration for the Soundgraph iMON IR/LCD remote:
include /usr/share/lirc/remotes/imon/lircd.conf.imon



**/etc/lirc/hardware.conf**
> # /etc/lirc/hardware.conf                                                                          
#                                                                                                  
#Chosen Remote Control                                                                             
REMOTE="Soundgraph iMON IR/LCD"
REMOTE_MODULES="lirc_dev lirc_imon"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="imon/lircd.conf.imon"
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



**/usr/share/lirc/remotes/imon/lircd.conf.imon**
> #                                                               
# contributed by Venky Raju (dev@venky.ws)                      
#                                                               
# brand: Soundgraph                                             
# model no. of remote control: iMON MultiMedian                 
#                                                               
# devices being controlled by this remote: HTPC                 
#                                                               

begin remote

  name           IMON_MultiMedian
  bits           16              
  flags          SPACE_ENC|CONST_LENGTH
  eps            30                    
  aeps           130                   

  header         9000  4500
  one            625   1625
  zero           625   375 
  ptrail         625       
  repeat         8875  2125
  pre_data_bits  16        
  pre_data       0x609F    
  gap            100000    
  toggle_bit     0         

  frequency    38000
  duty_cycle   33   

      begin codes
          App.Exit                 0x00000000000000FF
          Power                    0x000000000000807F
          1                        0x00000000000040BF
          2                        0x000000000000C03F
          3                        0x00000000000020DF
          4                        0x000000000000A05F
          5                        0x000000000000609F
          6                        0x000000000000E01F
          7                        0x00000000000010EF
          8                        0x000000000000906F
          9                        0x00000000000050AF
          0                        0x000000000000D02F
          Windows                  0x00000000000030CF
          Menu                     0x000000000000B04F
          App.Launcher             0x000000000000708F
          Function                 0x000000000000F00F
          Task.Switcher            0x00000000000008F7
          Back                     0x0000000000008877
          Select                   0x00000000000048B7
          Eject                    0x0000000000009867
          Delete                   0x00000000000018E7
          Up                       0x000000000000C837
          Right                    0x0000000000006897
          Down                     0x000000000000E817
          Left                     0x00000000000028D7
          Enter                    0x000000000000A857
          Vol-                     0x00000000000058A7
          Vol+                     0x000000000000D827
          Mute                     0x00000000000038C7
          Play                     0x000000000000B847
          Pause                    0x0000000000007887
          Prev                     0x000000000000F807
          Next                     0x00000000000002FD
          Rew                      0x000000000000827D
          Fwd                      0x00000000000042BD
          Stop                     0x000000000000C23D
          Open                     0x00000000000022DD
          Rec                      0x000000000000A25D
          Bookmark                 0x000000000000629D
          Thumbnail                0x000000000000E21D
          Aspect                   0x00000000000012ED
          DVD.Menu                 0x000000000000926D
          DVD.Caption              0x00000000000052AD
          DVD.Language             0x000000000000D22D
          Full.Screen              0x00000000000032CD
      end codes

end remote


Whats the status of 0.8.4 being introduced into the mainstream ?.

Thanks.

---

### Post by membuntu on 2008-12-28
Listed this as a bug with intrepid.
[https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/311890](https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/311890)

---

