---
title: "[SOLVED] Avant Window Manager applets not working"
date: 2008-07-12
forum: General Help
---

### Post by rossjman1 on 2008-07-12
I followed the instructions here [http://wiki.awn-project.org/DistributionGuides#Reacocard.27s_PPA](http://wiki.awn-project.org/DistributionGuides#Reacocard.27s_PPA) on how to get applets for Avant. Everything installed fine, but I still don't have any applets.

---

### Post by rossjman1 on 2008-07-12
bump

---

### Post by twntyonejay on 2008-07-12
im having the same problem after update

---

### Post by MattBD on 2008-07-12
Have you tried installing Ubuntu Tweak? I found this program made it easy to get the latest AWN applets. You can get it from [http://www.getdeb.net/app/Ubuntu+Tweak](http://www.getdeb.net/app/Ubuntu+Tweak) . Just download and install it, and when you run it just have a look through the menus, under Applications>Third Party Software Sources. You can also use it to keep up with other things, such as Compiz Fusion plugins and Google Gadgets.

---

### Post by twntyonejay on 2008-07-12
I got the tweak but I still cant figure it out how to restore the applets in the dock like weather and pandora

---

### Post by Enlitend on 2008-07-12
Hi,

It seems there's a problem with the recent update. Take a look at this thread:
[HOWTO: functional eye-candy with Avant-Window-Navigator]("http://ubuntuforums.org/showthread.php?t=762363&page=26")

---

### Post by MattBD on 2008-07-12
Which version are you running - Hardy or Gutsy?

---

### Post by twntyonejay on 2008-07-12
If u referring to me, I'm running 8.04

---

### Post by MattBD on 2008-07-12
OK. I was wondering because that guide showed the PPA for Gutsy and I didn't know whether the repositories had been cut-and-pasted in or adjusted for Hardy, as if they were just pasted they might not work in Hardy.
I managed to get it working about a week ago in Ubuntu Hardy fine. I didn't use that PPA - I installed the avant-window-navigator and awn-manager packages from the normal Ubuntu repositories, which got them working fine but without any applets other than the launcher.
I then added Ubuntu Tweak and used that to add the extra applets for AWN (as well as Compiz plugins, love the new sphere one!), and it all worked fine.
Judging by the thread Enlitend mentioned, if it is a problem with the applets themselves, it's now been solved so you might want to try again.

---

### Post by rossjman1 on 2008-07-12
The problem is that the applets just arn't available even though all the packages installed correctly. I'm running 8.04.

There is an option to install applets manually (like you would with a theme from gnome-look). So, if there is a place to download these applets like gnome-look is to themes, then I can uninstall the non-functional-waste-of-space awn-core-applets-bzr package. ;)

Edit: Also, I know that guide I pointed to in my original post was for Gutsy and not Hardy. The guide for Hardy points me to the Gutsy guide, because there is no applets package in Hardy (for some reason)...

---

### Post by MattBD on 2008-07-13
OK, if once you've added Ubuntu Tweak and used that to subscribe to the repositories, and run sudo apt-get update from the terminal, there should be several packages available. If you enter the following:
```
sudo apt-get install awn-applets-c-core awn-applets-c-extras awn-applets-python-core awn-applets-python-extras
```
Then go into awn-manager, you should have a load of applets available. I know this works as I've just this second done it.

---

### Post by rossjman1 on 2008-07-13
I installed Ubuntu Tweak, but it doesn't run.
> jeff@jeff-laptop:~$ ubuntu-tweak
/usr/lib/python2.5/site-packages/apt/__init__.py:18: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
Traceback (most recent call last):
  File "./ubuntu-tweak.py", line 68, in <module>
    launcher = TweakLauncher()
  File "./ubuntu-tweak.py", line 38, in __init__
    from MainWindow import MainWindow
  File "/usr/share/ubuntu-tweak/MainWindow.py", line 103, in <module>
    from ThirdSoft import ThirdSoft
  File "/usr/share/ubuntu-tweak/ThirdSoft.py", line 36, in <module>
    from PolicyKit import PolkitButton, DbusProxy
  File "/usr/share/ubuntu-tweak/PolicyKit/__init__.py", line 2, in <module>
    from DbusProxy import DbusProxy
  File "/usr/share/ubuntu-tweak/PolicyKit/DbusProxy.py", line 25, in <module>
    class DbusProxy:
  File "/usr/share/ubuntu-tweak/PolicyKit/DbusProxy.py", line 29, in DbusProxy
    proxy = system_bus.get_object('com.ubuntu_tweak.Mechanism', '/Tweak', INTERFACE)
  File "/var/lib/python-support/python2.5/dbus/bus.py", line 244, in get_object
    follow_name_owner_changes=follow_name_owner_changes)
  File "/var/lib/python-support/python2.5/dbus/proxies.py", line 241, in __init__
    self._named_service = conn.activate_name_owner(bus_name)
  File "/var/lib/python-support/python2.5/dbus/bus.py", line 183, in activate_name_owner
    self.start_service_by_name(bus_name)
  File "/var/lib/python-support/python2.5/dbus/bus.py", line 281, in start_service_by_name
    'su', (bus_name, flags)))
  File "/var/lib/python-support/python2.5/dbus/connection.py", line 607, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.Spawn.ChildExited: Launch helper exited with unknown return code 1
jeff@jeff-laptop:~$ 


---

### Post by MattBD on 2008-07-13
Hmm, not sure why it did that. I've just installed Tweak on a fresh install and it worked fine for me.

---

### Post by rossjman1 on 2008-07-13
The applet package had an update today, and I just checked quickly and the applets are there now! Don't have any time to test them out right now since I have work...

---

### Post by rossjman1 on 2008-07-13
All right the applets are awesome, but a few don't work (ones i dont use). :) I have 1 more quick question about the AWN Weather applet. I have seen screenshots of the applet showing a map, and there are settings for the map, but I don't know how to get the map to appear.
EDIT: I feel dumb, it's middle click.

---

