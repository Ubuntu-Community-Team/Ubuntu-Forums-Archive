---
title: "configuration for Magic Mouse Multitouch in maverick meerkat"
date: 2010-10-13
forum: Hardware
---

### Post by Rahmenlos on 2010-10-13
Is there a way to configure Apple's Magic Mouse's behavior in Maverick Meerkat? The new Multitouch support is nice and whatnot but thanks to that It's a torture to use it.

I have to be really careful to not touch the mouse with my palm otherwise I accidentally make a mouse click. That's not really how it should work as a default thing. And I really can't find anything to disable or at least configure the multitouch - the scrolling-multitouch is a good thing, just not the tapping on the mouse itself without physically clicking the mouse-"button".

Thanks in advance.

---

### Post by MountainX on 2010-10-13
I would like to know the same info. My MagicMouse moves the cursor much too fast, but scrolling is far too slow. I can't adjust Mouse Preferences because they are perfect for my main mouse as they are. So I need to set the behavior for just the MagicMouse somehow.

---

### Post by MountainX on 2010-10-13
I found some properties for my Magic Mouse. Now the challenge is how to write udev rules that will reset the correct properties as we wish them to be. I have no idea at the moment...

```
/dev/input$ xinput list-props 12
Device 'Magic Mouse':
    Device Enabled (121):    1
    Coordinate Transformation Matrix (123):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (244):    0
    Device Accel Constant Deceleration (245):    1.000000
    Device Accel Adaptive Deceleration (246):    1.000000
    Device Accel Velocity Scaling (247):    10.000000
    Evdev Reopen Attempts (238):    10
    Evdev Axis Inversion (248):    0, 0
    Evdev Axes Swap (250):    0
    Axis Labels (251):    "Rel X" (131), "Rel Y" (132)
    Button Labels (252):    "Button Left" (124), "Button Middle" (125), "Button Right" (126), "Button Wheel Up" (127), "Button Wheel Down" (128), "Button Horiz Wheel Left" (129), "Button Horiz Wheel Right" (130)
    Evdev Middle Button Emulation (253):    2
    Evdev Middle Button Timeout (254):    50
    Evdev Wheel Emulation (255):    0
    Evdev Wheel Emulation Axes (256):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (257):    10
    Evdev Wheel Emulation Timeout (258):    200
    Evdev Wheel Emulation Button (259):    4
    Evdev Drag Lock Buttons (260):    0
```

---

### Post by MountainX on 2010-10-13
maybe this is worth a try... I'm not sure if it will work yet...

put this in a file at: /etc/udev/rules.d/magicmouse.rules
```


# to check a new device on e.g., MagicMouse:
# # udevadm info -a -p $(udevadm info -q path -n /dev/input/by-id/YOUR_MOUSE)

ACTION!="add|change", GOTO="xorg_local_end"
        KERNEL!="event*", GOTO="xorg_local_end"
        ATTRS{uniq}!="YOUR_MOUSE_ID", GOTO="xorg_local_end"

        ENV{x11_options.DeviceAccelVelocityScaling}="0"
        ENV{x11_options.WheelEmulationInertia}="100"
         
LABEL="xorg_local_end"
```

---

### Post by Rahmenlos on 2010-10-13
is this for **your** problem with the different scrolling and cursor speed settings or **my** problem with the multitouch tap-clicking (instead of only physical clicking)? :confused:

---

### Post by MountainX on 2010-10-13
Here's a way that worked for me:

I reduced my acceleration for my MagicMouse from 4 to 0.5 using xinput as shown here:
```
# xinput get-feedbacks 12
1 feedback class
PtrFeedbackClass id=0
    accelNum is 4
    accelDenom is 1
    threshold is 4

    
# xinput set-ptr-feedback 12 4 1 2
# xinput get-feedbacks 12
1 feedback class
PtrFeedbackClass id=0
    accelNum is 1
    accelDenom is 2
    threshold is 4
```

---

### Post by MountainX on 2010-10-13
> **Rahmenlos said:**
> is this for **your** problem with the different scrolling and cursor speed settings or **my** problem with the multitouch tap-clicking (instead of only physical clicking)? :confused:

Yeah, sorry about that. I should have posted this info somewhere else. Maybe a moderator can move it all. That was bad of me to hijack your thread. I did not intend to do it. At first I thought a bump on your thread might help you get a response. But then I got carried away with the research on my problem. I should not have posted all that here.

---

### Post by lunkan on 2010-10-17
> **Rahmenlos said:**
> Is there a way to configure Apple's Magic Mouse's behavior in Maverick Meerkat? The new Multitouch support is nice and whatnot but thanks to that It's a torture to use it.

I have to be really careful to not touch the mouse with my palm otherwise I accidentally make a mouse click. That's not really how it should work as a default thing. And I really can't find anything to disable or at least configure the multitouch - the scrolling-multitouch is a good thing, just not the tapping on the mouse itself without physically clicking the mouse-"button".

Thanks in advance.

Hi! I'm also have the same problem as you Rahmenlos. It's very irritating that you can't have your fingers on the mouse, oops  and you have clicked somewhere. Hope someone has a solution.

---

### Post by lunkan on 2010-10-22
Solved, latest ubuntu updates disables "touch click right and left" on magic mouse.

---

### Post by droewors on 2010-10-26
> **lunkan said:**
> Solved, latest ubuntu updates disables "touch click right and left" on magic mouse.

Is this a configuration option (that I can'find)?
My meerkat install is up to date and it still occurs (though no proposed (beta) or backports installed)
Could you be a bit more specific with your solution?
Thanks

---

### Post by growlhero on 2010-10-28
Hi,

I don't know if this helps anyone but I was having trouble with the middle mouse copy paste command being initiated when i accidentally clicked too close to the middle of the mouse, which made, among other things Minecraft acting funny and me opening links in a different tab instead of the same tab.

To fix this I did this:

> xinput list | grep 'id=' //find id of magic mouse
xinput get-button-map (magic mouse id)// shows all the buttons mapped to the mouse
xinput set-button-map (magic mouse id) 1 0 3 // turns of middle mouse button

Found the directions somewhere else but I thought that this should be here to for people having trouble with the new magic mouse behavior in 10.10

---

### Post by Neolo on 2010-10-28
Omg!!! Give somebody solution for this stupid tap-to-click! This thing unuseable! I just on fresh install of 10.10 and Aplle Magic out of box, updates are not fixed this crap. :mad:

---

### Post by Rahmenlos on 2010-10-28
It would be the best to come up with an additional preferences tab in the mouse settings for the mutlitouch stuff - to enable/disable tap-to-click, third mouse button and regulate scrolling/cursor speed. That way not everyone is forced to use one setting OR the other.

---

### Post by MountainX on 2010-10-31
> **Rahmenlos said:**
> It would be the best to come up with an additional preferences tab in the mouse settings for the mutlitouch stuff - to enable/disable tap-to-click, third mouse button and regulate scrolling/cursor speed. That way not everyone is forced to use one setting OR the other.

I agree. I had to finally quit using Ubuntu and the Magic Mouse together. They don't work right together. :(

---

