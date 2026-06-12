---
title: "Laptop screen problems."
date: 2008-07-13
forum: Hardware
---

### Post by jeremywitt on 2008-07-13
First I have to say that I am a complete newbie to Linux.

I jumped into the deep end by completely formatting windows and installing Ubuntu 8.04 without any knowledge of Linux. That was last week and I have been using it without problems and having fun learning (slowly) the cool things about the OS.

I ran into a problem today. I went to hook up my projector and it didn't work, so I did some research and eventually got it to work (kind of) by installing a program using:
[I]sudo apt-get install kde-guidance
gksudo displayconfig-gtk[/I]

then:
running through the GUI of that program I set up the projector by setting the Screen 2 options to:
[I]Model: Monitor 1280x1024 (manufacturer set to Generic)
Resolution: 1280x1024 at 75 Hz[/I]

After rebooting the projector worked perfectly but my laptop screen is not right.
First it was displaying very large, I'm guessing 640x480. So I logged in and used:
*gksudo displayconfig-gtk*

I looked for the Model/Manufacturer under Dell but it wasn't available for my particular screen. So I set it to:
[I]Model: LCD Panel 1440x900 (widescreen) (Generic)
Resolution: 1440x900 at 50Hz[/I]

Reboot...
Now the resolution looks good but the "desktop" is larger than the screen. For example, when I move my cursor to the edge of the screen it scrolls over to display the rest of the "desktop".

So I went back into the displayconfig-gtk and attempted to have the program 'detect' my display... it decides "plug and play" (which is what it was set to before I set the projector up), when I hit the ok button it drops back into the terminal and displays:

-----------------------------------------------------------------------
[B][]
  File "/usr/lib/python2.5/site-packages/displayconfiggtk/DisplayConfig.py", line 690, in on_configure_device_clicked
    device.setMonitorAspect(ModeLine.ASPECT_16_9)
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 1810, in setMonitorAspect
    self._resyncResolution()
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 1817, in _resyncResolution
    (preferred_width,preferred_height) = self.getAvailableResolutions()[-1]
IndexError: list index out of range
Failed to get preferred width, height, or rate - Assuming none. IndexError:  list index out of range
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/displayconfiggtk/DisplayConfig.py", line 1033, in on_button_apply_clicked
    self.apply_changes()
  File "/usr/lib/python2.5/site-packages/displayconfiggtk/DisplayConfig.py", line 1103, in apply_changes
    self.xsetup.writeXorgConfig(tmpfilename)
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 702, in writeXorgConfig
    self._syncXorgConfig()
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 653, in _syncXorgConfig
    gfxcard._syncXorgConfig()
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 1470, in _syncXorgConfig
    self.screens[i]._syncXorgConfig(self.x_device[i])
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 2357, in _syncXorgConfig
    mode_list_line.extend([ mode_list[mode_index].getName() for mode_index in mode_indexes ])
IndexError: list index out of range[/B]
----------------------------------------------------------------------

If anyone could give me some advice I would appreciate it... I did try to research and fix myself, but I'm a complete newbie and suck at Linux.

Thank you,
Jeremy Witt
[email]jeremywitt@msn.com[/email]

---

### Post by kahlil88 on 2008-07-13
If the desktop is larger than the display area, you probably need to use a different resolution, possibly with a different aspect ratio.

---

### Post by jeremywitt on 2008-07-13
Thank you Kahlil88, I changed my resolution to 1280x800 and the screen looks great now.

The only problem with this is that my screen is suppose to be 1440x900... at least that was the setting when I was using Vista.

Any idea why the resolution is lower using Ubuntu?

---

### Post by matt$2 on 2008-07-13
That is probably right.  My nvidia card peaked at 1280 x 1024.
On Windows it would go much finer.  Don't know how or why.  Just experiment and see if that setting is where it peaks for Ubuntu and it will probably be a limitation to live with.

---

