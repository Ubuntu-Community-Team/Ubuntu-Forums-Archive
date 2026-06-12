---
title: "Mga 200 monitor unknown"
date: 2010-11-25
forum: Hardware
---

### Post by frrebora on 2010-11-25
I have a Dell Poweredge T110 with Matrox G200 ew integrated chip. In past i had a samsung crt well recognized and setted to 1024x768x75. unfortunately the monitor has crashed and now i have an Lg w1946 which maximum resolution is 1360x768 but which supports also 1024x768 both 75 and 60 hz. Now in display settings i found Monitor unknown and maximum res. is 800x600x60hz. for me is already good 1024x768.
xrandr is
Screen 0: minimum 640 x 480, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        60.0*    56.0  
   640x480        60.0  
in etc/gdm/init under 
PATH="/usr/bin:$PATH"
OLD_IFS=$IFS
i have added
xrandr --newmode "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
xrandr --addmode default 1024×768_60.00
xrandr --output default --mode 1024x768
i have restarted but nothing has changed.
I have installed matroxset, nouveau and mga-vid-source without changes.
Have you any suggestion?

---

### Post by dandnsmith on 2010-11-25
I'd start by an effective removal (rename it) of any xorg.conf file you've created (not sure if that is the correct name these days - I've a feeling that I discovered a change in the later models of Ubuntu) - and then boot up the system and let it sort things out.

By default, Ubuntu (nowadays) doesn't create a config file for the display setup, but configures it on the fly, getting the needed info from the graphics card and the monitor itself.
After that you can start playing...

I haven't needed to worry about changes of monitor or graphics chipset since it started using this system (unlike certain other OS)

HTH

---

### Post by frrebora on 2010-11-25
There is already nothing as xorg.conf both in etc/X11 and in lib/X11; In origin there weren't; i've created with correct modes and modelines, but nothing has changed (this was yesterday)
then i have renamed in xorg.back and this morning i have already deleted but nothing has changed. Oldest monitors are recognized; seems that mga driver doesn't recognize wide monitors. When i look at  logs i see lines that means that the interrogation in resolutions higher that 800x600x60hz are not supported by monitor (which is not real). after the inserting in gdm init xrandr lines, if i type in terminal xrandr 
i receive this answer
Screen 0: minimum 640 x 480, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        60.0*    56.0  
   640x480        60.0  
  1024x768_60.00 (0x10b)   63.0MHz
        h: width  1024 start 1072 end 1176 total 1328 skew    0 clock   47.4KHz
        v: height  768 start  771 end  775 total  798           clock   59.4Hz
This is exactly the modeline given by cvt at 1024 768.
When I go in display properties i don't see this resolution but only 800x600 maximum and i can't switch to it.

---

### Post by frrebora on 2010-11-25
There is already nothing as xorg.conf both in etc/X11 and in lib/X11; In origin there weren't; i've created with correct modes and modelines, but nothing has changed (this was yesterday)
then i have renamed in xorg.back and this morning i have already deleted but nothing has changed. Oldest monitors are recognized; seems that mga driver doesn't recognize wide monitors. When i look at  logs i see lines that means that the interrogation in resolutions higher that 800x600x60hz are not supported by monitor (which is not real). after the inserting in gdm init xrandr lines, if i type in terminal xrandr 
i receive this answer
Screen 0: minimum 640 x 480, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        60.0*    56.0  
   640x480        60.0  
  1024x768_60.00 (0x10b)   63.0MHz
        h: width  1024 start 1072 end 1176 total 1328 skew    0 clock   47.4KHz
        v: height  768 start  771 end  775 total  798           clock   59.4Hz
This is exactly the modeline given by cvt at 1024 768.
When I go in display properties i don't see this resolution but only 800x600 maximum and i can't switch to it.

---

### Post by dandnsmith on 2010-11-25
A passing thought, based on some Dell PCs I've recently had dealings with - is the monitor being driven via a VGA cable?

I ask because I've had my own problems using a LG (wide) display on one particular PC via a VGA cable (as that is the only output available), which I cannot persuade to operate in wide screen mode.
Curiously I have another system, with even older hardware, which was quite happily driving a (different) LG wide display full width via a VGA cable connection (Mind you, it looks much better now I've got a better graphics card which I can use DVI-D output.

---

### Post by frrebora on 2010-11-26
Yes, it's via Vga because the Mga chip is integrated on the mainborad; thank you for the support.  I ask another thing; the pc Dell is an ubuntu 10.04 file server; i have a gnome interface because, for simple things, other people have to access, so it has to be Windows-like. My network is Ubuntu 10.04, WinXp and Win7 64 based. There is a SBS 2003 server and the monitor is shared with a KVM switch D-link, so i can't drive it by DVI. But in a server is not important the resolution (it is only important for me because if i buy such monitor in a Ubuntu client I can have problems). The access to the server is by Tight vnc.
Is there any way to have only by tight vnc an higher resolution?
Thank you for all support; i was already in doubt that the problem was in recognition of monitor.

---

### Post by Fafler on 2010-11-26
Have you tried without the KVM switch? Or with another cable? It could be that the I2C bus (it has another name when were talking monitors, but it's basically the same thing) is not connected through the cable and the card is unable to identify it.

You could also mess around with the read-edid package and try to extract the edid and make a xorg.conf that includes that data.

---

### Post by dandnsmith on 2010-11-26
I'd go with that idea.
I abandoned use of a KVM switch on VGA cable a few years back, when I found that indeed the monitor went unidentified.
I could fix Windows partially, but not linux.
Somebody else on a forum suggested it was the suppression of the EDID info which caused the problem, and this was supported by another poster.

That episode resulted in eventually using both the VGA and DVI connections to my (then new) LG monitor - gets over the problem for the main machine, but I do do 2 separate switch actions.

---

