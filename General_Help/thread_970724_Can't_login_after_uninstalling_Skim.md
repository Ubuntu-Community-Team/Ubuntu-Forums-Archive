---
title: "Can't login after uninstalling Skim"
date: 2008-11-04
forum: General Help
---

### Post by moomooranch on 2008-11-04
Hi:

I hope you are doing well.

I am having a problem with Kubuntu 8.10; I am not able to get the display manager to start after I uninstalled Skim. Kubuntu starts normally, and at the login screen, only the background shows (no login box, sessions button, clock, etc). I can login with Ctrl+Alt+F#, but when I rstart kdm with:
sudo /etc/init.d/kdm restart
the same thing happens. If I stop kdm and use:
startx
the kubuntu login animation starts. It takes a long time for the login animation to go away, after which the previous session seems to load, but I get no display except for one program that was running in my previous session. Everything else is black, and Alt-F2 doesn't work so I can't start kwin manually. Sometimes the Skim logo pops up in a system tray with only that one item.

I've tried reinstalling skim to no avail.

I've tried apt-get purge kdm and reinstalling kdm and kubuntu-desktop, but that didn't help either.

I've tried installing UIM and im-switch -ing all locales to UIM

I have tried dpkg-reconfigure on kdm, skim, uim, kwin to no effect.

Has someone else experienced this issue or have some insights?

Thanks,
/mmr

---

### Post by mildlycrazy on 2008-12-30
mmr,

I had the same problem and I solved it by completely uninstalling the kde-environment using the command on this page
[http://psychocats.net/ubuntu/puregnome](http://psychocats.net/ubuntu/puregnome)  (I did a purge instead of just remove)
You can omit the last part that installs gnome unless you want it installed.
After that I just rebooted the machine and reinstalled the kubuntu-desktop package. It's not the most elegant solution, but it worked for me.

---

### Post by moomooranch on 2009-01-11
Thanks mildlycrazy. I reinstalled kubuntu after all but your tip will come in handy next time if something similar happens. Hopefully someone else will find this useful as well.

---

