---
title: "display?"
date: 2008-09-02
forum: General Help
---

### Post by hp owner on 2008-09-02
hi i installed ubuntu on my laptop, and i only get part of my desktop, the only part i see up to is the applications bar to the user name.

---

### Post by EmanresuusernamE on 2008-09-02
Seems like your Ubuntu is using a virtual screen then.  Under the main menu, there should be a program called Screens.  Make sure your system is using the proper screen size/depths.

---

### Post by hp owner on 2008-09-02
> **EmanresuusernamE said:**
> Seems like your Ubuntu is using a virtual screen then.  Under the main menu, there should be a program called Screens.  Make sure your system is using the proper screen size/depths.

ok, i click on it, and down in the bottom were it shows open windows, it says starting "administ..." & "starting screens and..." and thats it. then they go away, and nothing happens

---

### Post by EmanresuusernamE on 2008-09-02
Try moving your mouse down to the lowest right hand corner of your screen, this should hopefully move the virtual screen down enough for you to see the window..... Or better yet, restart and boot into Ubuntu Failsafe mode, and tell it fix X server.

---

### Post by hp owner on 2008-09-02
> **EmanresuusernamE said:**
> Try moving your mouse down to the lowest right hand corner of your screen, this should hopefully move the virtual screen down enough for you to see the window..... Or better yet, restart and boot into Ubuntu Failsafe mode, and tell it fix X server.
the moving to lowest right corner didn't work, and how do you boot into failsafe mode? and do i type fix x server in the terminal?

---

### Post by hp owner on 2008-09-02
i typed in "displayconfig-gtk" in the terminal, and got this 


[CODE]

Traceback (most recent call last):
  File "/usr/bin/displayconfig-gtk", line 75, in <module>
    app = DisplayConfig(options)
  File "/usr/lib/python2.5/site-packages/displayconfiggtk/DisplayConfig.py", line 189, in __init__
    debug_scan_pci_filename=self.options.pcitable)
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 394, in __init__
    self._finalizeInit()
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 404, in _finalizeInit
    gfxcard._finalizeInit()
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 1123, in _finalizeInit
    screen._finalizeInit()
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 1588, in _finalizeInit
    (cw,ch,x,x) = self.x_live_screen.getSize()
  File "/var/lib/python-support/python2.5/xf86misc.py", line 77, in getSize
    return self.sizes[self.currentsizeid]
IndexError: list index out of range
[\CODE]

---

### Post by hp owner on 2008-09-02
any one?

---

### Post by EmanresuusernamE on 2008-09-03
Restart your computer, when it comes up with the boot loader, choose Ubuntu Failsafe.

---

### Post by sayakb on 2008-09-03
Goto System->Preferences->Screen Resolution and try lowering down the screen resolution.

Btw, please give descriptive titles to your thread (See forum DOs and DONTs). So rather than just "display", please write a brief description of what the thread is about.

---

### Post by EmanresuusernamE on 2008-09-03
> **LinuxIsInnovation said:**
> Goto System->Preferences->Screen Resolution and try lowering down the screen resolution.
Kinda pointless if he can't see the window that pops up.

Edit your:
/etc/X11/xorg.conf
See if you have an option in there called Virtual, if you do, but a # in front of that line to comment it out and give it a test.

Also, when you restart your computer, you should get a list before Ubuntu starts to load, choose the one that has Failsafe, or recovery mode in it.

---

### Post by hp owner on 2008-09-03
> **EmanresuusernamE said:**
> Kinda pointless if he can't see the window that pops up.

Edit your:
/etc/X11/xorg.conf
See if you have an option in there called Virtual, if you do, but a # in front of that line to comment it out and give it a test.

Also, when you restart your computer, you should get a list before Ubuntu starts to load, choose the one that has Failsafe, or recovery mode in it.
how do you edit that? also how do you take a screen shot? the resolution changing screens doesn't do any thing when it starts

---

### Post by hp owner on 2008-09-03
here is a screen shot of the monitor resolution settings. i cant edit any thing. also i put it to were the screen ends for me

[http://i211.photobucket.com/albums/bb190/tmaxx15/Screenshot.png](http://i211.photobucket.com/albums/bb190/tmaxx15/Screenshot.png)

---

### Post by hp owner on 2008-09-03
bump, i would really like to fix this issue

---

### Post by hp owner on 2008-09-04
come on people i know one of you has to know how to fix this. also with that screen shot, i took it to photo shop on my other computer that the resolution is 1080x768

---

### Post by hp owner on 2008-09-04
i guess none of you can help me, so im just going to delete ununtu, and run xp again.

---

