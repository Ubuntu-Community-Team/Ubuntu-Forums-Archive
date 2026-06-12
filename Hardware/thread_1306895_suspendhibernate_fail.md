---
title: "suspend/hibernate fail"
date: 2009-10-30
forum: Hardware
---

### Post by drbobb on 2009-10-30
fail, as in: I choose suspend or hibernate from the gnome menu, and nothing happens. I press the suspend key combo - ditto. Well, actually the screen is locked, but no suspend or hibernation. When the battery runs low, the system shuts down abruptly instead of hibernating, as it's configured to do in the gnome settings dialogs. 

I find this somewhat unsettling, as I don't know that I did anything to make it happen, it just stopped working overnight. I could find nothing pertinent in the system logs, at all. For several days after installing Karmic, both suspend and hibernate were working perfectly, then just stopped.

SOLVED: of all things, it was pulseaudio that was blocking suspend/hibernate. It complained about the content of /etc/sudoers (which was not as the installer would have generated it, because I created my karmic koala via debootstrap).

---

### Post by DavidFourer on 2009-11-07
Same problem.  Can you explain what you did?  I Just did a very basic install of Karmic Ubuntu on an HP p6100z desktop.  Suspend-to-ram gets a blank screen with cursor blinking in top left.  I Have to do a forced shut-down.  Here is the /etc/sudoers file I found:
> david@david-desktop:~$ sudo cat /etc/sudoers
[sudo] password for david:  
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#


Defaults	env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL) ALL

# Uncomment to allow members of group sudo to not need a password
# (Note that later entries override this, so you might need to move
# it further down)
# %sudo ALL=NOPASSWD: ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
How did you figure out the problem?
Any help is appreciated.

---

### Post by drbobb on 2009-11-07
David, your problem is most likely unrelated to mine and has nothing to do with your sudoers file, which seems to be ok. 
Anyway, from the System menu, in Administration, open the System Log Viewer and look at the file pm-suspend.log (from the list in the left pane) for clues.

---

### Post by anton610 on 2009-11-21
> **DavidFourer said:**
> Same problem. Can you explain what you did? I Just did a very basic install of Karmic Ubuntu on an HP p6100z desktop. Suspend-to-ram gets a blank screen with cursor blinking in top left. I Have to do a forced shut-down. Here is the /etc/sudoers file I found:
How did you figure out the problem?
Any help is appreciated.
 
 
I've exactly the same problem!
 
does anybody solved it?
 
Kind Regards Anton

---

