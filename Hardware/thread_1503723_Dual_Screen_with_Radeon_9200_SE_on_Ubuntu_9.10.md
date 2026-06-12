---
title: "Dual Screen with Radeon 9200 SE on Ubuntu 9.10"
date: 2010-06-07
forum: Hardware
---

### Post by Naturofix on 2010-06-07
Ive got a  radeon 9200 SE graphics card. I would like to run a second screen on the DVI output but can't get it to connect.

I tried a number of things, it appears the default drivers are not compatible so I have purged the drivers.

I'm using Ubuntu 9.10, there is no xorg.conf file or xfix in the recovery mode as their used to be in older versions 

Has anyone else had this problem

What do I do to fix this.


xrandr

Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 1280 x 1280
VGA-0 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 340mm x 270mm
   1280x1024      75.0*+   60.0  
   1024x768       75.0     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     66.7     59.9  
   720x400        70.1  
DVI-0 disconnected (normal left inverted right x axis y axis)
S-video disconnected (normal left inverted right x axis y axis)

---

### Post by bnahrwold on 2010-07-07
I have Ubuntu 10.04 with a Radeon 9200 Pro (ATI RV280) with similar problems.
An attempt to use System => Preferences => Monitors => Deselect same image on all monitors does nothing.
An attempt to use dpkg-reconfigure xserver-xorg from telinit 3 also does nothing
I also have no xorg.conf since I am using the default driver.
Tried xrandr --output  DVI-0 --left-of DVI-1
Also does nothing.
Tried setting ~/.config/monitors.xml <clone></conle> tag to no and rebooting.  Still nothing,
My only option appears to be loading the 
xorg-driver-fglrx

[FONT=Verdana]driver, which I really don't want to do.  Any recommendations for 
resolving this configuration issue?

Thanks,

Bryan Nahrwold

[/FONT]

---

