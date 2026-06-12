---
title: "Monitor 1920x1080 apparently not supported by 14.04 LTS"
date: 2014-10-17
forum: Hardware
---

### Post by FredVanH on 2014-10-17
Hi.  I used to have a HP w2207 monitor (optimum resolution 1680x1050) which worked fine with Ubuntu 14.04 LTS (Dell Optiplex GX520).
2 weeks ago I replaced it with a Samsung S24D590L (optimum resolution 1920 x 1080).
That worked fine, too, at first;  until a day or so ago when the icons got really big and not much info fit on the screen anymore.
(Maybe I hit something with my elbow or something?).
On the Ubuntu Systems Settings/ Screen Display procedures, there are only 2 settings available:
1024 x 768 (4:3) (default) and 800 x 600 (4:3).  Naturally, I left the setting at the former.
I then tried a procedure which I had gotten off the forum and which had worked with the previous monitor:

In Terminal, I typed
 cvt 1920 1080
The response said 
# 1920x1080 59.96 Hz (CVT 2.07M9) hsync: 67.16 kHz; pclk: 173.00 MHz
Modeline "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
I typed
xrandr --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
after which I got the command prompt; and then typed
xrandr --addmode VGA1 1920x1080_60.00
after which I got the command prompt and the message "Unknown Display"

I get the feeling that Ubuntu has a list of display sizes and mine is not on the list.
I'm not a graphics kind of guy.
Any ideas how I may get this display to become compatible?
Thanks for any help, Fred.

---

### Post by papibe on 2014-10-17
Hi FredVanH.

Could you open a terminal run these commands, and post back the results (you can copy/paste the text)?
```
lspci -nnk | grep -iA2 vga

lsmod | grep -E 'nvidia|nouveau|i915|radeon|fglrx'

ls /etc/X11/xorg.conf

xrandr -q

xrandr -q --q1
```
Regards.

---

### Post by FredVanH on 2014-10-18
Hi, papibe.  Thanks for being interested.  Your instructions and their responses are below.  Sorry for the long Command Prompt name you have to wade thru!:

algonquin5@algonquin5-OptiPlex-GX520:~$ lspci -nnk | grep -iA2 vga
00:02.0 VGA compatible controller [0300]: Intel Corporation 82945G/GZ Integrated Graphics Controller [8086:2772] (rev 02)
    Subsystem: Dell Device [1028:01ad]
    Kernel driver in use: i915
algonquin5@algonquin5-OptiPlex-GX520:~$ lsmod | grep -E 'nvidia|nouveau|i915|radeon|fglrx'
i915                  709755  3 
video                  18903  1 i915
drm_kms_helper         48868  1 i915
drm                   244037  4 i915,drm_kms_helper
i2c_algo_bit           13197  1 i915
algonquin5@algonquin5-OptiPlex-GX520:~$ ls /etc/X11/xorg.conf
ls: cannot access /etc/X11/xorg.conf: No such file or directory
algonquin5@algonquin5-OptiPlex-GX520:~$ xrandr -q
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 32767 x 32767
VGA1 connected primary 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  
VIRTUAL1 disconnected (normal left inverted right x axis y axis)
algonquin5@algonquin5-OptiPlex-GX520:~$ xrandr -q --q1
 SZ:    Pixels          Physical       Refresh
*0   1024 x 768    ( 271mm x 203mm )  *60  
 1    800 x 600    ( 271mm x 203mm )   60   56  
 2    848 x 480    ( 271mm x 203mm )   60  
 3    640 x 480    ( 271mm x 203mm )   60  
Current rotation - normal
Current reflection - none
Rotations possible - normal left inverted right 
Reflections possible - X Axis Y Axis

---

### Post by FredVanH on 2014-10-18
Hi again.  In the interest of full disclosure (I hope not too much!), this new Samsung S24D590L (Optimum 1920 x 1080) monitor, along with a keyboard, mouse and audio connection, is connected to 3 computers on demand via an IOGear GCX634U KS Switch.
Connection 1:  Windows8 ZT Reliant 865Mi computer.
Connection 2:  Windows7 Dell Optiplex GX520 computer No. 1
Connection 3:  Unused
Connection 4:  Ubuntu 14.04 LTS Dell Optiplex GX520 computer No. 2
                      (Dual boot with an unused Windows 7 installation).
The monitor works fine with the Windows installations on Connections 1 & 2 - the problem is with Ubuntu on connection 4.
Connection 4 worked fine, too, until 2 days ago.

---

### Post by grahammechanical on 2014-10-18
I am getting 1920x1080 from my Sharp TV that I am using as a monitor. But I could not get that resolution using the VGA cable only when I used the HDMI connection. This is what I get when I run 

```
xrandr -q
```

> Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 8192 x 8192
DVI-I-1 disconnected (normal left inverted right x axis y axis)
VGA-1 disconnected (normal left inverted right x axis y axis)
HDMI-1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 16mm x 9mm
   1920x1080i     60.1*+   50.0     60.0  
   1920x1080      24.0     24.0  
   1280x720       60.0     50.0     59.9  
   1440x576i      50.1  
   1024x768       75.1     70.1     60.0  
   1440x480i      60.1     60.1     60.1  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   720x576        50.0  
   720x480        60.0     59.9  
   640x480        75.0     72.8     66.7     60.0     59.9  


What do you get?

> [COLOR=#000000]Screen 0: minimum 320 x 200, current 1024 x 768, maximum 32767 x 32767[/COLOR]
[COLOR=#000000]VGA1 connected primary 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm[/COLOR]

See the difference that not using a VGA connection will make?

Regards.

---

### Post by FredVanH on 2014-10-18
Thanks grahammechanical, for your suggestions.
The response I got to "xrandr -q" is listed below and was just what _you_ got for a VGA connection, plus a few lines.
My new Samsung S24D590L monitor has HDMI connections but my old, old Dell Optiplex GX520 computer does not.
I see that a VGA (computer) to HDMI (monitor) signal converter is available for about $30;
so I might go that route (thanks!) if something else doesn't materialize here when papibe returns.
As an aside, I still can't figure out why this monitor _did_ work for 2 weeks.
Thanks,  Fred

Screen 0: minimum 320 x 200, current 1024 x 768, maximum 32767 x 32767
VGA1 connected primary 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  
VIRTUAL1 disconnected (normal left inverted right x axis y axis)

---

### Post by papibe on 2014-10-22
A few thoughts:

I agree with grahammechanical's assessment about the VGA input.

Before buying a cable, I'd try this: some monitor and TV's manufacture publish their supported timings either in their manuals, online FAQ, or support forums. If you can get the proper timings for higher resolutions, you may be able to use xrandr to set them directly. Note that the resolutions and timings input are dependent so they usually are different from VGA and HDMI.

If you have a Windows computer that is able to get a higher resolution over VGA, you may obtain the timings from Windows and then use them on Linux.

If the Dell has a DVI output, I'd would buy a DVI->HDMI cable instead of a VGA->HDMI.

It might be useful information in the Xorg log. Could you post the content of this file?
```
/var/log/Xorg.0.log
```
Please paste it here: [pastebin.ubuntu.com]("http://pastebin.ubuntu.com/"), and then post back the link.

Regards.

---

### Post by FredVanH on 2014-10-22
Thanks, Papibe.  Here's what I got:
algonquin5@algonquin5-OptiPlex-GX520:~$ /var/log/Xorg.0.log
bash: /var/log/Xorg.0.log: Permission denied
I'm sure that's not satisfactory;  but i don't know what to do to overcome it.

I also posted that result to pastebin # 8631377, for what it was worth.

While I don't at this time know how to obtain timings (or what contexts to look for) or how to configure the xrandr command, I'll try to figure them out and do them.  N.B.  My Dell computer does not have a DVI connector.
Thanks,
Fred

---

### Post by tgalati4 on 2014-10-22
Some KVM's have limitations.  My IO-Gear is limited to 1600x1200 with VGA, even though you can push higher resolution through VGA.  You need to check the specifications of your KVM switch.  It's possible that it worked for a while at the higher resolution until something in the KVM got hot.

---

### Post by papibe on 2014-10-22
'/var/log/Xorg.0.log' is a text file.

Try this: open a terminal and run this:
```
gedit /var/log/Xorg.0.log
```
An new window will open, select all the text (Ctrl+a), copy it (Ctrl+c), and then in the browser open this page [http://paste.ubuntu.com/](http://paste.ubuntu.com/)

There paste the text on the box 'content', and press the button called 'Paste!' The browser will post the page and a new page will appear. Copy the new url on the browser and then paste it on a new post.

Regards.

---

### Post by FredVanH on 2014-10-22
OK, papibe - the result is posted at [http://paste.ubuntu.com/8632044/](http://paste.ubuntu.com/8632044/)
Thanks,
Fred

---

### Post by papibe on 2014-10-27
Thanks.

Unfortunately, there's no more useful details there.

At this point, I would go back to the points on post #7 about researching the timings and resolutions of the monitor's VGA output.

Regards.

---

### Post by FredVanH on 2014-10-27
Many thanks Papibe, for your suggestions.
While I have no idea where to begin with implementing them,
I'll certainly google the heck out of them and see if I understand
enough of the answers to get the timings
 and then do something with them.
If that doesn't pan out,
I may see if I can find someone who has actually
hooked up a 1920 x 1080 monitor to Ubuntu 14.04. LTS; 
and see if I can get him or her to step me through it.

Again, I'm very grateful for your responses.
Thanks,
Fred

---

