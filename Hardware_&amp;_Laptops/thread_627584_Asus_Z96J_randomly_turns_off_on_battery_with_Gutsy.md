---
title: "Asus Z96J randomly turns off on battery with Gutsy"
date: 2007-11-30
forum: Hardware &amp; Laptops
---

### Post by Bazirker on 2007-11-30
Since I updated to Gutsy my laptop has started randomly turning off while on battery.  It will be working just fine and then boom, black screen, power is gone as if someone ripped the battery out.  I never had the problem with Feisty and it only happens on battery.  I dual boot XP and it doesn't have this problem.  It is very odd behavior...does anyone have any thoughts?

---

### Post by crouton on 2007-11-30
Is the system totally dead or just gone into powersave?  Hitting the power button or suspend/hibernate do anything?

---

### Post by Bazirker on 2007-11-30
Totally dead.  Pushing the power button does nothing.  I have to either plug the system in or remove and replace the battery.  :(

---

### Post by Bazirker on 2007-12-05
So today I booted on battery and it didn't randomly turn off, which is good...all the other times it has died on me have been when I booted it plugged in and then unplugged it.  Maybe some power settings aren't resetting like they should when I unplug?

---

### Post by Bazirker on 2008-01-30
So it's been awhile and I still have this problem and I really want to use Gutsy on battery...no ideas?

---

### Post by Yellow Pasque on 2008-01-30
I believe Ubuntu is configured to shut off the laptop when the battery gets critically low. Perhaps there's an issue with the battery or the battery management.

One tip I can give you is to look at your gnome-power-manager settings by typing gconf-editor in the terminal and following this path:
/apps/gnome-power-manager

---

### Post by Bazirker on 2008-01-31
I took a look and there are LOTS of great settings that I modified, but none of them have fixed my problem.  When the battery gets super low, Ubuntu shuts down.  Problem is that my battery isn't low and Ubuntu isn't shutting down, the laptop is simply dying as if the power source is totally cut.  I'd think I have a battery problem but it works just fine in XP.

Any other suggestions?

---

### Post by Bazirker on 2008-02-12
OK I installed a fresh gutsy on my machine and it has the same problem.  I'm totally stumped.  Why would my laptop just suddenly turn off in Ubuntu but not in Windows XP?  Aside from a physical power failure, what else could possibly cause this?

:(

---

