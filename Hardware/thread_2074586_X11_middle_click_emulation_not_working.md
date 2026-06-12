---
title: "X11 middle click emulation not working"
date: 2012-10-21
forum: Hardware
---

### Post by zhangweiwu on 2012-10-21
I have currently installed the new release 12.10 of Ubuntu.

I could not enable the emulation of the middle button click by clicking the left and the right button.

The following method DO NOT work for me:

1. Create a fdi file.
In fact, there is no '/etc/hal' to start with. I forcibly created the folder and everything beneath it 

```

$ cat /etc/hal/fdi/policy/mouse-3button.fdi
<match key="info.product" string="eGalax Inc. USB TouchController">
 <merge key="input.x11_options.Emulate3Buttons" type="string">true</merge>
</match>


```

It doesn't work even if I reboot the machine.

Where I got the method:
[http://ubuntuforums.org/showthread.php?p=7001167](http://ubuntuforums.org/showthread.php?p=7001167)
[http://ubuntuforums.org/showthread.php?t=1335594](http://ubuntuforums.org/showthread.php?t=1335594)

2. The good old xorg.conf file doesn't help. However, it works when I don't use Unity (e.g. login to fluxbox session instead):
```

$ cat /etc/X11/xorg.conf 
Section "InputClass"
    Identifier "whatever"
    MatchIsPointer "on"
    Option "Emulate3Buttons" "on"
EndSection

```

Where I got the method:
[http://ubuntuforums.org/showthread.php?t=940446](http://ubuntuforums.org/showthread.php?t=940446)

3. create a udev rule.
```

$ cat /etc/udev/rules.d/mouse-3button.rules 
ENV{x11_options.Emulate3Buttons}="True"

```

Where I got the method:
[http://ubuntuforums.org/showthread.php?t=1426012](http://ubuntuforums.org/showthread.php?t=1426012)

4. just don't use a mouse with middle button.

It also doesn't work for me. I have a two-button mouse built in on my laptop, without any other device plugged on it, starts off clean, and no mouse button emuulation.

Where I got the method:
(same as above link)

P.S. What used to surprise me is the method to configure Ubuntu (and perhaps every distribution of Linux) changes EVERY YEAR. The above methods are used in year 2008, 2009, 2010, and no new article / method have been mentioned in year 2011, 2012, but old method stopped working nevertheless. Similar story is how to configure a bluetooh device: the method changes every year, and every year's attempt to configure such a device failed. I never ever got a bluetooth device working. Not a reason to leave Ubuntu exactly, I am getting used to it, and using Windows is not an acceptable compromise anyway.

---

### Post by 2F4U on 2012-10-22
Maybe this helps:

[http://askubuntu.com/questions/160164/how-do-i-enable-middle-mouse-button-emulation-in-12-04-lts](http://askubuntu.com/questions/160164/how-do-i-enable-middle-mouse-button-emulation-in-12-04-lts)

---

### Post by zhangweiwu on 2012-10-22
> **2F4U said:**
> Maybe this helps:

[http://askubuntu.com/questions/160164/how-do-i-enable-middle-mouse-button-emulation-in-12-04-lts](http://askubuntu.com/questions/160164/how-do-i-enable-middle-mouse-button-emulation-in-12-04-lts)

Thanks a lot! Learned from above method, I solved the problem in the end.

--- Here is a brief conclusion continue from the original post ---

Method 5: Install gpointing-device-setting. Failed.

I installed the package, expecting it adding an entry in gnome-control-panel, but it didn't. Trying to launch it directly results a core dump:
```

$ gpointing-device-settings 
Segmentation fault (core dumped)

```

All other articles mentioned how gpointing-device-setting worked for their touchpad. Mine is not a touchpad. My built-in mouse is a tinkpad-style track-point with two separate mouse buttons. Perhaps mine device isn't compatible with gpointing-device-settings .


Method 6: use getting command:
```

$ gsettings set org.gnome.settings-daemon.peripherals.mouse middle-button-enabled true

```

This finally worked, although I haven't test if it endures a reboot.

P.S.

So it seems, all through the years since 2009, the method to configure middle mouse button emulation went through the following:

- a change in xorg.conf config file, the good-old xorg.conf style.
- a change in udev rule in an INI-style config file.
- a change in fdi config file of XML-style config file.
- a command to set parameter (gsetting). Unlike previous 3, this method perhaps doesn't affect use outside of GNOME.


Evolution? :)

---

