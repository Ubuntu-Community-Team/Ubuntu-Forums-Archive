---
title: "mouse buttons don't work--Logitech, 2 devices via one receiver"
date: 2007-11-19
forum: Hardware &amp; Laptops
---

### Post by injoy on 2007-11-19
I'm totally new to Linux.  :-)  I'm using Gutsy.  I have the Logitech keyboard/mouse duo MX5000, which includes the MX 1000 mouse, so I've been trying to follow the instructions listed [here on the forums]("http://ubuntuforums.org/showthread.php?t=219894") and, when those haven't worked, I've also consulted and tried [this]("https://help.ubuntu.com/community/MX1000Mouse"), [this]("http://www.mattvanstone.com/2007/01/all_the_buttons_on_my_logitech/"), [this]("http://www.taet.com.au/mb.nsf/d6plinks/WEBB-7684G5"), and  [this]("http://web.archive.org/web/20060106225058/http://floam.sh.nu/?page=guides&section=mx1000").  Just so you know what all I HAVE tried.

The main problem seems to be that all of the instructions written for the MX1000 aren't appropriate for the MX 5000 duo because there are two devices (keyboard and mouse) with the same "name."  So the solution seems to be to be more specific in xorg.conf, and use "Device" to specify the mouse instead of "Name."  Thus, this is what I presently have in the relevant section of my xorg.conf file:```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "evdev"
        Option          "CorePointer"
	Option "Device" "/dev/input/event2"
        Option          "Name"  "Logitech Logitech BT Mini-Receiver"
	Option "AbsoluteScreen" "0"
EndSection
```There are quite a few combinations that "work," the only important line here seems to be the Device line.  I've tried every different suggested method in all of the above pages that I could find, usually with identical (or, rarely, worse) results.

The problem is that **when I restart**, it works the first time after I've updated the xorg.conf (and seems to recognize all my buttons, including the tilt wheel), but will never boot on subsequent restarts.  Instead, on the 2nd or more restart, it'll go to the point where it says "Running Local Boot Scripts", show the little X cursor, then go back to "Running Local Boot Scripts," and back and forth indefinitely until it finally pops up that it's running in  a limited graphics mode, do I want to continue or quit... if I push continue it just crashes very dramatically; if I push quit it puts me out to the command line.

So, to make a long story short, as I'm typing this, it seems to recognize my mouse buttons.  But the second I restart my computer, I know it'll essentially die until I restore a different xorg.conf file.  The really bizarre thing is that I have a couple of different xorg.conf.alt, xorg.conf.alt2, files that are different but all enable the extra mouse buttons, and I can restore back and forth between those whenever it crashes--it doesn't make me restore my ORIGINAL xorg.conf file, just one that's DIFFERENT from the one it was crashing on, even though it'll go on to crash on that one, too, once it's been restarted twice.

Any thoughts would be much appreciated; I've been trying to get this straightened out literally for days without any luck.  ](*,)  Thanks!

**UPDATE FOR ANYONE FINDING THIS LATER:**  Turns out to be a bug with evdev's implementation in Ubuntu.  The solution, which worked for me and also has worked for others, is to change CorePointer to SendCoreEvents.  :-)

---

### Post by injoy on 2007-11-20
No one has any ideas?  (Did I post this in the right forum?  I thought mice would be "hardware," but I wasn't quite sure...)

---

### Post by injoy on 2007-11-20
Could someone point me in the right direction of where to *ask* my question, then?  Or tell me where I would look (I'm a newbie) to find a log or something that might give me an actual error message, since I'm not getting one?

Thanks!

---

### Post by twoseids on 2007-11-27
Sorry, I'm looking for help on a similar issue with a Logitech mouse and am also getting no response from the community. Usually they are very good about it, but maybe this is a harder issue to diagnose?

Good luck...

---

