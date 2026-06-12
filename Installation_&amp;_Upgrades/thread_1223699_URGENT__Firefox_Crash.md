---
title: "URGENT :: Firefox Crash"
date: 2009-07-26
forum: Installation &amp; Upgrades
---

### Post by anuraggautam on 2009-07-26
Hi,

I was trying upgarde to firefox 3.5 and i came to know a thread for the same topic.One of the user suggest to run following command "sudo aptitude install firefox-3.5 firefox-3.5-branding firefox-3.5-gnome-support && sudo aptitude purge firefox-3.0 firefox-3.0-branding firefox-3.0-gnome-support"

I did that and i found i am unable to open my firefox.

Please help me to come up with such a drastic problem.Many of the data and bookmarks are saved in my firefox.Am i loosed all of them ?

Anyway I have a backup of previous firefox on my external disk , will it help ? How to roll back this change ,Please help me .

Regards

---

### Post by quixote on 2009-07-27
The "purge" part of the command completely removes a program, including all your personal settings.  Not good in your case.  The backup of the program doesn't contain your settings.  Those are in your home directory, under a hidden dir called .mozilla/firefox/*some-weird-letters-and-numbers*.default.  If you start nautilus (aka File Manager) there's an option on the View menu to show hidden files. So if you have a backup of your /home, then that's where your old settings will be.

If you're using Jaunty, Firefox 3.5 is available under Synaptic, and that's a much more foolproof way to install. (System > Administration > Synaptic) Type "firefox-3.5" in the search box at the top.  If you check just the one labelled "firefox-3.5" it should pull in all the other files you need.  Assuming you're running gnome, not kubuntu, be sure it's getting the firefox-gnome-support file too.

Before you do that, it's probably a good idea to run, in Synaptic, Edit > Fix Broken Packages.  Also hit the Reload button, so that you can be sure to get the latest versions of what's in the repositories.

Once firefox is installed, copy your backup profile, if you did have one, into the new .mozilla/firefox-3.5/ directory.  Rename the new default profile that you don't need something else, so you have it if you need it, and move it out of that firefox-3.5 directory.  If there's only one profile in there, I think you don't have to bother with profilemanager, which makes things a bit simpler.

If no backup, then I'm afraid there's some tedious days ahead getting things set back up.  :(

Hope this helps.

---

### Post by quixote on 2009-07-27
Postscript:  I haven't used aptitude much, but I understand it's good at retracing steps, so maybe there's some way to "undo" the purge and get your settings back that way.  Maybe see what it says about "aptitude" on the ubuntu wiki?

---

