---
title: "Tablet"
date: 2009-11-09
forum: Hardware
---

### Post by Anonymousable on 2009-11-09
I have a  (rather old) Logitech LT9395 USB tablet. It works when attached (It doesn't when not for some reason :P ), but for some reason I can't simulate a left-click. Right-clicking works (using the button on the side of the pen), but I don't know how to make a normal left click.

Any ideas?

Thanks in advance.

---

### Post by Anonymousable on 2009-11-10
Additionally, it doesn't work on resolutions higher than 1024x768... Is this an unfixable (i.e. hardware) problem, or is it not configured correctly?

And if anyone could help with the left-click problem, I'd be very grateful...

---

### Post by Favux on 2009-11-10
Hi Anonymousable,

Don't know if this will help but you could take a look at this [post]("http://ubuntuforums.org/showpost.php?p=7727817&postcount=70").  The link in it may be useful.

---

### Post by Anonymousable on 2009-11-10
I'm not sure about what the commands you gave me would do, so I looked at xinput's manpage, then used xinput test...
It recieves only motion information, no pressure or button information, which, I guess, would explain it. Any ideas? Thanks in advance.

Additionally, after resetting the screen resolution to 1280x1024, it still worked. One problem solved :D

---

### Post by Favux on 2009-11-10
Hi Anonymousable,

I don't know what driver your tablet uses.  Did you ever have it working in a previous version of Ubuntu/linux?

We could try to figure out what driver has it now.  In a terminal:
```
xinput --list
```
And look at Xorg.0.log.

---

### Post by Anonymousable on 2009-11-10
```
(II) config/hal: Adding input device Aiptek
(**) Aiptek: always reports core events
(**) Aiptek: Device: "/dev/input/event14"
(II) Aiptek: Found 3 mouse buttons
(II) Aiptek: Found x and y relative axes
(II) Aiptek: Found scroll wheel(s)
(II) Aiptek: Found x and y absolute axes
(II) Aiptek: Found absolute touchpad
(II) Aiptek: Found keys
(II) Aiptek: Configuring as touchpad
(II) Aiptek: Configuring as keyboard
(**) Aiptek: YAxisMapping: buttons 4 and 5
(**) Aiptek: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Aiptek" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "compaqeak8"
(**) Option "xkb_layout" "gb"
(**) Option "xkb_options" "grp:alts_toggle"
(WW) Aiptek: touchpads and touchscreens ignore relative axes.
(**) Aiptek: (accel) keeping acceleration scheme 1
(**) Aiptek: (accel) filter chain progression: 2.00
(**) Aiptek: (accel) filter stage 0: 20.00 ms
(**) Aiptek: (accel) set acceleration profile 0
(II) Aiptek: initialized for absolute axes.

```
That's the (probably) relevant section, but I have no idea what any of it means.

---

### Post by Favux on 2009-11-10
Hi Anonymousable,

Ok, it looks like it's a rebranded Aiptek tablet.  So you'll want to use the Aiptek drivers.  You could double check with "lsusb" and "cat /sys/bus/usb/devices/*/product"

Use Synaptic Package Manager to install the Aiptek driver.  The .fdi should automatically be installed.  If it isn't, on the same thread I linked you to we played with an [aiptek.fdi]("http://ubuntuforums.org/showpost.php?p=7604483&postcount=50").

By the way which version of Ubuntu are you using?

---

### Post by Anonymousable on 2009-11-10
9.10 :)

Thanks, but A: I don't think it installed the aiptek.fdi file
B: I don't know where to put it.

---

### Post by Favux on 2009-11-10
Hi Anonymousable,

Did you reboot?  Well do a search to make sure.  Or again check "xinput --list" and Xorg.0.log.  It's in the .fdi post I linked you to.  Use:
```
gksudo gedit /etc/hal/fdi/policy/10-aiptek.fdi
```
Copy and paste the .fdi in the empty file.  Save, close, and reboot.

---

### Post by Anonymousable on 2009-11-10
No, I haven't rebooted yet. I thought the fdi file would be installed along with the package. I'll reboot now though, and see if it works then. Thanks for the help so far :)

---

### Post by Anonymousable on 2009-11-10
UPDATE: Nope... Button clicks and pressure data is still not recieved. And there is no file anywhere called aiptek.fdi.

---

### Post by Favux on 2009-11-10
Alright.  You can try installing the one I linked you to.  There's the original one near the beginning of the thread.  I think it's the same as the other ones floating around.

---

### Post by Anonymousable on 2009-11-10
Trying it now, thanks.

---

### Post by Anonymousable on 2009-11-10
UPDATE. I've put the file in. Now, left-clicks don't work while the tablet is connected (It simulates constant pressing of the left mouse button, and releasing it only works by repeatedly bashing the tablet several times hard with the stylus). Removing the tablet crashes the X server. In short, it doesn't work.

And I'm going to bed now. Thanks for all the help, I'll try to fix it tomorrow.

---

### Post by Favux on 2009-11-10
Hi Anonymousable,

Well, a couple of things.

Make sure the aiptek.ko (kernel driver/module) is loading, i.e. appearing in "lsmod".  It should show up as aiptek.  Or:
```
lsmod | grep [Aa]iptek
```

Also as I remember your stylus uses a battery.  When was the last time the battery was replaced?

---

### Post by Anonymousable on 2009-11-11
About the battery: Yesterday... It was the first solution I came up with.

About the kernel module... It looks like it does get loaded, but only once the tablet is plugged in. I assume that this is the normal behaviour. I think that the click problem is due to an axis inversion (pressure problem) - Any ideas how to fix that?

---

### Post by Anonymousable on 2009-11-11
I think the pressure axis is being inverted... Any ideas how to reverse it?

---

### Post by Favux on 2009-11-11
Hi Anonymousable,

These four lines in the .fdi involve pressure:
```
        <merge key="input.x11_options.zMin" type="string">0</merge>
        <merge key="input.x11_options.zMax" type="string">511</merge>
        <merge key="input.x11_options.ZThreshold" type="string">5</merge>
        <merge key="input.x11_options.Pressure" type="string">linear</merge>

```
Notice it's setup up for having 512 levels of pressure.  If you had 1024 it would change to 1023 for zMax.  The last two lines may not be needed.  You could try commenting out all four of the lines, reboot and see what "xinput --list" and Xorg.0.log tell you.  They may show values for your tablet which you could plug back into the .fdi.

---

### Post by Anonymousable on 2009-11-11
Thanks...

But what do they do? Specifically the threshold value.

---

### Post by Favux on 2009-11-11
Hi Anonymousable,

That should be the minimum pressure necessary to trigger a response.  I think someone said there was a manual for Aiptek, so try:
```
man aiptek
```
and see if it pops up.

---

### Post by Anonymousable on 2009-11-11
Thanks. "man aiptek" gives information about how to use it with XOrg.conf, so it's not what I'm looking for.

The threshold is the right thing, I think. Thanks for the help :)

---

### Post by Anonymousable on 2009-11-12
UPDATE: It works now, thanks for the help. Is there, however, any way to completely "unbind" it from the X server, i.e. make it not even move the mouse? I want to use it ONLY to feed input to the GIMP.

Also, it still crashes the X server when unplugged. Is there any way to fix this (other than disabling it, obviously)?

---

### Post by Favux on 2009-11-12
Hi Anonymousable,

Great!  You're welcome.

> Is there, however, any way to completely "unbind" it from the X server, i.e. make it not even move the mouse? I want to use it ONLY to feed input to the GIMP.
I don't think that's possible.  The aiptek.ko is probably taking the raw data in the kernel from the input on the pci usb by-path and translating it to system data.  Then it passes it to Xinput/Xserver where probably some aiptek driver, call it aiptek_drv.so, takes over.  Then Gimp can get it's input.

> Also, it still crashes the X server when unplugged. Is there any way to fix this (other than disabling it, obviously)?
That was happening on the other thread with the .fdi I linked you too.  My guess is it's a bug with the Aiptek driver(s).  You should search launchpad for bug reports on the Aiptek.  Confirm the ones you can or post a new one if there aren't any relevant.  You could also look for the original Aiptek driver site and post bugs there.

---

### Post by Anonymousable on 2009-11-12
> **Favux said:**
> Hi Anonymousable,
I don't think that's possible.  The aiptek.ko is probably taking the raw data in the kernel from the input on the pci usb by-path and translating it to system data.  Then it passes it to Xinput/Xserver where probably some aiptek driver, call it aiptek_drv.so, takes over.  Then Gimp can get it's input.
Well... GIMP has its "cursor" which is moved using the tablet completely seperately from the mouse cursor... So I don't know.

---

### Post by Favux on 2009-11-12
Hi Anonymousable,

You could be right.  I'm hardly an expert.  If you figure it out I'd love to hear about it.

---

### Post by Anonymousable on 2009-11-12
OK, thanks... I'll meddle with XOrg.conf a little :)

---

### Post by Anonymousable on 2009-11-14
> **Anonymousable said:**
> OK, thanks... I'll meddle with XOrg.conf a little :)
UPDATE: I haven't found a way to disable the tablet, but NOT remove it from /dev/input. Any ideas? Thanks in advance.

---

