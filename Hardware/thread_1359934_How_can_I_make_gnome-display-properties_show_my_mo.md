---
title: "How can I make gnome-display-properties show my monitor's resolutions?"
date: 2009-12-20
forum: Hardware
---

### Post by ajay_g_m on 2009-12-20
I recently installed Ubuntu 9.10 on my desktop. The maximum resolution shown by gnome-display-properties is 1024x768. The same hardware was allowing higher resolutions on Ubuntu 8.04.

The details of my monitor are as follows:
Company: SAMSUNG
Model: Samtron 75E

Please note that I'm a novice as far as understanding Linux internals is concerned, so request you to please provide a solution with a little more details.

Thank You.

---

### Post by gordintoronto on 2009-12-20
I found this when I Googled your monitor model.  The command would be entered into a Terminal session; you should be able to copy/paste the command.

Using the same LiveCD (20060410), I tried "sudo dpkg-reconfigure xserver-xorg", answering the configuration questions, and then (reboot)... and all works perfectly. After that, I can use many different resolutions in the LiveCD: 1024x768, 1280x1024, 800x600, 640x480, 1280x960, 1280x800, 1152x864, 1280x768, 1152x768 and 832x624, at several refresh rates.

The entire discussion is at:
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/31830](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/31830)

---

### Post by ajay_g_m on 2009-12-20
When I run the above command I can not see any screen or feedback on the console where I can answer any questions. It just returns back to the prompt.
[FONT="System"]
[I][COLOR="Blue"]user@desktop:~$ sudo dpkg-reconfigure xserver-xorg 
user@desktop:~$[/COLOR] [/I]
[/FONT]
How can I get to run this command?

---

### Post by ajay_g_m on 2009-12-20
I tried to do some search on the net and found a bug on the following URL...
[https://bugs.edge.launchpad.net/ubuntu/+source/xorg-server/+bug/194760](https://bugs.edge.launchpad.net/ubuntu/+source/xorg-server/+bug/194760)

Not sure it is related to my issue, but have added my details to that bug (#37). If anyone can analyse the details I have posted there please look into it and help me.

Thanks.

---

### Post by ajay_g_m on 2009-12-20
> **ajay_g_m said:**
> When I run the above command I can not see any screen or feedback on the console where I can answer any questions. It just returns back to the prompt.
[FONT="System"]
[I][COLOR="Blue"]user@desktop:~$ sudo dpkg-reconfigure xserver-xorg 
user@desktop:~$[/COLOR] [/I]
[/FONT]
How can I get to run this command?

I found on the net that the X reconfiguration option has been removed from the latest versions and it has been replaced by an auto configuration step. There is a lot of backlash on the forums about this way of handling things.

So I guess the only option available right now for me is to figure out how I can configure the xorg.conf file for my machine. 
I also found out that there are various modelines available for various graphic cards and monitors.
Have to study that a bit to understand what are the right values for my hardware.

---

### Post by edubidu on 2010-01-03
Hi, I have a very specific question about this:
I have 2 profiles on my computer and unfortunately changed a too high screen resolution in one profile with the gnome-display-property (window). 

I get a non-input signal (for this profile).

All other profiles are yet ok. 
So in which specific file does the gnome-display-property write the new resolution for this one profile?:confused:

I'd like to change it back for this only  one userprofile into the right screen relolution.

Many thanks for help!

---

### Post by ajay_g_m on 2010-01-21
Need to study stuff mentioned at the following URL...
[https://wiki.ubuntu.com/X/Config/Resolution]("https://wiki.ubuntu.com/X/Config/Resolution")

---

### Post by ajay_g_m on 2010-01-21
The following are my findings...
The Max. Resolution for my monitor is 1280 x 1024.

This resolution was not visible in the output of the command "xrandr".
The following was the output...
```
$ xrandr

Screen 0: minimum 320 x 200, current 1024 x 768, maximum 2048 x 2048
VGA1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 306mm x 230mm
   1024x768       85.0     75.1     70.1*    60.0  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     66.7     60.0  
   720x400        87.8     70.1  
```

The above indicates that the system has not detected the max resolution (1280x1024), the current resolution is 1024x768 with 70Hz (indicated by * ) and the output name is "VGA1" (this is going to be used in some of the commands listed below so just remember it for now).

Now you are supposed to add the undetected resolution. To do this you need to add something called as modeline using the "xrandr" command.
To get the modeline you need to run the command "cvt" as shown below...
```

$ cvt 1280 1024

# 1280x1024 59.89 Hz (CVT 1.31M4) hsync: 63.67 kHz; pclk: 109.00 MHz
Modeline "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
```

The last part of the last line after "Modeline" should be copied and supplied to the "xrandr --newmode" command as shown below...

```
$ xrandr --newmode "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
```

The name of the new modeline is "1280x1024_60.00" and needs to be passed to the "xrandr --addmode" command as shown below...

```
$ xrandr --addmode VGA1 1280x1024_60.00
```


Now if you run the "xrandr" command again you will see that the new resolution is available.
Now you can goto the GUI tool to change the display resolution (System->Preferences->Display).


The only catch with the above approach is that this does not get permanently recorded i.e. the effect of these commands is lost once you logout of your session.

I will try to figure out how we can solve this problem permanently. 
Till then this is the only solution for me.

---

### Post by edubidu on 2010-04-22
Thank you!!
I had a rdiff-backup and recovered my entire /home directory. That worked. But for the next time and for other users you reply is great!

---

