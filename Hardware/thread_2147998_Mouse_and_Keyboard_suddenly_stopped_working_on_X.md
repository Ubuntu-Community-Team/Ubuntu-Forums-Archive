---
title: "Mouse and Keyboard suddenly stopped working on X"
date: 2013-05-23
forum: Hardware
---

### Post by CyberAngel on 2013-05-23
I have a Dell XPS 13 developer edition, on which I have Kubuntu 13.04 x86_64 installed.
The laptop was working flawlessly for more than a month without reboot (I use the sleep mode) until today!

When I woke it up from the sleep mode, the mouse was working but not the keyboard.
I had to hard reboot it from the power button and then guess! After the reboot, neither the keyboard or mouse was working!!

The problem occurs only on lightdm and I cannot even press ctrl+alt+f1 to go to the tty's! If I use ssh to connect to it and stop lightdm (sudo service lightdm stop), then the keyboard is working fine and I can move through the different ttys (alt+f1 to alt+f6).

After some research I made, I found some people creating an xorg.conf file (/etc/X11/xorg.conf) with the following contents:
```
Section "ServerFlags"
        Option "AutoAddDevices" "false"
EndSection
```
If I do that and restart lightdm, the mouse is working but the keyboard is not!

The problem is most probably related to udev and by grepping the Xorg.0.log for udev (when the manually created xorg.conf file is not present) I get this:

```
[  1132.843] (II) The server relies on udev to provide the list of input devices.
        If no devices become available, reconfigure udev or disable AutoAddDevices.
```

I am going crazy and especially since this happened so suddenly! :evil:
Anyone has any other idea please?

---

### Post by CyberAngel on 2013-05-23
OK! I solved the problem but I really don't know how...

My laptop might be haunted...

With the /etc/X11/xorg.conf file present, as I said before the mouse was working but not the keyboard. The Xorg.0.log was reporting that it 'Failed to load module "kbd"'.
Eventually I found that the file /usr/lib/xorg/modules/input/kbd_drv.so was not present and I could install it with the package xserver-xorg-input-kbd.

After I did that and restarted lightdm, both mouse and keyboard was working but the two fingers scrolling was not working on my laptop's touchpad. This is a function I use a lot. Then I removed the xorg.conf file and restarted the laptop to see its behaviour and everything is working fine now! I even removed the package xserver-xorg-input-kbd which I previously installed, and it looks like everything still works! :/

Let me mention that I restarted the laptop countless times and tried many different things before I post the question in the forums. I tried to boot with an older kernel, also in rescue mode, upgrade the system to the latest version etc...

---

