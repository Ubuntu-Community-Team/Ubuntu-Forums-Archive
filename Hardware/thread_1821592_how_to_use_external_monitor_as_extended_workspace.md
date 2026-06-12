---
title: "how to use external monitor as extended workspace?"
date: 2011-08-09
forum: Hardware
---

### Post by CryptKeeper777 on 2011-08-09
I have just installed Xubuntu on my MacBook. I have an external monitor which I use as extended workspace. When I plug it in, nothing happens, but I can activate the monitor in the system settings. The problem ist that my MacBook screen is mirrored onto the other screen, which is fine for beamers but makes no sense with external monitors. There's no option to use the monitor as exptended workspace. 

How can I make this work?

It's an Acer monitor, BTW, if that's important, and I'm running Xubuntu 11.04 (just downloaded and installed yesterday) on a MacBook 4.

Edit: **SOLUTION**: It easily works with URandR (sudo apt-get install urandr), a GUI to RandR. But URandR doesn't like Compiz, setting up a virtual screen of the right size fails if Compiz is running. The solution: Disable Compiz (xfwm4 --replace), then set up the virtual screen with URandR, and then turn on Compiz again (compiz --replace). Once the virtual screen is set up, there doesn't seem to be any problems with Compiz anymore.

Not the ideal solution, but I'm satisfied with this workaround.

---

### Post by Metaxa on 2011-08-10
Not sure if this works in Xubuntu as with Ubuntu, but in the Monitor section there should be a check box that controls mirroring. Checked being mirrored, unchecked being extended. I have an older HP laptop when I plug my external monitor in an un-select it, my desktop gets extended. 



Regards,

Metaxa

---

### Post by CryptKeeper777 on 2011-08-10
No there's nothing, if there was I didn't have a problem because I know what mirroring means. But if it works in Ubuntu, it should work in Xubuntu as well, because it worked on XFCE on Fedora and AFAIK Xubuntu = Ubuntu + XFCE (though that's maybe a too simple consideration, I don't know too much about this stuff being a Linux newbie). 

I suppose I need to install some package giving me more options, but I don't really know anything about this stuff. But I think it should work somehow because the problem isn't hardware incompatibility or something like that because the monitor works, just only in mirrored mode (and with suboptimal resolution).

---

### Post by Metaxa on 2011-08-10
At this point you may want to submit some information so others can offer their help. Xrandr is a program that manually lets you configure your monitors and video settings.

Start with the basic in a terminal window:

sudo xrandr -q

and then

sudo lshw -class display

Regards,

Metaxa

---

### Post by CryptKeeper777 on 2011-08-10
Alright, here you are:

```

ruestefa@XubuntuMB:~$ sudo xrandr -q
Screen 0: minimum 320 x 200, current 1680 x 1050, maximum 8192 x 8192
LVDS1 connected 1280x800+0+0 (normal left inverted right x axis y axis) 286mm x 179mm
   1280x800       59.9*+
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
DVI1 connected 1680x1050+0+0 (normal left inverted right x axis y axis) 433mm x 271mm
   1680x1050      60.0*+
   1280x1024      75.0     60.0  
   1440x900       75.0     59.9  
   1280x960       60.0  
   1152x864       75.0  
   1280x720       60.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  
TV1 unknown connection (normal left inverted right x axis y axis)
   848x480        30.0 +
   640x480        30.0 +
   1024x768       30.0  
   800x600        30.0  

``````

ruestefa@XubuntuMB:~$ sudo lshw -class display
  *-display:0             
       description: VGA compatible controller
       product: Mobile GM965/GL960 Integrated Graphics Controller (primary)
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:44 memory:d0100000-d01fffff memory:c0000000-cfffffff ioport:6110(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile GM965/GL960 Integrated Graphics Controller (secondary)
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:d0200000-d02fffff

```

---

### Post by CryptKeeper777 on 2011-08-18
nobody any idea..?

BTW I've found this [thread]("http://ubuntuforums.org/showthread.php?t=775214") over google in which it says:
>  i guess the package you're looking for is displayconfig-gtk 

I've tried to install this package, but it isn't in the repos, and I didn't find a similarly named package...

---

### Post by CryptKeeper777 on 2011-08-22
I finally solved the problem! I was looking for something in the Ubuntu Software Center when I suddenly had the idea to look for an app that could solve my external monitor problem, and I found the app "Multiple Screens" which allows me to group the monitors the way I want, so I could arrange them so that the right border of my MacBook screen is the left border of the external monitor.

---

### Post by CryptKeeper777 on 2011-08-24
Well unfortunately the mentioned program didn't solve the problem...

At first it worked (as far as my memory goes ;) ), but now it doesn't anymore. I am able to set up the desired monitor arrangement (the 13" MacBook screen on the left, and on the right of it the 20" external monitor), but then all behaves somehow crazy. Both monitors show what they should, the MacBook the normal XFCE desktop and the external monitor the empty desktop wallpaper. So far so good.

But the system assumes that my MacBook screen is 20" big and where this 20" desktop ends, measuring from the left border of the MacBook screen onto the 20" screen on the right of is, is a virtual border over which I can't push any window. And when I maximize a window, it's maximized on this virtual 20" screen...
 
Really strange. I made a quick sketch of it. The virtual 20" screen is green, and the right border of this virtual 20" screen is marked in red.

[IMG]http://img542.imageshack.us/img542/4848/20110824180438.jpg[/IMG]

Any ideas whatsoever? It's really annoying and somewhat unbelievable that it shouldn't be possible to use two monitors at the same time!

---

### Post by CryptKeeper777 on 2011-08-30
I finally solved the problem. Turns out this "Second Screen"-program from the Software Center is - or at least looks the same as - URandR. Per chance I read somewhere that URandR doesn't like Compiz which I have installed. So I turned off Compiz (xfwm4 --replace), configured the desired monitor setup with URandR, and then turned on Compiz again (compiz --replace). And it seems to work perfectly, once the monitor arrangement is configured, Compiz isn't problematic anymore.

Now I'm happy. :D

---

### Post by allankelly on 2012-03-15
Thanks for this. I have XUbuntu 11.10 - which is the standard Ubuntu 11.10 but with the xfce 4.8 desktop - and an external monitor. Xfce's Setting Manager -> Display did give me a copy of my laptop display on the external monitor, but that's not as much use as a desktop extension.

I couldn't find urandr in the repositories via Synaptic, nor Second Screen via Ubuntu Software Centre.

However Synaptic lists arandr which is a python GUI - and which works perfectly! I'm not running compiz.

Highly recommended.

Thanks again!
al.

---

