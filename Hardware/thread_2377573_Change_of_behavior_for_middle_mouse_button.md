---
title: "Change of behavior for middle mouse button"
date: 2017-11-14
forum: Hardware
---

### Post by cjsmall on 2017-11-14
Running Xubuntu 17.10 with an Nvidia Quadro K4000 GPU.

I have a standard 3-button (Sun) mouse with no scroll-wheel.  The middle mouse button worked normally until I upgraded to Xubuntu 17.04, at which point the middle button started to act like a wheel.  Holding it down now causes content in all apps (browser, terminal, etc.) to scroll.  I have a number of programs that rely upon the middle button for motion commands and they are all broken now.  I have tried to resolve this for the past nine months without luck and was waiting to see if anything improved in 17.10, but no, it remains the same.

Note that middle-mouse button click does the normal past operation from the selection buffer.  It is mouse motion that must be freed from this scrolling function.

I desperately need to restore normal function to the middle button.  Can anyone provide pointers as to what changed and how to fix it?  Thanks for your help.

(I'm going to post this is a number of locations, so apologies if you see it more than once.)

---

### Post by cjsmall on 2017-11-14
I discovered the solution on another forum and am posting the answer here in the hope that it will aid others.

1: Run the command:

  # **xinput list**

&#9121; Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; HID 0430:0100                             id=9    [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Power Button                              id=6    [slave  keyboard (3)]
    &#8627; Power Button                              id=7    [slave  keyboard (3)]
    &#8627; Device 2Port KVMSwitcher                  id=8    [slave  keyboard (3)]
    &#8627; HID 0430:0005                             id=10   [slave  keyboard (3)]
  This identified the mouse as device id **9**.


  2: Run the command:
  # **xinput list-props 9**

Device 'HID 0430:0100':
    Device Enabled (153):   1
    Coordinate Transformation Matrix (155): 1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    libinput Accel Speed (287): 0.000000
    libinput Accel Speed Default (288): 0.000000
    libinput Accel Profiles Available (289):    1, 1
    libinput Accel Profile Enabled (290):   1, 0
    libinput Accel Profile Enabled Default (291):   1, 0
    libinput Natural Scrolling Enabled (292):   0
    libinput Natural Scrolling Enabled Default (293):   0
    libinput Send Events Modes Available (272): 1, 0
    libinput Send Events Mode Enabled (273):    0, 0
    libinput Send Events Mode Enabled Default (274):    0, 0
    libinput Left Handed Enabled (294): 0
    libinput Left Handed Enabled Default (295): 0
    libinput Scroll Methods Available (296):    0, 0, 1
    libinput Scroll Method Enabled (297):   0, 0, 1
    libinput Scroll Method Enabled Default (298):   0, 0, 1
    libinput Button Scrolling Button (299): 0
    libinput Button Scrolling Button Default (300): 2
    libinput Middle Emulation Enabled (301):    0
    libinput Middle Emulation Enabled Default (302):    0
    Device Node (275):  "/dev/input/event2"
    Device Product ID (276):    1072, 256
    libinput Drag Lock Buttons (303):   <no items>
    libinput Horizontal Scroll Enabled (304):   1

  The line that indicated that scrolling was active for the middle mouse button was:

  [B]    libinput Button Scrolling Button (299): 2


[/B]  3: As root, run the command:

  # [B]xinput set-prop 9 "libinput Button Scrolling Button" 0

[/B]  This sets the scrolling to the non-existent button #0.


  4: Now rerun the second command to verify the change:

  [B]    libinput Button Scrolling Button (299): 0

[/B]  Yep, it took.  Now, when I swipe the mouse, I have my old middle mouse button behavior back.


  5: Add the command in step #3 to the **~/.xstartup** file so that it is executed every time the window manager starts.

This should work if you are running the X server.  I'm unclear as to what happens with Wayland in 17.10.

---

