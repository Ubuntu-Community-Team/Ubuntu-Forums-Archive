---
title: "Dual Backgrounds"
date: 2008-10-31
forum: General Help
---

### Post by jTips on 2008-10-31
Hi,

Just upgraded to 8.10... loving it.

Anyway... I have dual monitors going with nVidia, but I can't seem to figure out how to have separate backgrounds on them.

I can't even get the same back ground on each of them.

All I can do is have the one background that stretches across both screens or is tiled across both screens etc.

Any help is much appreciated.

Thanks,
Jeremy

---

### Post by loomsen on 2008-10-31
OK,

basically there are different ways to set up multiple screens.

What will work, and what will not is specified by your server layout in your xorg.conf.

For instance, this is mine. I'm using separate X-Screens, while a Screen is defined through a Videocard, and a Monitor it draws to.
```

ServerLayout "Layout0"
|
|-->Screen "Screen0" (0)
|   |-->Monitor "Monitor0"
|   |-->Device "Videocard0"
|
|
|-->Screen "Screen1" (1)
|   |-->Monitor "Monitor1"
|   |-->Device "Videocard1"
|
|
|-->Input Device "Keyboard0"
|-->Input Device "Mouse0"
|-->Input Device "Synaptics Touchpad"
|
Option "Xinerama" "0"

```

The line on the left is the connection of peripherals to my X-Server. As you can see, my screens are not bound together, but both connected to my X-Server.
Same for my Input Devices. In other words, my touchpad isn't aware of my mouse, nor of my keyboard or any screen. Equal for screens.

Just to keep things clear, before X starts, thats when your Screen flashes, you have only a BIOS = Basic Input Output System. 

Only when X-Server starts everything is bound together.

Now, to understand this, let's have a look how other dual-screen options layouts look. This will explain what is done to your desktop.

Possible other options are 
1) TwinView
layout would look sth like this:
```

ServerLayout "Layout0"
|
|   |-->Screen "Screen0" (0)
|   |-->Monitor "Monitor0"
|   |-->Monitor "Monitor1"
|   |-->Screen "Screen1" (1)
|-->Device "Videocard0"
|
|
|-->Input Device "Keyboard0"
|-->Input Device "Mouse0"
|-->Input Device "Synaptics Touchpad"
|
|
Option "Xinerama" "1"

```

In this case, as you see, There's only one Videocard, which draws to double horizontal Output. For instance, If we have a resolution of 1200x800 on each Screen, the Output of Videocard0 above is virtually set to 2400x800.

The layout shows that the Screens are bound together before they are connected to X-Server. So, obviously this will only work with Screens of the same resolution, as we have only one Videocard.
In this case Xinerama would be enabled(the possibility to drag windows over screens edge to the other Screen. The line in the picture above shows.

An example what would happen if we'd actually drag a window from top left of our left screen over the edge:

Our Input (Mouse) INdicates movement to X.
X parses this Input to Videocard0, which then draws the window according to our mouse-movement.
Just that the Videocard0 is virtually set to draw to a Screen of 2400x800.

This is the reason why compiz won't work with TwinView. Cause... how should it? Dragging a window over the edge initiates your cube to be rotate. 
But, where your screen had it's border earlier - at X=1200 - now is the middle of the screen. So, impossible to compose --> no compiz with TwinView.
But now you may drag windows from Screen 0 all the way down the short line to Videocard 0.

Understood?

Short:
Method 1) Independent Screens --> Only way with different resolutions
- connected each to X-Server, each Screen is defined by a unique Videocard and a unique Monitor.
- You can move the mouse from left to right and back, cause this is done through X
- You may not move windows between screens, cause they are drawn by your Videocard
- COMPIZ WORKS HERE (logic!)

Method 2) TwinView --> Only with Screens of the same Resolution
- The Output of ONE Videocard is virtually drawn over both Screens, 
- You may drag windows back and forth, because now the screens are bound together through your Videocard
- The line in the 2nd layout shows.



Then there's CloneOutput... 
```

[code]
ServerLayout "Layout0"
|
|   |-->Screen "Screen0" (0)
|   |-->Monitor "Monitor0"
|   |
|-->Device "Videocard0"
|   |
|   |-->Monitor "Monitor1"
|   |-->Screen "Screen1" (1)
|
|
|
|-->Input Device "Keyboard0"
|-->Input Device "Mouse0"
|-->Input Device "Synaptics Touchpad"
|
|

```

This should be pretty self-explainatory if you got me so far... 

So, if you want to have your Laptop draw to your TV when you're at home for instance, Method 1 would be your choice.

If you plan to set up two Screens for your Desktop-PC, where nor the PC neither the Screens will move after you set them up, Method 2) should be the call to make.

And if you have to present a OpenOffice Presentation for instance, and want to have your laptop in front of you, and bound to a VideoBeamer for example, CloneOutput is what you'd want.



---> Why do I have to restart X if I'd like to switch from TwinView to separate X-Screens?

The layouts show... TwinView and CloneOutput just have to reset the resolutions.
For separate X-Screens you need another VideoCard tho.

Got me?

---

### Post by jTips on 2008-10-31
Hi,
Thanks for the detailed info... but..

I have two screens working fine on  separate X, the only thing I can't figure out is how to have different backgrounds on them.

My current setup works fine. I have two screens next to each other and the cursor moves seemlessly from one to the other... just that the background is strecthed across both, or smack-bang in the middle of the two (spreads from one screen to the other).

Thanks,
Jeremy

---

### Post by jpkotta on 2008-11-02
I don't use Gnome, but I don't think it has the ability to do this.  KDE and XFCE do, however.  

Personally, I think it is much better to use a wallpaper designed for dual screens.  A dual screen wallpaper is something that you just can't have with a single screen, therefore it is "maximizing the utility" of your hardware in some sense.  Unfortunately, those wallpapers are harder to find, and maybe you have some single screen ones that you really like.  In that case, stitch them together with the Gimp.

I have looked for desktop-independent programs that will do this, because I use a plain window manager, and I can't find any.

---

### Post by loomsen on 2008-11-02
Right, you can't with gnome. But if you're using compiz you could prevent gnome from drawing your background, and instead activate wallpaper plugin. That will give you 8 different wallpapers then, assuming you have a cube with 4 faces. However, compiz has such options, but it won't work if you try and configure it while running. So I'd suggest you add the configuration file manually. 
Export your profile, don't skip default values, open the file in any editor and hardcode what you'd like for Screen 1 with s1 prepended to the lines.

You will figure out, s0 means Screen 0. Basically every option where a s0 is prepended in your profiles file is independently configurable for s1.

Sth like this for instance should work:
```

[wallpaper]
s0_bg_image = /home/docter/Pictures/1007.png;/home/docter/Pictures/1032.png;/home/docter/Pictures/1044.png;/home/docter/Pictures/1134.png;
s0_bg_image_pos = 1;1;1;1;
s0_bg_fill_type = 0;0;0;0;
s0_bg_color1 = #00000000;#00000000;#00000000;#00000000;
s0_bg_color2 = #00000000;#00000000;#00000000;#00000000;
s1_bg_image = /home/docter/Pictures/1007.png;/home/docter/Pictures/1032.png;/home/docter/Pictures/1044.png;/home/docter/Pictures/1134.png;
s1_bg_image_pos = 1;1;1;1;
s1_bg_fill_type = 0;0;0;0;
s1_bg_color1 = #00000000;#00000000;#00000000;#00000000;
s1_bg_color2 = #00000000;#00000000;#00000000;#00000000;

```

---

### Post by jTips on 2008-11-02
Whoa! That seems pretty complex for the sake of pictures :)

I've managed to find some dual-screen backgrounds that look pretty cool (see [http://www.dualscreenwallpaper.com](http://www.dualscreenwallpaper.com)). I didn't even think about find a wallpaper that big... doh!

Thanks for the help guys... perhaps 9.04 will support independent backgrounds better :)

---

### Post by jpkotta on 2008-11-02
I like [interfacelift]("http://interfacelift.com/wallpaper_beta/downloads/date/dual_monitors/2560x1024/").

---

### Post by Crafty Kisses on 2008-11-03
> **jpkotta said:**
> I like [interfacelift]("http://interfacelift.com/wallpaper_beta/downloads/date/dual_monitors/2560x1024/").

Nice link, I'm liking the wallpapers.

---

### Post by loomsen on 2008-11-03
#2

---

### Post by ad_267 on 2008-11-03
If you want a different wallpaper on each monitor, learn to use GIMP's crop, resize and copy and paste tools. :)

---

### Post by loomsen on 2008-11-03
Which doesn't sound 2 bad actually. Would you mind if I piped a |  more?

:)

Any howto, wiki, or just a keyword to look for should be enough. I'm absolutely unfamiliar with gimp, but that shouldn't be too hard cropping an image :D 
I wasn't aware gimp can draw your background actually.

---

### Post by jTips on 2008-11-03
I think what he means is to use gimp to take two separate images and make one big image, then use that as your background that spans both screens :)

---

### Post by LawFirmMakati on 2008-11-03
I didnt know that it would be that complicated and too code oriented to have dual background on your units. :) By the way I checked out the link given the "interfacelink" something, it it is a very nice site love the wallpapers there so cute and cool!

Maybe someday I'll get to learn more of these stuffs when I gain more experience, because I am still studying and I don't get a chance to explore much especially now I am under our OJT program with Kittelson and Carpo.

Maybe after sometime I'll try exploring dual backgrounds and get some helpfrom you guys in the future :)

**[carpolaw]("http://carpolaw.com")**

---

### Post by ad_267 on 2008-11-03
> **jTips said:**
> I think what he means is to use gimp to take two separate images and make one big image, then use that as your background that spans both screens :)

Yeah that's what I meant. I make a blank image the size of both my screens put together. I open the images I want and resize then crop them to the size of each individual monitor, then paste them onto the big image, save it and set it as my wallpaper. Yes it's not as nice as being able to do it automatically, but it works fine.

It would probably be pretty easy to setup a bash or python script using ImageMagick to automate this process.

---

### Post by loomsen on 2008-11-03
Oh well, yes, that shouldn't be 2 hard.

My problems are a little bit different tho. Using conky with different backgrounds hasn't been possible to me yet.
Tho conky will work without an own window, it will only draw to nautilus. Having compiz set the background conky wont draw to it. Or it will more likely, just it won't draw to the top of it. It's only visible with override option and transparent cube.

Anyway, thats not the point here. Thanks for sharing the links anyway :)

---

### Post by ad_267 on 2008-11-03
If anyone's interested I've made this script for generating a background from two images for dual monitors. It resizes and crops the images, keeping their aspect ratio and then sets the background in Gnome. It requires ImageMagick to be installed. Feel free to modify it and do what you want with it.

```
#!/bin/bash

# Configure for your monitor resolutions
AX=1280
AY=1024
BX=1024
BY=768

TEMP_DIR=/tmp

# Check input parameters
if [ $# -ne 3 ]; then
	echo "Usage: `basename $0` first_image second_image output_file"
	exit 1
fi

# Check for installed applications
if [ -z "$(which convert)" ]; then
    echo "$0: error: convert program not installed"
    exit 1
fi
if [ -z "$(which montage)" ]; then
    echo "$0: error: montage program not installed"
    exit 1
fi

# Set temporary file names
ATEMP=$TEMP_DIR/dualbackgroundA.$$.$RANDOM
BTEMP=$TEMP_DIR/dualbackgroundB.$$.$RANDOM

# Resize images and store in temp directory
convert "$1" \
          -resize x${AY} -resize "${AX}x<"  \
          -gravity center  -crop ${AX}x${AY}+0+0 +repage "$ATEMP" 
          
convert "$2" \
          -resize x${BY} -resize "${BX}x<"  \
          -gravity center  -crop ${BX}x${BY}+0+0 +repage "$BTEMP" 

# Join images to output file
montage "$ATEMP" "$BTEMP" -mode Concatenate -tile x1 -gravity south "$3"

# Get directory of output file
if [ ${3:0:1} = "/" ]; then
    FILEPATH=$3
else
    FILEPATH=`pwd`/$3
fi
# Set background
if [ ! -z "$(which gconftool-2)" ]; then
    gconftool-2 -t str --set /desktop/gnome/background/picture_filename "$FILEPATH"
fi

# Remove temporary files
rm "$ATEMP"
rm "$BTEMP"
```

---

### Post by jpkotta on 2008-11-10
I stumbled across a great app called nitrogen.  It's in the repos and it does what you want.

---

### Post by Zularan on 2008-11-12
> **jpkotta said:**
> I stumbled across a great app called nitrogen.  It's in the repos and it does what you want.

Nice find/stumble :)

---

### Post by saggitheman on 2008-11-29
I haven't dual monitors but waht i would recomend to you, is that you find out how large (Px) your screen resolution is. And open Gimp/photoshop and make a image that is twice as big as the wight on your screen, and the same size of the hight, and just copy the pictures in to it. and set it as the background.

---

