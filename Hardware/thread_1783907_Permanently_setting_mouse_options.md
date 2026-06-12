---
title: "Permanently setting mouse options?"
date: 2011-06-16
forum: Hardware
---

### Post by terryeden on 2011-06-16
Getting rather frustrated.
I want to change the order of my mouse buttons.
I can run
```
xinput set-button-map 'Kingsis Peripherals  Evoluent VerticalMouse 3 ' 0 2 3 4 5
```
and the buttons are mapped correctly.
But if I reboot, the settings are lost.
I can place the command in System > Preferences > Startup Applications.
But when I unplug the mouse and plug it back in, it loses the settings and I have to manually enter the command.

From Googling, I can see I might need to do something with Xorg.conf.d - but there is [NO DOCUMENTATION]("https://wiki.ubuntu.com/X/Config/Input")! 

The other thing I've had suggested in irc is using a udev rule.

I've created a udev rule which fires when the mouse is plugged in.
```
BUS=="usb",
SYSFS{idVendor}=="1a7c",
SYSFS{idProduct}=="0068",
RUN+="/bin/touch ~/Destop/udev.txt"

```

That works - the udev.txt file is created.
But if I use
```
RUN+="/usr/bin/xinput set-button-map [...] "
```

Nothing happens!

So, my question is two-fold.
1) How can I get udev to call xinput?
2) What's the correct way to permanently store mouse preferences - and where is it documented?

Thanks

(For those old enough to remember, this is a necro from [http://ubuntuforums.org/showthread.php?t=993073](http://ubuntuforums.org/showthread.php?t=993073) )

---

### Post by belltown on 2011-06-17
To permanently set mouse or touchpad options, put the settings in a file in the /usr/share/X11/xorg.conf.d directory.

For the man page documentation, type:

```
man xorg.conf
```For online documentation, see [http://manpages.ubuntu.com/manpages/natty/man5/xorg.conf.5.html](http://manpages.ubuntu.com/manpages/natty/man5/xorg.conf.5.html)

Depending on the mouse or touchpad, there should be documentation that describes the particular settings for that device.

---

### Post by terryeden on 2011-06-17
Aha! Many thanks, that seems to work (in Maverick, I'll try Natty later).

For those wanting to know how I did it...
1) Use lsusb to discover the USB ID of your device

2) Create a new conf file
```
sudo nano /usr/share/X11/xorg.conf.d/90-evoluent.conf
```

3) Use the following as a template
```
Section "InputClass"
        Identifier      "Evoluent"
        MatchUSBID      "1a7c:0068"
        Option "ButtonMapping" "0 2 3 4 5 6 7 8 1 10 11"
EndSection

```

Substitute your own USB ID and prefered button mapping.

4) Reboot.

---

