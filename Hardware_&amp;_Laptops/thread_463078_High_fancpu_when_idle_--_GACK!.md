---
title: "High fan/cpu when idle -- GACK!"
date: 2007-06-03
forum: Hardware &amp; Laptops
---

### Post by wyth on 2007-06-03
Has there been a satisfactory solution to the problem of high fan/cpu usage when a laptop goes idle?  I've combed this forum all weekend, and have found nothing that cracks it.

**The Problem:** Whenever my laptop either goes to screensaver (blank screensaver -- no graphics whatsoever) *or just sits idle*, the fan cranks into high gear and stays like that until  I start to use the machine again (pushing the mouse stops it).  

**Weirdness Factor I Don't Get: **Why would a machine work harder when you're not using it?

**Steps Taken: **I've added CPU scaling (cpufreqd) and set it to conservative.  Beagled is off.  I removed Beagle in the past, but that made no difference, and I like its functionality.  Besides, the posts that suggested removing Beagle also came back and reported that removing Beagle made no difference in this behavior.  I'm running fglrx for my ATI Radeon R250 card.  My machine is spotless on the inside -- no dust.  

**The Double-Check: **This doesn't happen on Windows.  In fact, when my screensaver goes blank on Windows, the machine gets [SIZE=1]very very quiet[/SIZE].

**The Screensaver Preferences: **Screensaver is set to turn on after an hour, and "Activate Screensaver When Idle" is ticked.  Ticking that or leaving it unticked makes no difference.  There is no option to turn the screensaver off -- which I would do if I could find a way, and just let the display sleep.  

*In fact, if there's a way to do this, I'd love to hear it.*

**The Power Management Preferences: **The display is set to sleep after 10 minutes.  

The signature below has the rest of the specs.

Help me, Ubuntuforums, you're my only hope.

---

### Post by wyth on 2007-06-03
up

---

### Post by Brinstar on 2007-06-03
Zenwalker here, so YMMV, but i'm guessing the fglrx driver is the culprit. I had similar problems with my nvidia, which were solved by installing the official nvidia driver package. It's probably because the fglrx driver doesn't have as good power management as the official ati driver. 

anyway, next time you buy a new machine, ask for nvidia :)

---

### Post by FuriousLettuce on 2007-06-03
If you want the screensaver not to activate, simply choose the "none" option under the list of the screensavers (it's right at the top)

---

### Post by wyth on 2007-06-03
Dadgum ATI... I wouldn't doubt it.  All the talk by AMD about working with the Linux community to get the ATI drivers up to snuff has so far been just that, talk.  In the meantime those of us who know just enough to break our systems have to toil and wait.

---

### Post by wyth on 2007-06-03
FuriousLettuce: I'm looking at my screensaver options, and the only two at the top are Blank Screen and Random...  Maybe something's borked?

---

### Post by FuriousLettuce on 2007-06-03
Ah, no it isn't, I just have a shoddy memory and didn't bother checking at the time - I was confusing 'none' and the 'blank screen' option. I think the only way to turn it off is to untick the 'screensaver when idle' box, but you've already tried that.

Make sure you aren't using a hardware accelerated screensaver (anything that looks remotely fancy), as this will surely exacerbate the issue - you're best off just sticking it on blank screen. 

You could attempt to remove 'gnome-screensaver', although this might have further reaching consequences than you might like (e.g., losing the ability to lock the screen), so I'd definitely check out all available data and proceed with caution on that front. 

Sorry I can't be more help.

---

### Post by teejay17 on 2007-06-04
> **wyth said:**
> Has there been a satisfactory solution to the problem of high fan/cpu usage when a laptop goes idle?  I've combed this forum all weekend, and have found nothing that cracks it.

**The Problem:** Whenever my laptop either goes to screensaver (blank screensaver -- no graphics whatsoever) *or just sits idle*, the fan cranks into high gear and stays like that until  I start to use the machine again (pushing the mouse stops it).  

**Weirdness Factor I Don't Get: **Why would a machine work harder when you're not using it?

**Steps Taken: **I've added CPU scaling (cpufreqd) and set it to conservative.  Beagled is off.  I removed Beagle in the past, but that made no difference, and I like its functionality.  Besides, the posts that suggested removing Beagle also came back and reported that removing Beagle made no difference in this behavior.  I'm running fglrx for my ATI Radeon R250 card.  My machine is spotless on the inside -- no dust.  

**The Double-Check: **This doesn't happen on Windows.  In fact, when my screensaver goes blank on Windows, the machine gets [SIZE=1]very very quiet[/SIZE].

**The Screensaver Preferences: **Screensaver is set to turn on after an hour, and "Activate Screensaver When Idle" is ticked.  Ticking that or leaving it unticked makes no difference.  There is no option to turn the screensaver off -- which I would do if I could find a way, and just let the display sleep.  

*In fact, if there's a way to do this, I'd love to hear it.*

**The Power Management Preferences: **The display is set to sleep after 10 minutes.  

The signature below has the rest of the specs.

Help me, Ubuntuforums, you're my only hope.
I have this same problem. The fan for my ATI Radeon x850XT Platinum Edition is continually fluctuating up and down; this is after I've installed the fglrx driver. 
However, I _**don't**_ have the screensaver enabled, and it continues to do this when I'm doing the most non-resource intensive tasks, like reading text, or typing. 
There seems to be a cycle too: I'd say it whirs up for about 5-10 minutes, then down again. Repeat. 
Anyone know why this might be so?

---

### Post by Znupi on 2007-06-04
About the screensaver -- maybe [this](http://ubuntuforums.org/showthread.php?t=442190) is the problem you're having, which I had, too, on my ATI card. It's a known bug, check mcduck's post.

---

### Post by Brinstar on 2007-06-04
try experimenting with the official ati drivers, if the fan problem still affects you, at least you know it's not that.

---

