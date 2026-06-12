---
title: "Upgraded to 8.10 - touchpad HAL/xorg issue"
date: 2008-10-31
forum: General Help
---

### Post by rosyatrandom on 2008-10-31
I've been encountering a few issues since upgrading to 8.10 (see [other thread]("http://ubuntuforums.org/showthread.php?p=6076459")), and here's one of them:

When I try to go to Preferences > Touchpad I get the error message 

"GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics"

which I've seen before (eventually it went away after putting setting the value to 'true' from 'on', I think)... but this time, looking at xorg.conf I see this:

```

# commented out by update-manager, HAL is now used
#Section "InputDevice"
#	Identifier	"Synaptics Touchpad"
#	Driver		"synaptics"
#	Option		"SHMConfig"		"on"
#	Option		"SendCoreEvents"	"true"
#	Option		"Device"		"/dev/psaux"
#	Option		"Protocol"		"auto-dev"
#	Option		"HorizEdgeScroll"	"0"
#EndSection
```

I hadn't even heard of HAL before this, but it looks like it's trying to run things here without telling everyone about it. Any ideas?

---

### Post by soro2005 on 2008-11-01
Look [here](https://help.ubuntu.com/community/SynapticsTouchpad) (Section "Enabling SHMConfig").

Just to make sure: It seems that the Xorg.config method is not good anymore, so you'd follow the instructions about "placing the the desired options in a HAL fdi file." You may have to reboot, not only log out, to get the effect.

---

### Post by Agrajag27 on 2008-11-03
Guys, not having any luck with this. Followed the directions for enabling SHMConfig but after re-login (and reboot as well) it's clear it's not enabled. Plus I still have NO idea what filename I should give the fdi file for my m1530 touchpad.

Any ideas? My touchpad response is horrific. Keep hoping to find someone who has this all in one nice inclusive file and just steal that. hehehe

---

### Post by soro2005 on 2008-11-04
The file should be called shmconfig.fdi, just as in the instructions, and you just copy the few lines that are quoted there. Did you try that? You have to reboot, and the gsynaptics should work again. The xorg.conf method is obsolete it seems, so it won't have any effect.

---

### Post by alhead on 2008-11-04
I'm having trouble as well.  I have added the necessary .fid for my desired setup, but it doesn't change anything.  I've tried shutting down and turning back on to make sure everything completely resets.  The synaptics section in xorg.conf is completely commented out, so I don't know what the problem is.

---

### Post by darinmiller@cableone.net on 2008-11-09
Ensure to perform the following to fully enable the touchpad on a Dell m1530:

Edit the /boot/grub/menu.lst file:

```
sudo gedit /boot/grub/menu.lst
```

[INDENT]Add **i8042.nomux=1** as follows:

# defoptions=quiet splash

so that it looks like this:

```
# defoptions=quiet splash **i8042.nomux=1**
```

This ensures subsequent kernel updates add the initialization code to the boot menu command.  

Next add i8042.nomux=1 to each of the kernel lines in the menu section. Your system will have a different UUID and/or kernel rev, thus the line below should not be copied, but rather used as reference.  Mine looks like this:

```
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=ecb31f13-4311-415c-a301-ba47c971b365 ro quiet splash **i8042.nomux=1**
```
[/INDENT]

Kill all references to pointing devices and keyboards in the xorg.conf file: 
```
sudo gedit /etc/X11/xorg.conf
```

Mine xorg.conf file looks like this:
[INDENT]```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Seiko"
    HorizSync       30.0 - 75.0
    VertRefresh     60.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600M GT"
    Option         "FlatPanelProperties" "Scaling = aspect-scaled"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-1"
    Option         "metamodes" "DFP-0: nvidia-auto-select +1920+0, DFP-1: nvidia-auto-select +0+0; DFP-1: 1600x1200 +0+0, DFP-0: null; DFP-1: 640x480 +0+0, DFP-0: null; DFP-1: 1920x1200 +0+0, DFP-0: null"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```[/INDENT]


Next, update the touchpad.fdi file: 
```
sudo gedit /etc/hal/fdi/policy/touchpad.fdi
```
to look like the following.  Note: I like very sensitive touchpads.  If you prefer less sensitivity, reduce the minspeed and maxspeed parameters.
```
[INDENT]
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
 <device>
          <match key="info.capabilities" contains="input.touchpad">
               <merge key="input.x11_options.SHMConfig" type="string">on</merge>
               <merge key="input.x11_options.HorizEdgeScroll" type="string">1</merge>
               <merge key="input.x11_options.VertEdgeScroll" type="string">1</merge>
               <merge key="input.x11_options.MinSpeed" type="string">0.7</merge>
               <merge key="input.x11_options.MaxSpeed" type="string">1.3</merge>
               <merge key="input.x11_options.AccelFactor" type="string">0.100</merge>
               <merge key="input.x11_options.EdgeMotionMinSpeed" type="string">5</merge>
               <merge key="input.x11_options.EdgeMotionMaxSpeed" type="string">10</merge>
          </match>
     </device>
</deviceinfo>[/INDENT]
```

Restart HAL: 
```
sudo /etc/init.d/hal restart
```

I have not succeeded in changing the window drag edge motion speed via the EdgeMotionMaxSpeed options.  If someone figures this out, please post.  Also, ensure to review Synaptics man pages.  I prefer the yelp pages for readability:

```
yelp man:synaptics
```

Your touchpad should now scroll horizontally and vertically.

Another note: You may find the gsynaptics utility useful. It seems to replicate the touchpad.fdi file settings but saves the touchpad settings elsewhere.

---

### Post by uelansh on 2008-11-11
I found a file with a ton of options to edit the touchpad. It's located at:

/usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi

---

### Post by Ronald Baljeu on 2008-11-22
On my system, a program called **mouseemu** caused the touchpad device to be busy. After removing it, the touchpad works. See also [http://linuxpc.info/node/47]("http://linuxpc.info/node/47").

---

### Post by bralsca on 2009-01-11
Hi, 
i'm new on this forum
I have seen all your post, but I can't repair my touchpad on a DELL XPS M1530.
can you explain to me how use touchpad and not mouse on this srt of computer? how parameter it?
you can send me a mail with all details at: [email]bralsca@free.fr[/email]. write "touchpad ubuntu" in object for the spam filter.
thanks

---

