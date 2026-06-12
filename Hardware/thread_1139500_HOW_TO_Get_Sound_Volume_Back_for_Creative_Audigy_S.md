---
title: "HOW TO: Get Sound Volume Back for Creative Audigy Soundcard After Jaunty Upgrade"
date: 2009-04-27
forum: Hardware
---

### Post by OzzyFrank on 2009-04-27
If you have a **Creative Audigy** soundcard and noticed the volume gone after upgrading Ubuntu to Jaunty, here is how to get it back. **This might also apply to many other sound cards out there**, so give it a try if you have different hardware but the same symptoms.

First thing you will notice upon reboot is that there is no sound, yet no app that uses it will complain that there is no appropriate hardware installed, or working drivers, etc etc. It will be like all these programs recognise your soundcard, but there will just be no volume, even though Master is at full, and same with PCM (which you might already be aware of if you have programs turn that down, which happens to me a bit, usually after running DVD Shrink in Wine, though happens with native Gnome/Linux apps too).

What you will need to do is open the Volume Control applet (which used to be accessed by double-clicking the volume icon in the system tray - that action now mutes volume, so single-click the volume icon and click the **[COLOR="Indigo"]Volume Control[/COLOR]** button that appears). Once again, if you're used to having to turn up the PCM volume every now and again, this applet will be familiar to you. But the answer is not in the first tab, but under [COLOR="#4b0082"]**Switches**[/COLOR] (should be the 2nd tab).

In my case, there are 2 options in that tab, and it is the top one - [COLOR="#4b0082"]**Audigy Analog/Digital Output Jack:**[/COLOR] - that needs to be disabled. That's it - your sound should now be happening again!

Hope this helps others with this sound error that is actually nothing life-threatening, but a pain in the @$$ nonetheless! If not, especially if you actually have something happening that is much more serious than a setting disabling the volume, check out this great (and somewhat huge!) post on sound issues: [http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

