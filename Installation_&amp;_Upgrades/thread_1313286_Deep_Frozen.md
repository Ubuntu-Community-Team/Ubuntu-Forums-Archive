---
title: "Deep Frozen"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by FelixS on 2009-11-03
I have installed Ubuntu 9.10 64-bit version in my computer, all fine during the installation, but when I turn on this, and enter to the desktop, it works for a few seconds, then all stops; when I say all, is all, it's like a pause in a movie. What's causing this?:confused:

---

### Post by RedSingularity on 2009-11-03
Have you taken a look at the error logs in /var/logs.

---

### Post by FelixS on 2009-11-03
Where can I get there? I am a beginner in Ubuntu.

Note: I have founded somebody more with a similar problem in this forum, he solved the problem. Was something about the drivers of the Intel GMA 950 Graphics Accelerator, but I don't know how to install them if I can't use the desktop of Ubuntu. I have a Intel(R) 82945G Express Chipset Family Graphics Accelerator. I'm waiting an answer there and here. Thanks.

---

### Post by RedSingularity on 2009-11-03
In a terminal type this...........

cat /etc/X11/xorg.conf

Post the whole output here.

---

### Post by FelixS on 2009-11-05
> **RedSingularity said:**
> In a terminal type this...........

cat /etc/X11/xorg.conf

Post the whole output here.

When I try to do this, it says to me that the file does not exists. I explored the hard drive in the few seconds when Ubuntu works (no more than 15) getting into /etc/X11 and there's no any file named xorg.conf. I only can see there this:
Folders:
[LIST]
app-defaults
cursors
fonts
xinit
xkb
Xresources
Xsession.d
[/LIST]
Archives:
[LIST]
[*]default-display-manager
[*]rgb.txt
[*]X (executable)
[*]Xsession
[*]Xsession.options
[*]XvMCConfig
[*]Xwrapper.config
[/LIST]
Is one of them the archive that I need to edit or there's another option?

Thanks.

---

### Post by RedSingularity on 2009-11-05
Ok you need to create one then.  Once you boot before the computer freezes push CTL + ALT + F1 and you will be in a terminal.

First stop the xserver with this......

sudo /etc/init.d/gdm stop

then configure a xorg file with this.....

sudo Xorg -configure

REBOOT

Now you should have a file.

---

### Post by FelixS on 2009-11-07
I did it all. Ubuntu is now working. Thanks.

Here is the content of the new archive: 
```
Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "record"
    Load  "dri2"
    Load  "glx"
    Load  "dri"
    Load  "dbe"
    Load  "extmod"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"                # [<bool>]
        #Option     "SWcursor"               # [<bool>]
        #Option     "ColorKey"               # <i>
        #Option     "CacheLines"             # <i>
        #Option     "Dac6Bit"                # [<bool>]
        #Option     "DRI"                    # [<bool>]
        #Option     "NoDDC"                  # [<bool>]
        #Option     "ShowCache"              # [<bool>]
        #Option     "XvMCSurfaces"           # <i>
        #Option     "PageFlip"               # [<bool>]
    Identifier  "Card0"
    Driver      "intel"
    VendorName  "Intel Corporation"
    BoardName   "82945G/GZ Integrated Graphics Controller"
    BusID       "PCI:0:2:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection
```

Is that all OK?

---

### Post by RedSingularity on 2009-11-07
It seems you have the proper driver installed for your hardware. 

Just to make sure port the output of 

lspci | grep VGA

---

### Post by FelixS on 2009-11-08
Here is it. lspci | grep VGA shows this: :-k
```
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
```Thanks.
But there`s something more, when I try to enable the visual effects in Screen Preferences, it starts to search the drivers and then says to me that the effects could not be enabled[-X
:sad: I like the effects of Ubuntu.

---

### Post by RedSingularity on 2009-11-08
Well it would seem that you do have the correct driver installed.

Check----- System>Admin>Hardware Drivers-----see if you can activate drivers from there.

---

### Post by FelixS on 2009-11-08
It starts to search the drivers and the shows a window that tells me that ¨exclusive controllers are not used in this system¨, and the window is empty, there`s nothing to activate.

---

### Post by RedSingularity on 2009-11-08
Thats what i though.  You are using an onboard graphics chip.  That may be the best you can have with that intel chip graphics wise.  Is it still freezing?

---

### Post by FelixS on 2009-11-08
No, theres no more freezings and issues except that. I have a nVidia GeForce 9400 GT but I can`t use this in this computer right now by a problem in the hardware, that`s other history. If are you interested in give me a idea to fix that, tell me.

Thanks for all.=D>

---

### Post by RedSingularity on 2009-11-08
Whats wrong with the 9400 exactly?

---

### Post by FelixS on 2009-11-08
The problem I think is not in the 9400, I think it may be font of power.
The problem started in the boot of the computer, it doesn`t started the BIOS, turned on all except the leds of the power button and of the hard drive. I first thinked in the RAM memory, I cheked that and it seems OK, I pull out this and then I install it again; 1 week doing that to turn on the computer. Then, it doesn`t started again, then I checked the whole computer, all the connections seems OK, I tried moving a jumper to clear the BIOS to it original configuration, 4 days doing that to turn on the computer.
Then nothing of that works, I tried pulling out the on-board battery and installing it again, only 3 days working with that method.
I was very angry, having a good computer, and can`t use this.:mad:
I tried then unconnecting some cables, nothing, then i pull out the 9400 and the computer turns on, but slower and now it takes a second between turning all in the case and turning on the frontal leds, it isn`t like when was OK. This video card have worked 3 months with no problems, and I have the same configuration that I have 3 months ago. Have you a idea about what`s causing this?

PS: I am not an expert in computers, only a curious user, a fifteen years old curious user interested to learn more.:smile:

---

### Post by Alex De Duck on 2009-11-08
> **RedSingularity said:**
> Ok you need to create one then.  Once you boot before the computer freezes push CTL + ALT + F1 and you will be in a terminal.

First stop the xserver with this......

sudo /etc/init.d/gdm stop

then configure a xorg file with this.....

sudo Xorg -configure

REBOOT

Now you should have a file.

See, I had the same problem. 

I took the steps, but when I put reboot the command was invalid, so I restarted it manually. But now when I look for the file, it's not there!

---

### Post by RedSingularity on 2009-11-08
Ok so when you insert the 9400 it wont even boot the bios?

---

### Post by FelixS on 2009-11-08
> **RedSingularity said:**
> Ok so when you insert the 9400 it wont even boot the bios?
Right. The BIOS and the leds.

---

### Post by RedSingularity on 2009-11-08
Sounds to me like a bad/burnt graphics card.

---

### Post by FelixS on 2009-11-08
> **Alex De Duck said:**
> See, I had the same problem. 

I took the steps, but when I put reboot the command was invalid, so I restarted it manually. But now when I look for the file, it's not there!
You will not find that file in /etc/X11. It was saved in your personal folder. In my computer was saved there.:-k

---

### Post by Alex De Duck on 2009-11-08
> **FelixS said:**
> You will not find that file in /etc/X11. It was saved in your personal folder. In my computer was saved there.:-k
Oh crap. I'm such a noob. 

I hope I didn't kill anything, and thank you! I really appreciate your answer.

---

### Post by FelixS on 2009-11-08
> **RedSingularity said:**
> Sounds to me like a bad/burnt graphics card.
But supposing that it was burnt (I had a GeForce 8400 GS, and it was burnt, i`m sure), What causes this?

About the 8400 GS, the problem wasn`t similar, it turned on properly but the 3D graphics were distorted and sometimes the computer got frozen (in Windows XP).

---

### Post by RedSingularity on 2009-11-08
Mishandling the card can damage it.  Even small static from your hands can burn it.  I have also had time when i inserted it wrong and it burned out too.  Sometimes it just happens though.  Its not necessarily the users fault.

---

### Post by FelixS on 2009-11-08
> **RedSingularity said:**
> Mishandling the card can damage it.  Even small static from your hands can burn it.  I have also had time when i inserted it wrong and it burned out too.  Sometimes it just happens though.  Its not necessarily the users fault.
:shock: I wish that this card is OK, I hope so. I will try to install this in another computer.

Apart from the 9400, what can cause the original problem (the boot)?

---

### Post by RedSingularity on 2009-11-08
Bad electrical circuits in the card can cause that.  I have had it happen with graphics cards and RAM.  Most of the time though i would just pull out the card and clean the PCI slot with compressed air.  May just be some dust.

---

### Post by FelixS on 2009-11-08
It`s all clean, is not the dust. About the electrical circuits, from where are you referring, the power supply, the motherboard, the video card, or my house?

---

### Post by RedSingularity on 2009-11-08
On the video card itself.  Are you going to plug this card into another computer?

---

### Post by FelixS on 2009-11-08
Yes, I will try.

---

### Post by RedSingularity on 2009-11-08
Great.  Let me know what happens.

---

### Post by FelixS on 2009-11-17
I didn't have tested it in another computer, but my father asked me why the computer doesn't worked and I said why, but when I installed it in my computer to prove it, the computer worked, it's very queer. I don't know what's happening in this computer? It's crazy. I'm not joking.

---

### Post by RedSingularity on 2009-11-17
Did you try putting the graphics card in another computer to see if it works?

---

### Post by FelixS on 2009-11-18
No,[-X I didn't have a chance to do this, because I'm really busy in my college (place where I thought test the video card in another PC).

---

