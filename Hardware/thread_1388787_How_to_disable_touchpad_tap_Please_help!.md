---
title: "How to disable touchpad tap? Please help!"
date: 2010-01-23
forum: Hardware
---

### Post by homesickalien on 2010-01-23
Hi,

I desperately need to disable the touchpad tap on my laptop.  It's almost unusable as the cursor just keeps hopping around the screen as I type.  I have searched all over the forums and google.  I have found many posts which ended with no solution and others where the solution did not fix my problem.

I have a Dell XPS M1530 laptop.  I have had Ubuntu installed since 8.04 and was always successfully able to disable the tap using xorg.conf in the past, but that no longer works in 9.10 Karmic.  So, I have also tried the HAL approach with no luck either.  In System | Preferences | Mouse, I have no touchpad tab on which to disable the tap, and the System | Preferences | Touchpad will not open saying that SHMConfig must be = True in xorg.conf.  I have tried enabling that feature in both xorg.conf and Hal with no luck.  Some posts have suggested to use SHMconfig = true, others suggested SHMConfig = "on".  I have tried both ways and upper, lower and proper case (True true TRUE On ON on, etc.).

Can someone please help me out here?  I have way too much time invested to reinstall the OS now.  

Here are my config files:

xorg.conf (/etc/X11/xorg.conf)

Section "InputDevice"

    # generated from default
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Protocol" "auto-dev"
    Option         "Device" "/dev/psaux"
    Option         "HorizEdgeScroll" "0"
    Option         "SHMConfig" "true"
    Option       "MaxTapTime" "0"
    Option       "tapbutton1" "0"    
    Option       "SHMConfig" "Yes"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    SubSection     "Display"
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection

and the HAL (/etc/hal/fdi/policy/shmconfig.fdi :)

<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
  <device>
    <match key="input.x11_driver" string="synaptics">
      <merge key="input.x11_options.SHMConfig" type="string">true</merge>
    <merge key="input.x11_options.MaxTapMove" type="string">0</merge>
    <merge key="input.x11_options.TapButton1" type="string">0</merge>
    <merge key="input.x11_options.TapButton2" type="string">0</merge>
    <merge key="input.x11_options.TapButton3" type="string">0</merge>
    </match>
  </device>
</deviceinfo>

Thanks in advance to anyone who can help me solve this!

Thanks

---

### Post by nishant.singh28 on 2010-01-23
Try gsynaptics

---

### Post by homesickalien on 2010-01-23
gsynaptics *is* System | Preferences | Touchpad, and that doesn't work.  I get the SHMConfig error mentioned in my post.

Also, I do not have a "Touchpad" tab under System | Preferences | Mouse.

This is why other forum threads have not yet helped me.  The only solution I have found for this issue so far is reinstalling the OS.  Should it really require that?

I had to reposition my mouse cursor about 5 or 6 times, just trying to reply to this message!

---

### Post by pi/roman on 2010-01-24
You should be able to temporarily disable tapping by using synclient:
synclient tapbutton1=0

Then find your 11-x11-synaptics.fdi configuration file:
locate 11-x11-synaptics.fdi

and make sure to include these:
<merge key="input.x11_options.SHMConfig" type="string">true</merge>
<merge key="input.x11_options.TapButton1" type="string">0</merge>

Then edit your xorg.conf and delete the "InputDevice" section because it will conflict with your HAL configuration.

---

### Post by djurny on 2010-01-24
following p.o.c. (piece of code ;)) will set all parameters having 'tap' or 'Tap' in their name to zero.. i personally use this to disable tap on my dell 1525.. :)

```

synclient $(synclient -l | awk '/[Tt]ap/ { print $1 "=0" }')

```

the most neat method is using the synapctics .fdi file as previous poster indicated..

---

