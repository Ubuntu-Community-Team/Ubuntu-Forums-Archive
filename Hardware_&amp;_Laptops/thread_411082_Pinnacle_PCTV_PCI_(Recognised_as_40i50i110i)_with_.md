---
title: "Pinnacle PCTV PCI (Recognised as 40i/50i/110i) with FMradio and Remote problem"
date: 2007-04-16
forum: Hardware &amp; Laptops
---

### Post by baryah on 2007-04-16
I am using Pinnacle PCTV PCI, recognized as 110i in Windows. can watch tv in Linux, but remote and radio not working. the remote is the 'grey one' (i.e. no colored keys on it) and not working.

'cat /proc/bus/input/devices' gives..

I: Bus=0018 Vendor=0000 Product=0000 Version=0000
N: Name="Pinnacle PCTV"
P: Phys=i2c-0/0-0047/ir0
S: Sysfs=/class/input/input3
H: Handlers=kbd event3
B: EV=100003
B: KEY=108fc010 2100802 0 0 0 0 48000 2180 c0000801 9e1680 0 0 4ffc

'lsinput' gives..

/dev/input/event3
bustype : BUS_I2C
vendor : 0x0
product : 0x0
version : 0
name : "Pinnacle PCTV"
phys : "i2c-0/0-0047/ir0"
bits ev : EV_SYN EV_KEY EV_REP

'input-kbd 3' gives..

map: 42 keys, size: 127/128
0x0000 = 401 # KEY_BLUE
0x0004 = 399 # KEY_GREEN
0x0007 = 173 # KEY_REFRESH
0x0008 = 158 # KEY_BACK
0x000a = 14 # KEY_BACKSPACE
0x000d = 353 # KEY_SELECT
0x0011 = 400 # KEY_YELLOW
0x0016 = 402 # KEY_CHANNELUP
0x0017 = 403 # KEY_CHANNELDOWN
0x0018 = 388 # KEY_TEXT
0x001e = 114 # KEY_VOLUMEDOWN
0x0020 = 103 # KEY_UP
0x0021 = 108 # KEY_DOWN
0x0022 = 105 # KEY_LEFT
0x0023 = 106 # KEY_RIGHT
0x0026 = 377 # KEY_TV
0x0029 = 167 # KEY_RECORD
0x002d = 115 # KEY_VOLUMEUP
0x002e = 207 # KEY_PLAY
0x002f = 372 # KEY_ZOOM
0x003d = 210 # KEY_PRINT
0x0048 = 398 # KEY_RED
0x0049 = 139 # KEY_MENU
0x004a = 116 # KEY_POWER
0x004b = 119 # KEY_PAUSE
0x004c = 128 # KEY_STOP
0x004d = 168 # KEY_REWIND
0x004e = 159 # KEY_FORWARD
0x0053 = 412 # KEY_PREVIOUS
0x0054 = 407 # KEY_NEXT
0x0059 = 113 # KEY_MUTE
0x0069 = 11 # KEY_0
0x006a = 2 # KEY_1
0x006b = 3 # KEY_2
0x006c = 4 # KEY_3
0x006d = 5 # KEY_4
0x006e = 6 # KEY_5
0x006f = 7 # KEY_6
0x0070 = 8 # KEY_7
0x0071 = 9 # KEY_8
0x0072 = 10 # KEY_9
0x0074 = 363 # KEY_CHANNEL

'input-events 3' gives ...

/dev/input/event3
bustype : BUS_I2C
vendor : 0x0
product : 0x0
version : 0
name : "Pinnacle PCTV"
phys : "i2c-0/0-0047/ir0"
bits ev : EV_SYN EV_KEY EV_REP

waiting for events
timeout, quitting

I mean I keep pressing keys after giving the command 'input-events 3' and nothing happens and it quits with the above messsage.

can some one help me out, as to what must i try now..
I am using KUBUNTU 6.10 Edgy Eft

---

### Post by baryah on 2007-04-16
I'v tried the howto given at
[http://ubuntuforums.org/showthread.php?t=221299](http://ubuntuforums.org/showthread.php?t=221299)

---

