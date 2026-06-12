---
title: "NVIDIA monitor out of range"
date: 2009-05-25
forum: Installation &amp; Upgrades
---

### Post by bachisanerd on 2009-05-25
I'm having quite a bit of trouble getting the NVIDIA driver to work right. 

I just installed Jaunty, and then activated the proprietary driver.  After rebooting, the login screen comes up beautifully at the monitor's native resolution of 1440x900.  When I log in, however, the monitor goes black as if switching modes, then it complains that the signal is out of range.  I have the same result with both versions of the driver in the Hardware Drivers utility.

I've used nvidia-xconfig to build the xorg.conf file, but that also sends the monitor out of range.  If I change the driver from "nvidia" to "vesa" I can get to my gnome desktop, but only at the very safe, default, plug-and-play resolution, whatever that might be.

I looked at the monitor's manual to find the exact HorizSync and VertRefresh values, and my Monitor section looks like:

```
Section "Monitor"
Identifier "Configured Monitor"
HorizSync 55.5 - 55.9
VertRefresh 60
EndSection
```

I also added modes to the Screen section's Display subsection to see if that would help:

```
Section "Screen"
Identifier "Screen0"
Device "Device0"
Monitor "Configured Monitor"
DefaultDepth 24
SubSection "Display"
 Modes "1440x900" "1024x768"
EndSubSection
EndSection
```

When I start GDM and the login window appears in all of it's beauty, the bottom of /var/log/Xorg.0.log says nothing about video, just some jabber about Macintosh mouse button emulation.  When I log in to GDM and get the monitor's "out of range" message, I go back to tty1 and tail the log again to find some new lines:
```
(II) Open ACPI successful (/var/run/acpid.socket)
(II) NVIDIA(0): Setting mode "1440x900"
(II) Logitech USB Receiver: Device reopened after 1 attempts.
(II) Logitech USB Receiver: Device reopened after 1 attempts.
(II) Macintosh mouse button emulation: Device reopened after 1 attempts.
(II) NVIDIA(0): Setting mode "800x600"
```

Where is it getting the 800x600 mode?  Is there a better way tell the driver the modes I want to use?  Anybody else having this problem?

Thanks.

EDIT: the card is a GeForce7100, the monitor is an Asus VK193D

---

### Post by rlogan on 2009-05-25
I am having a similar issue but in my case it is selecting the 1440x900 instead of 1920x1080. Like you I have no mention of this resolution in the xorg.conf file.

Did you get it sorted out ????

Cheers

Richard

---

### Post by bachisanerd on 2009-05-26
I don't have it figured out yet, no.  I'm sure there must be some way to force a mode, but I don't know what that might be.  Maybe I'll try building and using the latest driver from Nvidia.

---

### Post by bachisanerd on 2009-05-26
I've been reading around that one can set the resolution using the nvidia-settings utility as root.  Trouble is, you have to be in an X session to use the utility.  When I revert to the basic vesa driver and run the utility, it doesn't show any options relating to screen resolution, and overall is not very helpful.  Is this tool more useful when the NVIDIA driver is running?  Is there any kind of command-line alternative to this utility?

---

### Post by bachisanerd on 2009-05-27
It seems that the driver was unable to properly detect the monitor's abilities and was guessing what to do, even though I'd specified the modes in the xorg.config file.  I found this [NVIDIA Forum post]("http://forums.nvidia.com/lofiversion/index.php?t34069.html") which explained how to force the driver to trust you.

I added a line to the Device section, an option called UseEdid set to false:

```
Section "Device"
 Identifier "Device0"
 Driver "nvidia"
 Option "UseEdid" "FALSE"
 VendorName "NVIDIA Corporation"
EndSection
```

To summarize everything I did (as far as I remember):
1) Installed Jaunty
2) Installed nvidia driver from repositories, rebooted
3) Ran nvidia.xconfig from command line
4) Added the UseEdid option line to xorg.conf
5) Restarted GDM
6) Smiled. :)

Hope this helps somebody.

---

### Post by fierojo on 2009-05-28
I'm really new at this.  How do I add the line of code?  Is there a step by step section for this and similar changes?
 
Thanks.
 
S. Joe Wynman

---

### Post by bachisanerd on 2009-06-01
First, get a terminal by pressing Alt+Ctrl+1.  You should see a boring old text login prompt.  Log in, then type:
```
sudo cp /etc/X11/xorg.conf /var/X11/xorg.conf.bak
sudo nano /etc/X11/xorg.conf
```
You'll then have your xorg.conf open in a text editor.  Arrow down until you see:
```

Section "Device"

```
and make sure that somewhere in that device section you see a line like this:
```

Driver "nvidia"

```
If the nvidia line isn't there this trick might not work for you as I believe it's a driver-specific parameter.

If the nvidia driver line is there, make a new line below it and enter:
```

Option "UseEdid" "FALSE"

```
Press Ctrl+o to save, then Ctrl+x to exit the text editor

Now restart GDM, the Gnome Desktop Manager by typing:
```

sudo /etc/init.d/gdm restart

```
After a few seconds, your gnome login should appear.  If something is very broken (or the screen is completely blank) and you need to rever to your previous settings, go back to a terminal (Ctrl+Alt+1), login, and type:
```

sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf

```
and then restart GDM:
```

sudo /etc/init.d/gdm restart

```
and you should be back to where you started.

---

