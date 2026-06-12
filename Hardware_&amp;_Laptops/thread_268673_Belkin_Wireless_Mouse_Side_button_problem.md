---
title: "Belkin Wireless Mouse Side button problem"
date: 2006-09-30
forum: Hardware &amp; Laptops
---

### Post by greenwom on 2006-09-30
I just picked up a nice new Belkin wireless mouse (model number F8E845)

It has 7 buttons.  (from xev)
```
1= Left Click
2= Middle Click
3= right click
4= up wheel
5= down wheel
8= side button one
9= side button two
```

There isn't a 7 or 6.  I've read a number of threads and I've had the side buttons working on other mice so I can't figure out what's wrong here.  
Here's more of what I came up with.

One wierd problem is that the middle click button "pastes" test.  I'm not sure if that's normal pr not

I do have imwheel installed

Any help would be great.  My goal is to have firefox & nautilus working.  It would also be nice to get cut and paste going.  

xorg.conf
```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "Buttons"               "7"
        Option          "ButtonMapping"         "1 2 3 9 8"
        Option          "ZAxisMapping"          "4 5"
        #Option         "Emulate3Buttons"       "false"
        Option          "Resolution"            "800"
EndSection

```

/etc/X11/imwheel/imwheelrc (I added the first line and then made some changes to the other parts (changing 6 and 7s into 8 and 9s)
```
 ".*" None,Up,Alt_L|Left None,Down,Alt_L|Right
```

/etc/X11/Xsession.d/57modmap
```
#/bin/bash
  xmodmap -e "pointer = 1 2 3 4 5 8 9 6 7"

```

/etc/X11/Xsession.d/63modmap
```
killall imwheel
 xmodmap -e "pointer = 1 2 3 4 5 8 9 6 7"
 BINARY=$(which imwheel)
 $BINARY -k -p -b "67"

```

/home/mike1/.imwheelrc
```
".*"
None, Up, Alt_L|Left
 None, Down, Alt_L|Right

 "(null)"
 None, Up, Alt_L|Left
 None, Down, Alt_L|Right

```

cat /proc/bus/input/devices
```
I: Bus=0003 Vendor=050d Product=0845 Version=0101
N: Name="Wireless Mouse Wireless Mouse"
P: Phys=usb-0000:00:1d.0-1/input0
S: Sysfs=/class/input/input1
H: Handlers=mouse0 event1 ts0
B: EV=7
B: KEY=1f0000 0 0 0 0 0 0 0 0
B: REL=103

```


Again thanks, I don't remeber what I did with the different mice I've used in the past. is this a protocal issue in xorg.conf?
](*,)  ](*,)  ](*,)  ](*,)  ](*,)  ](*,)  ](*,)  ](*,)

---

### Post by nixternal on 2006-09-30
>  One wierd problem is that the middle click button "pastes" test.  I'm not sure if that's normal pr not

That is the normal operations of a center button click.

Now for the rest of the stuff, I couldn't help you with ;) Sorry bud, but I will see you in a few weeks anyways ;)

My MX700 just works, almost! ;)

---

