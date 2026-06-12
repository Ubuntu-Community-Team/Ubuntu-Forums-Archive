---
title: "Using widescreen resolutions on 2nd monitor on a 4:3 laptop"
date: 2010-01-18
forum: Hardware
---

### Post by Eddles on 2010-01-18
Hello all,

A month ago, I got a cheap second hand Toshiba Tecra M5 laptop with a Core Duo CPU with a 14" 4:3 screen driven by a nVidia Quadro NVS 110M with 256MB real memory, maybe 3 to 4 years old.  The laptop can only output analogue video.  I've got a HD 720p widescreen projector.  I've set Ubuntu 9.10 up so that the LCD laptop screen is disabled, and the main screen is output via analogue VGA to the projector.  When choosing the resolution from a list provided by the nVidia X Server Settings application, I'm only given options for a 4:3 aspect ratio, and one 16:9 ratio.  The 16:9 option is 1360x768 which doesn't fit well into 1280x720 - the surrounding parts are cropped off.

How do I achieve a widescreen resolution, preferably in 720p resolution (or 1080p if possible)?  Windows only gives options in 4:3 ratio all the way up to 2048 x 1536, and no widescreen option, which convinces me that the video card should be able to handle this...?

Thanks very much for your time in advance!

Here's the output from lshw:

piers@voyager:~$ sudo lshw -class display
[sudo] password for piers: 
  *-display               
       description: VGA compatible controller
       product: G72M [Quadro NVS 110M]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:fd000000-fdffffff memory:e0000000-efffffff(prefetchable) memory:fc000000-fcffffff
piers@voyager:~$

---

### Post by Fire_Chief on 2010-01-18
Not to be obvious, but did you try the Display control panel in the System -> Preferences menu? It detects and uses my external wirescreen LCD monitor flawlessly.

---

### Post by Eddles on 2010-01-18
This is exactly where I found the list of screen resolutions.

---

### Post by Fire_Chief on 2010-01-18
Ok, so let's just cover a few basics...

Are you using the restricted hardware driver for the Nvidia card? (System -> Administration -> Hardware drivers)
Are you getting proper EDID information from the projector? This is used to determine the capabilities of the projector (or other monitor device) and helps the OS know what resolutions are acceptable. You can find out by installing the read-edid package and then pulling the information.```
sudo apt-get install read-edid
sudo get-edid | sudo parse-edid
```

Have you been able to get the desired resolution from another computer or from another OS on the Toshiba?
Are you trying to use both the Nvidia X Server Settings panel and the Gnome Display Preferences panel together? This usually does not work well. I would suggest sticking with just one or the other.

Cheers!

---

### Post by Eddles on 2010-01-18
> **Fire_Chief said:**
> Ok, so let's just cover a few basics...

Are you using the restricted hardware driver for the Nvidia card? (System -> Administration -> Hardware drivers)

Don't know what exactly you mean by "restricted" - but I'm using the nVidia's proprietary driver, as originally installed by ubuntu.

> Are you getting proper EDID information from the projector? This is used to determine the capabilities of the projector (or other monitor device) and helps the OS know what resolutions are acceptable.

Almost certainly not - the projector isn't really a monitor.  I know already the projector doesn't pass the required data to the device (pretty obvious, as Windows and Ubuntu completely fails to use a decent resolution for the projector).  read-edid confirms this:

```
piers@voyager:~$ sudo get-edid | sudo parse-edid
parse-edid: parse-edid version 2.0.0
get-edid: get-edid version 2.0.0

	Performing real mode VBE call
	Interrupt 0x10 ax=0x4f00 bx=0x0 cx=0x0
	Function supported
	Call successful

	VBE version 300
	VBE string at 0x2110 "NVIDIA"

VBE/DDC service about to be called
	Report DDC capabilities

	Performing real mode VBE call
	Interrupt 0x10 ax=0x4f15 bx=0x0 cx=0x0
	Function supported
	Call successful

	Monitor and video card combination does not support DDC1 transfers
	Monitor and video card combination does not support DDC2 transfers
	0 seconds per 128 byte EDID block transfer
	Screen is not blanked during DDC transfer

Reading next EDID block

VBE/DDC service about to be called
	Read EDID

	Performing real mode VBE call
	Interrupt 0x10 ax=0x4f15 bx=0x1 cx=0x0
	Function supported
	Call failed

The EDID data should not be trusted as the VBE call failed
Error: output block unchanged
parse-edid: IO error reading EDID
piers@voyager:~$
```

> Have you been able to get the desired resolution from another computer or from another OS on the Toshiba?

As I mentioned earlier, Windows only give 4:3 resolutions up to 2048 x 1536.

I used to have a Mac Mini connected to the projector via DVI/HDMI and the Mac detected and displayed 1080p from first boot-up.  I'm assuming the projector is able to pass the required data via DVI/HDMI but not via analogue VGA.

> Are you trying to use both the Nvidia X Server Settings panel and the Gnome Display Preferences panel together? This usually does not work well. I would suggest sticking with just one or the other.

No, just the nVidia X Server Settings panel alone.  The Gnome Display Preferences Panel says it won't work with the driver and suggests using the nVidia X Server Settings Panel, so I've left the GDPP alone.

When I used Debian several years ago, I remember manually entering the monitor configuration information in the x11.conf file (or whatever it used to be called) along with the supported resolutions.  Is that still possible nowadays?

Thanks very much for your time, I appreciate it!

---

### Post by Fire_Chief on 2010-01-18
So Karmic is really really trying to do away with the xorg.conf file but occasionally it is still needed. This page has full information on configuring your displays with xrandr and using the xorg.conf file to make the changes permanent.

[https://wiki.ubuntu.com/X/Config/Resolution]("https://wiki.ubuntu.com/X/Config/Resolution")

Cheers!

EDIT:  If that doesn't look appealing or does not work, try this instead to keep the NVidia driver in use and just implement the xorg.conf changes...[http://ubuntuforums.org/showpost.php?p=8547377&postcount=13]("http://ubuntuforums.org/showpost.php?p=8547377&postcount=13")

---

### Post by Eddles on 2010-01-19
Thanks for your advice!

My computer isn't playing ball, however:

```
piers@voyager:~$ xrandr
Screen 0: minimum 320 x 240, current 2048 x 768, maximum 2048 x 768
default connected 2048x768+0+0 0mm x 0mm
   1024x768       50.0     64.0  
   840x525        51.0  
   800x600        52.0  
   800x512        53.0  
   720x450        54.0  
   680x384        55.0     56.0  
   640x512        57.0  
   640x480        58.0     59.0  
   576x432        60.0  
   512x384        61.0  
   400x300        62.0  
   320x240        63.0  
   2048x768       64.0* 
piers@voyager:~$ cvt 1280 720
# 1280x720 59.86 Hz (CVT 0.92M9) hsync: 44.77 kHz; pclk: 74.50 MHz
Modeline "1280x720_60.00"   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync
piers@voyager:~$ xrandr --newmode "1280x720_60.00"   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync
piers@voyager:~$ xrandr --addmode default 1280x720_60.00
piers@voyager:~$ xrandr
Screen 0: minimum 320 x 240, current 2048 x 768, maximum 2048 x 768
default connected 2048x768+0+0 0mm x 0mm
   1024x768       50.0     64.0  
   840x525        51.0  
   800x600        52.0  
   800x512        53.0  
   720x450        54.0  
   680x384        55.0     56.0  
   640x512        57.0  
   640x480        58.0     59.0  
   576x432        60.0  
   512x384        61.0  
   400x300        62.0  
   320x240        63.0  
   2048x768       64.0* 
   1280x720_60.00   59.9  
piers@voyager:~$ xrandr --output default --mode 1280x720_60.00
xrandr: Configure crtc 0 failed
piers@voyager:~$ 
```

Any ideas now?

---

### Post by Fire_Chief on 2010-01-19
xrandr says the current resolution is 2048x768???

It seems like the system is using both screens (built-in + projector) where each screen is set for 1024x768 and they are joined together. Do you have twinview or xinerama enabled in the nvidia-settings control panel?

Do you see both screens in the nvidia-settings tool?

This blog post is slightly off topic but does talk about connecting external displays to his 9.10 netbook with Nvidia.
[http://www.linux.com/news/hardware/peripherals/237262-external-linux-monitor-adventures]("http://www.linux.com/news/hardware/peripherals/237262-external-linux-monitor-adventures")

---

