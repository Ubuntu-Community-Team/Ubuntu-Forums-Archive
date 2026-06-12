---
title: "Synaptics multi finger _clicks_"
date: 2008-04-22
forum: Hardware
---

### Post by Who on 2008-04-22
Hi all,

I want to do multi finger + click remapping on a Snaptics touchpad - for example
Two finger on touchpad + Button 1 --> Button 3

I already have 
"tap two fingers on pad" --> Button 3 (using     
Option         "TapButton2" "3"    )

I have tried 
    Option         "TwoFingerButton1" "3"

and 
    Option         "MultiFingerButton1" "3"


But no love.

I _think_ I had it working on the WUBI install I did before I did this real install, and forgot to save the xorg.conf - but I can't make it work now, so perhaps I was dreaming at the time!

Thanks for any help,

Who

---

### Post by nnutter on 2009-05-02
Though this post is ancient I figured I'd answer it anyway as I discovered upon trying to solve the same problem (four years later, lol).

The old way would be to put the following in your _/etc/X11/xorg.conf_.

```

Option "ClickFinger2" "3"

```

The new way would be to create a HAL policy file _/etc/hal/fdi/policy/11-x11-synaptics.fdi_.

```

<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input.touchpad">
        <merge key="input.x11_driver" type="string">synaptics</merge>
        <!-- Arbitrary options can be passed to the driver using
             the input.x11_options property since xorg-server-1.5. -->
        <!-- EXAMPLE:
        <merge key="input.x11_options.LeftEdge" type="string">120</merge>
        -->
	<merge key="input.x11_options.ClickFinger1" type="string">1</merge>
        <merge key="input.x11_options.ClickFinger2" type="string">3</merge>
        <merge key="input.x11_options.ClickFinger3" type="string">2</merge>
    </match>
  </device>
</deviceinfo>

```

---

