---
title: "[SOLVED] Avant WIndow Navigator Problems"
date: 2008-07-16
forum: General Help
---

### Post by SlalomMan on 2008-07-16
Hey all,
I've been using Avant Window Navigator for some time; probably since Feisty. It used to be able to interface with pidgin somehow so that when I received a message, the task icon for my chat would flash or bounce or do whatever I set it to do.

I downloaded it again when I did a fresh install of Hardy, and it no longer does that. I've tried both the avant-window-navigator and avant-window-navigator-bzr packages. Is there some setting in the preferences window that I'm missing? 

Any help is appreciated.

---

### Post by moonbeam on 2008-07-16
AFAIK it's due to a change in pidgin configuration.

In pidgin you need to go to 

tools/plugins/message notificatin

Enabled "Message Notifications"

Configure Message Notifications

choose "set Window Manager Urgent Hint"

---

### Post by imnewtolinux on 2008-07-16
Hi,

I'm very new to linux, and I just installed AWN.  I have a different problem (I didn't want to make a new thread), and I also need some help.  My dock never wants to stay on the bottom on the screen... it tends to move up where the windows are.  This is very annoying... are there any fixes to this?

[edit] nvm... I did something stupid in the setting which I guess forced it to hide. still getting used to stuff :P

---

### Post by SlalomMan on 2008-07-16
Thanks, moonbeam. I never would have thought to look there; this also solved my other problem; pidgin used to not notify me of updates in group chats, now that *should* be fixed.

and imnewtolinux, it's great that you're trying to find solutions to your problems instead of moving back to windows or osx like many linux users who have problems do.

---

### Post by stoffe on 2008-10-07
> **moonbeam said:**
> AFAIK it's due to a change in pidgin configuration.

In pidgin you need to go to 

tools/plugins/message notificatin

Enabled "Message Notifications"

Configure Message Notifications

choose "set Window Manager Urgent Hint"

I don't seem to have that plugin and I can't find it in the repos either, am I missing something obvious? Thanks! :)

---

