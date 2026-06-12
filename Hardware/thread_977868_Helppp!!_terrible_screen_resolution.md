---
title: "Helppp!! terrible screen resolution"
date: 2008-11-10
forum: Hardware
---

### Post by 19890915 on 2008-11-10
I'm a newbie just installed an ubuntu 8.10 and have terrible screen resolution on it. 

Screen Size  	11.1"
Graphic Mode  	WXGA
Display Screen Type  	Active Matrix TFT Color LCD
Display Screen Technology  	VibrantView
Widescreen  	Yes
Display Resolution  	1366 x 768
Graphics Controller Manufacturer  	Intel
Graphics Controller Model  	GMA X3100

this is the screen i am using. right now it only has 800 by 600.

i did all of solutions i can find on the web, but no use.

---

### Post by ctopel on 2008-11-10
Make sure that your video card driver is installed.

Go to: 

System --> Administration --> Hardware Drivers

If nothing comes up, I'd head to the manufacturer's website and get your drivers that way.

---

### Post by cophew on 2008-11-10
This seems to be quite a common bug in 8.10. If your drivers are installed and **System >> Preferences >> Screen Resolution** doesn't show your resolution then try this workaround. Worked for me :)

Goto **Applications >> Accessories >> Terminal**

Assuming your monitor supports 60Hz (Which it probably will),
Copy and paste this :
```
xrandr --newmode "1368x768_60.00"  85.86  1368 1440 1584 1800  768 769 772 795  -HSync +Vsync
```

Then this :
```
xrandr --addmode "default" 1368x768_60.00
```

Now goto **System >> Preferences >> Screen Resolution** and select "1368 x 768 (16:9)". The resolution will probably not change, but make sure its selected and exit.

Log off and back on and it should have changed :)

Edit: Corrected the second code (oops!)

---

### Post by 19890915 on 2008-11-10
> **cophew said:**
> This seems to be quite a common bug in 8.10. If your drivers are installed and **System >> Preferences >> Screen Resolution** doesn't show your resolution then try this workaround. Worked for me :)

Goto **Applications >> Accessories >> Terminal**

Assuming your monitor supports 60Hz (Which it probably will),
Copy and paste this :
```
xrandr --newmode "1368x768_60.00"  85.86  1368 1440 1584 1800  768 769 772 795  -HSync +Vsync
```

Then this :
```
--addmode "default" 1368x768_60.00
```

Now goto **System >> Preferences >> Screen Resolution** and select "1368 x 768 (16:9)". The resolution will probably not change, but make sure its selected and exit.

Log off and back on and it should have changed :)

It hasnt change. and I when i put in the second code, it said cant find command.

---

### Post by blackened on 2008-11-10
The second command should be 
```
xrandr --addmode "default" 1368x768_60.00
```
Then check System->Preferences->Screen Resolution again.

---

### Post by 19890915 on 2008-11-11
> **blackened said:**
> The second command should be 
```
xrandr --addmode "default" 1368x768_60.00
```
Then check System->Preferences->Screen Resolution again.

I tried it again. it says "xrandr:cannot find output "default"

---

### Post by cophew on 2008-11-11
Well in "Screen Resolution", your screen should have a name like "LCD0" or something. Mine came up as "Unknown" so default worked. Sorry, I should have said that clearer.

---

### Post by blackened on 2008-11-11
Do ```
xrandr
``` by itself and it should output something like this ```
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 1280 x 1280
**LVDS connected 1280x800+0+0 (normal left inverted right x axis y axis) 0mm x 0mm**
   1280x800       59.9*+
   1024x768       85.0     75.0     70.1     60.0  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  

```

The first word from the line in bold is your output's name. You need to plug that name (probably VGA) into the following command:

Then use ```
xrandr --addmode **<youroutput>** 1368x768_60.00
``` and, once again, check System->Preferences->Screen Resolution for changes.

---

### Post by davidgeeee on 2008-11-11
1989 just in case this will help you...

 Re: Where is "Screens & Graphics" in 8.10
Just in case this helps someone that found this thread, here is how I fixed my screen resolution with 8.04.

First my graphics adapter and monitor were not detected. Tried all kinds of edits to xorf.conf with no success.

The Fix for me was this:

I used a 7.04 live CD to boot into Ubuntu (not install). The resolution was set to the highest my monitor could handle. Detected my graphics card correctly. Checked in "Screen Resolution" utility and all the resolutions were there. So, I copied xorg.conf to a USB drive. Restarted 8.04 and made a backup of the current(faulty) xorg.conf file. Then I copied the sections of xorg.conf (from 7.04) that were about the graphic card and monitor and modes to the xorg.conf of the 8.04 installation. Restarted X and everything was peachy!

I may try this with 8.10 today, but I am pretty sure it will work there too.

Hope this helps someone that has been banging their head like me!

---

### Post by 19890915 on 2008-11-11
> **blackened said:**
> Do ```
xrandr
``` by itself and it should output something like this ```
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 1280 x 1280
**LVDS connected 1280x800+0+0 (normal left inverted right x axis y axis) 0mm x 0mm**
   1280x800       59.9*+
   1024x768       85.0     75.0     70.1     60.0  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  

```

The first word from the line in bold is your output's name. You need to plug that name (probably VGA) into the following command:

Then use ```
xrandr --addmode **<youroutput>** 1368x768_60.00
``` and, once again, check System->Preferences->Screen Resolution for changes.

I had it tried. but it show my max only has 800x600. it should have 1366x768.

---

### Post by blackened on 2008-11-11
Please post the output of ```
xrandr
```

---

### Post by 19890915 on 2008-11-12
> **blackened said:**
> Please post the output of ```
xrandr
```

none of these work for me. but i downloaded the intel graphic 965 express driver family, but i dont know how to install.

---

### Post by 19890915 on 2008-11-12
> **davidgeeee said:**
> 1989 just in case this will help you...

 Re: Where is "Screens & Graphics" in 8.10
Just in case this helps someone that found this thread, here is how I fixed my screen resolution with 8.04.

First my graphics adapter and monitor were not detected. Tried all kinds of edits to xorf.conf with no success.

The Fix for me was this:

I used a 7.04 live CD to boot into Ubuntu (not install). The resolution was set to the highest my monitor could handle. Detected my graphics card correctly. Checked in "Screen Resolution" utility and all the resolutions were there. So, I copied xorg.conf to a USB drive. Restarted 8.04 and made a backup of the current(faulty) xorg.conf file. Then I copied the sections of xorg.conf (from 7.04) that were about the graphic card and monitor and modes to the xorg.conf of the 8.04 installation. Restarted X and everything was peachy!

I may try this with 8.10 today, but I am pretty sure it will work there too.

Hope this helps someone that has been banging their head like me!

I do understand what you saying, but i dont know how to do it . plz be specify and show me the steps.

---

### Post by Lemon on 2008-11-23
> **cophew said:**
> 
xrandr --newmode "1368x768_60.00"  85.86  1368 1440 1584 1800  768 769 772 795  -HSync +Vsync

Is there a reason why you use 1368 instead of 1366?

---

### Post by davidgeeee on 2008-12-10
[QUOTE=coolethan]i stumbled across your thread on screens and graphics in 8.1 and i was wondering if you were able to succesfully do this on 8.1 and where do i find the xorg.conf file on the disc?[/QUOTE]
The xorg.conf file is on that get written during the LiveCD setup of version 7.10 of Ubuntu.  I'll try to list the step from memory:
1. Download and burn a copy of Ubuntu 7.10
2. Boot with that CD and do not install just use the Livecd to get to the desktop.
3. At that point check that you can get to all the screen resolutions that you expect.
4. If so, copy /etc/X11/xorg.conf to a USB drive.
5. Then go to your installation  of 8.10 and copy and/or replace then portions of xorg.conf from the USB drive into the one installed by 8.10

If this works for you, post the text above as a reply to the message in the forum.  This thing frustrated me for along time and now I have used the technique on four machines and they all came out perfect.

---

### Post by davsinc2007 on 2008-12-10
I have the same issue.  I followed the instructions you mentioned and pasting below.  dsinclai@dsinclai-laptop:~$ xrandr --newmode 1600x1050_60.00  85.86  1368 1440 1584 1800  768 769 772 795  -HSync +Vsync
dsinclai@dsinclai-laptop:~$ xrandr --addmode VGA 1600x1050_60.00dsinclai@dsinclai-laptop:~$ xrandr
Screen 0: minimum 320 x 200, current 1400 x 1050, maximum 1600 x 2000
VGA connected 1400x1050+0+0 (normal left inverted right x axis y axis) 473mm x 296mm
   1600x1200      65.0     60.0  
   1600x1024      60.2  
   1400x1050      74.8*    70.0     60.0  
   1280x1024      75.0     60.0     60.0  
   1440x900       75.0     59.9     60.0  
   1280x960       60.0     60.0  
   1360x768       59.8  
   1280x800       60.0  
   1152x864       75.0     75.0     75.0     70.0     60.0  
   1024x768       75.1     75.0     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     72.8     75.0     66.7     60.0     59.9  
   720x400        70.1  
   1600x1050_60.00   60.0  
LVDS connected 1280x800+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1280x800       60.0*+
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
TV disconnected (normal left inverted right x axis y axis)
  1600x1050_60 (0xc4)   85.9MHz
        h: width  1368 start 1440 end 1584 total 1800 skew    0 clock   47.7KHz
        v: height  768 start  769 end  772 total  795           clock   60.0Hz

??

---

### Post by blackened on 2008-12-10
> **davsinc2007 said:**
> I have the same issue.  I followed the instructions you mentioned and pasting below.  dsinclai@dsinclai-laptop:~$ xrandr --newmode 1600x1050_60.00  85.86  1368 1440 1584 1800  768 769 772 795  -HSync +Vsync
dsinclai@dsinclai-laptop:~$ xrandr --addmode VGA 1600x1050_60.00

??

Are you sure you meant 1600x1050 and not 1680x1050?

Using the newmode/addmode method it should give you another selectable resolution in the "Screen Resolution" dialog under System->Preferences.

You can also enable activate a mode via the terminal by using this format:

```
xrandr --output VGA --mode 1600x1050_60
```

---

