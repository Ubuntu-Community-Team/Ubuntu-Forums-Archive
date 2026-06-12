---
title: "Any way to set Logitech wireless trackball orientation?"
date: 2009-01-26
forum: Hardware
---

### Post by Pro_D on 2009-01-26
I have a Logitech Cordless Optical Trackman.  Under windows the SetPoint software allows me to setup Orientation.  All I have to do is click a button and then slide the mouse in the direction that I think is up.  Pretty sure it's just tweaking the vertical and horizontal input a few degrees.

I don't know how I would do this on Ubuntu though (I have spent some time with Google to no result).  I am running a newly installed 8.10 on my laptop.  When the laptop is plugged into my monitor I use my keyboard/trackball on the laptop as well and it's a real pain navigating around when up is actually up and right on Ubuntu.  I would also need to know how to do this change before throwing Ubuntu on my desktop as I can't resort to a built in touch pad there...

If there is a file I can tweak and see changes without a reboot that would work fine.

---

### Post by lennyleonard on 2009-02-10
I also have the same problem since upgrading to intrepid. With Hardy, the etc/X11/xorg.conf entry looked like this.



Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Protocol"	"Auto"
	Option		"Buttons"	"10"
	Option		"ButtonMapping"	"1 2 3 8 9 11 12 10"
	Option		"EmulateWheel"	"true"
	Option		"EmulateWheelButton"	"2"
	Option		"ZaxisMapping"	"4 5"
	**Option		"AngleOffset"	"-31"**
	Option		"Resolution"	"800"
EndSection



With Intrepid, all the buttons worked immediately. But the AngleOffset option is what I need to orient the X and Y axes. Intrepid unfortunately doesn't use this file, and instead uses hal to control the mouse. I have added these entries to the etc/hal/fdi/policy/mouse.fdi file. (If this file is not present you can just create it. I have read that the name is not important, but the .fdi extension is.)



<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input.mouse">
      <match key="info.product" contains="Logitech USB Receiver">
       <merge key="input.x11_options.ButtonMapping" type="string">1 2 3 8 9 11 12 10</merge>
      <merge key="input.x11_options.EmulateWheel" type="string">true</merge>
      <merge key="input.x11_options.EmulateWheelButton" type="string">2</merge>
      <merge key="input.x11_options.ZAxisMapping" type="string">4 5</merge>
      <merge key="input.x11_options.**AngleOffset**" type="string">-31</merge>
      </match>
    </match>
  </device>
</deviceinfo>



Although this works for the buttons, I have read on another website that AngleOffset is no longer supported. If anyone knows if this is true please post.

I am now quite lost - and still being a bit of a newbie, I have run out of ideas. If anyone can help me it would really be appreciated. I will post again if I have more information or progress.

Thanks everyone, for all your help. Ubuntu ROCKS!!

---

### Post by lennyleonard on 2009-02-10
After more research, success.

For my Logitech Cordless Optical Trackman, I have done the following.


1. edit the xorg.conf file by opening the terminal and typing:

[I]sudo gedit /etc/X11/xorg.conf
[/I]


2. add the following lines at the end of the file:


[I]Section "ServerFlags"
        Option "AutoAddDevices" "False"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Protocol"	"Auto"
	Option		"Buttons"	"10"
	Option		"ButtonMapping"	"1 2 3 8 9 11 12 10"
	Option		"EmulateWheel"	"true"
	Option		"EmulateWheelButton"	"2"
	Option		"ZaxisMapping"	"4 5"
	Option		"AngleOffset"	"-31"
	Option		"Resolution"	"800"
EndSection[/I]



3. save the file and restart gnome by hitting ctrl-alt-backspace.


Please note that disabling "*AutoAddDevices*" in the *ServerFlags* section was **not** necessary when I was running Hardy. So only add that Section if you are running Intrepid.

All the buttons now work and the orientation is normal. So far, I have had no problems with disabling *AutoAddDevices*. USB drives still mount automatically. I also deleted the mouse.fdi file I created that I mentioned in my previous post, since I don't need it anymore.

Pro_D, the AngleOffset Option is the one that controls orientation. "-31" is 31 degrees clockwise. Obviously, you will find whatever rotation you find comfortable. 

If you use ctrl-alt-backspace instead of restarting the system, it will only restart gnome, which is all you need to reload the xorg.conf file. And if you open a terminal and press the up arrow key it will regenerate the last command(s). That makes it a bit faster to adjust the setting, and reboot.

Hope this helps.

---

### Post by Nazrax on 2010-03-05
Has anyone figured out how to do this using HAL under Karmic? This fix worked great on my desktop, but now that I'm on a laptop and will be using the trackball at work, a mouse at home, and the touchpad everywhere else, a static xorg config doesn't work too well any more ...

I tried to HALify your configuration as:
```

<?xml version="1.0" encoding="UTF-8"?> 
<deviceinfo version="0.2">
 <device>
  <match key="info.product" string="Logitech USB Receiver">
   <match key="info.capabilities" contains="input.mouse">
    <merge key="input.x11_driver" type="string">mouse</merge>
    <merge key="input.x11_options.Protocol" type="string">Auto</merge>
    <merge key="input.x11_options.AngleOffset" type="string">-31</merge>
    <merge key="input.x11_options.Buttons" type="string">10</merge>
    <merge key="input.x11_options.ButtonMapping" type="string">1 2 3 6 7 8 9 10 4 5</merge>
    <merge key="input.x11_options.ZaxisMapping" type="string">4 5</merge>
    <merge key="input.x11_options.Resolution" type="string">800</merge>
   </match>
  </match>
 </device>
</deviceinfo>

```

lshal shows all the right options. However, when I move the trackball (or click a button), things go haywire. The mouse jumps, menus pop up, desktops change, and half the time X stops reading inputs altogether and I have to kill it.

I tried removing most of the options; it seems that just specifying the driver as "mouse" is enough for it to go crazy, and mouse is the only driver that supports the AngleOffset option ...

---

### Post by Nazrax on 2010-03-08
I found the problem. It turns out that HAL was specifying the input device as /dev/input/eventX instead of /dev/input/mouseX. Once I told HAL to specify the mouse device, things worked much better. For some reason, the protocol autodetection is detecting a 3 button PS/2 mouse, so I had to manually specify ExplorerPS/2 as well.

Here's the full FDI file:
```

<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
 <device>
  <match key="info.product" string="Logitech USB Receiver">
   <match key="info.capabilities" contains="input.mouse">
    <merge key="input.device" type="string">/dev/input/by-id/usb-Logitech_USB_Receiver-mouse</merge>
    <merge key="input.x11_driver" type="string">mouse</merge>
    <merge key="input.x11_options.Protocol" type="string">ExplorerPS/2</merge>
    <merge key="input.x11_options.AngleOffset" type="string">-31</merge>
    <merge key="input.x11_options.Buttons" type="string">10</merge>
    <merge key="input.x11_options.ButtonMapping" type="string">1 2 3 6 7 8 9 10 4 5</merge>
    <merge key="input.x11_options.ZaxisMapping" type="string">4 5</merge>
   </match>
  </match>
 </device>
</deviceinfo>

```

---

### Post by Rogerborg on 2010-04-28
^^^
Winner!  =D>

Thank you so much for figuring that out and sharing it with us; it was driving me bonkers.  I now have a usable input device at last.

---

### Post by rdamazio on 2010-08-17
Any idea how to do the same in Ubuntu 10.04? It seems to ignore HAL files.

---

### Post by Rogerborg on 2010-12-08
Yes, I rashly updated to 10.04 as well, and now I'm back to diagonal movement again.   ](*,)

---

### Post by Rogerborg on 2010-12-10
Ah, got it.

On Ubuntu 10.04.1

First, I created an xorg.conf - this step may not be strictly necessary, but I'll document what I have working.

CTRL+ALT+F1

sudo service gdm stop
sudo Xorg -configure
sudo cp xorg.conf.new /etc/X11/xorg.conf
sudo service gdm start

Check that X is working OK with your shiny new old fashioned xorg.conf.

Now, 

cd /usr/lib/X11/xorg.conf.d
ls 

You should already have something like: 
05-evdev.conf 10-synaptics.conf 10-vmmouse.conf 10-wacom.conf files

Create a new file 99-logitech.conf with the following content:

sudo gedit 99-logitech.conf

Section "InputClass"
        Identifier "logitech"
        MatchIsPointer "on"
        MatchProduct "Logitech USB Receiver"
        MatchDevicePath "/dev/input/mouse*"
        Driver "mouse"
        Option "AngleOffset" "-31"
        Option "Protocol" "ExplorerPS/2"
EndSection

Restart X (e.g. sudo service gdm restart, or log out and back in) and you should have a usable trackball again.

---

### Post by Nazrax on 2011-02-04
Don't know how I missed your reply all this time ...

I'm really glad to see this solution. Now I can finally upgrade past 9.10.

I'm not so sure about putting custom files under /usr -- but it turns out that X also reads files under /etc/X11/xorg.conf.d, so I put the InputClass section in /etc/X11/xorg.conf.d/50-trackmanfx.conf (I had to create the directory). I didn't create an xorg.conf, and it works just fine.

---

### Post by Rogerborg on 2011-03-07
Thanks, Nazrax, that looks better.  I suspected the xorg.conf wasn't necessary, but I was just so happy to have a working trackball again that I didn't have the nerve to fiddle any further. ;)

---

### Post by mgorovoy on 2011-06-18
> **Rogerborg said:**
> 
CTRL+ALT+F1

sudo service gdm stop
sudo Xorg -configure
sudo cp xorg.conf.new /etc/X11/xorg.conf
sudo service gdm start

Check that X is working OK with your shiny new old fashioned xorg.conf.

Now, 

cd /usr/lib/X11/xorg.conf.d
ls 

You should already have something like: 
05-evdev.conf 10-synaptics.conf 10-vmmouse.conf 10-wacom.conf files

Create a new file 99-logitech.conf with the following content:

sudo gedit 99-logitech.conf

Section "InputClass"
        Identifier "logitech"
        MatchIsPointer "on"
        MatchProduct "Logitech USB Receiver"
        MatchDevicePath "/dev/input/mouse*"
        Driver "mouse"
        Option "AngleOffset" "-31"
        Option "Protocol" "ExplorerPS/2"
EndSection

Restart X (e.g. sudo service gdm restart, or log out and back in) and you should have a usable trackball again.

This solution works on Ubuntu 11.04 Natty Narwhal as well. I've been looking for a couple of days before I found this thread. Thank you very much!!

-Michael

---

### Post by Rogerborg on 2011-08-25
HTH.  

Just a note: I switched to another 10.04 setup recently, and tried Nazrax's solution without an xorg.conf.  Unfortunately, it ate my keyboard, so I went back to the xorg.conf version, which worked fine.

As an aside, I've remapped the buttons on my Logitech to emulate a Microsoft Trackball Explorer as closely as I can.  This is my current best approximation:

xmodmap -e "pointer = 1 8 9 4 5 6 7 3 2"

You can just add that as a System -> Preferences -> Startup Application command.

---

### Post by Nectarian on 2011-12-09
I tried your solution in 11.04 and it neither seems to work with the new file in /usr/lib/X11/xorg.conf.d nor /etc/X11/xorg.conf.d nor in /usr/share/X11/xorg.conf.d nor by editing the text directly into the xorg.conf . I'm not sure if I just did it wrong, or if the solution doesn't work on 11.04, has anyone got any Data about this?

---

