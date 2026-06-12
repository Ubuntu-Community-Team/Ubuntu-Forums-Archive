---
title: "Desktop Display Problem"
date: 2008-11-08
forum: General Help
---

### Post by Vorge on 2008-11-08
I just on this problem that started today when I turned on my computer. It's a Ubuntu 8.10(Intrepid Ibex) and when I log into my user account, it cuts off part of the screen which is really annoying. On the sign-in screen, it displays full screen,but once I log in it cuts the screen. Also the internet is zoomed in alot more. I have to scroll around so much just to check my e-mail.:( Here are some pictures of my problem.

This is the log in screen. It displays full:
[IMG]http://i38.tinypic.com/2w7pvgy.jpg[/IMG]

Now here is my desktop, its kinda hard to see(maybe standing up will help, but its cut on the top and right side.
[http://i34.tinypic.com/2cxg6qx.jpg](http://i34.tinypic.com/2cxg6qx.jpg)

Sorry its so big, but thats to make sure you can see it. Any help?
This is really annoying.:confused:

---

### Post by alwayshere on 2008-11-08
I guess you have tried resetting resolution already ?

---

### Post by Vorge on 2008-11-08
Yeah I did. I tried that thing in rescue mode ehre you type in sudo something x-org. It said I didn't have x-org installed and I can't use that command.

---

### Post by alwayshere on 2008-11-08
type in terminal


 sudo apt-get install  xorg

see how that goes

---

### Post by sirebral on 2008-11-08
It might be your refresh rate.

---

### Post by Vorge on 2008-11-10
I re-installed my operating system and I think I know what the problem was. I installed avast! antivirus, and after shutting off my computer and turning it on later it got screwed up again. I re-installed, installed avast again, and ran into the same problem. I re-installed and didn't install avast, and my computer works fine. But I'll keep this in my favorites in case i run into a problem and don't want to re-install my OS.

---

### Post by Vorge on 2008-11-10
Yeah my computer is doing that again and I screwed around with the resolution so now its giant and I can't do anything. I tried that xorg thing but it only reconfigures my keyboard, that's it.:confused:

---

### Post by blackened on 2008-11-10
Reconfiguring xorg under 8.10 doesn't work anymore for almost anything (unless you have a manually configured xorg.conf and want to restore it to a clean one). Your best bet will be using xrandr to add new resolutions/refresh rates. Should be something like this:

Find the modeline for your appropriate resolution/refresh a la:
```
cvt **<hres> <vres> <refresh>**
```

This will spit out a modeline that you need to paste into the following command:
```
xrandr --newmode **<modeline attained from cvt command>**
```

Then add it to the monitors listed modes (example for 1280x1024@75):
```
xrandr --addmode VGA 1280x1024_75.00
```

After doing all that you should see the newly listed resolution in System->Preferences->Screen Resolution.

Sorry if this is confusing. It's not exactly an easy thing to give examples of.

---

### Post by Vorge on 2008-11-16
> **blackened said:**
> Reconfiguring xorg under 8.10 doesn't work anymore for almost anything (unless you have a manually configured xorg.conf and want to restore it to a clean one). Your best bet will be using xrandr to add new resolutions/refresh rates. Should be something like this:

Find the modeline for your appropriate resolution/refresh a la:
```
cvt **<hres> <vres> <refresh>**
```

This will spit out a modeline that you need to paste into the following command:
```
xrandr --newmode **<modeline attained from cvt command>**
```

Then add it to the monitors listed modes (example for 1280x1024@75):
```
xrandr --addmode VGA 1280x1024_75.00
```

After doing all that you should see the newly listed resolution in System->Preferences->Screen Resolution.

Sorry if this is confusing. It's not exactly an easy thing to give examples of.

Its okay, I understand. I'll try this.

---

### Post by Kirky_D on 2008-11-17
When this happens to me I simply change the horizontal and vertical size on my monitor. Mine has an auto setting though so I just click that and it sorts it out for me. 

It looks to me that you can see you desktop fine but your monitor isn't displaying it right. Try changing the settings of your monitor

---

### Post by blackened on 2008-11-17
> **Kirky_D said:**
> When this happens to me I simply change the horizontal and vertical size on my monitor. Mine has an auto setting though so I just click that and it sorts it out for me. 

It looks to me that you can see you desktop fine but your monitor isn't displaying it right. Try changing the settings of your monitor

After looking at the pictures again I think I agree. Try using your monitor's on-screen display to adjust your horizontal and vertical positions and sizes.

---

### Post by crtlbreak on 2008-11-18
> **blackened said:**
>  ......

Find the modeline for your appropriate resolution/refresh a la:
```
cvt **<hres> <vres> <refresh>**
```

This will spit out a modeline that you need to paste into the following command:
```
xrandr --newmode **<modeline attained from cvt command>**
```

Then add it to the monitors listed modes (example for 1280x1024@75):
```
xrandr --addmode VGA 1280x1024_75.00
```

After doing all that you should see the newly listed resolution in System->Preferences->Screen Resolution. ....... 

Hi blackened
Apologies to be "jumping in" on someone else's thread 
When I try the xrandr --addmode VGA 1280x1024_75.00 
the reply is
xrandr: cannot find output "VGA"

Here is my lspci
abuser@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
01:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:0a.0 Communication controller: Conexant HCF V90 56k Data/Fax/Voice/Spkp PCI Modem (rev 89)
02:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller

and here is my lsh

abuser@ubuntu:~$ sudo lshw -C display
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: 82945G/GZ Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list
       configuration: latency=0

Regards

---

### Post by blackened on 2008-11-19
> **crtlbreak said:**
> Hi blackened
Apologies to be "jumping in" on someone else's thread 
When I try the xrandr --addmode VGA 1280x1024_75.00 
the reply is
xrandr: cannot find output "VGA"...


You're probably just using a different output. Your output (to put in place of VGA) will be listed as connected in xrandr (type xrandr by itself) like so:
```
trevor@zealotry:~$ xrandr
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 1680 x 1050
VGA disconnected (normal left inverted right x axis y axis)
**LVDS** connected 1280x800+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1280x800       59.9*+
   1024x768       85.0     75.0     70.1     60.0  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  

```

Because I don't have my external display hooked up to my laptop, LVDS is my active display, so I would use 
```
xrandr --addmode LVDS 1280x1024_75.00
```
if I wanted to add that mode to my laptop's built-in display. Get the idea?

---

### Post by michaeljeshurun on 2008-11-28
I was reading this post, and trying to add resolutions to my settings.  I hope nobody minds me continuing here. crtlbreak, I followed your instructions, but my xrandr is only showing a **default** monitor, and won't say whether its **VGA** or **LVDS**, etc.  The command "xrandr --addmode default 1024x768_60.00" just disappears when I type it into the terminal.

Also, I was a bit unclear as to when the modline started and when it ended, but I didn't get any errors, just an exaggerated set of details in xrandr.

Here's my output:

mike@mike-12l:~$ xrandr
Screen 0: minimum 320 x 240, current 800 x 600, maximum 800 x 600
**default** connected 800x600+0+0 0mm x 0mm
   800x600        60.0*    56.0  
   640x480        60.0  
   400x300        60.0     56.0  
   320x240        60.0  
  1280x1024_75.00 (0x8b)  138.8MHz
        h: width  1280 start 1368 end 1504 total 1728 skew    0                   clock   80.3KHz
        v: height 1024 start 1027 end 1034 total 1072                   clock   74.9Hz
  1280x1024_60.00 (0x8c)  109.0MHz
        h: width  1280 start 1368 end 1496 total 1712 skew    0                   clock   63.7KHz
        v: height 1024 start 1027 end 1034 total 1063                   clock   59.9Hz
  1024x768_60.00 (0x8d)   63.5MHz
        h: width  1024 start 1072 end 1176 total 1328 skew    0                   clock   47.8KHz
        v: height  768 start  771 end  775 total  798                   clock   59.9Hz

You can see I was trying to add the 1280x1024 res, but the refresh rates came out ridiculous, so I added the 1024x768.

Is there something I should do to get a designation for Sony lcd monitor I'm using?

Thanks.

---

### Post by blackened on 2008-11-28
> **michaeljeshurun said:**
> I was reading this post, and trying to add resolutions to my settings.  I hope nobody minds me continuing here. crtlbreak, I followed your instructions, but my xrandr is only showing a **default** monitor, and won't say whether its **VGA** or **LVDS**, etc.  The command "xrandr --addmode default 1024x768_60.00" just disappears when I type it into the terminal.

Also, I was a bit unclear as to when the modline started and when it ended, but I didn't get any errors, just an exaggerated set of details in xrandr...


Is there something I should do to get a designation for Sony lcd monitor I'm using?

Thanks.

When you use gtf or cvt it create an output something like this:
```
trevor@zealotry:~$ gtf 1280 1024 60

  # 1280x1024 @ 60.00 Hz (GTF) hsync: 63.60 kHz; pclk: 108.88 MHz
  Modeline **"1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync**

```

The bolded part is the modeline. So you would take that and plug it into xrandr:

First we create the mode
```
xrandr --newmode "1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync
```

Now we add the mode to a particular output:
```
xrandr --addmode default 1280x1024_60.00
```

Lastly, we switch to the mode we created:
```
xrandr --output default --mode 1280x1024_60.00
```

Hope this was more descriptive. There is no cut-n-paste solution to this problem as it will vary wildly depending on your system.

---

### Post by michaeljeshurun on 2008-11-28
Thanks, blackened, but somethings wrong.  Here's my output:

mike@mike-12l:~$ xrandr --output default --mode 1024x768_60.00
xrandr: cannot find mode 1024x768_60.00

I went back to $ xrandr , and the output is the same as before (see above).

I now know from your clarification, that I did enter the "--newmode" correctly.  That's something.

Here's my newbee guess.  This line in bold is holding the "--output" from working:
mike@mike-12l:~$ xrandr
Screen 0: minimum 320 x 240, current 800 x 600, **maximum 800 x 600**
...

I'm thinking I might have to install drivers for the monitor.

---

### Post by blackened on 2008-11-29
Ok then, let's back up and punt. Let's add the hsync and vrefresh to xorg.conf. That will usually help the system identify the monitor. You can look these numbers up in the documentation that came with your monitor (sometimes they're on the box), or you might be able to get them on the web if you search by model number.

When you find them, add them to xorg.conf like so:
```
gksudo gedit /etc/X11/xorg.conf
```

and in the subsequent gedit window:
```
Section "Monitor"
	Identifier	"Configured Monitor"
[B]	HorizSync          30-82
	VertRefresh        56-76[/B]
EndSection
```

The bold lines are what you need to add, replacing my values with your hsync and vrefresh. After that do

```
sudo /etc/init.d/gdm restart
``` or, failing that, do a ctrl+alt+backspace to kill X.

---

### Post by michaeljeshurun on 2008-11-29
That worked like a charm.  Thanks very much.  I have lots of choices for resolutions now.

---

### Post by blackened on 2008-11-29
> **michaeljeshurun said:**
> That worked like a charm.  Thanks very much.  I have lots of choices for resolutions now.

Don't know why I didn't mention that earlier. Really it's smarter to start with that and, if that doesn't work, then start mucking around with xrandr.

Glad you got it sorted out.

---

### Post by Linkfire on 2009-09-09
> **blackened said:**
> Don't know why I didn't mention that earlier. Really it's smarter to start with that and, if that doesn't work, then start mucking around with xrandr.

Glad you got it sorted out.

Thanks worked for me was nothing more than put 
 monitor configuration. 
 Thanks ...

---

### Post by 2benglish on 2009-12-28
I am trying to use a Panasonic Viera TV, connected with a monitor cable. I have it working from one hard drive (running 8.04), but am having problems going higher than 800 600 on another hard drive (9.10 ubuntustudio). I can add the mode 1280 1024. but not select it as the output.
Here is what I get in the terminal.

paul@desktop:~$ xrandr -q
Screen 0: minimum 320 x 240, current 800 x 600, maximum 1280 x 1024
default connected 800x600+0+0 0mm x 0mm
   800x600        60.0*    56.0  
   640x480        60.0  
   400x300        60.0     56.0  
   320x240        60.0  
   1280x1024_60.00   59.9  
paul@desktop:~$ xrandr --output default --mode 1280x1024_60.00
xrandr: Configure crtc 0 failed
paul@desktop:~$ 


Trying from the Display option returns the error CRTC 289.

Can anyone help?

---

### Post by mjlackner on 2010-01-06
I'm having the same experience without a solution yet.

NVIDIA - TNT card
Flatron - W2252TQ screen

I have this same monitor hooked to a KVM, and my [SIZE="1"]Windows[/SIZE] box gets the full 1680X1050 easy.
======
mjlackner@Wraith:~$ lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation NV4 [RIVA TNT] (rev 04)

mjlackner@Wraith:~$ xrandr
Screen 0: minimum 320 x 240, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        60.0*    56.0  
   640x480        60.0  
   400x300        60.0     56.0  
   320x240        60.0  

mjlackner@Wraith:~$ cvt 1680 1050 60
<enter>

# 1680x1050 59.95 Hz (CVT 1.76MA) hsync: 65.29 kHz; pclk: 146.25 MHz
Modeline [COLOR="Red"]"1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync[/COLOR]

mjlackner@Wraith:~$ xrandr --newmode [COLOR="Red"]"1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync[/COLOR]
<enter>

mjlackner@Wraith:~$ xrandr --addmode default "1680x1050_60.00"

mjlackner@Wraith:~$ xrandr -q
Screen 0: minimum 320 x 240, current 800 x 600, maximum 1680 x 1050
default connected 800x600+0+0 0mm x 0mm
   800x600        60.0*    56.0  
   640x480        60.0  
   400x300        60.0     56.0  
   320x240        60.0  
   1680x1050_60.00   60.0        # Nice!

---------
Now 1680X1050 shows up in System-Preferences-Display
but...upon selection...error

[I]The selected configuration for displays could not be applied
could not set the configuration for CRTC 288
[/I]

---------
There is a lot of juice out there on this topic.  I am investigating several 'opportunities'.

[LIST=1]
[*]As described above ([https://wiki.ubuntu.com/X/Config/Resolution]("https://wiki.ubuntu.com/X/Config/Resolution"))...do I randomly create a table of lengthXwidth & refresh rates, and try them all??  I like this method because its temp until you reboot, then easy enough to make permanent.  I would just like to know what 288 means before I go further.
[*]Manually manipulate xorg.conf
[*]sudo nividia-xconfig (I cannot find this command; which package is it in?)
[*][Ubuntu Forums > The Ubuntu Forum Community  > Main Support Categories  > Hardware & Laptops > [ubuntu] Fixing low screen resolution for legacy hardware]("http://ubuntuforums.org/showthread.php?t=1320785")
[/LIST] #4 is a cool idea, CD boot on 8.04 LTS, create a new xorg.conf, save it off, reboot from harddrive, copy in new xorg.conf & reboot.

I will continue to look and will post back if I find the solution.  You and I are experiencing a very similar event.  Keep me posted too.

---

### Post by Leppie on 2010-01-06
[removed]

---

### Post by mjlackner on 2010-01-07
Just wondering if 2benglish has found anything new?

---

### Post by mjlackner on 2010-01-09
I tried them all, no luck.  I'm wondering if this RIVA TNT is the problem because its sooooooo old.

Still looking for a solution.

---

