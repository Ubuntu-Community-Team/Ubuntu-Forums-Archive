---
title: "Problems with logging in and out using X and ATI fglrx"
date: 2005-11-14
forum: General Help
---

### Post by magnusbb on 2005-11-14
Hello.

I have a Acer notebook with a ATI Mobility Radeon 9700 card, and am using the proprietary fglrx driver.

But when I log out of my current session, and GDM is about to start, the screen resolution is completely wrong. It's completely unusable. I have to use CTRL + ALT + BACKSPACE to start X over again. Then it works perfectly.

And I can live with this solution, had it not been for this:

After a few times, when using CTRL + ALT + BACKSPACE to restart, say, 3 - 4 times, within 2 - 3 hours, it suddenly refuses to restart. And there I am stading at the standard UNIX login prompt. No X server, no GDM, and I have to login the old way, and use "startx".

Has someone else experienced this? I have tried other drivers for my card, "ati" and "radeon", and both behave the same on the restarting issue. After a few restarts, X refuses to start without logging in the old way, and invoking startx. Is there something with time-outs, perhaps?

---

### Post by Remmelas on 2005-11-14
Couple of things.
1) edit your xorg.conf file, and only enable the resolution you want gdm to be.  This I think would likely solve your problem all together, for example:
```
        SubSection "Display"
                Depth           24
                Modes           "1152x864"
        EndSubSection
```

2) when gdm fails to restart, you can log in at the console as you said, but instead of startx, do ```
sudo /etc/init.d/gdm restart
```

---

### Post by magnusbb on 2005-11-14
Ah, thank you very much!

That's it.

---

