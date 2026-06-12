---
title: "Alps Dualpoint: unable to use middle button"
date: 2012-06-11
forum: Hardware
---

### Post by duststorm on 2012-06-11
I have an "AlpsPS/2 ALPS DualPoint TouchPad" touchpad device and "Alps DualPoint Stick" in my Dell Latitude E6510, running ubuntu 12.04. I must say the driver has come along quite well: almost everything about it works very nicely, even two-finger scrolling.

My problem with it is that I cannot use the middle mouse button of it in Blender or gimp. It does work for X pasting however.

This is what the touchpad looks like:
[IMG]http://www.notebookcheck.nl/uploads/pics/dell_latitude_e6400_touchpad_06.jpg[/IMG]
There are actually 5 mouse buttons, but they (should) map to 3 physical mouse buttons (a regular 3 button mouse).

The middle mouse button doesn't work in applications like Blender or gimp. Funnily enough, in chromium it works (it closes tabs).
Also xev shows a "button 2" event when clicking it, and the fact that pasting works shows that the button press is recognized.

Could  it be the paste function that is canceling out further use of the button in other applications? Or can it have something to do with the driver? I really don't know what the cause is.
Strangely enough, if I remap the middle mouse button to another one, for example the right, it works in other applications.


Did someone have the same problem and have a solution? I don't really know where to look next.

---

### Post by duststorm on 2012-07-09
I think I found out the cause of my issue.
It's caused by the fact that the touchpad is controlled by the synaptics driver, but the stick and its associated buttons (the 3 button mouse) are still controlled by the xev generic driver.

The middle mouse button actually works, but I can't move the mouse with the touchpad while holding it (what you would do for panning in gimp or moving the camera in blender). It does work if I move the mouse using the stick. In other words, I cant combine mouse movement and buttons of different mouses. It's confusing however as they are integrated on the laptop as if they were one device.

This was no problem on my previous ubuntu 10.04 installation as there was no synaptics driver for the touchpad available at that time. Both devices used the generic driver, and hence combining buttons worked.

The solution to my problem is disabling the synaptics driver for the touchpad, but then I lose scrolling and palm detection. Or I can only use the stick together with the middle button.

Is it possible to switch input drivers for the touchpad on the fly? If so I could switch driver (for example with a shortcut or bash alias) when I work with Blender or Gimp.

Or I could use an external mouse.

---

### Post by tasuki on 2012-08-28
Duststorm, I had the same problem and this was the first thread I found. We're not the only ones, there's even one guy with a solution (which worked for me):

Edit "/usr/share/X11/xorg.conf.d/11-evdev-trackpoint.conf", and change the Option "EmulateWheel" to "false". [[source]]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/897131/comments/24")

---

### Post by duststorm on 2012-09-03
> **tasuki said:**
> Edit "/usr/share/X11/xorg.conf.d/11-evdev-trackpoint.conf", and change the Option "EmulateWheel" to "false". [[source]]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/897131/comments/24")

That's it! Thanks a million for helping me to the solution.
So in the end it was a fancy setting for the non-alps pointing device that was enabled. I must say I didn't really notice that it was meant for scrolling.

And then to think I have had that config file open in a text editor as well. ;)

Now I can use blender again without an external mouse.

---

