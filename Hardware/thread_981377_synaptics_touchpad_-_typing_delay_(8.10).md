---
title: "synaptics touchpad - typing delay? (8.10)"
date: 2008-11-13
forum: Hardware
---

### Post by HankB on 2008-11-13
Hi folks,
I desperately need to enable typing delay with a synaptics touchpad. Palm detection would also work, but I don't know how to configure that.

I have installed touchfreeze and it seems to do nothing. GSynaptics fails to start with "```
GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics
``` Likewise with synclient:
```
hbarta@baobab:~$ synclient -l
Can't access shared memory area. SHMConfig disabled?
hbarta@baobab:~$ 

```

I have added the following in /etc/X11/xorg.conf
```
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
        Option          "SHMConfig"             "on"
EndSection
```

both before and after 
```
Section "Device"
        Identifier      "Configured Video Device"
EndSection
```

In  /var/log/Xorg.0.log I find:
```
(==) Using config file: "/etc/X11/xorg.conf"
  .
  .
  .
(II) config/hal: Adding input device SynPS/2 Synaptics TouchPad
(II) LoadModule: "synaptics"

(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
        compiled for 1.5.2, module version = 0.15.2
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 2.1
(II) Synaptics touchpad driver version 0.15.2
(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
(**) Option "Device" "/dev/input/event8"
(--) SynPS/2 Synaptics TouchPad touchpad found
(**) SynPS/2 Synaptics TouchPad: always reports core events
(II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
(--) SynPS/2 Synaptics TouchPad touchpad found
```

I find no mention of SHMConfig and cannot find any warnings or errors related to the config file, but have to note that the config file is a lot *lot* smaller than it used to be, so either more things are autoconfigured or there is configuration information located elsewhere.

I would really appreciate help getting this configured properly as touching the pad during typing puts the cursor other than where it belongs and makes my ramblings even less intelligible.

thanks,
hank

---

### Post by HankB on 2008-11-15
If no one knows the direct answer to this one, I would very much appreciate pointers on where else to look. Typing and getting it scrambled because the cursor jumps around every time I get close to the touch pad is maddening. :confused:

thanks,
hank

---

### Post by estamand on 2008-11-15
HankB,

Try disabling tapping feature that way it doesn't 'click'

---

### Post by Yezinki on 2008-11-15
Disable/uninstall synaptic driver.....

---

### Post by HankB on 2008-11-15
> **estamand said:**
> HankB,
Try disabling tapping feature that way it doesn't 'click'

:( Then I have to go back to clicking on the buttons. I rather like tapping on the touch pad. 


> **Yezinki said:**
> Disable/uninstall synaptic driver.....
Then I lose all synaptic features.

Thanks for the suggestions, but both of these are rather a disappointment. I've had the synaptic touchpad working with full functionality since I first installed Ubuntu on this laptop in 2005. It seems rather a disappointment that I cannot continue with full H/W support. In this regard 8.10 seems a bit of a step back.

thanks,
hank

---

### Post by mannheim on 2008-11-16
Maybe [this post]("http://ph.ubuntuforums.com/showpost.php?p=5927284&postcount=1") is relevant.

---

### Post by HankB on 2008-11-17
> **mannheim said:**
> Maybe [this post]("http://ph.ubuntuforums.com/showpost.php?p=5927284&postcount=1") is relevant.
Thanks for the tip. I tried it but it didn't seem to make any difference in getting SHNConfig set.

best,
hank

---

