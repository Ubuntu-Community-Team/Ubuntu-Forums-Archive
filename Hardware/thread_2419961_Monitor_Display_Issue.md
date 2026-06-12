---
title: "Monitor Display Issue"
date: 2019-05-27
forum: Hardware
---

### Post by t26427 on 2019-05-27
## My Setup ##
I have 3 identical monitors (3 s2240l's) and a sapphire nitro r9 380 graphics card.


These monitors only accept HDMI and VGA inputs.
The r9 380 has 3 outputs i'm trying to use: an HDMI output, a DisplayPort output, and a DVI output. Because of this, I use a Displayport --> HDMI converter and a DVI --> VGA converter for two of the monitors.


I triple boot Ubuntu, Arch Linux, and Windows 10 to test this configuration on.




----------
## The Issue ##


Whenever I first boot my computer all 3 monitors light up and stay lit through the bios screen. However, as soon as an OS starts to boot, the DVI --> VGA monitor goes to sleep and displays no output for the rest of the session.


In Windows, this problem was resolved after I installed the AMD graphics driver. To my understanding Ubuntu comes with open source drivers for AMD cards so I shouldn't have to install anything, although I could be wrong about that. So now I'm kind of left wondering how I'm supposed to resolve this problem in Ubuntu (and other Linux distros I might want to run as well since I know the same issue occurs in Arch after I've got a DE installed).


I'd love to switch to Linux and possibly Ubuntu as my my daily driver but If I can't get all of my hardware working properly on it then this poses a problem. 




----------
## Notes / What I've tried ##


1. Ubuntu is for sure detecting that the monitor is plugged in. When I check the display settings the monitor is there and I can move my cursor and windows into the area that the monitor should be. The only difference between the problem monitor and the working monitors I can see from this screen is that I don't have an option to change the refresh rate on the problem monitor while I can on the other monitors. This is peculiar so maybe somebody can help find a lead from this. 


2. I know that it isn't an issue with the fact that there are multiple monitors.
If I disconnect all monitors besides the DVI to VGA one then I still lose visual once the OS starts to boot.


3. I've tried googling and reading wikis as well with no results. Somebody had a very similar question [here]("https://askubuntu.com/questions/1131649/cant-get-output-to-monitor-via-dvi-i-to-vga-adapter") but no one ever responded. In fact, my xrandr output was incredibly similar to that persons as well.




----------
## Stuff you might find useful  ##


Here is my output from xrandr:


```
> Screen 0: minimum 320 x 200, current 5760 x 1080, maximum 16384 x 16384
DisplayPort-0 connected 1920x1080+3840+0 (normal left inverted right x axis y axis) 476mm x 267mm
   1920x1080     60.00*+  50.00    59.94  
   1680x1050     60.00  
   1280x1024     75.02    60.02  
   1440x900      60.00  
   1280x800      60.00  
   1152x864      75.00  
   1280x720      60.00    50.00    59.94  
   1024x768      75.03    60.00  
   800x600       75.00    60.32  
   720x576       50.00  
   720x480       60.00    59.94  
   640x480       75.00    60.00    59.94  
   720x400       70.08  
HDMI-A-0 connected primary 1920x1080+1920+0 (normal left inverted right x axis y axis) 476mm x 267mm
   1920x1080     60.00*+  50.00    59.94  
   1680x1050     60.00  
   1280x1024     75.02    60.02  
   1440x900      60.00  
   1280x800      60.00  
   1152x864      75.00  
   1280x720      60.00    50.00    59.94  
   1024x768      75.03    60.00  
   800x600       75.00    60.32  
   720x576       50.00  
   720x480       60.00    59.94  
   640x480       75.00    60.00    59.94  
   720x400       70.08  
DVI-D-0 disconnected (normal left inverted right x axis y axis)
DVI-D-1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 476mm x 267mm
   1920x1080     60.00*+
   1680x1050     60.00  
   1280x1024     75.02    60.02  
   1440x900      60.00  
   1280x800      60.00  
   1152x864      75.00  
   1280x720      60.00  
   1024x768      75.03    60.00  
   800x600       75.00    60.32  
   640x480       75.00    59.94  
   720x400       70.08
```


.


Also here is a picture for the configuration of the problem monitor in display settings. Note the lack of a refresh rate option:
[https://i.stack.imgur.com/KNXZ5.png](https://i.stack.imgur.com/KNXZ5.png)





I've gone ahead and booted back into windows to look at the monitor stats there.
Here is a picture of that:
[https://i.stack.imgur.com/pyC1T.png](https://i.stack.imgur.com/pyC1T.png) 


And here it is in the AMD control panel:
[https://i.stack.imgur.com/7R79I.png](https://i.stack.imgur.com/7R79I.png)


One thing I noticed is that on Windows the monitor seems to be listed as a VGA while on Ubuntu its listed as DVI through xrandr. It's also listed as analog on windows if that means anything. Hopefully I've added enough here for somebody to be able to help.

---

### Post by wildmanne39 on 2019-05-27
Hello and welcome to the forum!

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

Please use the attachment facility by clicking on the paperclip or  use url's for images because apart from bandwidth issues for some, it makes it difficult for those using mobile devices to browse the forum.

---

### Post by t26427 on 2019-05-28
Welp, after numerous days with google and nearly 24 hours after asking about this showstopping issue across 3 different forums the only response I've gotten is a critique on my forum etiquette...
Since the community isn't going to be able to help me either I think I'm just gonna go ahead and delete the linux partitions to reclaim space.

Guess I'll check back into the linux scene in another couple years... hopefully display issues so seemingly simple as this will be resolved by then.

---

