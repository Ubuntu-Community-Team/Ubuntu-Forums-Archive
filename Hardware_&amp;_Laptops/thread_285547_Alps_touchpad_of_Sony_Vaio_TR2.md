---
title: "Alps touchpad of Sony Vaio TR2"
date: 2006-10-26
forum: Hardware &amp; Laptops
---

### Post by scubajeff on 2006-10-26
Just upgrade to Edgy, the udev program has been upgraded, so there are some changes to the process of configuring Alps touchpad, here it's:

1. Find out what device handle the hardware

```
cat /proc/bus/input/devices
```

2. Found out the handlers for Alps Glidepoint device in step 1, on my machine it's event3. Use it in the following command to find out how to identify the device's description in udev. 
```
udevinfo -a -p `udevinfo -q path -n **/dev/input/event3**`
```

Here's the output of the above commmand on my machine:
```

  looking at device '/class/input/input3/event3':
    KERNEL=="event3"
    SUBSYSTEM=="input"
    SYSFS{dev}=="13:67"

  looking at device '/class/input/input3':
    ID=="input3"
    BUS=="input"
    DRIVER==""
    SYSFS{modalias}=="input:b0011v0002p0008e7321-e0,1,2,3,k110,111,112,145,14A,r0,1,a0,1,18,mlsfw"
    SYSFS{uniq}==""
    SYSFS{phys}=="isa0060/serio1/input0"
    SYSFS{name}=="AlpsPS/2 ALPS GlidePoint"

  looking at device '/devices/platform/i8042/serio0':
    ID=="serio0"
    BUS=="serio"
    DRIVER=="psmouse"
    SYSFS{resync_time}=="0"
    SYSFS{resetafter}=="5"
    SYSFS{resolution}=="200"
    SYSFS{rate}=="100"
    SYSFS{protocol}=="AlpsPS/2"
    SYSFS{bind_mode}=="auto"
    SYSFS{modalias}=="serio:ty01pr00id00ex00"
**    SYSFS{description}=="i8042 Aux Port"**

  looking at device '/devices/platform/i8042':
    ID=="i8042"
    BUS=="platform"
    DRIVER=="i8042"

  looking at device '/devices/platform':
    ID=="platform"
    BUS==""
    DRIVER==""

```


4. The useful part of the above output is highlighted. Then create a file: "/etc/udev/rules/55-alps.rules", with the "SYSFS{description}" part matching the output of udevinfo. File content:

```

BUS=="serio", SYSFS{description}=="i8042 Aux Port", KERNEL=="event?", SYMLINK+="input/alps"

```

With the above udev rule, the udev process will create a symbolic link "/dev/input/alps" pointing to the correct event handler device file during booting.


5. Edit /etc/X11/xorg.conf file. 

Use "/dev/input/alps" for Device and "event" for Protocol in xorg.conf:
```

Option	"Device"	"/dev/input/alps"
Option	"Protocol"	"event"

```

To turn on the “double tap and drag” function, turn off GuestMouseOff option:
```
Option	"GuestMouseOff"	"0"
```

Ok, now reboot, and you will never miss your Alps again.


Sample xorg.conf file attached here:
```

Section "InputDevice"
        Identifier      "ALPS"
        Driver          "synaptics"
        Option          "AlwaysCore"
        Option          "Device"                "/dev/input/alps"
        Option          "Protocol"              "event"
        Option          "LeftEdge"              "120"
        Option          "RightEdge"             "830"
        Option          "TopEdge"               "120"
        Option          "BottomEdge"            "650"
        Option          "FingerLow"             "14"
        Option          "FingerHigh"            "15"
        Option          "MaxTapTime"            "180"
        Option          "MaxTapMove"            "110"
        Option          "ClickTime"             "0"
        Option          "EmulateMidButtonTime"  "75"
        Option          "VertScrollDelta"       "10"
        Option          "HorizScrollDelta"      "0"
        Option          "MinSpeed"              "0.45"
        Option          "MaxSpeed"              "0.75"
        Option          "AccelFactor"           "0.020"
        Option          "EdgeMotionMinSpeed"    "200"
        Option          "EdgeMotionMaxSpeed"    "200"
        Option          "UpDownScrolling"       "1"
        Option          "CircularScrolling"     "0"
        Option          "CircScrollDelta"       "0.1"
        Option          "CircScrollTrigger"     "2"
        Option          "GuestMouseOff"         "0"
        Option          "SHMConfig"             "true"
EndSection

```

---

### Post by eems01 on 2006-10-30
Thanks again subajeff (you also were a great help with dapper).  I think there is one correction for the above udev folder path, it should be: 
 
"/etc/udev/rules.d/55-alps.rules"

This would make a great ALPS HOWTO since it looks like a lot of people are still having trouble with their touchpads.

Compaq Presario R3200 with Edgy

---

### Post by mjpoetic on 2006-11-05
Great How-to...but it didn't work for me...yet.  I just had a quick question.  Is it supposed to read **[COLOR=Sienna]"event?"[/COLOR]** in the **[COLOR=Navy]/etc/udev/rules.d/55-alps.rules[/COLOR]** file?  That is...mine reads:

[B][COLOR=Green] BUS=="serio", SYSFS{description}=="i8042 Aux-3 Port", KERNEL==[COLOR=Sienna]"event?"[/COLOR], SYMLINK+="input/alps"

[/COLOR][/B][COLOR=Green][COLOR=Black]So should it instead read "event6" (in my case) as given by the **udevinfo** command?  This is what I got from the **cat /proc/bus/input/devices** command:

[/COLOR][/COLOR]```
I: Bus=0011 Vendor=0002 Product=0008 Version=7321
N: Name="AlpsPS/2 ALPS GlidePoint"
P: Phys=isa0060/serio4/input0
S: Sysfs=/class/input/input7
H: Handlers=mouse1 event6 ts1 
B: EV=f
B: KEY=420 0 70000 0 0 0 0 0 0 0 0
B: REL=3
B: ABS=1000003

```[COLOR=Green][COLOR=Black]

This is what the **udevinfo** command gives in full:

[/COLOR][/COLOR]```

$ udevinfo -a -p `udevinfo -q path -n /dev/input/event6`

looking at device '/class/input/input7/event6':
    KERNEL=="event6"
    SUBSYSTEM=="input"
    SYSFS{dev}=="13:70"

  looking at device '/class/input/input7':
    ID=="input7"
    BUS=="input"
    DRIVER==""
    SYSFS{modalias}=="input:b0011v0002p0008e7321-e0,1,2,3,k110,111,112,145,14A,r0,1,a0,1,18,mlsfw"
    SYSFS{uniq}==""
    SYSFS{phys}=="isa0060/serio4/input0"
    SYSFS{name}=="AlpsPS/2 ALPS GlidePoint"

  looking at device '/devices/platform/i8042/serio3':
    ID=="serio3"
    BUS=="serio"
    DRIVER=="psmouse"
    SYSFS{resync_time}=="0"
    SYSFS{resetafter}=="5"
    SYSFS{resolution}=="200"
    SYSFS{rate}=="100"
    SYSFS{protocol}=="AlpsPS/2"
    SYSFS{bind_mode}=="auto"
    SYSFS{modalias}=="serio:ty01pr00id00ex00"
    SYSFS{description}=="i8042 Aux-3 Port"

  looking at device '/devices/platform/i8042':
    ID=="i8042"
    BUS=="platform"
    DRIVER=="i8042"

  looking at device '/devices/platform':
    ID=="platform"
    BUS==""
    DRIVER==""

```

---

### Post by scubajeff on 2006-11-06
mjpoetic,

Yes, it should read "event?" in the /etc/udev/rules.d/55-alps.rules file. Do you see a symbolic link file "alps" in your /dev/input directory?

---

### Post by mjpoetic on 2006-11-07
> **scubajeff said:**
> mjpoetic,

Yes, it should read "event?" in the /etc/udev/rules.d/55-alps.rules file. Do you see a symbolic link file "alps" in your /dev/input directory?

Yes I do.  Well, I seem to have done what you did.  The pad works fine except I can't move up and down on web pages using the scrolling at the side.  Like others have said...Dapper was okay with this when I used the xserver-xorg-input-synaptics_0.14.3+seriouslythistime-0ubuntu3_i386.deb for my synaptics driver.  I tried installing that on edgy, but nothing.

By the way, I should mention that I am using a VAIO VGN-FS920, I don't know if that makes a difference (but i don't think it should).

---

### Post by scubajeff on 2006-11-07
Mine is xserver-xorg-input-synaptics 0.14.6-0ubuntu3, which I believe comes with Edgy. And the scrolling and dragging work just fine. Maybe you should take a look at your xorg.conf.

---

### Post by mjpoetic on 2006-11-07
> **scubajeff said:**
> Mine is xserver-xorg-input-synaptics 0.14.6-0ubuntu3, which I believe comes with Edgy. And the scrolling and dragging work just fine. Maybe you should take a look at your xorg.conf.

Is there a guide somewhere for the options?  I am just using everyone elses at the moment (e.g., like yours for example).  I think mine needs a bit more customization...that's what I love about linux though!!

---

### Post by mjpoetic on 2006-11-09
@**scubajeff[B]:** [/B]Just a follow-up to this issue.  Everything seems to be working fine...and I didn't change any options in my xorg.conf file (so it looks exactly as your setup example in post#1).  I read in another thread where switching to tty1 and then back to tty7 would do the trick of the alps touchpad being configured correctly.  This is annoying to have to do every boot up...but at least it works.

Why this worked for me....I can't say, but you may want to add that to the guide for people who are trying to troubleshoot.

---

