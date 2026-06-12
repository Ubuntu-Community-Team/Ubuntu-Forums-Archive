---
title: "X11/Nvidia fails to use correct EDID on Onkyo receiver reconnect/plugin"
date: 2015-07-21
forum: Hardware
---

### Post by threeleggedcat-forum on 2015-07-21
Hi,


Setup is Ubuntu 14.04 with latest updates installed, Nvidia 610 graphic card with HDMI connected to an Onkyo PR-SC5507 receiver.  The receiver is connected via HDMI to a Panasonic plasma TV.  Main use is Kodi.


/proc/version is 'Linux version 3.13.0-57-generic (buildd@brownie) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #95-Ubuntu SMP Fri Jun 19 09:28:15 UTC 2015'.  Current Nvidia driver, installed from 352.21-0ubuntu0~xedgers14.04.1, is v 352.  Also tried drivers 331 'on up' to 352.


System has been behaving itself for months until after an ubuntu upgrade which, I believe, included a new kernel.  System boots fine and the display is excellently set to 1920x1080 60Hz progressive (mode "1920x1080_60").  Problem comes in when the receiver (and TV) are turned OFF and then back ON.  The display is now interlaced resulting in two pictures offset vertically by about a pixel.  It looks fuzzy.  It seems to be either an X11 or Nvidia driver problem, hence the use of X11/Nvidia.


I can issue command:
    xrandr --output HDMI-0 --mode 1920x1080 --rate 60.0 
and the TV picture is back to its progressive self.


I have tried changing the xorg.conf (in /etc/X11) file to force mode "1920x1080_60", which is the 60Hz progressive mode obtained from the EDID by:
    
1) Adding 'Option "PreferredMode" "1920x1080_60"' to the "Monitor" section


2) Using nvidia-settings to output the EDID in binary and including a 'Option         "CustomEDID" "GPU-0:DFP-1:/etc/X11/onkyoHdmiEdid.bin"'  in the "Screen" section


3) Added a Modeline as 'Modeline "1920x1080w60.00"  148.50  1920 2008  2052 2200  1080 1084  1089 1125  +HSync +Vsync' (based on Xorg.0.log) to the "Monitor" section along with "ModeValidation" options to not use the EDID or not use EDID modes, etc.


Number 3 I could not get working, Nvidia or X11 just ignored the modeline and choose a muddy producing one instead.  I gave up on this one.  At least it was consistently bad across the OFF/ON boundary.


Numbers 1 and 2 produced exactly the same results.  The Xorg.0.log is from number 2.  When the receiver turns OFF, udef triggers and X11/Nvidia writes to the log file "NVIDIA(0): ACPI: received event: jack/lineout LINEOUT plug".  Turning the receiver ON produces the 8,995 lines below this marker.  X11/Nvidia then tries to read the EDID file (ignoring the binary file) which has the pixel clock halved.  It does this a whopping 11 times.


This wouldn't be too bad if it choose the right EDID. After the ON event, it reads the correct EDID five times, the sixth is "wrong" and that's the one (perhaps) it uses to set the mode (search for "Setting mode").


My fix will be to write a udev rule.  But something is just not right with the Linux box handshakes over HDMI with the receiver.  Probably something stupid I've done.


Any suggestions (other than a udev rule?) for fixing this?


thanks!


mark

---

### Post by papibe on 2015-07-21
Hi threeleggedcat-forum. Welcome to the forum ):P

I would use the TV EDID info instead of the receiver. That way the PC would transmit the proper signal for the receiver to route to the TV.

To do that, I would connect the Ubuntu machine to the TV using an HDMI cable, test everything looks OK, and create a personalized xorg.conf:
```
sudo nvidia-xconfig
```
Then, I would obtain the EDID info of the TV, and I would add it to the file (CustomEDID option). Then I would restart the machine to test if every thing works OK.

Then I would put the receiver in the middle. It may be necessary to add the option IgnoreEDID so that the Nvidia driver won't even probe the receiver.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by threeleggedcat-forum on 2015-07-22
Hey papibe,

I did somewhat as you suggested and it turns out, other than substituting "Panasonic ..." for "Onkyo..." the two EDIDs produced the same mode pool.  

I did solve this problem though.  Turns out scenario number 2 was not working as proceeding the CustomEDID device:fileName with GPU-0: was not correct.  Taking that out seems to be working in that X11 only sets the mode once (on X11 startup) and not when the receiver is turned back on (still generates a bunch of stuff, but doesn't seem to use it).  Even with a verbosity level 7, there was no indication that the custom EDID file was being read or being applied to the correct device.  A "No screen device found for GPU-0:DFP-1" would have clued me in.

A Nvidia developer (same thread on their forum) suggested that the GUI (Gnome in my case) was the possible culprit by capturing (udev?) events and issuing a xrandr call.  Don't know how to figure that out.  Perhaps a udev utility can report all the subscribers to an event.

thanks again,

mark

---

### Post by papibe on 2015-07-23
I'm glad you solve your problem :D

---

