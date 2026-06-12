---
title: "Can an external monitor be connected to a laptop?"
date: 2011-05-03
forum: Hardware
---

### Post by southafricanguy on 2011-05-03
Hi everyone,

After getting Ubuntu up and running with a few teething problems I was wondering if I can use the OS to add and configure an external monitor?

I'm using a Packard Bell Easynote with SiS Mirage 3 graphics (bad I know). I tried attaching the external monitor and rebooting but can't set anything (unlike Win 7). 

Sincere thanks.

Jas

---

### Post by Blasphemist on 2011-05-03
Yes, you can have an external monitor and the laptop internal monitor, or two monitors on a desktop using Ubuntu. This is normally done with two outputs from one gpu. It sounds like your external monitor isn't being seen as connected. Please post the output of these commands.

```
xrandr
```

```
sudo lspci
```

---

### Post by Maheriano on 2011-05-03
Go into your nVidia/Catalyst settings and configure it, you might need to enable it. Or you might just need to install the latest driver.

---

### Post by southafricanguy on 2011-05-03
Hi,

Thanks for the quick reply.

Here is the output:

```
jas@jas-EasyNote-MX37-T-003:~$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768        0.0* 
   800x600         0.0  
   640x480         0.0  

jas@jas-EasyNote-MX37-T-003:~$ sudo lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03)
00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)
02:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
```

Where do I find my Catalyst settings?

Sincere thanks.

Jas

---

### Post by Blasphemist on 2011-05-03
I have looked into the SiS Mirage 3 671MX gpu and found very little. Here is a description I found from 2006.

> The SIS Mirage 3+ is an onboard (shared memory) graphics card for laptops on the SIS 671MX chipset. No Vista Premium (Aero) support. Not usable for 3D games. The successor, the Mirage 3+ is DirectX 9 capable (and therefore ready for Aero) but still not usable for 3D games.

I find nothing in launchpad or the forums, or any other Ubuntu related site for that matter. There is a bug relating to update manager linked to a system with this but that is all. 

Was your second monitor connected when you ran xrandr? It seems to not recognize a second connection. It sounds as if you're confident in the cable to the external monitor from win 7 use. Is that right? 

I did find this driver but I can't speak for whether it will help. I'll do more research.

---

### Post by southafricanguy on 2011-05-03
[FONT=Tahoma][SIZE=2]Hi,[/SIZE][/FONT]
[FONT=Tahoma][SIZE=2][/SIZE][/FONT] 
[FONT=Tahoma][SIZE=2]Many thanks for the post and research etc.[/SIZE][/FONT]
[FONT=Tahoma][SIZE=2][/SIZE][/FONT] 
[SIZE=2][FONT=Tahoma]Yes, I'm using the external monitor now via Win 7 and it was definitely connected when I ran xrandr. The screen was receiving the output but was at the same (low) resolution as the internal monitor.[/FONT][/SIZE]
[FONT=Tahoma][SIZE=2][/SIZE][/FONT] 
[FONT=Tahoma][SIZE=2]Sincere thanks.[/SIZE][/FONT]
[FONT=Tahoma][SIZE=2][/SIZE][/FONT] 
[FONT=Tahoma][SIZE=2]Jas[/SIZE][/FONT]

---

### Post by Blasphemist on 2011-05-03
What port is the second monitor connected to? xrandr should allow us to tell the system to use that port and with what paramters. 

See this.

```
man xrandr
```

I'll help figure out the command if needed.

---

### Post by southafricanguy on 2011-05-03
Hi,
 
Tried running that but not sure what parameters it needs. Any idea?
 
Sincere thanks.
 
Jas

---

### Post by Blasphemist on 2011-05-03
I need to know which connection you are using. DVI1, HDMI, etc.

I'm going to recommend you run grandr instead of xrandr as it's easier to set it all right. If your output doesn't show on the left, we'll have to reconsider that.

The screen shot is what will come up when you run grandr. Select the appropriate output and choose a mode. On the layout tab, drag the display to the right if it is to the right of the laptop.

If the display or mode doesn't show up, we'll have to do it in xrandr I believe and I'm still trying to understand all of the newmode command.

---

### Post by southafricanguy on 2011-05-04
Hi,
 
Okay, did that. I only got one (default) output listed on the left?
 
Was there a driver or something I was meant to install?
 
Many thanks.
 
Jas

---

### Post by Maheriano on 2011-05-07
Install any hardware drivers available for your card and then load Catalyst under the programs. If you're using ATI.

---

### Post by southafricanguy on 2011-05-08
Hi, 
 
Thanks for the post.
 
I've installed the drivers as per:
 
[http://hellbunker.blogspot.com/2011/03/driver-sis-m671-m672-for-upcoming-natty.html](http://hellbunker.blogspot.com/2011/03/driver-sis-m671-m672-for-upcoming-natty.html)
 
Not sure what Catalyst is or where to find it? Also not sure if I'm using ATI or not. How do I find out?
 
Sincere thanks.
 
Jas

---

### Post by Blasphemist on 2011-05-08
> **southafricanguy said:**
> Hi, 
 
Thanks for the post.
 
I've installed the drivers as per:
 
[http://hellbunker.blogspot.com/2011/03/driver-sis-m671-m672-for-upcoming-natty.html](http://hellbunker.blogspot.com/2011/03/driver-sis-m671-m672-for-upcoming-natty.html)
 
Not sure what Catalyst is or where to find it? Also not sure if I'm using ATI or not. How do I find out?
 
Sincere thanks.
 
Jas

Glad you found that post Jas. You have sis, not ati so you don't use catalyst. It looks like Martin Lee has the best solution as shown in his blog. It wouldn't hurt for you or Martin to do an instruction post in these forums.

---

### Post by southafricanguy on 2011-05-08
Hey Jim,
 
Still early days... :lol: I still haven't managed to get my external monitor up to 1400 x 900 though my laptop screen resolution has been upped. Am I missing something? Only one output coming up when using grandr too.
 
Regards
 
Jas

---

### Post by Blasphemist on 2011-05-08
What's the output of xrandr now? I'm curious about what it shows now for the external monitor. The addmode option of xrandr should allow for adding a mode with the resolution you want. Try this command. Use the name of your external monitor in xrandr to replace VGA in the example. And change the 1024x768 to your desired resolution. If the mode you want doesn't yet exist in xrandr, you'll need to use the newmode option.

```
xrandr --addmode VGA 1024x768
xrandr --output VGA --mode 1024x768
```

Here is my xrandr status right now. Notice in blue the offset that sets my external to the right of my laptop. In red note that if you have to add a mode you'll need to provide a refresh rate.
```
jim@jim-Satellite-L505:~$ xrandr
Screen 0: minimum 320 x 200, current 2966 x 900, maximum 8192 x 8192
LVDS1 connected 1366x768+[COLOR="Blue"]0+0[/COLOR] (normal left inverted right x axis y axis) 353mm x 198mm
   1366x768       [COLOR="Red"]60.0[/COLOR]*+
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 connected 1600x900+[COLOR="blue"]1366+0[/COLOR] (normal left inverted right x axis y axis) 443mm x 249mm
   1600x900       [COLOR="red"]60.0[/COLOR]*+
   1280x800       59.8  
   1152x864       75.0  
   1280x720       60.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  
DP1 disconnected (normal left inverted right x axis y axis)
TV1 unknown connection (normal left inverted right x axis y axis)
   848x480        30.0 +
   640x480        30.0 +
   1024x768       30.0  
   800x600        30.0  

```

This page is the xrandr reference for the version in natty.
[http://manpages.ubuntu.com/manpages/natty/man1/xrandr.1.html](http://manpages.ubuntu.com/manpages/natty/man1/xrandr.1.html)

---

### Post by southafricanguy on 2011-05-13
Hey Jim,

Here is the output of xrandr:

```
jas@jas-EasyNote-MX37-T-003:~$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 1280 x 800, maximum 1280 x 800
default connected 1280x800+0+0 0mm x 0mm
   1280x800       60.0* 
   1024x768       75.0     70.0     60.0  
   800x600        75.0     72.0     60.0     56.0  
   640x480        75.0     73.0     60.0  
``` 

Should I try add another output?

Sincere thanks.

Jas

---

### Post by Blasphemist on 2011-05-13
Yes Jas, do try that. I don't understand the first line you are getting from xrandr.
> xrandr: Failed to get size of gamma for output default
I don't know why that is coming up. I still don't understand why it isn't seeing the external monitor either but yes do try to add it.

---

### Post by southafricanguy on 2011-05-16
Hey Jim,
 
I'm about to give that a go.
 
Is there anyway I can disable the internal monitor and just have the external one enabled as in Win 7?
 
Many thanks.
 
Jas

---

### Post by Blasphemist on 2011-05-16
There is a way to do that Jas but I think you should get them both working first and then think about the disabling of the internal. Personally, I'm going to implement a script that will auto-detect the presence of the external and use them both when it does. I have another task this evening and then I'm hoping to work on that. I'll check back and see how this is going for you too.

---

### Post by Mathias1 on 2011-05-17
I would be very interested in that sor of script.
 
I have  a similar problem.
I'm using a nVidia 7600go card.
 
I've placed my Ubuntu-laptop on my desk and "docked" it with external screen mouse, keyboard and such.
When I want to go out and flash my Pro-OS ( ;) ) I want to grab my laptop and pull the cables.
When I get back home, I want to "dock" the laptop to my external hardware and use my external screen again.
 
Is this possible? With script or grandr?
I know that in Windows, you can use the Fn+f7 combination, to easily change screen output.

---

### Post by Blasphemist on 2011-05-17
This is the script I was referring to.
[https://help.ubuntu.com/community/BinaryDriverHowto/DynamicMultiMonitor](https://help.ubuntu.com/community/BinaryDriverHowto/DynamicMultiMonitor)
I'm hoping to get it implemented for my system today.

---

### Post by southafricanguy on 2011-05-18
Hey Jim,

I'm not sure how to set the offset. This is what I have done so far:

```
jas@jas-EasyNote-MX37-T-003:~$ xrandr | grep maximum
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 1280 x 800, maximum 1280 x 800
jas@jas-EasyNote-MX37-T-003:~$ xrandr --newmode "XM7" 135.00 1440 1520 1672 1904 900 901 904 932 -HSync +VSync
xrandr: Failed to get size of gamma for output default
jas@jas-EasyNote-MX37-T-003:~$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 1280 x 800, maximum 1280 x 800
default connected 1280x800+0+0 0mm x 0mm
   1280x800       60.0* 
   1024x768       75.0     70.0     60.0  
   800x600        75.0     72.0     60.0     56.0  
   640x480        75.0     73.0     60.0  
  XM7 (0x134)  135.0MHz
        h: width  1440 start 1520 end 1672 total 1904 skew    0 clock   70.9KHz
        v: height  900 start  901 end  904 total  932           clock   76.1Hz

```

Many thanks.

Jas

---

### Post by Blasphemist on 2011-05-18
> **southafricanguy said:**
> Hey Jim,

I'm not sure how to set the offset. This is what I have done so far:

```
jas@jas-EasyNote-MX37-T-003:~$ xrandr | grep maximum
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 1280 x 800, maximum 1280 x 800
jas@jas-EasyNote-MX37-T-003:~$ xrandr --newmode "XM7" 135.00 1440 1520 1672 1904 900 901 904 932 -HSync +VSync
xrandr: Failed to get size of gamma for output default
jas@jas-EasyNote-MX37-T-003:~$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 1280 x 800, maximum 1280 x 800
default connected 1280x800+0+0 0mm x 0mm
   1280x800       60.0* 
   1024x768       75.0     70.0     60.0  
   800x600        75.0     72.0     60.0     56.0  
   640x480        75.0     73.0     60.0  
  XM7 (0x134)  135.0MHz
        h: width  1440 start 1520 end 1672 total 1904 skew    0 clock   70.9KHz
        v: height  900 start  901 end  904 total  932           clock   76.1Hz

```

Many thanks.

Jas

This should do it Jas.
```
xrandr --output XM7 --pos 1280x800
```
This is assuming XM7 is not the default monitor and is to the right of the default. Let me know if that is not right or if there are still issues after using this. Getting close to having it?

---

### Post by Mathias1 on 2011-05-19
Hello again.

I've managed to get the nVidia X-server settings to automatically enable the external monitor, but it won't disable the laptop monitor, so I get a little messed up picture. I've tried to use grandr, but it only detects one outpu "default" and that is the external screen.
Please help.

---

### Post by southafricanguy on 2011-05-19
Hey Jim,

Still no luck. Here is the output:

```
jas@jas-EasyNote-MX37-T-003:~$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 1280 x 800, maximum 1280 x 800
default connected 1280x800+0+0 0mm x 0mm
   1280x800       60.0* 
   1024x768       75.0     70.0     60.0  
   800x600        75.0     72.0     60.0     56.0  
   640x480        75.0     73.0     60.0  
  XM7 (0x134)  135.0MHz
        h: width  1440 start 1520 end 1672 total 1904 skew    0 clock   70.9KHz
        v: height  900 start  901 end  904 total  932           clock   76.1Hz
jas@jas-EasyNote-MX37-T-003:~$ xrandr --output XM7 --pos 1280x800
xrandr: Failed to get size of gamma for output default
warning: output XM7 not found; ignoring
```

Sincere thanks.

Jas

---

### Post by Blasphemist on 2011-05-19
I'm somewhat confused with what to do in nvidia and what do in xrandr since I don't have nvidia to look at. It would also help me to see what the screens look like. Could you take a screen shot of the desktop showing both monitors? Printscreen will do it. With that I think I can recommend changes in xrandr. I'm surprised about what xrandr shows now but I don't want to make a recommendation till I see what it looks like now.

---

### Post by jocko on 2011-05-20
> **Blasphemist said:**
> I'm somewhat confused with what to do in nvidia and what do in xrandr since I don't have nvidia to look at. It would also help me to see what the screens look like. Could you take a screen shot of the desktop showing both monitors? Printscreen will do it. With that I think I can recommend changes in xrandr. I'm surprised about what xrandr shows now but I don't want to make a recommendation till I see what it looks like now.
If the nvidia proprietary driver is installed, you have to use nvidia-settings (or edit /etc/X11/xorg.conf) to handle the outputs. With the nvidia driver, xrandr will never detect more than one output, but that output is a combination of all active monitors, so if you set up two monitors side by side in nvidia-settings, xrandr will see one output with the combined width of both your monitors and the height of your largest monitor.

@Mathias1: Not sure exactly how, but it should be possible to set up xorg.conf so that it uses the external monitor if it's connected and otherwise uses the laptop monitor.
You probably need to add specific sections for both monitors in xorg.conf and make sure twinview is not active... Unfortunately I have too little time right now, so I won't be able to figure out how to do it, but I'm sure you'll get help if you search the forum or make a new thread to ask your question...

---

### Post by southafricanguy on 2011-05-20
Hi all,

Okay, I'm really befuddled. :-? I should be using some kind of SiS Mirage 3 (or compatible) driver. Where does nvidia fit into the mix of things?

Sorry - I'm a bit new to Ubuntu.

Many thanks.

Jas

---

### Post by Blasphemist on 2011-05-20
The nvidia stuff was for another person in the thread Jas. Sorry for the confusion. I saw something in another thread that may not be the solution for you but I'd like for you to see how it does. I'd like you to use the resolutions you want and make the output names match yours. Notice this command sets both outputs mode and positions. You could run it first to see what happens.
```
xrandr --output VGA1 --mode 1920x1080 --pos 0x0 --output HDMI3 --mode 1920x1080 --pos 1920x0
```
> **Re: Ubuntu 11.04 Dual monitor problems**
A colleague of mine wrote a simple script

```
#!/bin/bash

if [ "$1" = "dock" ]; then
xrandr --output LVDS1 --off
xrandr --output VGA1 --mode 1920x1080 --pos 0x0 --output HDMI3 --mode 1920x1080 --pos 1920x0
else 
xrandr --output VGA1 --off --output HDMI3 --off
xrandr --output LVDS1 --mode 1366x768 --pos 0x0
fi

unity --replace &
```
I have a Lenovo T510 laptop and a docking station. The dockstation has 1 VGA and 1 HDMI port. I have a Samsung 23" monitor connected to each port (i.e., 2 monitors total). 

Run the script after booting into Unity and docked with

```
dockedMonitor.sh dock
```
Run the script without the "dock" param again to go back to just the laptop (i.e., when you're undocked).

Run 

```
xrandr
```
to see what options are available for your particular setup, and update the script accordingly.

Note: if you're running Ubuntu Classic, then be sure to remove the last line of the script above.

---

