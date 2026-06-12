---
title: "eGalax touchscreen support"
date: 2011-05-08
forum: Hardware
---

### Post by V[i]ctor on 2011-05-08
Hello everybody!
I have an Acer ASPIRE laptop with eGalax touchscreen  running Ubuntu 11.04. I can't make the touchscreen work properly. Now  when I trap the screen, cursor moves to the left upper corner and  activates mouse button 1 click. I've tried evtouch and egalax drivers,  both attempts were unsuccessful: I couldn't even find 64-bit evtouch and  I couldn't install egalax driver. Here are some logs and config files:
[quote=evtest /dev/input/event5]Input driver version is 1.0.1
Input device ID: bus 0x3 vendor 0xeef product 0x7253 version 0x210
Input device name: "eGalax Inc. USB TouchController"
Supported events:
  Event type 0 (Sync)
  Event type 1 (Key)
    Event code 256 (Btn0)
    Event code 272 (LeftBtn)
    Event code 273 (RightBtn)
    Event code 320 (ToolPen)
    Event code 325 (ToolFinger)
    Event code 330 (Touch)
  Event type 3 (Absolute)
    Event code 0 (X)
      Value      0
      Min        0
      Max     4095
    Event code 1 (Y)
      Value      0
      Min        0
      Max     4095
    Event code 2 (Z)
      Value      0
      Min        0
      Max     4095
    Event code 3 (Rx)
      Value   3508
      Min        0
      Max     4095
    Event code 4 (Ry)
      Value      0
      Min        0
      Max    32767
    Event code 5 (Rz)
      Value      0
      Min        0
      Max    32767
    Event code 40 (Misc)
      Value      0
      Min        0
      Max       16
  Event type 4 (Misc)
    Event code 4 (ScanCode)
Testing ... (interrupt to exit)
Event: time 1304861971.043192, type 3 (Absolute), code 2 (Z), value 1994
Event: time 1304861971.043199, type 3 (Absolute), code 3 (Rx), value 1800
Event: time 1304861971.043201, -------------- Report Sync ------------
Event: time 1304861971.044121, type 4 (Misc), code 4 (ScanCode), value 90001
Event: time 1304861971.044125, type 1 (Key), code 272 (LeftBtn), value 1
Event: time 1304861971.044137, -------------- Report Sync ------------
Event: time 1304861971.093223, type 3 (Absolute), code 2 (Z), value 1998
Event: time 1304861971.093229, type 3 (Absolute), code 3 (Rx), value 1798
................................[/quote]

[quote=udev rules]ACTION!="add|change", GOTO="xorg_touchscreen_end"
    KERNEL!="event*", GOTO="xorg_touchscreen_end"
    ATTRS{product}!="*alax", GOTO="xorg_touchscreen_end"
    DRIVERS=="evdev"
    ENV{x11_options.minx}="16"
    ENV{x11_options.maxx}="1025"
    ENV{x11_options.miny}="761"
    ENV{x11_options.maxy}="1"
    LABEL="xorg_touchscreen_end"[/quote]

[quote=grub.cfg].......
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root 9ef21ebf-f2d7-446e-8ee5-04e0ee94cd27
     linux    /vmlinuz-2.6.38-8-generic  root=UUID=27069639-e19f-41e1-8709-b2ab96530b23 ro   quiet splash  acpi_osi=Linux acpi_backlight=vendor vt.handoff=7
    initrd    /initrd.img-2.6.38-8-generic
}
.......[/quote]

[quote=xorg.conf]Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
#    InputDevice "touchscreen"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    HorizSync       28.0 - 33.0
#    VertRefresh     43.0 - 72.0
    Option         "DPMS"
    DisplaySize     361 203
    Option         "DPI" "96 x 96"
EndSection

Section "Device"
    Identifier     "Device0"
#    BusID          "PCI:1:0:0"
#    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    Option         "ConnectedMonitor" "CRT"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1366x768_75.00"
    EndSubSection
EndSection

Section "InputDevice"
     Identifier "touchscreen" # I didn't know what tot do so I tried to  comment and uncomment everything, this config I have found on a random  forum
    Driver "evdev"
    Option "Device" "/dev/input/event5"
#    Option "DeviceName" "touchscreen"
#    Option "MinX" "68"
#    Option "MinY" "161"
#    Option "MaxX" "1893"
#    Option "MaxY" "1864"
#    Option "ReportingMode" "Raw"
#    Option "Emulate3Buttons"
#    Option "Emulate3Timeout" "50"
    Option "SendCoreEvents" "On"
    Option "SwapY" "1"
#    Option "Calibrate" "1"
EndSection
[/quote]

[quote=cat  /var/log/Xorg.0.log | grep eGalax][  3313.562] (II) config/udev: Adding  input device eGalax Inc. USB TouchController (/dev/input/event5)
[  3313.562] (**) eGalax Inc. USB TouchController: Applying InputClass "evdev tablet catchall"
[  3313.562] (**) eGalax Inc. USB TouchController: Applying InputClass "eGalax"
[  3313.562] (II) Using input driver 'evdev' for 'eGalax Inc. USB TouchController'
[  3313.562] (**) eGalax Inc. USB TouchController: always reports core events
[  3313.562] (**) eGalax Inc. USB TouchController: Device: "/dev/input/event5"
[  3313.562] (--) eGalax Inc. USB TouchController: Found 3 mouse buttons
[  3313.562] (--) eGalax Inc. USB TouchController: Found absolute axes
[  3313.562] (--) eGalax Inc. USB TouchController: Found x and y absolute axes
[  3313.562] (--) eGalax Inc. USB TouchController: Found absolute tablet.
[  3313.562] (II) eGalax Inc. USB TouchController: Configuring as tablet
[  3313.563] (**) eGalax Inc. USB TouchController: YAxisMapping: buttons 4 and 5
[  3313.563] (**) eGalax Inc. USB TouchController: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  3313.563] (II) XINPUT: Adding extended input device "eGalax Inc. USB TouchController" (type: TABLET)
[  3313.563] (II) eGalax Inc. USB TouchController: initialized for absolute axes.
[  3313.563] (**) eGalax Inc. USB TouchController: (accel) keeping acceleration scheme 1
[  3313.563] (**) eGalax Inc. USB TouchController: (accel) acceleration profile 0
[  3313.563] (**) eGalax Inc. USB TouchController: (accel) acceleration factor: 2.000
[  3313.563] (**) eGalax Inc. USB TouchController: (accel) acceleration threshold: 4
[  3313.563] (II) config/udev: Adding input device eGalax Inc. USB TouchController (/dev/input/mouse0)
[/quote]

---

### Post by AgentWD-40 on 2011-06-17
Hey V[i]ctor,

You used to be able to download the eGalax drivers from [http://home.eeti.com.tw/web20/eGalaxTouchDriver/linuxDriver.htm]("http://home.eeti.com.tw/web20/eGalaxTouchDriver/linuxDriver.htm") for Ubuntu 10.04 and earlier. These drivers do not work with 11.04 though due to a new version of X (1.10). I sent an email to the developer and he told me that he will have a new driver ready in a few days. I'll let you know here when I hear something back.

---

### Post by hidminds on 2011-06-22
Did you hear any news about the new driver from the developer? ;-)

Is there actually any working alternative to the eGalax drivers? Maybe with the usbtouchscreen driver which is loaded by default in Ubuntu 11.04 "Natty" ?

Meanwhile I have found a matching Launpach bug entry: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/549447](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/549447)

---

### Post by AgentWD-40 on 2011-06-24
I haven't heard anything since his first reply. I just sent him another email asking when it will be ready. I'm not sure which other drivers are out there for touch screens, but I remember trying to get some other ones to work back on 10.04. The eGalax driver was the only one that was user friendly. After installation I was given a settings manager tool as well as a calibration tool. I simply had to calibrate it and it was good to go!

I'm going to give them a little bit longer, but if they take too long I may look into updating the driver code myself. This approach will take some time though as I'm not familiar with what they have done.

---

### Post by claytronic on 2011-07-19
Did you ever hear back from the driver guy?

---

### Post by AgentWD-40 on 2011-07-19
It's kind of funny that you're asking today since I just heard back from him this morning. He told me that he's been working on the driver and now has a beta version ready, but it's a little buggy. He asked me to only use it if it's an emergency, but he didn't attach it to his email and it hasn't been updated on the EETI site. His main concern with the beta version is that if you unplug the touch screen USB cable from your machine it will crash your X server. In any case, I'm personally going to be using this with a car PC which is very low risk, so I responded and asked him if he could send me a copy of the beta version. I'll let you know when I hear back!

---

### Post by claytronic on 2011-07-20
That's good news. Thanks for the update.

---

### Post by AgentWD-40 on 2011-07-20
No problem! :D So are you up to anything cool with your touchscreen?

---

### Post by serafxxx on 2011-07-20
Yes! I'm also waiting for it (only 32-bit version)!! Please, post it here as soon as possible)

---

### Post by serafxxx on 2011-07-27
Any news?

---

### Post by serafxxx on 2011-08-05
news?

---

### Post by AgentWD-40 on 2011-08-13
EETI just put up the new driver a couple days ago!! I just installed it and since running the calibration it's been working great! Here is how to get it working:

1. Download the driver from [http://home.eeti.com.tw/web20/eGalaxTouchDriver/linuxDriver.htm]("http://home.eeti.com.tw/web20/eGalaxTouchDriver/linuxDriver.htm") and save it in your Downloads folder (usually this happens by default through Firefox).

2. Open a terminal and enter the command (without the quotes) "sudo su", then enter your password.

3. Enter the command (without the quotes) "cd Downloads" followed by "./setup.sh"

4. Follow the simple instructions given in your terminal.

5. Reboot your computer once setup has completed.

6. Push Alt+F2 and type "eGalaxTouch" then press enter.

7. From here you can run calibation and set up your screen. After calibration it should work like a charm!

---

### Post by serafxxx on 2011-08-15
And I can't got it working! wrote to developers, here is what they answered:
[FONT=Times New Roman][SIZE=2][COLOR=#1f497d][COLOR=#1F497D]
[/COLOR][/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2][COLOR=#1f497d][COLOR=#1F497D]>Unfortunately, you may be victim of counterfeit.[/COLOR][/COLOR][/SIZE][/FONT]
  [FONT=Times New Roman][SIZE=2][COLOR=#1f497d][COLOR=#1F497D]>Please refer below link:[/COLOR][/COLOR][/SIZE][/FONT]
  [FONT=Times New Roman][SIZE=2][COLOR=#1f497d][COLOR=#1F497D][>http://home.eeti.com.tw/web20/URG.html]("http://home.eeti.com.tw/web20/URG.html")[/COLOR][/COLOR][/SIZE][/FONT]
>[FONT=Times New Roman][SIZE=2][COLOR=#1f497d][COLOR=#1F497D]Please contact your supplier to solve your problem.[/COLOR][/COLOR][/SIZE][/FONT]

Drivers intalled ok, but touchscreen don't work.

But I got it working with usbtouchscreen module. Only can't calibrate. 
Standart ubuntu callibration utitlity gives wrong parameters.

Could anybody explain the meaning of calibration params MIN_X and MAX_X ?

---

### Post by AgentWD-40 on 2011-08-15
Hey serafxxx, what type of screen are you using? Under a fresh install of Natty the screen at least reacted to touch. The cursor would just jump all over the screen and it wasn't really usable. Before I installed this new driver I did a clean install of Natty (32-bit). I ran all the OS updates after the touchscreen driver was installed.

---

### Post by serafxxx on 2011-08-16
I'm using eGalax touchscreen. Yes, you are right, it's working out from the box:) if you connect touchscreen and reboot (this was the problem)

Now I can't calibrate it with standart X calibration utility - it returns wrong data.
I tryed to calibrate it with hands, but can't do it preciacely.

Drivers from eGalax and their calibration utility are not working for me.

---

### Post by serafxxx on 2011-08-19
Supplyer showed another set of drivers for my screen: [http://www.fancyview.com/support/support_en.asp](http://www.fancyview.com/support/support_en.asp) , but there is no one for Ubuntu..
Any way will try them soon.

---

### Post by serafxxx on 2011-08-19
> Did you actually listen to back again using the driver guy?
Sorry, can't understand you..

---

