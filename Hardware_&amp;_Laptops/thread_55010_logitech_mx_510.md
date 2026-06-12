---
title: "logitech mx 510"
date: 2005-08-07
forum: Hardware &amp; Laptops
---

### Post by shockertwin on 2005-08-07
Ok i am having massive problems here. I tried the method with evdev, and i could not get anythign working and i tried the method with imwheel and could not get it to install. Can someone help me out here?

here is my cat /proc/bus/input/devices
I: Bus=0003 Vendor=046d Product=c01d Version=2100
N: Name="Logitech USB-PS/2 Optical Mouse"
P: Phys=usb-0000:00:1d.1-2/input0
H: Handlers=mouse0 event2 ts0
B: EV=f
B: KEY=ff0000 0 0 0 0 0 0 0 0
B: REL=103
B: ABS=300 0

here is my xorg.conf
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

if anyone could give me a hand it would be appreciated. thanks.

---

### Post by hanover.fiste on 2005-08-07
Here's my xorg mouse config for a mx1000. The 510 is a bit similar, I would suppose with the exception of the dev name.

```

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Buttons"               "12"
        Option          "Dev Name"              "Logitech USB Receiver"
        Option          "Resolution"            "800"
        Option          "Protocol"              "evdev"
        Option          "Emulate3Buttons"       "false"
        Option          "ZAxisMapping"          "11 12"

```

And I got the dev name from cat /proc/bus/usb/devices
```

T:  Bus=03 Lev=02 Prnt=02 Port=02 Cnt=02 Dev#=  4 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=046d ProdID=c512 Rev=30.07
S:  Manufacturer=Logitech
S:  Product=USB Receiver
C:* #Ifs= 2 Cfg#= 1 Atr=a0 MxPwr= 98mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=01 Driver=usbhid
E:  Ad=81(I) Atr=03(Int.) MxPS=   8 Ivl=10ms
I:  If#= 1 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid
E:  Ad=82(I) Atr=03(Int.) MxPS=   8 Ivl=10ms

```

Do the same on your system, then combine the manf. and product lines. In my .profile, I put:
```
if [ "$DISPLAY" != "" ];
        then xmodmap -e "pointer = 1 2 3 6 7 8 9 10 11 12 4 5";
fi

if [ -x /usr/bin/xbindkeys ] &&
        [ "$DISPLAY" != "" ];
        then /usr/bin/xbindkeys;
fi

```

My .xindkeysrc looks like this:
```

# back and forward
 "xvkbd -xsendevent -text "\[Alt_L]\[Left]""
 m:0x10 + b:6
 "xvkbd -xsendevent -text "\[Alt_L]\[Right]""
 m:0x10 + b:7

 # the up and down by the wheel pages up and down
 "xvkbd -xsendevent -text "\[Page_Up]""
 m:0x10 + b:9
 "xvkbd -xsendevent -text "\[Page_Down]""
 m:0x10 + b:10

 # Left and Right on the wheel switch tabs
 "xvkbd -xsendevent -text "\[Control_L]\[Page_Up]""
 m:0x10 + b:11
 "xvkbd -xsendevent -text "\[Control_L]\[Page_Down]""
 m:0x10 + b:12

```

You will, of course, have to install xbindkeys and xvkbd. This also assumes that you're using a USB port for the 510.

---

### Post by shockertwin on 2005-08-07
.profile, .xindkeysrc

where would i go about finding these?

also, when i tried to install xvkbd, all i got was around 90000 complie errors...

---

### Post by woedend on 2005-08-07
[QUOTE=shockertwin].profile, .xindkeysrc

where would i go about finding these?

also, when i tried to install xvkbd, all i got was around 90000 complie errors...[/QUOTE]
 shocker i think you make things harder than necessary.  I have the mx518...should be same model?  Anyhow, I get everything to work except the one button in the middle, the small one at the bottom... not sure what its supposed to do anyways.  Mouse, back, fwd, wheel, clicks, and sensitivity buttons all work.  The only mod needed is in xorg.conf to change ImPS/2 to ExplorerPS/2 and adding Option "Buttons" "8" and reboot.  It should look like so.
```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"Buttons"		"8"
	Option		"ZAxisMapping"		"4 5"
EndSection
``` 

  Getting that last button to work may be a pain, though, but I can live without it.

---

### Post by shockertwin on 2005-08-08
well the scroll down button works properly now, but the scroll up button goes back. I dont use those anyway though.THANKS!!!

Now if someone could just help me out by telling me how i would go about uninstalling xbindkeys??? thanks.

^^ your a god.

---

### Post by woedend on 2005-08-08
it doesn't do that by default...it must have been one of the programs you installed...bad bad.  Whats cool that i didnt know...the middle button..if you click it on a link it opens in a new tab, rather than a new window.

---

### Post by runt on 2005-08-08
my working MX510 stuff
xorg.conf
```

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mice"
    Option        "Protocol"        "ExplorerPS/2"
    Option        "Emulate3Buttons"    "false"
    Option        "ZAxisMapping"        "4 5"
    Option        "Buttons"        "9"
EndSection

```

end of imwheelrc
```

#Firefox Settings
"^.*firefox$"
None, Left, Alt_L|Left
None, Right, Alt_L|Right
Control_L, Left, Control_L|Left
Control_L, Right, Control_L|Right

#Default Settings
".*"
@Priority = -1000
None, Left, Control_L|Left
None, Right, Control_L|Right
Control_L, Left, Control_L|Left
Control_L, Right, Control_L|Right 

```

---

