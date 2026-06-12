---
title: "Lenovo Yoga 11s Unresponsive Touchpad"
date: 2015-11-27
forum: Hardware
---

### Post by killian-widdis on 2015-11-27
I just did a clean install of Kubuntu 15.10 and am having problems with the touchpad. Whenever I reboot or power cycle the touchpad is initially unresponsive, but after about 20-30 minutes magically starts working again. The only clue I have to go on is in the Xorg server log file, where it looks like the server tries to load the device twice. How do I troubleshoot this?

[FONT=monospace][COLOR=#000000]cat /var/log/Xorg.0.log | grep -i synaptics:[/COLOR]
[/FONT][FONT=monospace]
[/FONT]```
[FONT=monospace][COLOR=#000000][     4.977] (II) config/udev: Adding input device SynPS/2 [/COLOR][COLOR=#FF5454]**Synaptics**[/COLOR][COLOR=#000000] TouchPad (/dev/input/event7)[/COLOR]
[     4.977] (**) SynPS/2 [COLOR=#FF5454]**Synaptics**[/COLOR][COLOR=#000000] TouchPad: Applying InputClass "evdev touchpad catchall"[/COLOR]
[     4.977] (**) SynPS/2 [COLOR=#FF5454]**Synaptics**[/COLOR][COLOR=#000000] TouchPad: Applying InputClass "touchpad catchall"[/COLOR]
[     4.977] (**) SynPS/2 [COLOR=#FF5454]**Synaptics**[/COLOR][COLOR=#000000] TouchPad: Applying InputClass "Default clickpad buttons"[/COLOR]
[     4.977] (**) SynPS/2 [COLOR=#FF5454]**Synaptics**[/COLOR][COLOR=#000000] TouchPad: Applying InputClass "touchpad catchall"[/COLOR]
[     4.977] (**) SynPS/2 [COLOR=#FF5454]**Synaptics**[/COLOR][COLOR=#000000] TouchPad: Applying InputClass "Default clickpad buttons"[/COLOR]
[     4.977] (II) LoadModule: "[COLOR=#FF5454]**synaptics**[/COLOR][COLOR=#000000]"[/COLOR]
[     4.977] (II) Loading /usr/lib/xorg/modules/input/[COLOR=#FF5454]**synaptics**[/COLOR][COLOR=#000000]_drv.so[/COLOR]
[     4.977] (II) Module [COLOR=#FF5454]**synaptics**[/COLOR][COLOR=#000000]: vendor="X.Org Foundation"[/COLOR]
[     4.977] (II) Using input driver '[COLOR=#FF5454]**synaptics**[/COLOR][COLOR=#000000]' for 'SynPS/2 [/COLOR][COLOR=#FF5454]**Synaptics**[/COLOR][COLOR=#000000] TouchPad'[/COLOR]
[     4.977] (**) SynPS/2 [COLOR=#FF5454]**Synaptics**[/COLOR][COLOR=#000000] TouchPad: always reports core events[/COLOR]
[     5.012] (II) [COLOR=#FF5454]**synaptics**[/COLOR][COLOR=#000000]: SynPS/2 [/COLOR][COLOR=#FF5454]**Synaptics**[/COLOR][COLOR=#000000] TouchPad: found clickpad property[/COLOR]
[     5.012] (--) [COLOR=#FF5454]**synaptics**[/COLOR][COLOR=#000000]: SynPS/2 [/COLOR][COLOR=#FF5454]**Synaptics**[/COLOR][COLOR=#000000] TouchPad: x-axis range 1242 - 5702 (res 51)[/COLOR]
[     5.012] (--) [COLOR=#FF5454]**synaptics**[/COLOR][COLOR=#000000]: SynPS/2 [/COLOR][COLOR=#FF5454]**Synaptics**[/COLOR][COLOR=#000000] TouchPad: y-axis range 1124 - 4730 (res 62)[/COLOR]
[     5.012] (--) [COLOR=#FF5454]**synaptics**[/COLOR][COLOR=#000000]: SynPS/2 [/COLOR][COLOR=#FF5454]**Synaptics**[/COLOR][COLOR=#000000] TouchPad: pressure range 0 - 255[/COLOR]
[     5.012] (--) [COLOR=#FF5454]**synaptics**[/COLOR][COLOR=#000000]: SynPS/2 [/COLOR][COLOR=#FF5454]**Synaptics**[/COLOR][COLOR=#000000] TouchPad: finger width range 0 - 15[/COLOR]
[     5.012] (--) [COLOR=#FF5454]**synaptics**[/COLOR][COLOR=#000000]: SynPS/2 [/COLOR][COLOR=#FF5454]**Synaptics**[/COLOR][COLOR=#000000] TouchPad: buttons: left double triple[/COLOR]
[     5.012] (--) [COLOR=#FF5454]**synaptics**[/COLOR][COLOR=#000000]: SynPS/2 [/COLOR][COLOR=#FF5454]**Synaptics**[/COLOR][COLOR=#000000] TouchPad: Vendor 0x2 Product 0x7[/COLOR]
[     5.012] (--) [COLOR=#FF5454]**synaptics**[/COLOR][COLOR=#000000]: SynPS/2 [/COLOR][COLOR=#FF5454]**Synaptics**[/COLOR][COLOR=#000000] TouchPad: touchpad found[/COLOR]
[     5.012] (**) SynPS/2 [COLOR=#FF5454]**Synaptics**[/COLOR][COLOR=#000000] TouchPad: always reports core events[/COLOR]
[     5.028] (II) XINPUT: Adding extended input device "SynPS/2 [COLOR=#FF5454]**Synaptics**[/COLOR][COLOR=#000000] TouchPad" (type: TOUCHPAD, id 15)[/COLOR]
[     5.028] (**) [COLOR=#FF5454]**synaptics**[/COLOR][COLOR=#000000]: SynPS/2 [/COLOR][COLOR=#FF5454]**Synaptics**[/COLOR][COLOR=#000000] TouchPad: (accel) MinSpeed is now constant deceleration 2.5[/COLOR]
[     5.028] (**) [COLOR=#FF5454]**synaptics**[/COLOR][COLOR=#000000]: SynPS/2 [/COLOR][COLOR=#FF5454]**Synaptics**[/COLOR][COLOR=#000000] TouchPad: (accel) MaxSpeed is now 1.75[/COLOR]
[     5.028] (**) [COLOR=#FF5454]**synaptics**[/COLOR][COLOR=#000000]: SynPS/2 [/COLOR][COLOR=#FF5454]**Synaptics**[/COLOR][COLOR=#000000] TouchPad: (accel) AccelFactor is now 0.035[/COLOR]
[     5.028] (**) SynPS/2 [COLOR=#FF5454]**Synaptics**[/COLOR][COLOR=#000000] TouchPad: (accel) keeping acceleration scheme 1[/COLOR]
[     5.028] (**) SynPS/2 [COLOR=#FF5454]**Synaptics**[/COLOR][COLOR=#000000] TouchPad: (accel) acceleration profile 1[/COLOR]
[     5.028] (**) SynPS/2 [COLOR=#FF5454]**Synaptics**[/COLOR][COLOR=#000000] TouchPad: (accel) acceleration factor: 2.000[/COLOR]
[     5.028] (**) SynPS/2 [COLOR=#FF5454]**Synaptics**[/COLOR][COLOR=#000000] TouchPad: (accel) acceleration threshold: 4[/COLOR]
[     5.028] (--) [COLOR=#FF5454]**synaptics**[/COLOR][COLOR=#000000]: SynPS/2 [/COLOR][COLOR=#FF5454]**Synaptics**[/COLOR][COLOR=#000000] TouchPad: touchpad found[/COLOR]
[     5.029] (II) config/udev: Adding input device SynPS/2 [COLOR=#FF5454]**Synaptics**[/COLOR][COLOR=#000000] TouchPad (/dev/input/mouse2)[/COLOR]
[     5.029] (**) SynPS/2 [COLOR=#FF5454]**Synaptics**[/COLOR][COLOR=#000000] TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"[/COLOR]
[   101.650] (--) [COLOR=#FF5454]**synaptics**[/COLOR][COLOR=#000000]: SynPS/2 [/COLOR][COLOR=#FF5454]**Synaptics**[/COLOR][COLOR=#000000] TouchPad: touchpad found[/COLOR]

[/FONT]
```

---

