---
title: "Gutsy Intel 855GM Tv Out"
date: 2007-11-22
forum: Hardware &amp; Laptops
---

### Post by Mulefire on 2007-11-22
I'm using a clean install of Gutsy Gibbon on an IBM ThinkPad R51 with the Intel 82852/855GM video hardware. When I run xrandr I see my LCD and VGA outputs but no TV output. According to what I have seen online I would expect to see 'TV Disconnected' at the end of the output or something similar. As it is I see no mention of TV only VGA and LVDS. I used to have the TV output working under Feisty Fawn and the old i810 driver but for the life of me can't get it working now.

I've tried blowing away my xorg.conf and reconfiguring again but there is nothing in the resulting xorg that speaks to the TV output. It looks like the hardware isn't being detected at all, so none of my config changes or other configurations are having any affect.

My current xorg looks like the following (note that all the 3d graphics stuff is commented out since when I run dual screen at work the resolution is to large for DRI etc).

```

Section "Device"
        Identifier      "Intel Corporation 82852/855GM Integrated Graphics Device"
        Driver          "intel"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Monitor"
        Identifier      "ACER AL2223W"
        Option          "DPMS"
        HorizSync       31-81
        VertRefresh     56-75
EndSection

Section "Monitor"
        Identifier      "External TV"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 82852/855GM Integrated Graphics Device"
        Monitor         "Generic Monitor"
        Option          "monitor-VGA" "ACER AL2223W"
        Option          "monitor-TV" "External TV"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                #Virtual         2704 1050                                                                                                                             
                Virtual         1024 768
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        #InputDevice     "stylus"       "SendCoreEvents"                                                                                                               
        #InputDevice     "cursor"       "SendCoreEvents"                                                                                                               
        #InputDevice     "eraser"       "SendCoreEvents"                                                                                                               
        InputDevice     "Synaptics Touchpad"
EndSection

#Section "Module"                                                                                                                                                      
        #Load           "glx"                                                                                                                                          
        #Load           "GLcore"                                                                                                                                       
        #Load           "v4l"                                                                                                                                          
#EndSection                                                                                                                                                            

#Section "ServerFlags"                                                                                                                                                 
#EndSection

```

The output from xrandr looks like the following using the above xorg.conf:
```

Screen 0: minimum 320 x 200, current 1024 x 768, maximum 1024 x 768
VGA disconnected (normal left inverted right)
LVDS connected 1024x768+0+0 (normal left inverted right) 0mm x 0mm
   1024x768       59.3*+   85.0     75.0     70.1     60.0  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  

```

Any ideas?

---

### Post by LauraSakura on 2007-12-24
Its been a long time for this post... but I'm bumping because I have the same problem. I have a HP Pavilion dv1170us laptop. My graphics card is Intel 855GM. Back when I had XP I was able to use my Svideo-out to use my laptop with the TV. It seems Ubuntu (using XRandR) doesn't even recognize that I have TV-out. However, my port for an external vga monitor DOES work. Strange..

---

### Post by uC10uD on 2007-12-27
> **LauraSakura said:**
> Its been a long time for this post... but I'm bumping because I have the same problem. I have a HP Pavilion dv1170us laptop. My graphics card is Intel 855GM. Back when I had XP I was able to use my Svideo-out to use my laptop with the TV. It seems Ubuntu (using XRandR) doesn't even recognize that I have TV-out. However, my port for an external vga monitor DOES work. Strange..

plug in the cable then 

xrandr --output S-video --auto

try this

---

### Post by LauraSakura on 2007-12-28
I tried that :( It seems that XRandR doesn't recognize that my laptop has SVideo Out. The only thing it finds is the monitor port. If I do the line you wrote, and then type xrandr, I get this

```
Screen 0: minimum 320 x 200, current 1280 x 768, maximum 1400 x 1050
VGA disconnected (normal left inverted right)
LVDS connected 1280x768+0+0 (normal left inverted right) 305mm x 183mm
   1280x768       60.0*+   60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  

```

---

### Post by LauraSakura on 2007-12-29
I have read that it is a bug in gutsy where people with intel graphics are having issues using TV out with S-Video. makes me wonder if anyone has gotten it to work?

---

### Post by BuntuFreak on 2008-01-03
Same problem here. Can't get the damn thing to work on my Dell Latitude CPxJ. I fell in love with Ubuntu and removed the dual boot and installed Ubuntu from scratch.

BIG MISTAKE !!!

---

### Post by LauraSakura on 2008-01-06
same here, and I love it, my only real problem is because of the lack of S-video. I can live without it, it would just be nice to get it to work. From what I've read, its a problem in Gutsy so maybe it will be fixed in Hardy? I hope so

---

### Post by giruzz on 2008-01-12
> **LauraSakura said:**
> same here, and I love it, my only real problem is because of the lack of S-video. I can live without it, it would just be nice to get it to work. From what I've read, its a problem in Gutsy so maybe it will be fixed in Hardy? I hope so

Anyone got luck?

g.

---

### Post by LauraSakura on 2008-01-15
Should I bring this up in the Hardy dev forum as something that needs to be looked at for the next release? I want to get this working so I might try a few different distro's on my other partition and see if it works on any of them. If it works on one of them and not Ubuntu Gutsy, ill try to find out why :) Ill let you all know if i figure anything out.
(When something isn't working for me, I usually don't just let it go... i try to figure out WHY and more importantly HOW to fix it. Yes, I'm a true geek haha )

---

### Post by giruzz on 2008-01-15
> **LauraSakura said:**
> Should I bring this up in the Hardy dev forum as something that needs to be looked at for the next release? I want to get this working so I might try a few different distro's on my other partition and see if it works on any of them. If it works on one of them and not Ubuntu Gutsy, ill try to find out why :) Ill let you all know if i figure anything out.
(When something isn't working for me, I usually don't just let it go... i try to figure out WHY and more importantly HOW to fix it. Yes, I'm a true geek haha )

Yes please. I've spent a night trying to have this sorted out but I'm still without TV-OUT which is something I need and is the only thing I'm using in WinXP.

g.

---

### Post by 08runner on 2008-04-20
Has anybody got it to work yet? According to posts in other threads all cards bellow 910 are not supported for tv-out with cuurent drivers. But then again how some people got it working on Feisty?

On my thinkpad R51 all attempts failed :( S-video is not even detected. And it looks like its not working in Hardy either.

---

### Post by giruzz on 2008-04-20
> **08runner said:**
> Has anybody got it to work yet? According to posts in other threads all cards bellow 910 are not supported for tv-out with cuurent drivers. But then again how some people got it working on Feisty?

On my thinkpad R51 all attempts failed :( S-video is not even detected. And it looks like its not working in Hardy either.

I gave up. I don't think this will ever work...

g.

---

### Post by RamR on 2008-06-15
Bump -- Any progress with this yet.  Still doesn't work for me in Hardy.  Very frustrating.

---

### Post by mohtasham1983 on 2008-06-18
It didn't work in my hardy either. However, when I press fn+F8, I can see something changing on TV, but it s not even close to anything.

---

### Post by Craig73 on 2008-07-04
Same here as well... Inspiron 700m and S-video not working.

As a note - for the Intel driver it should be TV not S-video (check man intel)

xrandr --prop
shows no sign of TV

xrandr --output TV --set load_detection 1 
just returns and error

---

### Post by Sirius1977 on 2008-07-08
> **Craig73 said:**
> Same here as well... Inspiron 700m and S-video not working.

As a note - for the Intel driver it should be TV not S-video (check man intel)

xrandr --prop
shows no sign of TV

xrandr --output TV --set load_detection 1 
just returns and error

Have you tried the solution i posted here: [http://ubuntuforums.org/showthread.php?t=849994&highlight=855gm+svideo](http://ubuntuforums.org/showthread.php?t=849994&highlight=855gm+svideo)

This works for me on a Thinkpad R51.

Here is my xorg.conf: [http://ubuntuusers.de/paste/389739/](http://ubuntuusers.de/paste/389739/)

Hope this helps.

Sirius

---

