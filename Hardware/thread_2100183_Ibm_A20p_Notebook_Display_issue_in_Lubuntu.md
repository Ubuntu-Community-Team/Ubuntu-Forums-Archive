---
title: "Ibm A20p Notebook Display issue in Lubuntu"
date: 2012-12-31
forum: Hardware
---

### Post by VitalBodies on 2012-12-31
Greetings and Happy New Years, at least if you are in the US. 
My new years resolution is to fix the resolution on my notebook. 
After an install of Lubuntu 12.10 using the alternative installer, (because of having only 384mb of ram) I noted the screen resolution is wrong on an old IBM Thinkpad A20p. It is the same wrong I got running the 12.10 Ubuntu liveCD. 
Rather than 1400x1050 it is 1024x768 at 60hz. This causes the screen to look somewhat ripped in half vertically then doubled on the right. Very challenging to navigate. 

A nice yet brief description of the machine is here in the ThinkWiki: 
[IBM ThinkPad A20p]("http://www.thinkwiki.org/wiki/Category:A20p")
Puppy Linux was able to get the resolution right running from the liveCD so I know there is hope. 

In trying to research the matter I ran into a few problems with the Lubuntu documentation. 
This page offers what would seem like the best approach: 
[https://help.ubuntu.com/community/Lubuntu/Monitor_or_Screens#Can.27t_Change_to_Screen_Resolution_I_need_For_My_Monitor_or_Laptop_Screen]("https://help.ubuntu.com/community/Lubuntu/Monitor_or_Screens#Can.27t_Change_to_Screen_Resolution_I_need_For_My_Monitor_or_Laptop_Screen")

The keyboard command (ctrl+alt+f1) takes you out of the GUI so you suddenly loose your instructions. 
It was not clear how to get back to the GUI &#8211; how do you? 

With a second computer displaying the instructions, I tried the first command: sudo service lxdm stop
&#8220;LXDM: Unrecognized Service&#8221; Was the message I got back. I did the same in the terminal and got the same message. 
I got the same for GDM and KDM? So what service do I need to stop? 

Since the first command does not stop the service, the second command onward on does not work. 

Although I am not sure what the display problem really is, or how to correct it, I am guessing editing the Xorg.conf as mentioned in the instructions might be the answer by editing the resolution. I am not sure how to go about this. The xorg.conf is not in the locations mentioned in any post I have read so far. 

In addition, the Lubuntu menu choice Preferences > Hardware Drivers does not exist in this version? 
This was also offered as a suggestion in many of the posts I found during researching the issue.  

Of Note: This is also a very very old problem for what I could tell from other very old resources on the net. 

Help is needed and appreciated.

---

### Post by Isamu715 on 2013-01-01
> The keyboard command (ctrl+alt+f1) takes you out of the GUI so you suddenly loose your instructions. 
It was not clear how to get back to the GUI &#8211; how do you? You can get back to the GUI with Ctrl+Alt+F7.

It is possible you don't have a xorg.conf on your machine, in such case you'd need to create it*. *To do that go to single-user mode:
```
sudo init 1
```then:
```
Xorg -configure
```Note that this command will not work if the X server is running. The file is going to be created in */root/xorg.conf.new*. Move it to */etc/X11*:
```
mv /root/xorg/conf.new /etc/X11/xorg.conf
```With that done you can proceed to editing the file with your desired text editor.

In the *Screen* section there's a subsection *Display *where you can edit resolution options, it should look similar to this:
```
Section "Screen"
    Identifier         "Screen0"
    Device             "Card0"
    Monitor            "Monitor0"
    SubSection         "Display"
            Viewport    0 0
            Depth       24
            Modes       "1400x900"
    EndSubsection
EndSection
```Resolution options are located in the *Modes* line, add your resolution and some smaller ones like 640x480 and 800x600 as fallback. Xorg will pick the first correct value when initialized.

---

### Post by VitalBodies on 2013-01-01
Thank you so much for taking the time to answer! 
I will give this a try today. Would be nice if some day making these kinds of changes were built in the GUI. 
I will try to report back on how this worked.

---

### Post by VitalBodies on 2013-01-01
Code:
sudo init 1

...Sent Lubuntu in to a blue screen with the lubuntu logo with five white dots under it. 
Like you might see durning shut down. 
Ctrl alt F1 or F6 would not bring it out of that mode. 
Was not sure what to do other than power down.

---

### Post by Isamu715 on 2013-01-01
If that doesn't work you'd have to start Ubuntu in single user mode instead. What is the output of:
```
xrandr
```on your machine?

---

### Post by VitalBodies on 2013-01-01
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       60.0* 
   800x600        60.0     56.0  
   640x480        60.0

---

### Post by VitalBodies on 2013-01-01
One other thing of interest is that the screen was not ripped in half on the blue logo screen.

---

### Post by VitalBodies on 2013-01-01
So the stop service commands did not work. I get the impression the goal was to stop the X Display MANAGER. Ok, so what is the X Display manager in Lubuntu 12.10?

So far I think it is LightDM.

[http://en.wikipedia.org/wiki/LightDM](http://en.wikipedia.org/wiki/LightDM)

An updated note: the stop command mentioned in the instructions did stop LightDM. 
I added LightDM to the official documentation instruction page. 

I followed the instructions and edited the Xorg.conf and no change in resolution? 
I might try to see my Xorg.conf in the GUI. 
And should it be xorg or Xorg?
Seems like xorg.conf.

---

### Post by Isamu715 on 2013-01-02
> And should it be xorg or Xorg?It's */etc/X11/xorg.conf*.
> In addition, the Lubuntu menu choice Preferences > Hardware Drivers does not exist in this version? It was moved and now exists as a tab in Software Sources.

From your *xrandr* output I can see that Xorg sees only few resolution modes, instead of all supported by the graphics card. It's possible to add a new mode, take a look at [this thread]("http://forums.debian.net/viewtopic.php?f=16&t=78330"), the first post contains detailed instructions on how to do that.

---

### Post by VitalBodies on 2013-01-02
Do you think we should try to add modes (which I tried and failed both using xrandr and xorg) or try to get Ubuntu to properly recognize the card? I tried editing the xorg.conf and saw no changes after adding more modes. By adding VideoRam to xorg.conf DEVICE the computer would no longer boot properly so I had to reload it so I am back to a new install. 

Ideas: 
How to get lubuntu to recognize the card? 
I read modes will not take effect, if, Lubuntu thinks there is not enough VideoRam - not sure if that is true and current or not. 
Is there a way to change resolution temporarily? 

I tried what I saw here: 
[https://wiki.ubuntu.com/X/Config/Resolution#Dynamically_testing_different_resolutions]("https://wiki.ubuntu.com/X/Config/Resolution#Dynamically_testing_different_resolutions")

...But it did not work, I am guessing because of the video ram issue.  
Although I was not really sure what to command as LVDS and VGA1 did not work? 
Do I use "default"?

Does the monitor resolution have to be defined in xorg.conf for the modes to work?

---

### Post by VitalBodies on 2013-01-03
$ lspci | grep VGA
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Rage Mobility M3 AGP 2x (rev 02)

*-display UNCLAIMED
                description: VGA compatible controller
                product: Rage Mobility M3 AGP 2x
                vendor: Advanced Micro Devices [AMD] nee ATI
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 02
                width: 32 bits
                clock: 66MHz
                capabilities: agp agp-2.0 pm vga_controller bus_master cap_list
                configuration: latency=66 mingnt=8
                resources: memory:f8000000-fbffffff ioport:2000(size=256) memory:f0200000-f0203fff memory:f0220000-f023ffff

---

### Post by VitalBodies on 2013-01-03
$ lspci | grep VGA
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Rage Mobility M3 AGP 2x (rev 02)

*-display UNCLAIMED
                description: VGA compatible controller
                product: Rage Mobility M3 AGP 2x
                vendor: Advanced Micro Devices [AMD] nee ATI
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 02
                width: 32 bits
                clock: 66MHz
                capabilities: agp agp-2.0 pm vga_controller bus_master cap_list
                configuration: latency=66 mingnt=8
                resources: memory:f8000000-fbffffff ioport:2000(size=256) memory:f0200000-f0203fff memory:f0220000-f023ffff

**COMMANDS (that worked so far) **
cvt 1400 1050 60
# 1400x1050 59.98 Hz (CVT 1.47M3) hsync: 65.32 kHz; pclk: 121.75 MHz
Modeline "1400x1050_60.00"  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync

XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX

 xrandr --newmode "1400x1050_60.00"  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync

XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX

xrandr --addmode default 1400x1050

XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX

xrandr --addmode default 1400x1050
xrandr: Failed to get size of gamma for output default
xrandr: cannot find mode "1400x1050"
$ xrandr --output default --mode 1400x1050
xrandr: cannot find mode 1400x1050
$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       60.0* 
   800x600        60.0     56.0  
   640x480        60.0  
  1400x1050_60.00 (0x19e)  121.8MHz
        h: width  1400 start 1488 end 1632 total 1864 skew    0 clock   65.3KHz
        v: height 1050 start 1053 end 1057 total 1089           clock   60.0Hz

XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX

Still stuck but possibly getting closer. Hard to navigate a ripped in half screen. 
Note the word UNCLAIMED above.

---

### Post by Isamu715 on 2013-01-03
This error:
```
xrandr: Failed to get size of gamma for output default
```may mean you're using the VESA drivers in which case Lubuntu failed to load a driver appropriate for your graphics card. Did you check for other options in "Additional drivers" section? Legacy ATI drivers are no longer supported by the Xorg version in 12.10, they still are in 12.04 though, it may get troublesome if you need those as even if you manage to get them to work any Xorg update may cause breakage. 

I found [another thread]("http://ubuntuforums.org/showthread.php?t=1594308") dealing with a similar issue, you my want to check it out.

Does the following command give any better options than 1024 x 768?
```
sudo dpkg-reconfigure xserver-xorg
```Did you try booting into low-graphics/failsafe mode or using the *nomodeset* kernel parameter?

---

### Post by VitalBodies on 2013-01-03
Additional drivers is blank with no options to do anything that I could tell. 
I have not tried your other suggestions as yet but would like to.

---

### Post by VitalBodies on 2013-01-06
> **Isamu715 said:**
> 

Does the following command give any better options than 1024 x 768?
```
sudo dpkg-reconfigure xserver-xorg
```Did you try booting into low-graphics/failsafe mode or using the *nomodeset* kernel parameter?
No it did not.

---

### Post by VitalBodies on 2013-02-08
I did try nomodeset, but from what can tell that would only allow me to setup the video card once I had done so. And I would have had to set it up from the command line. I was not sure how to do so. 

Still struggling with this. Found some additional resources though. 

[http://huaxin79662.wordpress.com/2011/05/19/solve-the-ibm-thinkpad-a20p-display-problem-in-lubuntu-11-04/]("http://huaxin79662.wordpress.com/2011/05/19/solve-the-ibm-thinkpad-a20p-display-problem-in-lubuntu-11-04/")

Having done the first suggestions to the point of editing the xorg file I can no longer boot into the GUI or past the blue screen with the Lubuntu logo. That makes me feel like I might need to delete it and try again or continue with additional steps. Not sure how to get back to the command line or the GUI? Next round I will try the keyboard commands you mentioned Ctrl+Alt+F7 and Ctrl+Alt+F1.

[http://ubuntuforums.org/showpost.php?p=10198430&postcount=37]("http://ubuntuforums.org/showpost.php?p=10198430&postcount=37")

---

