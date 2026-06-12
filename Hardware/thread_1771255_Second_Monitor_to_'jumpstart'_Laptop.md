---
title: "Second Monitor to 'jumpstart' Laptop"
date: 2011-05-30
forum: Hardware
---

### Post by jonathon6017 on 2011-05-30
I have recently installed Ubuntu 11.04 and It's pretty good on this laptop I had one sound issue that I got fixed now I have a second concern. Whenever my laptop boots up it will play the drum sounds and log me in automatically (as I selected in the install menu) but the Laptop screen is blank. If I want to get it to start working I have to plug up a second monitor and then my laptop screen comes up, I can then unplug the second if wanted. This would be fine if it was a desktop and I always had the second monitor available to me but considering that this is a laptop and I do travel with it I would like to get this fixed. Does anybody have any idea of what may be causing this.

---

### Post by jonathon6017 on 2011-05-30
(Hey Sorry I double checked it does not appear I am running a 64bit Variant I believe it is just a plain old 32bit)

Sorry That is incorrect i ran the wrong command it IS 64bit lol :confused:

---

### Post by jonathon6017 on 2011-05-30
Anyone?

---

### Post by DanEames on 2011-06-22
I have exactly the same problem. I'm struggling to find any solution. I don't know that I have an nVidia graphics card or any other for that matter. But the problem has come about as a result from upgrading.

If I find anything I'll post it here.

---

### Post by DanEames on 2011-06-22
I've tried all ideas that I can find on here. I tried nomodeset in the GRUB as described in previous posts and known faults with work arounds.
 
My laptop uses an Intel Atom N455 with PineTrail chipset. The graphics are integrated. This did work on 10.04. Maybe I need to roll back to that release.
 
Does anyone else have any ideas?
 
Thanks!
 
Dan

---

### Post by DanEames on 2011-06-23
One more thing to add. I am using 32bit software.
 
Thanks,
 
Dan

---

### Post by Blasphemist on 2011-06-23
There is a graphic way to do this and a command. I think, though I don't remember for sure, that you need to install the Displays application through the software center. That will allow you to choose one of your displays as the default. See screen shot, make default button at the bottom with one of the displays selected. At the next login, the chosen screen should be the default and your issue should be resolved.

Also, xrandr is your friend. It can also be used to set the default but it is referred to as primary in xrandr. The following command shows my current outputs and some of the detail on them. I've colored the output names.
```
jim@jim-Satellite-L505:~$ xrandr
Screen 0: minimum 320 x 200, current 2966 x 900, maximum 8192 x 8192
[COLOR="red"]LVDS1[/COLOR] connected 1366x768+0+0 (normal left inverted right x axis y axis) 353mm x 198mm
   1366x768       60.0*+
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
[COLOR="Red"]VGA1[/COLOR] connected 1600x900+1366+0 (normal left inverted right x axis y axis) 443mm x 249mm
   1600x900       60.0*+
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
jim@jim-Satellite-L505:~$ 

``` 
LVDS1 and VGA1 are connected. I can set LVDS1 as the primary output with this command.
```
xrandr --output LVDS1 --primary
```

---

### Post by DanEames on 2011-06-28
Jim,
 
Thanks for the steer. Unfortunetly the problem persists. I even set a new resolution up in;
 
/etc/gdm/Init/Default
 
But the same, I need to plug a remote monitor in and then it works. I can change the resolution but I just don't seem to be able to force the LVDS1 to start up, even though when I check xrandr it appears to be the default.
 
Is this just an Intel (the laptop graphics is part of the Intel chipset I think) driver issue?
 
Thanks,
 
Dan

---

### Post by Blasphemist on 2011-06-28
Dan, let me ask some questions please and lets gather some detail.

When you are at the grub menu with only the laptop monitor, if you boot into rescue mode, do you get display on the laptop?

If you boot to the Ubuntu live CD and choose try ubuntu, does the laptop display work?

If not for either of the above, do any of these put anything on the screen?
> <Ctrl><Alt><F1> 
Switch to the first text terminal. Under Linux you can have several (6 in standard setup) terminals opened at the same time. Terminals start as tty0 and go up from there. Most of the time the normal boot text console, that is present "under" the GUI or Xsession (in Ubuntu) is tty1, so you would press <Cntrl><Alt><F2> to get to it... 

<Ctrl><Alt><Fn> (n=1..6) 
Switch to the nth text terminal. 

tty<Enter> 
Print the name of the terminal in which you are typing this command. 

<Ctrl><Alt><F7> 
Switch to the first GUI terminal (if X-windows is running on this terminal). 
Are you getting anything in the X error log (/home/username/.xsession-errors)?

Please run this command and post the results.
```
sudo lshw -c Display
```
Please run this and post the kernel version results it provides.
```
uname -a
```
Run this and look for the OpenGL version string. Mine is 2.1 Mesa 7.10.2. It will be near the beginning.
```
glxinfo -v | more
```
Please post the xrandr query results.
```
xrandr -q
```
We made need for you to do some kernel mode setting but please post these results.

---

### Post by DanEames on 2011-06-29
Jim,
 
Thanks for coming back with so many things for me to try.
 
Here goes;
 
1) I hold down the Shift key and see Recovery mode. After that I need a monitor to see any more, A recovery menu is then seen on the laptop screen. I only have to plug a switch on monitor in for a few seconds, remove the cable and the screen recovers.
 
2) There is no CD, I can try a boot USB stick. This worked on previous versions, maybe no help.
 
3) I had to fire up the screen to do this, it didn't cause the screen to come on. I can use the combination <Ctrl><Alt><Fn> and see that the ttyn message matches the Fn key. It then asks me to login, which I can do. If I type tty <CR> it comes back with /dev/tty1. However that changes to match the corresponding Fn.
 
4) I type sudo lshw -c Display, something flashes  then;
 
*-display:0 
description: VGA compatible controller
product: N10 Family Integrated Graphics Controller
vendor: Intel Corporation
physical id: 2
bus info: pci@0000:00:02.0
version: 00
width: 32 bits
clock: 33MHz
capabilities: msi pm vga_controller bus_master cap_list rom
configuration: driver=i915 latency=0
resources: irq:46 memory:98180000-981fffff ioport:60c0(size=8) memory:80000000-8fffffff memory:98000000-980fffff
*-display:1 UNCLAIMED
description: Display controller
product: N10 Family Integrated Graphics Controller
vendor: Intel Corporation
physical id: 2.1
bus info: pci@0000:00:02.1
version: 00
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list
configuration: latency=0
resources: memory:98100000-9817ffff
^[[Adan@dan-MAL-91013Nsudo lshw -c Display
*-display:0 
description: VGA compatible controller
product: N10 Family Integrated Graphics Controller
vendor: Intel Corporation
physical id: 2
bus info: pci@0000:00:02.0
version: 00
width: 32 bits
clock: 33MHz
capabilities: msi pm vga_controller bus_master cap_list rom
configuration: driver=i915 latency=0
resources: irq:46 memory:98180000-981fffff ioport:60c0(size=8) memory:80000000-8fffffff memory:98000000-980fffff
*-display:1 UNCLAIMED
description: Display controller
product: N10 Family Integrated Graphics Controller
vendor: Intel Corporation
physical id: 2.1
bus info: pci@0000:00:02.1
version: 00
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list
configuration: latency=0
resources: memory:98100000-9817ffff
 
5) uname -a;
 
Linux dan-MAL-91013N 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 i686 i386 GNU/Linux
 
6) glxinfo -v | more
 
The program 'glxinfo' is currently not installed. You can install it by typing:
sudo apt-get install mesa-utils
 
7) xrandr -q
 
Screen 0: minimum 320 x 200, current 1024 x 600, maximum 4096 x 4096
LVDS1 connected 1024x600+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
1024x600 60.0*+
800x600 60.3 56.2 
640x480 59.9 
VGA1 disconnected (normal left inverted right x axis y axis)
 
 
 
Thank you for your assistance,
 
Dan

---

### Post by DanEames on 2011-07-10
Using a USB stick with the 10.04 installer on I could run Ubuntu without any issue. Through frustration at needing my laptop and a monitor to get it going I have now rolled back to 10.04. This is working without issue. I don't know what or why 11.04 won't work with the Intel N10 Graphics but I will stick to 10.04 for now.

---

### Post by Blasphemist on 2011-07-10
I'm not sure what to say. You are using the right driver in 11.04. I don't see from the information you provided a reason for the issue. I've seen reports from others that are using that n10 with natty, including the person that reported this bug that is a different video issue. [http://fossplanet.com/f10/%5Bbug-768401%5D-%5Bnew%5D-acer-aspire-one-d255e-intel-n10-graphics-display-partially-garbled-returning-hibernate-s4-130678/](http://fossplanet.com/f10/%5Bbug-768401%5D-%5Bnew%5D-acer-aspire-one-d255e-intel-n10-graphics-display-partially-garbled-returning-hibernate-s4-130678/) As you can see in that bug, the proposed kernel solved the issue. You could try that. 

Is this your pc? [http://www.malata.com/en/product_detail.aspx?classid=643&id=24](http://www.malata.com/en/product_detail.aspx?classid=643&id=24)

Another thing you might try is this. Burn the oneiric daily build and try it. That is one of my disto's installed. I'm finding natty very solid, just not the gnome shell. It is using the 3.0 kernel so at least running that from the iso to check it out might be worthwhile. [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

---

### Post by stony999 on 2011-07-13
I have the same problem with my Fujitsu NH570 (Intel GMA HD Graphics) and Natty 64bit and Gnome 2. I use a dual monitor setup with primary screen on external monitor HDMI1 and secondary screen on Laptop Monitor LVDS1. Therefore I manually run some xrandr commands in a script to set this up after laptop starts up.

When I boot up **without an external monitor attached**, I can see the Grub Boot menu, then screen gets black. After a while a mouse cursor appears. But screen remains black. 
Ctrl-Alt-F1 and so on does not work. I can see some flickering in the top 1st line on the screen, so there may be a problem with synchronisation. Back to Ctrl-Alt-F7 there is still the black screen with the mouse pointer.

As soon as I attach a VGA or HDMI monitor, I can see the login menu. I can detach the external monitor then and can continue working.

But using the laptop without external monitor within reach therefore is not possible.

Any hints how to solve that?
Maybe I can run some xrandr command during bootup as a workaround? If yes: Where should I put the commands?

Here is some data:
```

# uname -a
Linux NH570 2.6.38-10-generic #46-Ubuntu SMP Tue Jun 28 15:07:17 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
# lsmod |grep video
uvcvideo               72195  0 
videodev               82052  1 uvcvideo
v4l2_compat_ioctl32    17078  1 videodev
video                  19438  1 i915

```

---

### Post by DanEames on 2011-07-13
Jim,
 
Thanks for checking back on me, I appreciate it. I will give the bug a look over and see if it is the same fix. 
 
The PC you have found a link to certainly looks like my netbook though it was bought from a local company that put their name to a lot of OEM equipment. Since it came with no reference you've probably identified the manufacturer.
 
I'm not too sure what to do with the daily build but I will try to make some time this weekend to try that out.
 
Thanks,
 
Dan
 
 
 
Stony,
 
It sounds like you have the same problem. Any xrandr strings didn't help me. There are a number of suggestions out there but they appear to be for resolution or primary display faults. Look in etc/gdm/Init/Default around the Splash section. Google will throw some results up I am sure.
 
Dan

---

### Post by DanEames on 2011-10-18
All,

I don't know if the fix was there all along but this is what I have come to find fixes this problem.

Booting up the PC I closed the screen so the laptop went in to hibernation. I opened the screen up and there was the log in.

So it isn't perfect but it works without a second monitor.

Latest updates installed but the original fault remains. I've not updated to the new version of Ubuntu.

Dan

---

