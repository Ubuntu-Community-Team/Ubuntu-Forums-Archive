---
title: "Screen resolution issue"
date: 2014-01-28
forum: Hardware
---

### Post by Vinay Balraj on 2014-01-28
Hello there, I have an Nvidia configured graphics card that use on my Ubuntu 13.10. I was able to install the drivers through bash, but the max resolution that I’ve been getting is 1360x768, but my monitor supports a resolution of 1920x1200. I do not see that option anywhere, and trying to change resolutions through n-vidia control panel hasn’t been useful either. My graphics card is connected to the monitor through a DVI to VGA adaptor as my monitor does not have a DVI port.Is that the reason why my resolution is not being detected? How do I work my way around this?

Thanks in advance for any help offered... :popcorn:

---

### Post by TheFu on 2014-01-28
Please run **xrandr** to see the resolutions supported by the card/driver. You'll never set anything beyond those until the driver recognizes a different resolution.

---

### Post by Vinay Balraj on 2014-01-28
Hello Thefu, thanks for replying. But I had already tried xrandr. and the maximum resoltion listed there is 1360x768 too..

these are its logs
-----------------------------------------------------------------------------------------------------------------------
Screen 0: minimum 8 x 8, current 1360 x 768, maximum 16384 x 16384
DVI-I-0 connected primary 1360x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0 +
   1360x768       60.0*    59.8  
   1152x864       60.0  
   800x600        72.2     60.3     56.2  
   680x384        60.0     59.8  
   640x480        59.9  
   512x384        60.0  
   400x300        72.2  
   320x240        60.1  
DVI-I-1 disconnected (normal left inverted right x axis y axis)
DVI-I-2 disconnected (normal left inverted right x axis y axis)
DVI-I-3 disconnected (normal left inverted right x axis y axis)
HDMI-0 disconnected (normal left inverted right x axis y axis)
------------------------------------------------------------------------------------------------------------------

Please tell me what i can do next..

---

### Post by jp734 on 2014-01-28
Can you look in your** /usr/share/X11/xorg.conf.d** folder and see if you have **monitor.conf** and check your **/etc/X11 **for **xorg.conf** as well.

---

### Post by Vinay Balraj on 2014-01-29
Hi jp734, I looked up in both places and both of the files you mentioned above seem to be missing. How can I proceed on this?

Thanks for the help.

---

### Post by jp734 on 2014-01-29
You can try creating a config file for your monitor and screen. I would suggest creating individual config files for monitor and screen and store on /usr/share/X11/xorg.conf.d. If you go back to that folder, you will notice that files are named with numbers first. Example: **10_evdev.conf**. So for your files, just use a number not being used yet. Lets say, 30_monitor.conf and 40_screen.conf. 

Here is an example:

**30_monitor.conf**
Section "Monitor"
	Identifier	"Monitor0"
	Option		"DPMS"
        HorizSync	30-81	  **For this numbers, you will have to do some research for your monitor**
        VertRefresh	56-75  **As well as for this.**
        VendorName      "VendorName"
# More Options...
EndSection

**40_screen.conf**
Section "Screen"
	Identifier     "Screen0"
	Monitor        "Monitor0"
	Option         "DPMS" "true"
	DefaultDepth    24
	SubSection     "Display"
		Depth       24
		Modes      "1400x1050" **Add "1920x1200" or whatever resolution you want here.**
	EndSubSection
EndSection

Good Luck!

---

### Post by Vinay Balraj on 2014-01-29
Hi, jp734, for the file 30_monitor.conf, you have mentioned "for this numbers, i will have to do some research for my monitor", as well as the next line, can you please post a sample file so that I would have an idea of what information I'm looking out for?

I did try this link "[https://wiki.archlinux.org/index.php/xorg](https://wiki.archlinux.org/index.php/xorg)" where the above mentioned lines arent present. So, I'm again clueless on what to do. Sorry for asking to be spoon fed. Though being an advanced user, I'm kind of new to editing and creating the files themselves.

Thanks in advance.

---

### Post by Vinay Balraj on 2014-02-04
No reply??? :/

---

### Post by jp734 on 2014-02-05
An example is exactly what I have posted. That's what it will look like.

---

### Post by jp734 on 2014-02-05
I was looking back at your post. You said the max is 1360x768 but it actually says 16384x16384.

---

### Post by Vinay Balraj on 2014-02-05
Exactly... I'm confused too... But the display wont go above 1360x768... I mean i dont get the options for it. I tried placing those 2 files in the respective folders and restarted to take effect, but still same issue.

And I know for a fact that the resolution goes upto 1920x1200 cuz my previous OS, windows 7 used to go upto it.

Please advice on how to go about it.

---

### Post by Vinay Balraj on 2014-02-05
Exactly... Thats what confuses me too... Well, i know for a fact my displat goes upto 1920x1200, as my previous OS, win 7 used to run at that resolution.. But now, in Ubuntu, 1360x768 is the max i've been able to achieve. I did create those files as you suggested, and also restarted for changes to take effect, but did not work... :\

I wonder what to do... Please advice.

---

### Post by jp734 on 2014-02-05
Try this command on terminal.

xrandr --output DVI-I-0 --mode 1920x1200

---

### Post by Vinay Balraj on 2014-02-06
Thank you for all the help... But I dont know... The latest update seems to have fixed this. I am now able to configure the 1920x1200 through the display settings itself... But still I wonder what was going on all this while... :\

---

