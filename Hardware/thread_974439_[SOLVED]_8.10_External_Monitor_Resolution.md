---
title: "[SOLVED] 8.10 External Monitor Resolution"
date: 2008-11-07
forum: Hardware
---

### Post by abrichr on 2008-11-07
I originally posted at [http://ubuntuforums.org/showthread.php?t=969014&page=3](http://ubuntuforums.org/showthread.php?t=969014&page=3), but since that thread was marked as solved, and none of the solutions worked, I decided to repost.

I have an nVidia GeForce Go 7600 on a Compal HEL80 laptop. My external monitor is a Soyo Topaz S, with a native resolution of 1920x1200. The nv driver upon default install of Ubuntu 8.10 detects this without a problem.

I installed the nvidia-glx-177 driver through the Restricted Driver Manager. Upon reboot, my laptop's display was displaying correctly, but Nvidia-Xsettings shows a max resolution of 1360x768, which my monitor is unable to display correctly. I ran:

sudo dpkg-reconfigure -phigh xserver-xorg
sudo nvidia-xconfig

And received an error about the driver not being specified in the Device section. Upon restarting X, there was no change in Nvidia-Xsettings. I set it to 1024x768, which is displaying correctly.

I installed read-edid, and ran:

sudo get-edid > /tmp/get-edid.dat

I have attached the contents of get-edid.dat, as well as the output of lspci -vvnn, and /var/log/Xorg.0.log, at a bug report: [https://bugs.launchpad.net/ubuntu/+bug/223005](https://bugs.launchpad.net/ubuntu/+bug/223005). I didn't create this bug, but it seemed appropriate to post there.

Following the guide at [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution), I performed the following steps:

```

$ gtf 1920 1200 60

# 1920x1200 @ 60.00 Hz (GTF) hsync: 74.52 kHz; pclk: 193.16 MHz
Modeline "1920x1200_60.00" 193.16 1920 2048 2256 2592 1200 1201 1204 1242 -HSync +Vsync

$ xrandr --newmode "1920x1200_60.00" 193.16 1920 2048 2256 2592 1200 1201 1204 1242 -HSync +Vsync

$ xrandr --addmode 0x1ac 1920x1200_60.00

$ xrandr
Screen 0: minimum 320 x 240, current 1024 x 768, maximum 1920 x 1200
default connected 1024x768+0+0 0mm x 0mm
1024x768 50.0*
800x600 51.0 52.0 53.0
680x384 54.0 55.0
640x480 56.0
576x432 57.0
512x384 58.0
400x300 59.0 60.0 61.0
320x240 62.0
1920x1200_60.00 60.0

$ xrandr --output 0x1ac --mode 1920x1200_60.00
xrandr: Configure crtc 0 failed

```

(I should remark that I got the 0x1ac identifer from xrandr --verbose)

The resolution is now visible under System -> Preferences -> Screen Resolution, but selecting it and clicking "Apply" does nothing.

The last xrandr command only reported the error the first time; repeating it does nothing (no output, no change in display).

---

### Post by abrichr on 2008-11-08
Bump.

I haven't received any replies to either of my posts, or the bug report.  Any suggestions would be really appreciated!

---

### Post by ppatalano on 2008-11-08
I'm confused how to find out what to put as output.

---

### Post by occhiso on 2008-11-08
BUMP!

I have this exact same problem. Im trying to get my laptop producing 1920x1200 for my 24" LCD, which worked fine in Hardy, using displayconfig-gtk.

I was reading this document:
    [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)
and followed the same steps as you did and got the exact same result.

Here is my attempt:
```
$ xrandr
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 1280 x 800
default connected 1280x800+0+0 0mm x 0mm
   1280x800       60.0* 
   1280x768       60.0  
   1280x720       60.0  
   1024x768       85.0     75.0     72.0     70.0     60.0  
   800x600        85.0     75.0     72.0     70.0     60.0     56.0  
   720x480        60.0  
   640x480        85.0     75.0     72.0     60.0  
   640x400        60.0  
   512x384        60.0  
   400x300        60.0  
   320x240        60.0  
   320x200        60.0  
$ gtf 1920 1200 60

  # 1920x1200 @ 60.00 Hz (GTF) hsync: 74.52 kHz; pclk: 193.16 MHz
  Modeline "1920x1200_60.00"  193.16  1920 2048 2256 2592  1200 1201 1204 1242  -HSync +Vsync

$ xrandr --newmode 1920x1200  193.16  1920 2048 2256 2592  1200 1201 1204 1242  -HSync +Vsync
$ xrandr --addmode default 1920x1200
$ xrandr
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 1920 x 1200
default connected 1280x800+0+0 0mm x 0mm
   1280x800       60.0* 
   1280x768       60.0  
   1280x720       60.0  
   1024x768       85.0     75.0     72.0     70.0     60.0  
   800x600        85.0     75.0     72.0     70.0     60.0     56.0  
   720x480        60.0  
   640x480        85.0     75.0     72.0     60.0  
   640x400        60.0  
   512x384        60.0  
   400x300        60.0  
   320x240        60.0  
   320x200        60.0  
   1920x1200      60.0  
$ xrandr --output default --mode 1920x1200
xrandr: Configure crtc 0 failed
$ 

```


ppatalano, the name of the output is specified in the output of xrandr.
For example, in abrichr's example, the name of the output is "default"
> Screen 0: minimum 320 x 240, current 1024 x 768, maximum 1920 x 1200
default connected 1024x768+0+0 0mm x 0mm
1024x768 50.0
...

---

### Post by ppatalano on 2008-11-08
So I added the new resolution, but when I try to set it, it just does nothing. And when I reboot, the new resolution disappears as a choice.

---

### Post by ppatalano on 2008-11-09
This is what I get when I try to change the mode:

> 
peter@peter-desktop:~$ xrandr --output default --mode 2960x1050_60.00
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  158 (RANDR)
  Minor opcode of failed request:  7 ()
  Serial number of failed request:  15
  Current serial number in output stream:  16


Any ideas...

---

### Post by abrichr on 2008-11-09
I think the solution is to add the modeline into /etc/X11/xorg.conf.  I've been busy all weekend, and I don't know that I'll have time to try this at all this week.  But when I do, I'll be sure to post back with my results.

In the meantime, some input from someone who knows what they're doing would be much appreciated...

---

### Post by chevkoch on 2008-11-11
same problem here. has nothing to do with a monitor being external or not.

please help!

---

### Post by abrichr on 2008-11-12
It appears that this issue has been solved in the glx-96 driver, which is currently in the "proposed" repo.  Right now I'm running Compiz, and I have the full 1920x1200 resolution on my external display.  Here's what I did:

[LIST=1]
[*]System -> Administration -> Synaptic Package Manager
[*]Settings -> Repositories
[*]Under "Updates", check "Pre-released updates (intrepid-proposed)"
[*]Click "Close", then "Reload"
[*]Search for "nvidia",  Right-click on "nvidia-glx-96", and select "Mark for installation"
[*]Accept all the dependencies, install them, and wait for it to finish
[*]Run the following command:

```
sudo nvidia-xconfig --add-argb-glx-visuals -d 24
```

[*]Hit ctrl+alt+backspace to restart X (if this doesn't work, try restarting your system)
[/LIST]

My resolution was detected automatically after that.  Now, proceed as usual to enable compiz, by going to System -> Preferences -> Appearance -> Visual Effects, and selecting "Extra".

Initially, I'd ran nvidia-xonfig without the --add-argb-glx-visuals option, and was getting windowless borders, so be sure to include it.

Hope someone can find this useful :)

*EDIT*: you may want to disable the proposed repo after you install the glx-96 driver.  If so, go back to System -> Administration -> Synaptic Package Manager, Settings -> Repositories, Updaets, and uncheck "Pre-released updates (intrepid-proposed)".

---

### Post by HerrKaputt on 2009-10-20
What about those of us that don't have Nvidia drivers? My Ubuntu is a guest under VMware, so this solution doesn't work for me...

---

### Post by jcstockdale on 2010-03-14
Hi,
I have tried all the solutions offered here and still I'm not getting anywhere. I'm running Ubuntu 9.10. My monitor is an ADI Microscan a715 and I have onboard graphics on an Asus A7N8X Deluxe motherboard. No matter what I do, the Nvidia control panel only gives me the option for 640x480 or 800x600. I have tried all the command line stuff using xrandr and that has not been successful either.
What else can I try?

Thanks.

---

