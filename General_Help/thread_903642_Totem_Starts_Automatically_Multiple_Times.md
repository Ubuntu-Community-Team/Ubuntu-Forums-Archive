---
title: "Totem Starts Automatically Multiple Times"
date: 2008-08-28
forum: General Help
---

### Post by Twintop on 2008-08-28
Hi all,

I'm running Ubuntu 8.04.1 x86_64. Today, Totem started opening up automatically. Closing/killing it closes the current window, but it reappears several seconds later. Also, when Totem is open it frequently keeps reopening itself and stealing focus.

I've tried uninstalling it using apt-get, but then get an error window that says:

> Couldn't execute command: totem
Verify that this is a valid command.

It doesn't appear that cron is running it (I killed it), but I'm at a loss as to figure out what is causing it. Any help would be appreciated, since this issue is making my laptop virtually unusable!

Thanks in advance!

---

### Post by ExquisiteDeadGuy on 2008-08-28
> **Twintop said:**
> Hi all,

I'm running Ubuntu 8.04.1 x86_64. Today, Totem started opening up automatically. Closing/killing it closes the current window, but it reappears several seconds later. Also, when Totem is open it frequently keeps reopening itself and stealing focus.

I've tried uninstalling it using apt-get, but then get an error window that says:



It doesn't appear that cron is running it (I killed it), but I'm at a loss as to figure out what is causing it. Any help would be appreciated, since this issue is making my laptop virtually unusable!

Thanks in advance!

Try System/Preferences/Preferred Applications click the multimedia tab and make sure totem isn't the default application.

There's got to be an underlying problem though why it keeps trying to do that. Maybe someone with more knowledge can chime in.

---

