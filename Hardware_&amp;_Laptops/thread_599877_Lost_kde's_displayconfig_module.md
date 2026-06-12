---
title: "Lost kde's displayconfig module"
date: 2007-11-01
forum: Hardware &amp; Laptops
---

### Post by quini on 2007-11-01
Hi.

I'm using Kubuntu Gutsy (updated from Feisty); the problem is that the displayconfig module from kde-guidance won't load, showing the following errors if run from a console:

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

Mattigras' post [http://ubuntuforums.org/showthread.php?p=3686856]("http://ubuntuforums.org/showthread.php?p=3686856") shows a solution that's not working for me, as I get the above output when trying to run displayconfig after removing *python-numeric, python-glade2, python-gtk2 & python-cairo* packages; I've also tryed reinstalling kde-guidance with no luck.

And the main problem is that my laptop's screen is not being powered off (uptime problem)  :mad:

Any idea?  TIA  ;)

---

### Post by mattigras on 2007-11-02
I removed those python packages using *sudo apt-get autoremove*. Did you use that or remove them manually? As far as I can tell, Kubuntu doesn't explicitly give you an option to turn off your monitor when you close the laptop lid.  I think remember an option somewhere in xorg.conf where you can tell the server that you're using a laptop and it will get state information about whether the lid is up or down, but I'm searching through the man pages now and I can't find it. It might have been specific to my display driver (i810). I'll post back if I find anything.

Also, I think the control module is usually called via ```
kcmshell displayconfig
```. See if that works, or post the error msgs.

---

### Post by quini on 2007-11-02
> **mattigras said:**
> I removed those python packages using *sudo apt-get autoremove*. Did you use that or remove them manually?
*sudo apt-get autoremove* did nothing, because I've got programs with those dependencies, so I removed them manually (also those programs: gcompris, wifi-radar and a few more) using *aptitude remove*

> **mattigras said:**
> As far as I can tell, Kubuntu doesn't explicitly give you an option to turn off your monitor when you close the laptop lid.
Yes, through the power manager applet, **but** the feature I'm missing is the right tab of the displayconfig module, where you can set the # of minutes it has to wait to power the screen off.

> **mattigras said:**
> I think remember an option somewhere in xorg.conf where you can tell the server that you're using a laptop and it will get state information about whether the lid is up or down, but I'm searching through the man pages now and I can't find it. It might have been specific to my display driver (i810). I'll post back if I find anything.
I've always used displayconfig (I didn't even know its name till now, as I called it from kcontrol); if there's no other solution I'd use this one, but it seems a "hard" one.

My laptop's got a 915GM chipset, using the same i810 X driver as yours.

> **mattigras said:**
> Also, I think the control module is usually called via ```
kcmshell displayconfig
```. See if that works, or post the error msgs.
I'm sorry; here it is (thanks in advance ;) ):

```
quini@quinilg:~$ kcmshell displayconfig
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


Pythonize constructor -- pid = 879
Python interpreter initialized!



Pythonize constructor -- pid = 879
Traceback (most recent call last):
  File "<string>", line 8, in kcontrol_bridge_create_displayconfig
  File "/var/lib/python-support/python2.5/displayconfig.py", line 1698, in create_displayconfig
    return DisplayApp(parent, name)
  File "/var/lib/python-support/python2.5/displayconfig.py", line 478, in __init__
    self._loadConfig()
  File "/var/lib/python-support/python2.5/displayconfig.py", line 1031, in _loadConfig
    self.targetgamma = self.availabletargetgammas.index(t)
ValueError: list.index(x): x not in list
Error in sys.excepthook:
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/apport_python_hook.py", line 42, in apport_excepthook
    binary = os.path.realpath(os.path.join(os.getcwdu(), sys.argv[0]))
AttributeError: 'module' object has no attribute 'argv'

Original exception was:
Traceback (most recent call last):
  File "<string>", line 8, in kcontrol_bridge_create_displayconfig
  File "/var/lib/python-support/python2.5/displayconfig.py", line 1698, in create_displayconfig
    return DisplayApp(parent, name)
  File "/var/lib/python-support/python2.5/displayconfig.py", line 478, in __init__
    self._loadConfig()
  File "/var/lib/python-support/python2.5/displayconfig.py", line 1031, in _loadConfig
    self.targetgamma = self.availabletargetgammas.index(t)
ValueError: list.index(x): x not in list
error: *** runFunction failure
```

---

### Post by mattigras on 2007-11-05
Hey sorry about not getting back to you on this thread. I forgot to subscribe to it but I'll get notifications now.

> **quini said:**
> 
I use to have the laptop on or suspended, and its battery is always in the bag; if I'm moving somewhere I then insert the battery and suspend it again.


I don't exactly understand what you're saying. Do you make it Hibernate and then pull out the battery?

> **quini said:**
> 
I did so yesterday, and it now powers the screen off after the 2 minutes delay I set last time the displayconfig module was working.  The screen is being powered off either with AC or battery.

But displayconfig still doesn't open  :(

Does the above info give you any idea on what's happening?  8-?


So it's still going by the values that you set in the module, Its just having a problem displaying the GUI

> **quini said:**
> *sudo apt-get autoremove* did nothing, because I've got programs with those dependencies, so I removed them manually (also those programs: gcompris, wifi-radar and a few more) using *aptitude remove*


I've now realized that those specific Python pkgs aren't the problem because I've installed programs that need those dependencies (I think most/all Gnome apps need them) since I solved my problem and my *displayconfig* still works.

When you do run *displayconfig* doesn't the window that shows up say a possible reason is something like "KDE upgrade leaving an orphaned control module"?
You mentioned that you just upgraded to Gutsy, and I'm assuming that included a KDE upgrade. Maybe there is a problem there?

> **quini said:**
> 
```
quini@quinilg:~$ kcmshell displayconfig
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


Pythonize constructor -- pid = 879
Python interpreter initialized!



Pythonize constructor -- pid = 879
Traceback (most recent call last):
  File "<string>", line 8, in kcontrol_bridge_create_displayconfig
  File "/var/lib/python-support/python2.5/displayconfig.py", line 1698, in create_displayconfig
    return DisplayApp(parent, name)
  File "/var/lib/python-support/python2.5/displayconfig.py", line 478, in __init__
    self._loadConfig()
  File "/var/lib/python-support/python2.5/displayconfig.py", line 1031, in _loadConfig
    self.targetgamma = self.availabletargetgammas.index(t)
ValueError: list.index(x): x not in list
Error in sys.excepthook:
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/apport_python_hook.py", line 42, in apport_excepthook
    binary = os.path.realpath(os.path.join(os.getcwdu(), sys.argv[0]))
AttributeError: 'module' object has no attribute 'argv'

Original exception was:
Traceback (most recent call last):
  File "<string>", line 8, in kcontrol_bridge_create_displayconfig
  File "/var/lib/python-support/python2.5/displayconfig.py", line 1698, in create_displayconfig
    return DisplayApp(parent, name)
  File "/var/lib/python-support/python2.5/displayconfig.py", line 478, in __init__
    self._loadConfig()
  File "/var/lib/python-support/python2.5/displayconfig.py", line 1031, in _loadConfig
    self.targetgamma = self.availabletargetgammas.index(t)
ValueError: list.index(x): x not in list
error: *** runFunction failure
```


I'm really stumped. I wouldn't worry about those X Error's b/c a lot of my apps run fine and still give those.  I'm just barely familiar with python and when mine wasn't working I tried looking at those scripts and understanding the error msgs and I was completely lost. 

A couple ideas:
  1. It could have something to do with your Python install, maybe try reinstalling?
  2. Maybe some other Python-dependent app changed an environment variable. You could try removing/adding apps that depend on Python one by one and see if that gets you anywhere
  3. I'm sure that when you change values in the *displayconfig* module, all it's doing is writing those values to a text configuration file. You could try hunting around for that file and edit it by hand to give the behaviour you want. (I'd start looking in *~/.kde* or locate any files matching *rc)
  4. If *displayconfig-gtk* can control the option that you need to modify, it might just be easier to reinstall it and leave the KDE *displayconfig* broken:)
  5. Last resort and definitely overkill: Back-up your data and try a fresh Gutsy install.

---

### Post by quini on 2007-11-07
> **mattigras said:**
> Hey sorry about not getting back to you on this thread. I forgot to subscribe to it but I'll get notifications now.
Thanks for subscribing  :popcorn:


> **mattigras said:**
> I don't exactly understand what you're saying. Do you make it Hibernate and then pull out the battery?
No.  The battery is always out of the laptop; only when I'm going to bring it with me (and maybe use it on battery), I plug the battery in, then suspend (not hibernate) it.


> **mattigras said:**
> So it's still going by the values that you set in the module, Its just having a problem displaying the GUI
That's it.


> **mattigras said:**
> I've now realized that those specific Python pkgs aren't the problem because I've installed programs that need those dependencies (I think most/all Gnome apps need them) since I solved my problem and my *displayconfig* still works.

When you do run *displayconfig* doesn't the window that shows up say a possible reason is something like "KDE upgrade leaving an orphaned control module"?
Yes, it also says I may have some old third party modules...


> **mattigras said:**
> You mentioned that you just upgraded to Gutsy, and I'm assuming that included a KDE upgrade. Maybe there is a problem there?
May be  :confused:


> **mattigras said:**
> I'm really stumped. I wouldn't worry about those X Error's b/c a lot of my apps run fine and still give those.  I'm just barely familiar with python and when mine wasn't working I tried looking at those scripts and understanding the error msgs and I was completely lost. 

A couple ideas:
  1. It could have something to do with your Python install, maybe try reinstalling?
  2. Maybe some other Python-dependent app changed an environment variable. You could try removing/adding apps that depend on Python one by one and see if that gets you anywhere
  3. I'm sure that when you change values in the *displayconfig* module, all it's doing is writing those values to a text configuration file. You could try hunting around for that file and edit it by hand to give the behaviour you want. (I'd start looking in *~/.kde* or locate any files matching *rc)
  4. If *displayconfig-gtk* can control the option that you need to modify, it might just be easier to reinstall it and leave the KDE *displayconfig* broken:)
  5. Last resort and definitely overkill: Back-up your data and try a fresh Gutsy install.

1. do you know how to reinstall python?  *aptitude reinstall python* only applies to a 145KB package...  :confused:
2. I'll try that option
3. that's probably right, but as I've now got back the behaviour I want...
4. AFAIK displayconfig-gtk doesn't include the "time for screen power off" option  :(
5. that would be the hardest solution... hope I don't have to do so  :popcorn:

Again, thanks  :)

---

