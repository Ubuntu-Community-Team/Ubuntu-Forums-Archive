---
title: "How do I roll-back a recent change/update? (new power management problem)"
date: 2016-07-07
forum: Hardware
---

### Post by edsvoboda on 2016-07-07
I've been running Ubuntu 16.04 (Gnome) on my Dell Precision M4600 with no power management or shutdown problems since 16.04 was released.

I've been updating my system about every 1-2 days, usually doing it by simply agreeing to the "updates available" dialog that usually appears each morning.

However, after updating this morning, I found that my system would no longer power-off automatically when shutting down. I've tested this over several cycles.


I'd like to look at the list or log of what has been updated in the past day or two and troubleshoot from there. I don't want to invest much time so my strong preference would simply be to roll back anything that might affect shutdown. I presume a change was made in one of the most recent package updates that broke something.

Where do I look?

---

### Post by Martin.Weinberg on 2016-07-07
You can look at the apt history to get a clue about what package might be an issue.  For example:

```
less /var/log/apt/history.log
```

or

```
tail -n24 /var/log/apt/history.log
```

Once you've worked out which package it was that caused your problem you  can force the version of that package to the one that worked and then  lock that package to that version so that you won't get further updates.

That said, I don't recall any upgrade to powermgt, gnome-power-manager, etc.  I'm sure you've already checked your power management settings, but wouldn't hurt to look again.  Or perhaps you installed the caffeine indicator or some other application is inhibiting lock screen, etc.

---

### Post by edsvoboda on 2016-07-07
My problem disappeared. No idea what happened but I can no longer reproduce.

Thank you for your response. That log may be useful in the future!

---

