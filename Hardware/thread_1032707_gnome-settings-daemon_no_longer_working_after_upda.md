---
title: "gnome-settings-daemon no longer working after update"
date: 2009-01-06
forum: Hardware
---

### Post by frozen_zeus on 2009-01-06
Hi all, I have recently updated the xterm shown below taken from the synaptic history

> 
Upgraded the following packages:
xterm (235-1ubuntu1) to 235-1ubuntu1.1


I'm pretty sure it was this that caused it, I have also used the following commands recently but can't imagine it being them, I'll post them anyway...

gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_9 "<Control><Alt>Delete"

gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_9 "gnome-system-monitor"

Now when I try to change a theme or anything like that I get the message

> 
Unable to start the settings manager 'gnome-settings-daemon'.
Without the GNOME settings manager running, some preferences may not take effect. This could indicate a problem with Bonobo, or a non-GNOME (e.g. KDE) settings manager may already be active and conflicting with the GNOME settings manager.


I have created new users and tried old users but the problem exists on all logins, I have restarted multiple times and tried both kernels on the boot screen. I have been through this thread

[http://ubuntuforums.org/showthread.php?t=587410&highlight=gnome+settings+daemon](http://ubuntuforums.org/showthread.php?t=587410&highlight=gnome+settings+daemon)

with no success. Any ideas what I can do?
P.S I am running Ubuntu 8.10 64 bit.

---

### Post by frozen_zeus on 2009-01-07
*bump*

---

### Post by battlesound on 2009-01-07
yup, I just investigated this a little while ago.  I wanted to know why the **keyboard shortcuts** from System>Preferences (terminal cmd: **gnome-keybinding-properties**) wouldn't work for setting certain shortcuts.

I wanted shortcuts to work again for home folder, lock screen, eject, etc...

Turns out the ones that don't work are listed together under **/apps/gnome_settings_daemon/keybindings** in **configuration editor** (terminal cmd: **gconf-editor**).

I extremely miss opening my home folder with <control><alt><h>.  It would go to the nautilus view of my home folder... it's so quick to get to documents.  Anyway, this really is bothering me.  I can't wait to fix this.  What could it be?  How do I make sure the gnome_settings_daemon/keybindings thing starts or is working?

So how does this get fixed.  I wonder if there's a problem, like you said, because of the xterm update.  I lost track of what updates or installs I did when it stopped working.  I've been trying KDE stuff (specifically the theme manager, which hasn't worked yet for this computer)... don't know if that would conflict.

---

### Post by battlesound on 2009-01-17
well, I tried to remove any conflicting xsettings managers through synaptic package manager.  I restart, but I still can't use any of the keyboard shortcuts.

I can't start **gnome-settings-daemon** because it's conflicting with another x-settings manager.

```
$ sudo gnome-settings-daemon 
[sudo] password for maxone: 

** ERROR **: You can only run one xsettings manager at a time; exiting

aborting...
Aborted
```

So how do I find out what other xsettings managers are installed, running, etc?  How do I change this?

BTW, I'm using 64 bit ubuntu studio, 8.04.

---

### Post by mitchellroe.236 on 2009-03-24
*bump*

---

