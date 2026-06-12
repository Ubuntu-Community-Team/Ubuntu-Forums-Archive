---
title: "Disable LockedDrags on touchpad"
date: 2010-01-26
forum: Hardware
---

### Post by sumi76 on 2010-01-26
Hi Folks,

I'm struggling to find a way to disable the annoying locked drags (a.k.a. locked click) option on my Acer TravelMate 290, touchpad: AlpsPS/2 ALPS GlidePoint, Synaptics driver.

I've installed gpointing-device-settings, it is disabled there, and the same shows up in the terminal:
```

~$ xinput list-props "AlpsPS/2 ALPS GlidePoint"
Device 'AlpsPS/2 ALPS GlidePoint':
    Device Enabled (96):    1
    ...
    Synaptics Tap FastTap (291):    1
    ...
    Synaptics Locked Drags (307):    0
    Synaptics Locked Drags Timeout (306):    5000
    ...
```Despite the fact that it seems to be disabled locked drag is still working. The strange thing is, that fast tapping set by gpointing is working, so gpointing is not entirely useless.

I've tried to edit the corresponding .fdi file:

/usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi

by adding:
```
<merge key="input.x11_options.LockedDrags" type="string">false</merge>
```but it didn't change anything. I don't actually see how the .fdi file is taking care of the settings as it supposed to be in Karmic, 'cose it's pretty empty... (my xorg.conf file has no input device section at all)

Any thoughts?

---

### Post by sumi76 on 2010-02-03
There are a few more things to this.

I was playing around with the 11-x11-synaptics.fdi file and checking the results.

The only thing I was able to achieve is to enable SHMConfig.
Other settings don't take effect, don't even show up if I check it in the terminal using xinput or synaptics commands. I'm only able to change them using xinput or synaptics (except for the very few in the gsynaptics GUI), but some of them have no effect at all.

e.g.: edge scrolling, fast tapping can be switched on-off, however two finger scrolling, locked drags remain always as they were: locked drags is on, no matter what is set, two finger scroll is off, even though it supposed to be on.

It seems that touchpad issues are quite a plague. I was searching for similar ones on the forum and many of them are unsolved or not even replied to...

Is out there a different driver maybe?

---

### Post by IcarusR on 2010-02-03
Checkout the synaptics manual

```
man synaptics
```

>  Option "LockedDrags" "boolean"
              If  off,  a  tap  and  drag  gesture  ends when you release the finger.  If on, the gesture is active until you tap a second time, or until
              LockedDragTimeout expires.

Loads of options listed there, add to xorg.conf.

---

### Post by sumi76 on 2010-02-05
Icarus,

thanks for the reply! Actually I was hoping to be able to turn it off, since it keeps dragging my folders all over the place. 
I guess I can set the time out to 0.
xorg.conf? I thought HAL takes care of this in Karmic...

---

### Post by IcarusR on 2010-02-07
Yes HAL does do it in Karmic. As far as I'm aware you can have both.

Some info on configuring to use HAL
[https://wiki.ubuntu.com/X/Config/Input#Input%20Configuration%20with%20HAL]("https://wiki.ubuntu.com/X/Config/Input#Input%20Configuration%20with%20HAL")

---

