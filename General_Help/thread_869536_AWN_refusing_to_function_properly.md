---
title: "AWN refusing to function properly"
date: 2008-07-24
forum: General Help
---

### Post by SSB on 2008-07-24
When I booted up Ubuntu a few minutes ago, all my launchers worked, but all the applets showed that white line that appears when they don't load properly. Understandably flustered, I removed them all and redid all the applets. But when I did that, the calendar applet just showed up way too big and no launchers showed up. I logged in again and now I just had applets, though the launchers showed up in the awn manager. Additionally, there were a few blank launchers that I could not delete. I tried to remove everything AWN-related and reinstall it, but all the old settings came up. I tried looking for ~/.awn, but I found nothing. I deleted ~/.config/awn, but that did nothing. I saw awn needed to be updated, so I updated. Same problems.

So how can I either fix this or remove all my old configuration for AWN? I'm updating from the bzr repos, reacocard's or whoever-the-who it is.

---

### Post by Lakjin on 2008-07-25
i dont know how to fix your problem, but may i suggestion a thing called cairo dock?

i think its a lot better then AWN.

---

### Post by SSB on 2008-07-25
I'm trying out cairo dock right now, but I think I like AWN more. This one is far too flashy for me.

---

### Post by moonbeam on 2008-07-25
Make sure you have the Launcher/Taskmanager applet activated in awn-manager.  if you do then try removing it and adding it again (awn will likely crash).

The clock/cal issue was a temporary issue with trunk.  I suspect the packages were made a bad time for that applet.  It's been fixed in trunk so it should be resolved on the next update.

---

