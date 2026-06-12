---
title: "Lost displayconfig control module in Kubuntu"
date: 2007-10-17
forum: Hardware &amp; Laptops
---

### Post by mattigras on 2007-10-17
I'm running Kubuntu Feisty on an Acer Aspire 5570

"K"->"System Settings"->"Monitor & Display" *was* working fine straight out of the box, but now I'm getting the "The module Display & Monitor could not be loaded" screen. I noticed the problem after fooling around with my xorg.conf while trying to enable Xinerama. (which still doesn't work quite right and is currently disabled). Even if I reload my original vanilla xorg.conf, it still doesn't load in System Settings.

The module still runs and functions correctly if I run ```
$ displayconfig #with or without kdesu
``` from the Konsole, so it's not that big of a deal, but I hate having broken stuff.

Here's the output of $ kcmshell displayconfig
```


Pythonize constructor -- pid = 6467
Python interpreter initialized!



Pythonize constructor -- pid = 6467
Traceback (most recent call last):
  File "<string>", line 8, in kcontrol_bridge_create_displayconfig
NameError: global name 'create_displayconfig' is not defined
Error in sys.excepthook:
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/apport_python_hook.py", line 44, in apport_excepthook
    binary = os.path.realpath(os.path.join(os.getcwdu(), sys.argv[0]))
AttributeError: 'module' object has no attribute 'argv'

Original exception was:
Traceback (most recent call last):
  File "<string>", line 8, in kcontrol_bridge_create_displayconfig
NameError: global name 'create_displayconfig' is not defined
error: *** runFunction failure
;

```

Possible reasons given:
"KDE upgrade leaving an orphaned control module" -- I noticed the problem after attempting xinerama, pretty sure I haven't upgraded any portions of KDE.

"You have old third party modules laying around." -- Did it break because I installed displayconfig-gtk? Next I'll try uninstalling and see if that works.

I don't think this is a case of that old bug where Python wouldn't load the unusual xinerama resolutions, I'm currently running 1280x800.

Anybody have any ideas? Is there a way I could just reinstall the kcmshell and/or the module to see if that fixes it? Maybe I need to redefine a python or environment variable.

--------------------------------------------------------
**[COLOR="Blue"]FIXED:[/COLOR]** I removed *displayconfig-gtk* and did an auto-remove that removed some python pkgs and now the module shows up in System Settings again.
```
sudo apt-get remove displayconfig-gtk
sudo apt-get autoremove
```

Auto-removed packages: (displayconfig-gtk dependencies)
```
python-numeric 
python-glade2 
python-gtk2 
python-cairo
```

---

### Post by quini on 2007-11-01
Hi,

I've got the same problem, displayconfig is not opening, but, unlike you, removing python-numeric, python-glade2, python-gtk2 & python-cairo is not working for me, as I've got the same errors:

```
quini@quinilg:~$ displayconfig
X Error: BadDevice, invalid or uninitialized input device 158
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 158
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Traceback (most recent call last):
  File "/usr/bin/displayconfig", line 1720, in <module>
    displayapp = DisplayApp()
  File "/usr/bin/displayconfig", line 478, in __init__
    self._loadConfig()
  File "/usr/bin/displayconfig", line 1031, in _loadConfig
    self.targetgamma = self.availabletargetgammas.index(t)
ValueError: list.index(x): x not in list
Error in sys.excepthook:
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/apport_python_hook.py", line 42, in apport_excepthook
    binary = os.path.realpath(os.path.join(os.getcwdu(), sys.argv[0]))
IndexError: list index out of range

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/displayconfig", line 1720, in <module>
    displayapp = DisplayApp()
  File "/usr/bin/displayconfig", line 478, in __init__
    self._loadConfig()
  File "/usr/bin/displayconfig", line 1031, in _loadConfig
    self.targetgamma = self.availabletargetgammas.index(t)
ValueError: list.index(x): x not in list
```

Any help?  Up to date Gutsy.

TIA  ;)

---

### Post by mattigras on 2007-11-01
> **quini said:**
> Hi,

I've got the same problem, displayconfig is not opening, but, unlike you, removing python-numeric, python-glade2, python-gtk2 & python-cairo is not working for me, as I've got the same errors:



Was your displayconfig module working before and then stopped working? and did you ever install the displayconfig-gtk package?

---

### Post by quini on 2007-11-02
Yes, my displayconfig module was working but it sometimes failed in feisty; I didn't remember that, as I used to open it very few often.

Now the screen is not being turned off, and that's annoying for a laptop, mainly when on battery  :(

And yes, I also had displayconfig-gtk installed, and I removed it, removed python-numeric, python-glade2, python-gtk2 & python-cairo (and it's dependencies (gcompris...)...  I even reinstalled kde-guidance with no luck  :(

I've opened a new thread ([http://ubuntuforums.org/showthread.php?t=599877]("http://ubuntuforums.org/showthread.php?t=599877")), as I thought yours could confuse people... because it's got the word "solved" in its topic  ;)

Thanks for your answer  ;)

---

### Post by quini on 2007-11-05
Hi,

I use to have the laptop on or suspended, and its battery is always in the bag; if I'm moving somewhere I then insert the battery and suspend it again.

I did so yesterday, and it now powers the screen off after the 2 minutes delay I set last time the displayconfig module was working.  The screen is being powered off either with AC or battery.

But displayconfig still doesn't open  :(

Does the above info give you any idea on what's happening?  8-?

TIA  ;)

---

