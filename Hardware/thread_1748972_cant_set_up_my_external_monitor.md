---
title: "cant set up my external monitor"
date: 2011-05-04
forum: Hardware
---

### Post by captainfig on 2011-05-04
I have an HP Pavillion running ubuntu 11.04

I have connected my Acer H2332 monitor via HDMI cable but it wont set as the correct resolution so not everything is displayed on the monitor.

Basically what i want to do is have my laptop closed and use only the external monitor as a clone.

I am struggling to set this up.

I also cannot get the computer to automatically register the monitor when the system boots.

Please help
Thanks

---

### Post by waspbloke on 2011-05-04
I have my machine set up this way.

You want to launch the Monitor Preferences gizmo (gnome-display-properties from a terminal). *Uncheck* 'same image on all monitors' and select the laptop monitor in the little viewer pane and switch it off.

It sounds like maybe your laptop has a 1080p resolution while your external display has 720p native, which would explain why the external display is a clipped portion of the laptop display. Turning off mirroring will allow each display to maximize its display based on its best highest resolution.

If the external display doesn't initialize during boot even when the laptop lid is closed (after following the method above) you may need to add the external display mode settings to xrandr.

---

### Post by captainfig on 2011-05-05
I am using Ubuntu 11.04 with Unity.

The graphics card is a Nvidia Gforce 8400.

How do I get the laptop to automatically register the external monitor when the machine boots up? so i can use only the external monitor with the laptop lid closed.

Also with the correct resolution of 1080. 

when i launch the monitor properties is does not allow me to check the box to turn the monitor off.

it worked fine like this on windows but i want to use ubuntu

Thanks

---

### Post by waspbloke on 2011-05-05
Unity is just a shell replacement, you still have all the guts of gnome underneath. I don't use Unity so I'm not sure of the menu path but using its search field, look for "Monitors" or just type "gnome-display-properties" from a terminal window will get you to the same place.

The window that opens will have basic settings for the monitors that have been detected (Laptop & any other) with a little layout display. The layout display may just have one item with "Mirror Screen" on, if so *uncheck* the box with "Same image on all monitors" and apply...Now you should have 2 screens displayed that you can click on each one and set its properties (on/off, resolution, refresh etc). If you only have one screen (laptop) then for some reason the external display has not been properly detected and initialized - try unplugging and re-plugging the HDMI cable. Assuming you see 2 screens, select the external displays screen and make sure it is set to "on" and the correct resolution, then select the laptop screen and set to "off"...and apply.

Alternately, assuming you are using the Nvidia driver, use the Nvidia Settings utility to do the same thing. There will be a section for enabling/disabling connected displays and setting the resolutions.

Either way, you want to disable the laptops display and enable the external display. If neither route recognizes your external display you will need to roll your sleeves up and try something a bit more involved. In case of that, run "xrandr -q" in a terminal and post the output here.

---

### Post by captainfig on 2011-05-05
This is what i get when i type that into the terminal :

xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 175, current 1920 x 1080, maximum 1920 x 1080
default connected 1920x1080+0+0 0mm x 0mm
   1280x800       50.0    100.0  
   1024x768       51.0     52.0  
   960x540        53.0  
   840x525        54.0  
   832x624        55.0  
   800x600        56.0     57.0     58.0     59.0     60.0  
   800x512        61.0  
   720x450        62.0  
   720x400        63.0  
   700x525        64.0  
   680x384        65.0     66.0  
   640x512        67.0     68.0  
   640x480        69.0     70.0     71.0     72.0     73.0  
   640x400        74.0  
   640x350        75.0  
   576x432        76.0     77.0     78.0     79.0     80.0     81.0  
   512x384        82.0     83.0     84.0     85.0     86.0  
   416x312        87.0  
   400x300        88.0     89.0     90.0     91.0     92.0  
   360x200        93.0  
   320x240        94.0     95.0     96.0     97.0  
   320x200        98.0  
   320x175        99.0  
   1920x1080     100.0     50.0* 



i have managed to set it up that the laptop monitor is off but i cant get the computer to boot with the external monitor.

i have to set it up each time.

also when i go through the ubuntu monitor settings it just says unknown - will only show the laptop monitor as unknown, not the external ( however the nvidia settings recognise both)

the only problem that im having now is to boot the system and having the external monitor recognised and working without having to change any settings every time i boot up

Many thanks once again

---

### Post by waspbloke on 2011-05-05
Reading around, it's not entirely clear whether nvidia drivers fully support xrandr which might explain why the output you posted doesn't look how I expected it to.

Still, next (and simplest) thing to try is to make your external monitor the default. There's probably a way using the nvidia settings but certainly by going again into the System > Preferences > Monitors (gnome-display-properties) application. Just select the external monitor in the layout view then click the "Make default" button and apply.

It may be, looking at the output you posted, that it already is the default, in which case you might want to look into reconfiguring X with a fresh xorg.conf file but TBH, being an ATI guy, you might want to search for similar nvidia related posts as there's likely to be some quirks relating to that driver that I'm not aware of.

---

