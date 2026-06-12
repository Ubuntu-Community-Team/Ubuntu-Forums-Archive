---
title: "Have to Press Lid Close Button Twice to Suspend"
date: 2008-08-31
forum: Hardware
---

### Post by kuloch on 2008-08-31
I was really happy to see the setting for when I close my laptop's lid (which I didn't have in Fedora 5), and it works great - except that I have to press the lid button before closing the lid (or close the lid twice).

Pressing it once doesn't seem to do anything after leaving it for a couple minutes.  But pressing it a second time will immediately start the HDD activity light blinking, putting it in suspend a few seconds later.

Any idea what would make the listener not fire on the first press but only on the second?  It's almost like a "double-click" for the laptop lid close button.  Pretty minor, but I'm sure there's some way to fix it.

---

### Post by kuloch on 2008-09-02
... could anyone perhaps tell me where I could find some relevant config files?  I'm up for poking around and testing, as I can always log into the terminal and fix anything that breaks X.

---

### Post by kuloch on 2008-09-05
Having now run on Ubuntu (essentially Xubuntu, since I've switched from Gnome to Xfce) for over a week, I'm finding that it doesn't always respond to the laptop-lid-closing-button being pressed.  I'd say... roughly 80-90% of the time it works fine (but needs to be pressed twice, as described above).  The other handful of times it doesn't respond even after hitting the close button a dozen or so times.

Again, it's not horribly inconvenient - just an extra several seconds to realize it's not shutting down, hit the power button to pull up the options, and press Standby.  But I'm *sure* there's some way I can look into this.  I just need a starting point, which I'm not finding on my own.

---

### Post by kuloch on 2008-09-22
*bump*

Nothing's changed.  Just wondering if anyone has any ideas.

---

### Post by viduliya on 2008-09-30
I just started to play with the suspend, hibernation settings and noticed that my Toshiba Satellite laptop behave the same way.  Essentially, I need to close the lid twice to suspend.   I am also looking for a solution to fix this issue.

Bug report found here:  [URL="https://bugs.launchpad.net/ubuntu/+source/linux/+bug/44825"]https://bugs.launchpad.net/ubuntu/+source/linux/+bug/44825

[/URL]

---

### Post by Colie on 2009-01-19
Do you have CIFS Drives mapped?  I noticed on mine that if the drives are still mapped, that they hang the suspend process the first time, because the wireless networking is turned off before the drives are unmounted.  There is like a 20 second lag before the drives are "forced" closed, but the suspend/hibernate has failed by that point.  The second time works, though, because the drives are unmounted at that point.

---

### Post by johnp51d on 2009-02-14
Ok, I've finally come up with a pretty good work around for this.  First, go to this website: [http://www.linux.com/articles/54610](http://www.linux.com/articles/54610)  and follow the instructions to create your own sleep file and command to launch it when the lid is closed.  You don't need to bother with the commands for hibernating when the power button is pushed.  One thing I did differently though than the web site was when you write this line:

event=button[ /]lid.*

I did it this way instead:

event=button[/]lid.*

Once you restart, the computer should reliably suspend when you close the lid. You can leave it like this if you like, but the gnome-power-management wont control anything.  

If you want to get gnome-power-manager working again, log in as root and go to /etc/acpi  and pull the event and actions folder to the desktop.  Now open up synaptic and search for acpi.  Go through and select each result and check it for reinstall.  Then apply the changes and your /ect/acpi directory should be back to it's original defaults.  Now drag the actions and events folders that you put on the desktop into /etc/acpi and overwrite when prompted.  Restart the computer and then open up power management.  Select action when lid is closed for a/c and battery to “do nothing.”  This is because our new commands will handle that, but every other aspect of gnome-power-management still works normally.  

The only problems with this workaround on my Inspiron 700M is that it does not prompt for a password when you resume from suspend.  This is actually preferable for me, but I'm sure someone can figure a way to add that feature in.  Also, lid state always returns as “closed” now instead of going back and forth.  I have not found anything yet, however, that is impacted by this.

---

