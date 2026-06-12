---
title: "Proper resolution for external monitor not listed."
date: 2008-12-16
forum: Hardware
---

### Post by szymex on 2008-12-16
Hi,
I need to change resolution for an external monitor which is connected to my laptop, it is LSD TV for which the best resolution is 1280x768. With the "screen resolution" tool I can choose 1024x768 or 1360x768 (which doesn't looks weird).

I tried to use sudo dpkg-reconfigure xserver-xorg but it does not ask at any point about resolution.

I'm using latest Ubuntu (installed week ago).

Any suggestion how to add missing resolution to a list?

---

### Post by drcrazy4 on 2009-04-28
Bump. I am having the exact same problem in Jaunty.

---

### Post by mktexpress on 2009-04-29
Me too.

---

### Post by planetLars on 2009-06-04
I have the same issue, any solutions?

Best Regards

Lars

---

### Post by planetLars on 2009-06-05
This does it for me:

[https://wiki.ubuntu.com/X/Config/Resolution#Dynamically testing different resolutions]("https://wiki.ubuntu.com/X/Config/Resolution#Dynamically testing different resolutions")

On my system:

lars@lars-laptop:~$ xrandr
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 1680 x 1200
VGA-0 connected 1024x768+0+0 (normal left inverted right x axis y axis) 433mm x 271mm
   1680x1050      60.0 +
   1280x1024      75.0     60.0  
   1280x960       60.0  
   1152x864       75.0  
   1024x768       75.0     70.1     60.0* 
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     66.7     59.9  
   720x400        70.1  
LVDS connected (normal left inverted right x axis y axis)
   1280x800       60.0 +
   1280x720       59.9  
   1152x768       59.8  
   1024x768       59.9  
   800x600        59.9  
   640x480        59.4  
S-video disconnected (normal left inverted right x axis y axis)
lars@lars-laptop:~$ xrandr --output VGA-0 --mode 1680x1050
lars@lars-laptop:~$ 


After I have chosen 1680x1050 it was availilable in systems display options. I have the impression that once one has chosen a resolution, all higher resolutions are not shown as this happened when I first switched to 1024x768: 1280x1024 was available before but only because of the internal display and wasn't available afterwards. This might be a bug. an anyone confirm this?

Best Regards

Lars

---

### Post by planetLars on 2009-06-05
Here is an attempt at a bash script for .xprofile. Unfortunately, while .xprofile gets executed for me, its settings get overridden a few seconds later. See [here]("http://ubuntuforums.org/showthread.php?t=1179987"). The script itself woks though.
Pay attention to the output device you have (**VGA-0** for me) and the state it is in after initial login(**VGA-0 connected 1024x768+0+0 (normal left inverted right x axis y axis) 433mm x 271mm**  for me). Do a **xrandr | grep *yourdevice*** and replace the string **after** the **=** **in** the **if** appropriately.

[COLOR="DarkOrange"]This is to make sure you only set the resolution when the device is actually connected![/COLOR]

```
EX=`xrandr | grep VGA-0`
if [ "$EX" = "VGA-0 connected 1024x768+0+0 (normal left inverted right x axis y axis) 433mm x 271mm" ]; then
	xrandr --output VGA-0 --mode 1680x1050
fi
```

---

### Post by Jeahavee on 2009-07-02
What about dvmi or dvi. I have a dvmi slot on my Pavilion going to a dvi moniter. After I reset twice it finds the right screen setting but after running windows and back it forgets.

---

### Post by planetLars on 2009-07-02
xrandr should show your devices. Then adress the proper device, eg. DVI-0. I don't know whether DVI hardware can be permanently programmed and whether Windows does so thus leading to problems under Linux. Could you describe what you do and what exactly doesn't work? Thanks! Lars

---

### Post by Jeahavee on 2009-07-02
Basically for Ubuntu I log in and my laptop screen goes to 1366x768 (it never forgets that). I plug in my monitor and go to display settings and find the Gateway 19". I go to it and change the resolution BUT the option for 1440x900 isn't there I leave it alone. I reset then plug it in again. It knows about the monitor more I guess and I can select 1440x900 I do so. I shut off and run Vista then return to Ubuntu it "forgets" and BOTH screen go blank. I unplug my monitor reset back to Ubuntu and the laptop regains it's 1366x768 resolution.:mad: I repeat it over and over ...

Vista I run it leave my monitor plugged in and it runs just fine. I can close my laptop and run vista like a desktop.:KS

---

### Post by Jeahavee on 2009-07-03
What I ended up doing was stacking one monitor on top of the other in the display options
So the 19" is above the 16". Now I can keep both setup on the correct size and the laptop can remain close when I'm looking at the main monitor. Kind of like how I have it on Vista (kind of). Had to get different wallpapers though.

---

### Post by planetLars on 2009-07-03
Hi, I experienced a similar issue in which the proper resolution wasn't shown. Also after using Windows XP over a weekend. I found a solution which I posted here: [http://ubuntuforums.org/showthread.php?t=1187965](http://ubuntuforums.org/showthread.php?t=1187965). I wasn't detailing it very well though. cvt creates a modeline for a given resolution (at 60 Hz default) which can be used with xrandr --newmode. Then the newmode can be --addmode to a display like DVI-0. Then it is selectable in the display preferences again. I did this once and now the script in this thread works every time (I have it run from the Startup-Manager). Use cvt -h and xrandr --h for detailed help.

Best Regards

Lars

---

### Post by Jeahavee on 2009-07-03
Well I thought it would boot up right, but even the screen shot show that it won't "read" pass the 16" nature resolution. So follow me now my 1440x900 background image is - 1368x866 image = how much you see now AND the bottom half WORKS but can't be see it in the screen shot.

The second shot is how it should look. After I readjusted it.

Now I wonder ...
[https://wiki.ubuntu.com/X/Config/Resolution#Dynamically%20testing%20different%20resolutions](https://wiki.ubuntu.com/X/Config/Resolution#Dynamically%20testing%20different%20resolutions)
... is there a way to "delete"  the sizes I'll NEVER use so that only 1366x768 and 1440x900 are left

---

### Post by planetLars on 2009-07-03
Hmm, when stretching the display, I once read about issues with different graphics chips such as the horizontal virtual resolution being limited, I have an ATi and I don't have problems with the procedure outlined below. Regarding deleting modes: try --delmode or --rmmode:```

lars@lars-laptop:~$ xrandr --h
usage: xrandr [options]
  where options are:
  -display <display> or -d <display>
  -help
  -o <normal,inverted,left,right,0,1,2,3>
            or --orientation <normal,inverted,left,right,0,1,2,3>
  -q        or --query
  -s <size>/<width>x<height> or --size <size>/<width>x<height>
  -r <rate> or --rate <rate> or --refresh <rate>
  -v        or --version
  -x        (reflect in x)
  -y        (reflect in y)
  --screen <screen>
  --verbose
  --dryrun
  --nograb
  --prop or --properties
  --fb <width>x<height>
  --fbmm <width>x<height>
  --dpi <dpi>/<output>
  --output <output>
      --auto
      --mode <mode>
      --preferred
      --pos <x>x<y>
      --rate <rate> or --refresh <rate>
      --reflect normal,x,y,xy
      --rotate normal,inverted,left,right
      --left-of <output>
      --right-of <output>
      --above <output>
      --below <output>
      --same-as <output>
      --set <property> <value>
      --scale <x>x<y>
      --transform <a>,<b>,<c>,<d>,<e>,<f>,<g>,<h>,<i>
      --off
      --crtc <crtc>
      --panning <w>x<h>[+<x>+<y>[/<track:w>x<h>+<x>+<y>[/<border:l>/<t>/<r>/<b>]]]
      --gamma <r>:<g>:<b>
      --primary
  --noprimary
  --newmode <name> <clock MHz>
            <hdisp> <hsync-start> <hsync-end> <htotal>
            <vdisp> <vsync-start> <vsync-end> <vtotal>
            [+HSync] [-HSync] [+VSync] [-VSync]
  --rmmode <name>
  --addmode <output> <name>
  --delmode <output> <name>
```.

Using the preferences->display settings I first set the external display to 1024x768 (the maximum possible at first). Then I disabled my internal laptop display. After that I used cvt, xrandr as written before and then used the display preferences again to set the proper resolution (1680x1050 in my case). Now it remains at that resolution thanks to my startup script after every login.

I don't think I can help you further. Perhaps someone else will be able to.

Best Regards

Lars

---

### Post by Jeahavee on 2009-07-04
That kind of helped, but I not too sure "how" to do it can ya give me a few step by step. Terminal > .....

---

### Post by planetLars on 2009-07-05
Hi,

first check that xrandr works and which modes you have. Open a Terminal (Application->Accessories->Terminal (translated from German)) (the default Terminal on Ubuntu is the bash (Born Again SHell)).

Type xrandr and press return.

You should get sth. like the following:

```

lars@lars-laptop:~$ xrandr
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 1680 x 1050
VGA-0 disconnected (normal left inverted right x axis y axis)
LVDS connected 1280x800+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1280x800       60.0*+
   1280x720       59.9  
   1152x768       59.8  
   1024x768       59.9  
   800x600        59.9  
   640x480        59.4  
S-video disconnected (normal left inverted right x axis y axis)

```

LVDS is the internal display of my laptop.

If you want to remove modes, do the following -- Attention: dangerous! I never did this and I don't know what happens if a mode Ubuntu wants to use has been removed eg. if you have an external display connected and any hardware (BIOS, graphics chip, display) reports only one mode possible at boot time for example. -- find the resolution you want to remove from xrandr s output. Type xrandr --delmode LVDS 800x600 where you replace LVDS by the output from which you want to remove the resolution and 800x600 by the resolution you want to remove. Press enter.

If you want to add a mode, first obtain a modeline. Type cvt 1680 1050 60.0 where you replace 1680 by the horizontal resolution, 1050 by the vertical resolution and 60.0 by the desired refresh rate. You'll get sth. like:

```

lars@lars-laptop:~$ cvt 1680 1050 60.0
# 1680x1050 59.95 Hz (CVT 1.76MA) hsync: 65.29 kHz; pclk: 146.25 MHz
Modeline "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync

```

Check with your display manual that the pixel clock (pclk) is supported by your display for the given resolution.

You may have to obtain the full display manual online from your displays vendor and you may have to obtain cvt via Synaptic first.

Now type xrandr --newmode 1680x1050  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync where you replace 1680x1050  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync by the modeline obtained from cvt and where you have replaced the "" part of the modeline (the name of the modeline) by 1680x1050 respectively the resolution you want to add.

Then type xrandr --addmode LVDS 1680x1050 where you replace LVDS by the output you want the mode to be added to (sth. like DVI in your case I guess) and 1680x1050 by the modes name you assigned in the previous step (the resolution you wanted to add).

Then you're basically done. Open the display preferences and you should be able to select the new mode for your display. Disable every other display. You may have to relogin. Click OK or Close if there's no OK, and logout, then login again. You should have the newly resolution applied.

Unfortunately you have to set the new resolution after every shutdown and restart. Simply type xrandr --output VGA-0 --mode 1680x1050 in bash after a login after a restart to get the proper resolution. Replace VGA-0 by your outputs name (DVI... or so) and 1680x1050 by the resolution. You can automate this by a script as posted in this thread. If you want help on that script, ask again. Good Luck!

Best Regards

Lars

---

### Post by Jeahavee on 2009-07-09
awwwww
X Error of failed request:  BadAccess (attempt to access private resource denied)
  Major opcode of failed request:  150 (RANDR)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  25
  Current serial number in output stream:  26

but yeah you answered me I thank you

---

### Post by planetLars on 2009-07-09
perhaps a "sudo xrandr --whatever" helps if its a privieged instruction (deleting modes?)

---

