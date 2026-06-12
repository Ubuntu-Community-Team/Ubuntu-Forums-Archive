---
title: "Monitor Out of Range after installing nvidia-glx"
date: 2007-05-12
forum: Hardware &amp; Laptops
---

### Post by quaunaut on 2007-05-12
I was following the MaximumPC article here([http://www.maximumpc.com/linux?page=0%2C2)](http://www.maximumpc.com/linux?page=0%2C2)), and after installing my Nvidia drivers, upon reboot I was out of range.

I tried going into xorg.conf, and put in HorizSync & VertRefresh values, but I wasn't sure about either. The only refresh rate I'm sure my monitor *always* works at is 60hz, so I was setting the values to 60.0.

How can I fix this?

---

### Post by heimo on 2007-05-12
Monitor and graphics card model would be helpful information - and also relevant parts from your xorg.conf. You could try following these instructions / tips:
[HOWTO: Solving resolution/refresh rate problems in Xorg]("http://www.ubuntuforums.org/showthread.php?t=83973")

---

### Post by quaunaut on 2007-05-12
Monitor is a VX2025wm, and my card is a NVidia GeForce 7900GT 256mb.

As to relevent parts, I honestly have no clue how I would get that to you.

---

### Post by heimo on 2007-05-12
Yeah, sorry - I was vague. Important parts are Device, Monitor and Screen sections. Mine looks like:


```
Section "Device"
        Identifier      "nVidia Corporation G71 [GeForce 7300 GS]"
        Driver          "nv"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "CM752"
        Option          "DPMS"
        HorizSync       40-80
        VertRefresh     60-90
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation G71 [GeForce 7300 GS]"
        Monitor         "CM752"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1440x1050" "1280x1024" "1024x768"
                Virtual         1600    1200
        EndSubSection
EndSection


```

---

### Post by quaunaut on 2007-05-12
Nono, what I mean is, I don't know how to get that information from where I am. I'm on the same PC, but in XP. I know my Screen section had half a dozen lines of dozens of resolutions on it though.

---

### Post by heimo on 2007-05-12
You should be able to change to virtual console by hitting ctrl+alt+F2 or by booting to recovery mode (select it at grub menu), log in and reconfigure using instructions in the howto I linked above or here:
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

You can view file contents using less, for example:
```
less /etc/X11/xorg.conf
```

q to quit

---

### Post by quaunaut on 2007-05-12
Yeah, but then how would I take that, and get it into a Browser? If only manual copy is possible, well, I guess I'm staying up late.

I just followed the main piece of that article- setting my HorizSync to 30-82, and my VertRefresh to 50-75. Still nothing.

I was looking through the page summore though, and noticed the bottom part- thats only for the nvidia package, not the nvidia-glx package, correct?

---

### Post by heimo on 2007-05-12
To get at least some GUI, you could run:
```
sudo dpkg-reconfigure xserver-xorg
```

And choose nv instead of nvidia.

---

### Post by quaunaut on 2007-05-12
Okay, so I went and I used that GUI, and now I've got more issues than before. My middle mouse button doesn't work(Should I have said yes to 3 button mouse emulation? I figured since I didn't want to have to click left and right to use the middle, why emulate it? Would enabling that turn on my scroll wheel click?), and furthermore, its like I never installed a graphics package at all- and Ubuntu can't tell what my resolutions are, so now its just defaulting me to 1024x768. When going into the screen resolution menu, I get no widescreen values, and nothing higher than 1024x768 anyhow(I need 1680x1050).

During the GUI, I even selected(or so I think) 1680x1050, and now I've got nothing. The reason I say 'so I think' is 'cause I couldn't figure out how to select any of the resolution options- I wanted to select 1680x1050, so I highlighted it out of all the other resolutions, and pressed enter. Also, I noticed upon doing the thing a second time(to make sure of my settings), it hadn't saved my refresh rates, or monitor version.

But now that I can access my terminal and browser, here is my xorg.conf:

```
Section "Device"
        Identifier      "NVIDIA GeForce 7900GT"
        Driver          "nvidia"
        Busid           "PCI:3:0:0"
        Videoram        256000
        Option          "AddARGBVisuals"        "True"
        Option          "AddARGBGLXVisuals"     "True"
        Option          "NoLogo"        "True"
EndSection

Section "Monitor"
        Identifier      "VX2025wm"
        Option          "DPMS"
        Horizsync       30-82
        Vertrefresh     50-75
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA GeForce 7900GT"
        Monitor         "VX2025wm"
        Defaultdepth    24
        SubSection "Display"
                Depth   1
                Modes           "1024x768"      "800x600"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   4
                Modes           "1024x768"      "800x600"       "640x480"
       EndSubSection
        SubSection "Display"
                Depth   8
                Modes           "1024x768"      "800x600"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   15
                Modes           "1024x768"      "800x600"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   16
                Modes           "1024x768"      "800x600"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   24
                Modes           "1024x768"      "800x600"       "640x480"
        EndSubSection
EndSection
```

Note that it seems it saved everything but my resolution selection. The HorizSync and VertRefresh rates look correct.

---

### Post by heimo on 2007-05-12
You could now add missing resolutions manually. Hmm.. I haven't paid attention before, but I now notice that my "mouse section" actually has 3 button emulation enabled even though I have regular 3 button wheel mouse. Like this:
```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

```Yeah those HorizSync / VertRefresh lines are probably right (I didn't check, but looks like ok). You could always try nv driver instead of nvidia, but you'll then lose 3d acceleration.

---

### Post by quaunaut on 2007-05-12
Do I have to restart for my changes to xorg.conf to take effect? If not, then they aren't working.

I'm getting no options other than a few basic non-widescreen resolutions, and no refresh rates higher than 50.

And my mouse wheel click doesn't work.

---

### Post by heimo on 2007-05-12
> **quaunaut said:**
> Do I have to restart for my changes to xorg.conf to take effect?

You need to restart Xorg. Usually logging out and hitting ctrl+alt+backspace is enough.

---

### Post by quaunaut on 2007-05-12
Well, no go there when I entered "1680x1050" under the 24 bit depth option. I'm guessing because it was trying a refresh rate of 50.

How can I force it to use a refresh rate of just 60?

Edit: Okay, I tried putting "1680x1050" as the second option, after 1024x768, but for some reason it has a refresh rate by default of 60- and I notice that now, the same drivers I just enabled are all disabled.

Now, this brings up an issue for me. My ubuntu install isn't saving **anything** of my settings. Whenever I want to connect to the internet, I've gotta manually input my secondary DNS, each and every time. Why is this? Why doesn't it save it? This also leads me to ask why my drivers are suddenly turned off. Grr, etc.

Edit: Now that I turned them back on, my refresh rate is at 50. Can't I have a 60 refresh rate and my drivers at the same time?

---

### Post by quaunaut on 2007-05-12
Bump.

---

