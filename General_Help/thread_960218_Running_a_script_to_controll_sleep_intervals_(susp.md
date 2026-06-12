---
title: "Running a script to controll sleep intervals (suspend)"
date: 2008-10-27
forum: General Help
---

### Post by b166er on 2008-10-27
Hi
This might be a strange question, But can one create a script that would tell the computer to suspend and wake up again?

I have a graphics card that creats alot of heat. And my computer is inside a very small room without proper air-circulation.

I'm a bit scared to leave my computer running all day because of this.
So I thought that having it suspend for a half hour and then be awake for 2 hours and then sleep again (and so on) would reduce the heat buildup.

I know that there is a command called "pm-suspend" but I doubt that this would work:
```

pm-suspend
sleep 1800
Wakeup-command
sleep 10 800
pm-suspend
# and so on...

```
I think the script would be suspended aswell :)

But Would cron still be running? 
Or can you specify a suspend time with the command?

I know that this sounds like a really silly soulution to a problem that could be fixed by simply pushing the power-button. 

But isn't finding silly workarounds one of the things that makes linux fun? :)

---

### Post by sdennie on 2008-10-27
Wakeups are controlled by /proc/acpi/wakeup but, none of the options are a timer so I'm not sure how you'd get it to wakeup at a certain time.  One option would be to set the machine to Wake on Lan and then have another machine ping it every once in a while.

As for the heat issue, have you tried cleaning the machine with canned air?  Also, what makes you think the graphics card is getting to hot?  Some graphics cards use a lower clock frequency when in 2D mode so, disabling compiz might cool it off.

---

### Post by b166er on 2008-10-27
I like your idea with disabling compiz (but doesn't that need a restart of the xserver?).

I have 4 500gig disks too and I think they add alot to the heat..

But here's a thought, what about puting only the Graphics-card, and the disks to sleep?

I don't mean puting the monitor to sleep, but the graphics card. 
Wouldn't I be able to run a script during that time?
Or is it possible to put only a Graphics card to sleep?

---

### Post by sdennie on 2008-10-27
You don't need to restart X to turn off compiz.  Go to System->Preferences->Appearance and in the Visual Effects tab, select "None".  Alternatively, you can do this from the command line or Alt-F2 run dialog with:

```

metacity --replace

```

And to turn compiz back on:

```

compiz --replace

```

As for putting the disks/graphics to sleep, about the only thing you can do for the graphics is, if you have an nvidia card, underclock the card.  Though, if you've turned off compiz, you may not be able to underclock it lower than the 2D speeds anyway.  For disks, you can indeed get them to stay mostly in standby (which does reduce heat by a noticeable amount).  However, I believe desktop disks have a very limited number of standby/resume cycles so, probably the safest thing to try would be to just reduce the amount of disk activity rather than forcing them into standby.  See: [  HOWTO: Decrease disk activity]("http://ubuntuforums.org/showthread.php?t=839998").

Reducing heat and laptop power savings are similar so, you may want to look at some of the guides in my signature to see if you can find anything else interesting to reduce heat.  Just be aware that desktop disks and laptop disks differ so I wouldn't recommend setting them to aggressively standby.

---

