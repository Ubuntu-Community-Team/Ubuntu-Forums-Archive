---
title: "Tablet mode on Toshiba Tecra M4"
date: 2005-12-23
forum: Hardware &amp; Laptops
---

### Post by glacierre on 2005-12-23
Hello!, this is my first post on this forums.

I have a toshiba tecra m4 (a laptop convertible to tabletpc), and don't know how to make it respond to the stylus.

I'm using Ubuntu Breezy with wacom-tools and the wacom modules for xorg installed.

I've been following some instructions from a gentoo howto, it says that I should do:

[INDENT]setserial /dev/ttyS0 port 0x0338 irq 4 autoconfig
wacdump -f c100 /dev/ttyS0[/INDENT]

With this, I get a: "WacomOpenTablet: Invalid argument". 
Same result with ttyS1. I've also tried with port number 03f8 (since the windows device manager tells the wacon is on the 0338-03f8 )

I don't know what more to do &#191;can you help me? Thanks

---

### Post by 23meg on 2005-12-23
You may not need to set your serial port with setserial; the Tecra M4 digitizer usually gets intialized with /dev/ttyS12 to 14 in Ubuntu installations. Enter the following commands one by one and see if you can find port 0x0338. Once you find the correct device, enter it as an argument to wacdump and see if you can get it to respond to stylus movement.

```
setserial /dev/ttyS12
setserial /dev/ttyS13
setserial /dev/ttyS14
```

---

### Post by glacierre on 2005-12-23
Thank you very much!, it was the ttyS14. Now I'll deal with the xorg.conf to use it.

---

### Post by glacierre on 2005-12-23
Ok, got the xorg.conf from [http://gentoo-wiki.com/HARDWARE_Toshiba_Tecra_M4](http://gentoo-wiki.com/HARDWARE_Toshiba_Tecra_M4), almost everything seems to work fine.

Now, xrandr can rotate the screen, but the stylus remains "horizontal"

xsetwacom set "stylus" Rotate CCW

fails, googling about it seems that there's a patch, but the idea of compiling the whole x system looks horrifying. Is there another way?

By the way, how do I perform middle and right clics with the pen?

---

### Post by 23meg on 2005-12-23
That patch is already compiled into the version of the driver that Ubuntu ships. I'm proud to have submitted a last minute bug that led to it being correctly implemented in Breezy :cool: What error do you get when you do ```
xsetwacom set stylus rotate CCW
```?

I get errors when I do it sometimes, but they're only cosmetic; the rotation works even when I get errors. Plus, make sure you put this line in the "Device" section of your xorg.conf```
       Option 	        "RandRRotation" "on"
```

---

### Post by glacierre on 2005-12-24
You were right, it gave an error but the stylus gets rotated.

Thanks.

---

### Post by 23meg on 2005-12-25
Cool, is everything working fine now? Here are my tablet settings in xorg.conf should you or others need them. I think the "Button" line will  help you with clicking. ```
Section "InputDevice"
    Driver        "wacom"
    Identifier    "cursor"
    Option        "Device"        "/dev/ttyS14"
    Option        "InputFashion" "Tablet"
    Option        "ForceDevice"    "ISDV4"
    Option        "Name" "GRAPHIRE / INTUOS (SERIAL)"
    Option        "SendCoreEvents" "on"
    Option        "Type"          "cursor"
    Option        "Mode"          "absolute" 
    Option        "Vendor" "WACOM"
    Option        "Speed"         "3.0"
    Option        "Threshold"     "1"
    Option        "Tilt"          "on"
    Option	     "Button2"	"3"
    #Option    "DebugLevel"    "10"
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "stylus"
    Option        "Device"        "/dev/ttyS14"
    Option        "Type"          "stylus"
    Option        "InputFashion" "Pen"
    Option        "SendCoreEvents" "on"
    Option        "Name"          "GRAPHIRE / INTUOS Stylus (SERIAL)"
    Option        "ForceDevice"    "ISDV4"
    Option        "Mode"          "absolute"
    Option        "Vendor" "WACOM"
    Option        "Tilt"          "on"
    Option        "TiltInvert"    "on"
    Option        "Threshold"     "1"
    Option	     "Button2"	"3"
   #Option    "DebugLevel"    "10"
EndSection

Section "InputDevice"
 Driver       "wacom"
 Identifier   "eraser"
 Option       "Device" "/dev/ttyS14"
 Option       "InputFashion" "Eraser"
 Option       "Name" "GRAPHIRE / INTUOS Eraser (SERIAL)"
 Option       "Type" "eraser"
 Option       "Mode" "absolute"
 Option       "Vendor" "WACOM"
 Option       "ForceDevice" "ISDV4" 
 Option        "SendCoreEvents" "on"
EndSection
```

---

### Post by anasofiapaixao on 2006-06-16
Hi, this is my first post just to put in my 2 cents of advice...

I am also using a Tecra M4 Tablet and was having nightmares setting the pen to work, but after reading this post I tried to scan ALL ports' serials; and finally found beloved 0x0338 on... ttyS4!

For anyone having trouble after wacom modules installed, scanning all the ports and then copy pasting the settings above and only altering "Device" [port location] worked for me ;)

---

### Post by sitka on 2007-11-15
setserial /dev/input/wacom

/dev/input/wacom, UART: 16550A, Port: 0x0338, IRQ: 4


it is pointed to /dev/input/wacom in my /etc/X11/xorg.conf

it still doesn't work.    this worked well in fiesty out of the box....

---

### Post by tovarish_luca on 2008-01-28
Hi guys! I just installed Ubuntu Gutsy and now way I can get the touchscreen working :-( I tried modifying the xorg.conf but no success...The watcom device is on ttyS0. i attached my xorg.conf. Hope you can help...it`s the only thing not working here. Thanks very much!
Luca

---

### Post by bradlis7 on 2008-02-26
I know this post is old, but can someone tell me if i'm required to use the stylus to use the touchscreen? I ordered it off ebay, and didn't get the stylus, so I'm wondering if I configured it wrong, or if it's just the fact that I don't have the stylus.

---

### Post by nmz787 on 2008-02-29
yes you need the stylus, there is space for a backup/extra stylus next to the battery.

---

### Post by CrazyAzn65 on 2008-05-19
um yea i tried to this to get the rotate thing to work and yea it didnt work :( it only messed up the configuration of the stylus for example the mouse with move in a different direction that i want it to. =/ newho yea i fixed the stylus and got it back to normal but am still looking for a way to make the screen rotate wen i go into tablet mode.

---

