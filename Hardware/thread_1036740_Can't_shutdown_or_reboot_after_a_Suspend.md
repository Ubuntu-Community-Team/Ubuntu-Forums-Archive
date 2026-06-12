---
title: "Can't shutdown or reboot after a Suspend"
date: 2009-01-11
forum: Hardware
---

### Post by Cnhy on 2009-01-11
I'm running Ubuntu 8.10 on an Asus X58C laptop.

Suspend and Hibernate both seem to work fine ... except for a small quirk with Suspend. 

After Suspending, the system seems to resume without any problems. However, if I then try to restart the system (System > Shut Down > Restart) it hangs with the progress bar at 'empty', and I have to force it with the power button. The same is true of [FONT="Courier New"]sudo reboot[/FONT] in the Terminal.

If I haven't used Suspend, Restart works normally. 

*EDIT FOR CORRECTION:* Shut Down (System > Shut Down > Shut Down) seems to work normally regardless.

I have disabled apmd (under System > Administration > Services) but this has had no effect.

---

