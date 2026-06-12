---
title: "Set Hybrid-SLI mode?"
date: 2009-08-15
forum: Hardware
---

### Post by Lokiii on 2009-08-15
Hi all!

I got a Dell Studio XPS 13 and I have been searching all over the place in order to figure this one out, but since I didnt find any answers, Il post a topic.

The Studio XPS 13 has a hybrid SLI setup with a GeForce 9400m + 9200m. In Windows Vista I can hotswap between using both of them or just the 9200m one. I know that I cant do the same with the Linux Nvidia drivers, even Nvidia has said that they arent working on it.

However, there must be possible to somehow configure it so that when you boot up only the integrated GPU (9200m) is active. Would it be possible to somehow blacklist the 9400m card? 

In Linux, I doubt I will ever need both the GPU's active because I only really need it when Im gaming, which I do in Windows anyways..

Thanks for any help!

---

### Post by sdennie on 2009-08-15
Possibly.  Can you choose to disable one of the cards via BIOS?  If not, what is the output of:

```

lspci | grep VGA

```

It's possible to specify the device address in /etc/X11/xorg.conf so, if the two cards have different addresses, you may be able to force X to use the card you want.

---

### Post by Lokiii on 2009-08-15
Output:

```
02:00.0 VGA compatible controller: nVidia Corporation GeForce 9200M GS (rev a1)
03:00.0 VGA compatible controller: nVidia Corporation GeForce 9400M G (rev b1)

```

Thanks for the reply!

---

### Post by Francoisst on 2009-09-20
I'm interested into this also... When the xps 13 runs with both videocard the fan get noisy. 

I tried specifying the bus id of the 9200m and disabling the hybrid sli like this without any succes (can't start gdm):
```

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "keyboard"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    BusID	   "PCI:2:0:0"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "NoLogo" "True"
    Option         "SLI" "off"
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection

```

---

### Post by Francoisst on 2009-09-20
/var/log/Xorg.0.log
```

(EE) Sep 20 20:53:18 NVIDIA(GPU-1): Failed to initialize the NVIDIA graphics device PCI:2:0:0. 
(EE) Sep 20 20:53:18 NVIDIA(GPU-1):     Please check your system's kernel log for additional error
(EE) Sep 20 20:53:18 NVIDIA(GPU-1):     messages and refer to Chapter 8: Common Problems in the
(EE) Sep 20 20:53:18 NVIDIA(GPU-1):     README for additional information.
(EE) Sep 20 20:53:18 NVIDIA(GPU-1): Failed to initialize the NVIDIA graphics device!
(II) Sep 20 20:53:18 NVIDIA(0): Initialized GPU GART.
(II) Sep 20 20:53:18 NVIDIA(0): ACPI display change hotkey events enabled: the X server is new
(II) Sep 20 20:53:18 NVIDIA(0):     enough to receive ACPI display change hotkey events.
(II) Sep 20 20:53:18 NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Loading extension NV-GLX
(II) Sep 20 20:53:18 NVIDIA(0): Initialized OpenGL Acceleration
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) Sep 20 20:53:18 NVIDIA(0): Initialized X Rendering Acceleration

```



kern.log
```

Sep 20 20:53:18 xps-laptop kernel: [  125.406582] NVRM: RmInitAdapter failed! (0x31:0xffffffff:1039)
Sep 20 20:53:18 xps-laptop kernel: [  125.406587] NVRM: rm_init_adapter(0) failed

```

---

### Post by jezjones on 2009-09-30
Why disable the more powerful one?

---

### Post by Sephoroth on 2009-10-17
> **Lokiii said:**
> However, there must be possible to somehow configure it so that when you boot up only the integrated GPU (9200m) is active. Would it be possible to somehow blacklist the 9400m card?

You've got it wrong.  It is the 9400M G that is integrated and the 9200M GS (with 256MB GDDR3 RAM) that is discrete.  The only reason you might want the 9200M GS enabled is if you run many highly RAM-consume applications and wish to conserve as much of it as possible.

---

