---
title: "Optical PS/2 Mouse does not work"
date: 2005-12-28
forum: Hardware &amp; Laptops
---

### Post by greecesking on 2005-12-28
I have assembled a new computer: Pentium 4 HT 3GHZ, 1 GB Dual Channel Memmory, Radeon 9600 XT, Optical PS/2 Mouse Dr. Hank.
The mouse pointer appears but that does not work.
I verified that modules devmouse* (*I think this is wrote so) and psmouse are loaded.

I tried to edit /etc/X11/xorg.conf changing:

Section "InputDevice" 
    Identifier  "Configured Mouse" 
    Driver      "mouse" 
    Option        "CorePointer" 
    Option        "Device" "/dev/input/mice" 
    Option        "Protocol" "ImPS/2" 
    Option        "Emulate3Buttons" "true" 
    Option        "ZAxisMapping" "4 5" 
EndSection 

to: 

Section "InputDevice" 
    Identifier  "Configured Mouse" 
    Driver      "mouse" 
    Option        "auto" 
    Option        "Device" "/dev/psaux" 
    Option        "Protocol" "PS/2" 
EndSection 

unsucessfuly.

I can't get to run gpm, xorgconf, xorgconfig, xfree86cfg, Xconfigurator. It seem that Ubuntu didn't install them.
By the way, the mouse lights when I turn on the computer and PS/2 keyboard is recognized.

I verified /proc/bus/devices/input and the mouse is not listed there, only the speaker and keyboard are.

Somebody have any suggestion?

---

### Post by lptr on 2005-12-28
Hello,

here the same. This one is PS/2 connected.

I used this mouse in Hoary 5.04 since January 2005 without any problems (switching back and for between diff machines via KVM switch and so it is exactly same condition). In Breezy 5.10 no way. It sticks on the left upper corner and does really nothing. Inbetween I did another fresh install on a completely different machine (previous had Intel graph chipset built in). There was same behaviour. Sticking left upper.

In the beginning I thought it is maybe a X-Server problem. But it isn't because I switched over to VESA and all is same.

This machine I currently trying is equiped with ATI Mach64. Graphics are fine but much more than graphical login isn't possible (without mouse).

Following the last lines of my X.log. Any ideas?

[SIZE="1"][FONT="Courier New"](**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "de"
(**) Generic Keyboard: XkbLayout: "de"
(**) Option "XkbVariant" "nodeadkeys"
(**) Generic Keyboard: XkbVariant: "nodeadkeys"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 5
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0
Warning: font renderer for ".pmf" already registered at priority 0[/FONT]
[/SIZE]

---

### Post by lptr on 2005-12-30
:rolleyes: Problem found :rolleyes: 

Because in another thread I read from troubles regarding KVM switches I directly plugged in another MS PS/2 mouse to the system. The keyboard and monitor I left on the KVM.

Guess what: ...of course the mouse is fully functional being connected directly to PS/2 port and working smoothly. What I did not try is to replace the Logitech MX1000 on KVM switch with MS Intellimouse optical what sticks now on the 5.10 machine.

The thing I don't understand is that exactly this KVM switch (Equipe with four input ports) never made trouble. Ok - this is not completely true - when I am booting a machine and monitor is off or the booting machine is not the active one, then usually the 1600x1200 pixel resolution is not delivered to the machine then even X11 init fails and returns anything with 1280x or 1024x (I don't remember...) yes and because it is a TFT not handling more than 65 Hz after switching to machine the monitor is out of sync. Rebooting is necessary, then. But this does not matter with knowing it.

But this one with PS/2 mouse troubles I never had. 

Mouse is detected but obviously not initialized correctly. So I assume the init routines from Hoary 5.04 are implemented different. Maybe a to tight timing during init? It is definitive a problem in Breezy because I installed several Hoary machines and inbetween two Breezy. Hoary worked, Breezy not.

Should I post a bug report for this? What do you think?

---

### Post by greecesking on 2006-01-02
I Can't help you with that.
I have no experience in kvm switches.

---

### Post by greecesking on 2006-01-02
Does have somebody a PS/2 mouse working?

Because I already think that is a problem with the kernel hardware detection.

---

### Post by greecesking on 2006-01-04
The mouse does not appear em lspci or /proc/bus/input/devices.

But, the PS/2 controller is detected in dmesg, assignning irq 12 to mouse.

The follow message is delivered:
             mice: PS/2 mouse device common for all mice.

The BIOS detects the mouse as well.

Does somebody any suggestion?

---

### Post by lptr on 2006-01-04
[QUOTE=greecesking]The mouse does not appear em lspci or /proc/bus/input/devices.

But, the PS/2 controller is detected in dmesg, assignning irq 12 to mouse.

The follow message is delivered:
             mice: PS/2 mouse device common for all mice.

The BIOS detects the mouse as well.

Does somebody any suggestion?[/QUOTE]

Seems to be maybe a harware defect? :???: 
Don't you have a different mouse (other brand) you could try? Other problem could be a malfunctioning PS/2 port on your mainboard... The last days (see my previous posts) showed me several strange things in hardware land.

I never tried it. I assume that if you having a unused USB port you could eventually use this for mouse? 

regards,

rob*

---

