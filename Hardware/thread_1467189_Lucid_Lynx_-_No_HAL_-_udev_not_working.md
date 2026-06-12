---
title: "Lucid Lynx - No HAL - udev not working"
date: 2010-04-30
forum: Hardware
---

### Post by AnotherMuggle on 2010-04-30
This is the HAL file I was using for my 9.10 installation.  A simple file that modified just the scroll region of my laptop.  Worked a treat.

```
<deviceinfo version="0.2">
&#8722;
<device>
&#8722;
<match key="input.x11_driver" string="synaptics">
<merge key="input.x11_options.SHMConfig" type="string">on</merge>
<merge key="input.x11_options.RightEdge" type="string">5910</merge>
</match>
</device>
</deviceinfo>
```

I have updated my installation to 10.04 as of last night and have been fighting with udev since.  I cannot seem to get the settings to have any effect.  

Can anyone help?

---

### Post by partymetroid on 2010-04-30
HAL was removed in Lucid Lynx. :(

... that's all I know.  I don't have a solution. :v

Sorry! :confused:

---

### Post by dino99 on 2010-04-30
> **tomkear2006 said:**
> This is the HAL file I was using for my 9.10 installation.  A simple file that modified just the scroll region of my laptop.  Worked a treat.

```
<deviceinfo version="0.2">
&#8722;
<device>
&#8722;
<match key="input.x11_driver" string="synaptics">
<merge key="input.x11_options.SHMConfig" type="string">on</merge>
<merge key="input.x11_options.RightEdge" type="string">5910</merge>
</match>
</device>
</deviceinfo>
```

I have updated my installation to 10.04 as of last night and have been fighting with udev since.  I cannot seem to get the settings to have any effect.  

Can anyone help?

this does not speak to me but udev is now used instead of hal in most of the cases. Wonder if your file interfere with the default settings.

in case: sudo dpkg-reconfigure udev

---

### Post by AnotherMuggle on 2010-04-30
> **dino99 said:**
> this does not speak to me but udev is now used instead of hal in most of the cases. Wonder if your file interfere with the default settings.

in case: sudo dpkg-reconfigure udev

"sudo dpkg-reconfigure udev" makes no difference. 

I backed up everything and did a fresh Lucid install.  The udev config file still seems to have no effect.

---

### Post by Ayuthia on 2010-04-30
You might try the following:
```

sudo mkdir /etc/X11/xorg.conf.d
cd /etc/X11/xorg.conf.d
gksu gedit 11-synaptics.conf
```
and then add the following:
```

Section "InputClass"
    Identifier "synaptics-all"
    Driver "synaptics"

    MatchIsTouchpad "on"
    MatchProduct    "SynPS/2 Synaptics TouchPad"
    Option "SHMConfig" "true"
    Option "RightEdge" "5910"
EndSection

```

You will most likely need to replace the MatchProduct line because that is used for my laptop's touchpad.  You can find the information by doing the following:
```
sudo apt-get install input-utils
```
Once it is installed:
```

sudo lsinput

```
In there you should be able to find the name of your touchapd.  You can then replace that name with the one that I have above.

---

### Post by AnotherMuggle on 2010-04-30
> **Ayuthia said:**
> You might try the following:
```

sudo mkdir /etc/X11/xorg.conf.d
cd /etc/X11/xorg.conf.d
gksu gedit 11-synaptics.conf
```
and then add the following:
```

Section "InputClass"
    Identifier "synaptics-all"
    Driver "synaptics"

    MatchIsTouchpad "on"
    MatchProduct    "SynPS/2 Synaptics TouchPad"
    Option "SHMConfig" "true"
    Option "RightEdge" "5910"
EndSection

```

You will most likely need to replace the MatchProduct line because that is used for my laptop's touchpad.  You can find the information by doing the following:
```
sudo apt-get install input-utils
```
Once it is installed:
```

sudo lsinput

```
In there you should be able to find the name of your touchapd.  You can then replace that name with the one that I have above.

That seems to have gotten the touchpad working as I wanted, but now none of the keys on the keyboard work.

I am currently using a different machine.

---

### Post by Ayuthia on 2010-04-30
Try creating 10-evdev.conf in /etc/X11/xorg.conf.d:
```

#
# Catch-all evdev loader for udev-based systems
# We don't simply match on any device since that also adds accelerometers
# and other devices that we don't really want to use. The list below
# matches everything but joysticks.

Section "InputClass"
        Identifier "evdev pointer catchall"
        MatchIsPointer "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection                                                                                                                 
                                                                                                                           
Section "InputClass"                                                                                                       
        Identifier "evdev keyboard catchall"                                                                               
        MatchIsKeyboard "on"                                                                                               
        MatchDevicePath "/dev/input/event*"                                                                               
        Driver "evdev"                                                                                                     
EndSection                                                                                                                 
                                                                                                                           
Section "InputClass"                                                                                                       
        Identifier "evdev touchpad catchall"                                                                               
        MatchIsTouchpad "on"                                                                                               
        MatchDevicePath "/dev/input/event*"                                                                                
        Driver "evdev"                                                                                                     
EndSection                                                                                                                 
                                                                                                                           
Section "InputClass"                                                                                                      
        Identifier "evdev tablet catchall"                                                                                
        MatchIsTablet "on"                                                                                                
        MatchDevicePath "/dev/input/event*"                                                                               
        Driver "evdev"                                                                                                    
#EndSection

Section "InputClass"
        Identifier "evdev touchscreen catchall"
        MatchIsTouchscreen "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection

```
It appears that once you create the xorg.conf.d, you need to add the evdev driver conf file also.  I wasn't for sure if that was a pre-release thing or not.

---

### Post by Wheel_nut on 2010-04-30
\with 10.04 you have to use the GPointing Device Settings tool. You will find it in the Synaptics Package Manager. 

See [http://www.thinkwiki.org/wiki/File:Screenshot-GPointing_Device_Settings-TrackPoint.png](http://www.thinkwiki.org/wiki/File:Screenshot-GPointing_Device_Settings-TrackPoint.png)

It worked for me.

---

### Post by AnotherMuggle on 2010-05-01
> **Wheel_nut said:**
> \with 10.04 you have to use the GPointing Device Settings tool. You will find it in the Synaptics Package Manager. 

See [http://www.thinkwiki.org/wiki/File:Screenshot-GPointing_Device_Settings-TrackPoint.png](http://www.thinkwiki.org/wiki/File:Screenshot-GPointing_Device_Settings-TrackPoint.png)

It worked for me.

I'm confused at why none of these solutions are working for me.  Especially as the hal configuration was such a breeze. :(

---

### Post by Ayuthia on 2010-05-01
If you have added the evdev conf file and it still does not work (and removed the xorg.conf.d directory and tried the other post), I would check /var/log/Xorg.0.log or /var/log/Xorg.0.log.old) and see where it is getting stuck.

The udev change was supposed to go from the.fdi files over to the .conf files that are now located in /etc/X11/xorg.conf.d.  The change is completed in Xorg-server 1.8.  The Gentoo guide has some information on how to use it a little bit.  I have found tools like:
```

udevadm info --export-db
lsinput

```
helpful.  lsinput is a command that you need to install via the input-utils package and udevadm comes with the system.  They do not provide the information like lshal (which is no longer on the system for Ubuntu) so I am still trying to find a tool that can help determine if a device is a tablet/touchpad/touchscreen.

---

### Post by Wheel_nut on 2010-05-01
> **tomkear2006 said:**
> I'm confused at why none of these solutions are working for me.  Especially as the hal configuration was such a breeze. :(

I forgot to say that I had to set the Mouse Buttons to 2. Once I did that it suddenly lit up the scroll functions, both vertical and horizontal.

---

### Post by AnotherMuggle on 2010-05-04
I'm still having difficulties here...like completely failing at getting the touchpad configured.

Does this mean anything to anyone, from Xorg.0.log:
```
(II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event7)
(**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
(**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
(II) Synaptics touchpad driver version 1.2.2
(**) Option "Device" "/dev/input/event7"
(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
(II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
(II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
(II) SynPS/2 Synaptics TouchPad: buttons: left right middle double triple
(--) SynPS/2 Synaptics TouchPad: touchpad found
(**) SynPS/2 Synaptics TouchPad: always reports core events
(II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
(**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
(**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 0
(**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
(**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
(--) SynPS/2 Synaptics TouchPad: touchpad found
(II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
```

---

### Post by AnotherMuggle on 2010-05-04
This blog post got it working for me :D

[http://www.bhagwad.com/blog/2010/technology/alps-synaptics-touchpad-configuration-in-lucid-lynx-ubuntu-10-04.html](http://www.bhagwad.com/blog/2010/technology/alps-synaptics-touchpad-configuration-in-lucid-lynx-ubuntu-10-04.html)

---

### Post by monkeys on 2010-05-05
Hey, I just converted over and now my edge settings are lost too. I only want to alter the RightEdge of my touchpad but can't seem to get things to work out.

Anyone had any luck?

I looked at the blog post and tried to edit the 10-synaptics.conf file but no change.

---

