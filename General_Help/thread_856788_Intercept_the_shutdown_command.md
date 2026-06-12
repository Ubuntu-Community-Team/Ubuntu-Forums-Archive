---
title: "Intercept the shutdown command"
date: 2008-07-11
forum: General Help
---

### Post by puffyzacd on 2008-07-11
Hey all,

I've been working on a little project that I could use some help on. When the user clicks on the "Shutdown" or "Restart" buttons, I want to be able to run some checks and maybe present a dialog asking if we should continue shutting down or not.

My specific situation is that I'm running a mythtv backend that I normally shut down at night because I rarely record anything after midnight and I want to save on electricity :). However, every once and a while I'll accidentally shut it down while it's in the middle of doing something like recording or transcoding, which is undesirable. I'd like to be able to check if the backend is busy (probably using the mythshutdown command), then present a dialog to the user and maybe do some more things after that...

I've tried a couple things which didn't turn out very well:
[LIST=1]
[*]I tried to add shutdown scripts in /etc/rc0.d and /etc/rc6.d, but I couldn't get them to be executed before closing the running programs and the session. And even if I could get this working, I'm not sure if it would be possible to stop the shutdown process once it had started.
[*]I tried to make a panel launcher which behaves similar to the "Quit..." applet but launches my own shell scripts instead. The closest I got was a drawer with several icons inside for restart, quit, etc. The look and feel of this was not very close to the "Quit..." applet or the "Quit..." item in the main menu applet.
[/LIST]

So that's where I stand. If any of you have some advice for me, I would love to hear it. Thanks! :)

---

### Post by puffyzacd on 2008-07-11
bump

---

### Post by puffyzacd on 2008-07-12
Nobody has any ideas? Maybe this is impossible after all?

---

### Post by koenn on 2008-07-12
A bit impatient, are we ? Bumping after 1 hr ...


When you use kill scripts (init scripts starting with K.. ) the order is inportant, as is the run level (rc directory) where you axecute them from. In this case you want a K-script that runs when you're about to leave run level 2, before gdm shuts down - probably before anything else - so thats a K-script in rc2.d with a very low (or high, I don't know the order for kill scripts) number

Another option are scripts and config files in /etc/gdm. gdm.conf or gdm.conf-custom might let you re-define the reboot / shutdown / .... commands that are used in the desktop environment, so possibly in stead of calling 'shutdown', you can call a custom script that does some checks before shutdown.

---

### Post by puffyzacd on 2008-07-12
Thanks for the advice, I will look closely at what you mentioned and if I have some success I will post here. :)

---

