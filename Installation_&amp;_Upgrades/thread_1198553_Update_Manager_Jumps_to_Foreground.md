---
title: "Update Manager Jumps to Foreground"
date: 2009-06-27
forum: Installation &amp; Upgrades
---

### Post by SeanOB on 2009-06-27
Hi Everyone!

With my upgrade to 09.04 I've noticed that rather than getting a little icon on the panel when updates are available that I'm now seeing the entire update manager tool launch and jump to the foreground.

This wouldn't be a big deal except that it's occuring on my media / mythtv frontend box.  So we're watching a show and then BAM! updates available window pops up in the foreground.

Is there an option that I'm missing somewhere?  How can I get this back to just having a little icon on the panel in the background.

Thanks!

Sean

---

### Post by starcraft.man on 2009-06-27
I think it's the following entry in the gconf-editor (launch via alt+f2 run "gconf-editor"):

/ > apps > update-notifier > auto_launch

Set to off. I think this is the entry that results in the auto launching of the update manager upon a criteria.

If that doesn't work, I'd just turn all updates off from the software sources page of the admin menu and update manually when you feel like it (when not watching your mythTV).

---

