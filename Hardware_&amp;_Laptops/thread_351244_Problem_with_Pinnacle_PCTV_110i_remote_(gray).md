---
title: "Problem with Pinnacle PCTV 110i remote (gray)"
date: 2007-02-01
forum: Hardware &amp; Laptops
---

### Post by Darrarski on 2007-02-01
I have problem with remote control plugged to Pinnacle PCTV 110i tv card on Ubuntu 6.10. When I'm pressing the same key two or more times, nothing happed. For example when I press key "1", I can't press it again until I've pressed another key. So, I cannot change tvtime channel to 11 or 22 or 33 etc.
Other symptom is that I can't configure LIRC:
```
Hold down an arbitrary button.
```
here I have to hit keys repeatedly like crazy, otherwise "gap not found"
```
................................................................................
Found gap length: 208087
```
Sometimes 208087, sometimes 208085, etc.
```
Please enter the name for the next button (press <ENTER> to finish recording)
1
Now hold down button "1".
Please enter the name for the next button (press <ENTER> to finish recording)
2
Now hold down button "2".
Please enter the name for the next button (press <ENTER> to finish recording)
3
Now hold down button "3".
[ CUT ]
Checking for toggle bit.
Please press an arbitrary button repeatedly as fast as possible (don't hold it down!).
..............................
Invalid toggle bit.
irrecord: closing '/dev/input/event3'
Successfully written config file.
```
And only two first keys are saved to .conf file.
I [read]("http://lists-archives.org/video4linux/09209-pinnacle-pctv-50i-remote-control-non-colored-buttons.html") that there is some repeat issue, but I can't find more info about this issue.
I'm using saa7134 module with pinnacle_remote=1 option, because without this remote doesn't work at all.
Please help me, and sorry for my bad english. I hope you understood me.

[COLOR="Red"]EDIT[/COLOR]
I found in v4l source, in file ir-kbd-i2c.c this note:
> /* The grey pinnacle PCTV remote
 *
 *  There are one issue with this remote:
 *   - I2c packet does not change when the same key is pressed quickly. The workaround
 *     is to hold down each key for about half a second, so that another code is generated
 *     in the i2c packet, and the function can distinguish key presses.
 *
 * Sylvain Pasche <sylvain.pasche@gmail.com>
 */
So, I found reason. Maybe new version of v4l resolve this problem.

---

### Post by baryah on 2007-04-16
I am using Pinnacle PCTV PCI, recognized as 110i in Windows. can watch tv in Linux, but remote and radio not working. the remote is the grey one (i.e. no colored keys on it)

cat /proc/bus/input/devices gives..

I: Bus=0018 Vendor=0000 Product=0000 Version=0000
N: Name="Pinnacle PCTV"
P: Phys=i2c-0/0-0047/ir0
S: Sysfs=/class/input/input3
H: Handlers=kbd event3
B: EV=100003
B: KEY=108fc010 2100802 0 0 0 0 48000 2180 c0000801 9e1680 0 0 4ffc

lsinput gives..

/dev/input/event3
   bustype : BUS_I2C
   vendor  : 0x0
   product : 0x0
   version : 0
   name    : "Pinnacle PCTV"
   phys    : "i2c-0/0-0047/ir0"
   bits ev : EV_SYN EV_KEY EV_REP


/dev/input/event3
   bustype : BUS_I2C
   vendor  : 0x0
   product : 0x0
   version : 0
   name    : "Pinnacle PCTV"
   phys    : "i2c-0/0-0047/ir0"
   bits ev : EV_SYN EV_KEY EV_REP

input-kbd 3   gives..

map: 42 keys, size: 127/128
0x0000 = 401  # KEY_BLUE
0x0004 = 399  # KEY_GREEN
0x0007 = 173  # KEY_REFRESH
0x0008 = 158  # KEY_BACK
0x000a =  14  # KEY_BACKSPACE
0x000d = 353  # KEY_SELECT
0x0011 = 400  # KEY_YELLOW
0x0016 = 402  # KEY_CHANNELUP
0x0017 = 403  # KEY_CHANNELDOWN
0x0018 = 388  # KEY_TEXT
0x001e = 114  # KEY_VOLUMEDOWN
0x0020 = 103  # KEY_UP
0x0021 = 108  # KEY_DOWN
0x0022 = 105  # KEY_LEFT
0x0023 = 106  # KEY_RIGHT
0x0026 = 377  # KEY_TV
0x0029 = 167  # KEY_RECORD
0x002d = 115  # KEY_VOLUMEUP
0x002e = 207  # KEY_PLAY
0x002f = 372  # KEY_ZOOM
0x003d = 210  # KEY_PRINT
0x0048 = 398  # KEY_RED
0x0049 = 139  # KEY_MENU
0x004a = 116  # KEY_POWER
0x004b = 119  # KEY_PAUSE
0x004c = 128  # KEY_STOP
0x004d = 168  # KEY_REWIND
0x004e = 159  # KEY_FORWARD
0x0053 = 412  # KEY_PREVIOUS
0x0054 = 407  # KEY_NEXT
0x0059 = 113  # KEY_MUTE
0x0069 =  11  # KEY_0
0x006a =   2  # KEY_1
0x006b =   3  # KEY_2
0x006c =   4  # KEY_3
0x006d =   5  # KEY_4
0x006e =   6  # KEY_5
0x006f =   7  # KEY_6
0x0070 =   8  # KEY_7
0x0071 =   9  # KEY_8
0x0072 =  10  # KEY_9
0x0074 = 363  # KEY_CHANNEL

input-events 3  gives ...

/dev/input/event3
   bustype : BUS_I2C
   vendor  : 0x0
   product : 0x0
   version : 0
   name    : "Pinnacle PCTV"
   phys    : "i2c-0/0-0047/ir0"
   bits ev : EV_SYN EV_KEY EV_REP

waiting for events
timeout, quitting                     


can some one help me out, as to what must i try now..
I am using KUBUNTU 6.10 Edgy Eft

---

### Post by baryah on 2007-04-16
I mean I keep pressing keys after  giving the command 'input-events 3' and nothing happens

---

### Post by baryah on 2007-05-06
now using Feisty ..... and remote 1. modprobe saa7134 pinnacle_remote=1

input-kbd gives

/dev/input/event2
   bustype : BUS_I2C
   vendor  : 0x0
   product : 0x0
   version : 0
   name    : "Pinnacle PCTV"
   phys    : "i2c-0/0-0047/ir0"
   bits ev : EV_SYN EV_KEY EV_REP

map: 41 keys, size: 128/128
0x0007 = 159  # KEY_FORWARD
0x000b = 128  # KEY_STOP
0x000d = 207  # KEY_PLAY
0x000e = 168  # KEY_REWIND
0x000f = 114  # KEY_VOLUMEDOWN
0x0013 = 159  # KEY_FORWARD
0x0015 = 119  # KEY_PAUSE
0x0016 = 168  # KEY_REWIND
0x0017 = 402  # KEY_CHANNELUP
0x0018 = 365  # KEY_EPG
0x0019 = 207  # KEY_PLAY
0x001a = 119  # KEY_PAUSE
0x001b = 115  # KEY_VOLUMEUP
0x001c = 403  # KEY_CHANNELDOWN
0x001d = 139  # KEY_MENU
0x001e = 372  # KEY_ZOOM
0x001f =  38  # KEY_L
0x0025 = 358  # KEY_INFO
0x0026 = 386  # KEY_TUNER
0x0027 = 167  # KEY_RECORD
0x0029 = 388  # KEY_TEXT
0x002a = 226  # KEY_MEDIA
0x002b =  23  # KEY_I
0x002d = 372  # KEY_ZOOM
0x002e =  25  # KEY_P
0x002f = 116  # KEY_POWER
0x0031 =   2  # KEY_1
0x0032 =   3  # KEY_2
0x0033 =   4  # KEY_3
0x0034 =   5  # KEY_4
0x0035 =   6  # KEY_5
0x0036 =   7  # KEY_6
0x0037 =   8  # KEY_7
0x0038 =   9  # KEY_8
0x0039 =  10  # KEY_9
0x003a =  11  # KEY_0
0x003b = 106  # KEY_RIGHT
0x003c = 113  # KEY_MUTE
0x003d = 105  # KEY_LEFT
0x003e = 108  # KEY_DOWN
0x003f = 103  # KEY_UP



still no key press detected



dmesg keeps on giving 


[ 7710.916875] Pinnacle PCTV: unknown key: key=0x01 raw=0x01 down=1
[ 7711.024706] Pinnacle PCTV: unknown key: key=0x01 raw=0x01 down=0
[ 7712.965633] Pinnacle PCTV: unknown key: key=0x2c raw=0x2c down=1
[ 7713.073463] Pinnacle PCTV: unknown key: key=0x2c raw=0x2c down=0
 repeatedly??

---

### Post by stoone on 2008-04-29
Same here. Can't find a solution.

---

