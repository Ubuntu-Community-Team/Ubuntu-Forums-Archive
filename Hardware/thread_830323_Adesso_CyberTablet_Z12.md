---
title: "Adesso CyberTablet Z12"
date: 2008-06-15
forum: Hardware
---

### Post by Zizzech on 2008-06-15
Laptop, Gateway MT3707
Ubuntu 8.04
ATI Radeon xPress 200M Graphics Card, ATI Official Driver

I have an [Adesso CyberTablet Z12]("http://www.adesso.com/products_detail.asp?productid=347"), it's seen as another mouse on Ubuntu,
I'd like it to work as a tablet (point precision),
It's using the Wacom driver and Wacom-Tools package.

If someone could, would you help me thoroughly 'cause I'm new to this.

[COLOR="Orange"]lsusb:[/COLOR]
```
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 172f:0031  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000
```

[[COLOR="Blue"]XORG.CONF[/COLOR]]("http://pastebin.com/f4fba4f74")
[[COLOR="Blue"]cat /.../devices[/COLOR]]("http://pastebin.com/f31d45e0a")

---

### Post by Zizzech on 2008-06-15
bump =/

---

### Post by Zizzech on 2008-06-16
bump again =/

---

### Post by calraith on 2008-06-17
Your xorg.conf seems to be missing quite a bit of information about your tablet.  Here's mine.  It works well with my Wacom Graphire4.

```
Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Porn" 0 0
    InputDevice    "WacomMouse"        "SendCoreEvents"
    InputDevice    "Stylus"        "SendCoreEvents"
    InputDevice    "Eraser"        "SendCoreEvents"
    InputDevice    "Pad"
    InputDevice    "Trackball"        "CorePointer"
    InputDevice    "KickassKeyboard"    "CoreKeyboard"
EndSection

Section "Files"
    RgbPath         "/etc/X11/rgb"
    ModulePath      "/usr/lib/xorg/modules"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/X11R6/lib/X11/fonts/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/X11R6/lib/X11/fonts/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "glx"
    Load           "extmod"
    Load           "xtrap"
    Load           "record"
    Load           "dbe"
    Load           "type1"
EndSection

Section "InputDevice"
    Identifier     "KickassKeyboard"
    Driver         "kbd"
EndSection

Section "InputDevice"
    Identifier     "Trackball"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
EndSection

Section "InputDevice"
    Identifier     "Stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "USB" "on"
    Option         "ForceDevice" "ISDV4"
    Option         "PressCurve" "50,0,100,50"
    Option         "Stylus2" "3"
EndSection

Section "InputDevice"
    Identifier     "Eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"
    Option       "PressCurve" "50,0.100,50"
    Option         "USB" "on"
EndSection

Section "InputDevice"
    Identifier     "WacomMouse"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "Mode" "relative"
    Option         "ForceDevice" "ISDV4"
    Option         "USB" "on"
EndSection

Section "InputDevice"
    Identifier     "Pad"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "pad"
    Option         "USB" "on"
EndSection

Section "Monitor"
    Identifier     "MahScreen"
    VendorName     "KDS"
    ModelName      "K-22MDWB"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Card0"
    Driver         "nvidia"
    VendorName     "nVidia Corporation"
    BoardName      "GeForce 7300 GS"
EndSection

Section "Screen"
    Identifier     "Porn"
    Device         "Card0"
    Monitor        "MahScreen"
    Option         "AddARGBGLXVisuals" "True"
    Option         "RenderAccel" "True"
    Option         "AllowGLXWithComposite" "True"
    Option         "backingstore" "True"
    Option         "TripleBuffer" "True"
    SubSection     "Display"
        Viewport    0 0
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       4
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       8
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       15
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       16
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       24
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection
```

---

### Post by Zizzech on 2008-06-17
I'm not sure how to edit my xorg, since I can't find any linux support for my tablet

---

### Post by calraith on 2008-06-17
> **Zizzech said:**
> I'm not sure how to edit my xorg, since I can't find any linux support for my tablet

Ah.  If you can boot to a console and get logged in, you can edit it without having to be in any windowing system.  Before I elaborate, this would be a good time to point out a couple of things:

[LIST=1]
[*]The filesystem in Linux is case-sensitive.  For instance, "Temp, temp, tEmp, tEmP," etc. are not the same file.  "xorg" is not the same thing as "Xorg."
[*]Tab completion is wonderful.  Say you have a directory named "Pseudoantidisestablismentarianismic."  You can type a capital P, maybe an s and an e, and hit the Tab key on your keyboard to fill in the rest.
[/LIST]
Now.  To modify your Xorg conf file, type the following.  Don't enter the stuff in parentheses.  Those are my notes to you.

```
cd /etc
cd X11                         (or cd X<tab>)
sudo cp xorg.conf xorg.bak     (or sudo cp xor<tab> xorg.bak)
sudo nano -w xorg.conf         (or sudo nano -w xor<tab>)
```/etc is the directory containing most of your system-wide configuration files.  The cd command changes directory. sudo runs a command with superuser rights.  cp copies a file.  nano is an easy to use text editor for the console.  -w is a switch for nano that disables automatic line wrapping (which can be bad for configuration files).  xorg.conf is your Xorg configuration file.  Tab completion also works when typing a full path.  sudo nano -w /et<tab>X<tab>xor<tab> will result in sudo nano -w /etc/X11/xorg.conf but without the usual finger cramps.

My xorg.conf is probably different than yours should be.  I have a 22" monitor, and an Nvidia video card.  I hope you will only use my xorg.conf as a guide, and not copy it in its entirety.  The relevant sections would be "Server Layout" (including the stylus, eraser, pad, or whatever else would be applicable to your tablet), and the "Input Device" sections for stylus, eraser, pad, and whatever else.

---

### Post by Zizzech on 2008-06-17
my new [[COLOR="Blue"]xorg.conf[/COLOR]]("http://pastebin.com/f32383cb0")

i don't have /dev/input/wacom, just events 0-9, mice, and mouse 0-2

no point precision =/

---

### Post by calraith on 2008-06-17
Try adding "SendCoreEvents" after "Stylus" in your ServerLayout section.  Also add Synaptics Touchpad and Generic Keyboard to the ServerLayout section.

```
InputDevice     "Stylus"     "SendCoreEvents"
InputDevice     "Synaptics Touchpad"     "CorePointer"
InputDevice     "Generic Keyboard"     "CoreKeyboard"
```

---

### Post by Zizzech on 2008-06-20
After I did that, it stopped responding D=
*after a restart*

---

