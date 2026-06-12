---
title: "[SOLVED] No Keyboard After Suspend"
date: 2008-12-04
forum: Hardware
---

### Post by Rodney9 on 2008-12-04
Hello, After I resume from suspend my usb keyboard just flashes continuously and is totally unresponsive, all I can do is reboot.

How can I get my keyboard to work after suspend ?

Rodney.

---

### Post by Rodney9 on 2008-12-05
No keyboard after 30 minutes of hibernate as well .

---

### Post by Rodney9 on 2008-12-05
I have found many posts of this same problem with previous versions, gutsy etc, but can't find any fixes for Intrepid.

---

### Post by Rodney9 on 2008-12-05
Does any one know why my keyboard will not work after suspend/hibernate, it is just a usb keyboard, nothing special, not a wireless.

---

### Post by Rodney9 on 2008-12-05
I have all new hardware, would a reinstall help, is the iso download the latest, does it have all the updates ?

---

### Post by Rodney9 on 2008-12-05
On another forum (I'm trying to find the answer everywhere) someone suggested this losing keyboard after suspend/hibernate problem is a Intrepid Ibex bug, but I have searched the bugs and can find no mention,
So I sincerely hope this means there is a fix ???

---

### Post by Rodney9 on 2008-12-06
I solved this with help from another forum - [http://forums.whirlpool.net.au/](http://forums.whirlpool.net.au/) linux/bsd

 I learnt plugging my keyboard into a hub, lets it still work after suspend.

Thank You
Rodney

---

### Post by miaviator278 on 2008-12-22
solved for desktop users.

---

### Post by ladgrove on 2009-01-24
Further details, or an actual link...

---

### Post by FoH on 2009-03-04
I have the same problem. I think Rodney and I have the same kind of keyboard, a **Logitech Illuminated Keyboard**.

I've found out that the keyboard works great after resume if you unplug it and then reinsert it again. After resume and without unplugging it, it just sits there flashing as Rodney described. In dmesg there's a lot of these messages: ```
[ 2266.228115] usb 2-1: reset full speed USB device using uhci_hcd and address 3
```

These messages stops after reinserting the keyboard. Full dmesg of the suspend process attached.

---

### Post by FoH on 2009-03-04
Problem solved, I think. I used the method described here: [http://people.freedesktop.org/~hughsient/quirk/quirk-suspend-advanced.html](http://people.freedesktop.org/~hughsient/quirk/quirk-suspend-advanced.html)

Created the file ```
/etc/pm/config.d/unload_modules
``` with the content ```
SUSPEND_MODULES="uhci_hcd"
```

This unloads the full speed USB module before suspending, and it seems to be working. Have tried suspending a couple of times and the keyboard works directly. Dmesg attached.

---

### Post by DLGandalf on 2009-07-05
has anyone figured out howto get it working on jaunty, without having to reattach the usb connector every time?

---

### Post by geomorillo on 2009-11-24
How can this be solved if the solution is to unplug the keyboard, what if (in my case) you had a laptop, i had to open it to unplug it... so fix this already in 9.10 and no fix?? come on....

---

### Post by miaviator278 on 2009-11-24
Even in the bug report canonical has given up.  It seems fairly obvious that this is not considered an important part of the user experience.  

The solution for laptop users is to suspend twice.  So I have gnome set to suspend when the laptop lid is closed.  I have to close the lid, wait for the system to suspend, open the lid, wait for the system to come out of suspend, close the lid again, wait for the system to suspend, and then open the lid again and use my computer.  In karmic we are down to a 20% Kernel Panic on the second resume!

(The real solution is for someone at canonical or the kernel development team to become passionate that this is a user experience issue and work to get the code fixed.  This issue has existed in at least the last four releases of ubuntu)   

// hey #[www.GOOGLE.com](www.GOOGLE.com) index this! //

---

### Post by DLGandalf on 2009-11-24
completely solved for me in the karmic kernel icw a logitech illuminated.
what exactly are the symptoms on a laptop, are the caps lock, numLock etc flashing, or does it have flashing backlit keys like the logitech illuminated ?

---

