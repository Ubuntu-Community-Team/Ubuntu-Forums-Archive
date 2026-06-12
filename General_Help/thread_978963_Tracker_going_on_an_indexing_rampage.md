---
title: "Tracker going on an indexing rampage"
date: 2008-11-11
forum: General Help
---

### Post by emakarov on 2008-11-11
Hello,

My tracker (trackerd and tracker-applet processes) seem to go crazy.

(1) They take 100% of one of the two processors.

(2) The statistics from the applet menu says it indexed > 1.6 million files whereas Computer | Fylesystem | Properties says that there are only ~ 300,000 files. The size of ~/.cache/tracker/file-index.db is 105M, and the size of of file-meta.db is 974M. There is another operating system on the same hard drive, but "Index mounted directories" is unchecked in the indexer preferences.

(3) I don't know exactly when it started behaving like this: it used to run only occasionally. Then when it started working constantly, "Pause all indexing" seemed to stop it. Then, even while pausing, the CPU was still 100% busy. I had to kill tracker with "kill -9". (Now, after about a month of not running tracker, pausing works again.)

(3) I unchecked tracker and tracker-applet in Systems | Preferences | Sessions, but this did not help. They kept starting when the computer booted up. I removed those entries completely from Sessions and removed tracker-applet.desktop and trackerd.desktop from ~/.config/autostart -- this did not help either. Finally, I removed *.desktop files from /etc/xdg/autostart, and this finally prevented them from starting. Now I see that besides ~/.config/autostart there is ~/.config/etcxdgautostart, which still has tracker files -- was that the reason?

I would appreciate any help in making tracker behave normally.

Thank you,
Evgeny

---

