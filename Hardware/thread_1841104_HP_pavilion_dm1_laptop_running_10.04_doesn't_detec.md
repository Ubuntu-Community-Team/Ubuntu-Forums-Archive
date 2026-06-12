---
title: "HP pavilion dm1 laptop running 10.04 doesn't detect projector"
date: 2011-09-08
forum: Hardware
---

### Post by jabrilm on 2011-09-08
I have Ubuntu 10.04 dual-booting on the HP Pavilion DM1, specs here:

[http://www.newegg.ca/Product/Product.aspx?Item=N82E16834157940](http://www.newegg.ca/Product/Product.aspx?Item=N82E16834157940)

After solving some wireless problems, I now have realized that my laptop won't connect with a projector when running Ubuntu. Under Monitors, nothing happens when I click "Detect Monitors" either. Is this a graphics card driver issue? If so, can I add a driver to the hardware drivers manager? The graphics card is AMD Radeon HD 6310.

Any suggestions?

---

### Post by Toz on 2011-09-08
Are you pressing the Fn+F4 key to switch between separate display configurations with the projector plugged in? 

See: [http://h10032.www1.hp.com/ctg/Manual/c02842989.pdf]("http://h10032.www1.hp.com/ctg/Manual/c02842989.pdf") - page 20.

---

### Post by jabrilm on 2011-09-08
Yes, I tried function + f4 a bunch of times with no luck. In Windows, I was able to get it to work with a projector, just not under Ubuntu.

---

### Post by Toz on 2011-09-09
Do any of your functino keys work?

Open a terminal window, and enter in this command?
```
acpi_listen
```
The program will then sit and listen for events. Press Fn+F4. Does anything show up in the terminal window?

Press Ctrl+c in the terminal window to cancel the acpi_listen program.

With the projector plugged in, try entering the following command:
```
sudo acpi_fakekey 227
```
Any luck?

---

### Post by jabrilm on 2011-09-09
Doing* acpi_listen* and pressing function+f4 gives output:

^[OS^[OS^[OS^[OSbattery BAT0 00000080 00000001
battery BAT0 00000081 00000001

When I do *sudo acpi_fakekey 227* with the projector plugged in, nothing happens.

I tried the first three steps here to install a new graphics driver:

```
[http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Ubuntu_X_Team.27s_PPA](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Ubuntu_X_Team.27s_PPA)
$ sudo add-apt-repository ppa:ubuntu-x-swat/x-updates 
$ sudo apt-get update

$ sudo apt-get install fglrx
``` 
I rebooted and still no luck detecting the projector. I opened a terminal and typed 

$ fglrxinfo

and get a segmentation fault.

I removed that driver and went to [http://support.amd.com](http://support.amd.com) and downloaded the relevant driver using their drop-down boxes (notebook drivers - radeon hd - 6310 - linux x86 64). That seemed to install fine.

```
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: AMD Radeon HD 6300 series Graphics
OpenGL version string: 4.1.11005 Compatibility Profile Context
```

But now when I plug in the projector and click 'Detect Monitors' my display goes completely haywired, with the display all fragmented and the desktop background all sliced and diced and frozen. Removing the projector doesn't help and I have to force the laptop to power down and restart.

Any suggestions? Anyone seen that before?

Is there another way of trying to force Ubuntu to recognize a connected projector? I have tried function+f4 which does nothing, and 'Detect Monitors' which causes the errors described above.

---

### Post by Toz on 2011-09-09
It doesn't look like your Fn+F4 is sending the correct codes. You might be able to do this using xrandr. Have a look at the following post: [http://ubuntuforums.org/showthread.php?t=1395876]("http://ubuntuforums.org/showthread.php?t=1395876")

As for updating the ATi driver, do you have anything listed under additional drivers (the ubuntu preferred way of installing the proprietary drivers)?

---

### Post by jabrilm on 2011-09-09
Do you mean under Administration --> Hardware Drivers? Yes, it lists the "ATI/AMD proprietary FGLRX graphics driver."

Not sure the guide you linked will work for me, e.g. I don't have a /etc/X11/xorg.conf file.

---

### Post by Toz on 2011-09-09
> **jabrilm said:**
> Do you mean under Administration --> Hardware Drivers? Yes, it lists the "ATI/AMD proprietary FGLRX graphics driver."

Have you enabled it?

> **jabrilm said:**
> Not sure the guide you linked will work for me, e.g. I don't have a /etc/X11/xorg.conf file.

You could start from point #2. No need to create the script right away. What does the following return with the projector plugged in:
```
xrandr -q
```

---

### Post by jabrilm on 2011-09-10
I don't have a projector at home, so won't be able to test this out again till Monday. But I just tried to connect with my desktop monitor at home and it also wasn't recognized. The output of

$ xrandr -q

is 

```
Screen 0: minimum 320 x 200, current 1600 x 900, maximum 1600 x 1600
LVDS connected 1366x768+0+0 (normal left inverted right x axis y axis) 256mm x 144mm
   1366x768       60.0*+
   1360x768       60.0  
   1280x768       60.0  
   1280x720       60.0  
   1024x768       60.0  
   1024x600       60.0  
   800x600        60.0  
   800x480        60.0  
   640x480        60.0  
DFP1 disconnected (normal left inverted right x axis y axis)
CRT1 connected (normal left inverted right x axis y axis)
   1440x900       60.1 +   75.0  
   1400x1050      74.9  
   1280x1024      75.0     60.0  
   1280x960       60.0  
   1280x800       74.9     60.1  
   1280x768       74.9     60.1  
   1280x720       60.0  
   1024x768       75.0     70.1     60.0  
   1024x600       75.0     70.1     60.0  
   800x600        72.2     75.0     60.3     56.2  
   800x480        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     67.0     59.9
```

Also, when I go to Preferences --> AMD Catalyst Control Center, my display immediately becomes all static and frozen. So it seems there are major issues with the driver I downloaded.

---

### Post by Toz on 2011-09-10
> **jabrilm said:**
> I don't have a projector at home, so won't be able to test this out again till Monday. But I just tried to connect with my desktop monitor at home and it also wasn't recognized. The output of

$ xrandr -q

is 

Screen 0: minimum 320 x 200, current 1600 x 900, maximum 1600 x 1600
LVDS connected 1366x768+0+0 (normal left inverted right x axis y axis) 256mm x 144mm
   1366x768       60.0*+
   1360x768       60.0  
   1280x768       60.0  
   1280x720       60.0  
   1024x768       60.0  
   1024x600       60.0  
   800x600        60.0  
   800x480        60.0  
   640x480        60.0  
DFP1 disconnected (normal left inverted right x axis y axis)
CRT1 connected (normal left inverted right x axis y axis)
   1440x900       60.1 +   75.0  
   1400x1050      74.9  
   1280x1024      75.0     60.0  
   1280x960       60.0  
   1280x800       74.9     60.1  
   1280x768       74.9     60.1  
   1280x720       60.0  
   1024x768       75.0     70.1     60.0  
   1024x600       75.0     70.1     60.0  
   800x600        72.2     75.0     60.3     56.2  
   800x480        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     67.0     59.9

You're system _is_ recognizing two displays (LVDS & CRT1). Try this command:
```
xrandr --output CRT1 --mode 1280x1024
```

Here's another link: [http://linuxconfig.org/enable-multiple-clone-displays-to-vga-interface-projector-tv]("http://linuxconfig.org/enable-multiple-clone-displays-to-vga-interface-projector-tv")

---

### Post by Toz on 2011-09-10
> **jabrilm said:**
> Also, when I go to Preferences --> AMD Catalyst Control Center, my display immediately becomes all static and frozen. So it seems there are major issues with the driver I downloaded.

You should be using the proprietary driver provided by ubuntu and install-able via the Additional Drivers menu item. What happens when you go to the Additional Drivers screen and enable the driver there?

---

### Post by jabrilm on 2011-09-13
I have now been able to connect successfully with the projector. The trick has been to have the projector connected before I boot up. Then when Ubuntu starts up, the projector is automatically recognized. If I wait to plug it in until Ubuntu is already running, I still get problems like a frozen screen when I try to use the Catalyst software or do xrandr -q.

> You should be using the proprietary driver provided by ubuntu and  install-able via the Additional Drivers menu item. What happens when you  go to the Additional Drivers screen and enable the driver there? 	

Are you referring to System --> Administration --> Hardware Drivers? The driver there is currently deactivated. I wasn't having luck with it so I downloaded the driver from the AMD/ATI website. Also having problems with that one (sometimes a frozen screen) but the projector is at least connecting sometimes.

---

