---
title: "Problems with new monitor"
date: 2008-10-09
forum: General Help
---

### Post by Farajamo on 2008-10-09
So I recently got a 22" monitor by HANNS.G model# HG216D. It currently hooks up directly into my geForce 8600.  But unfortunately, I've been having problems with it.  I had to replace my xorg.conf with the standard because I had some display issues, and wanted to start fresh.  I went to appearance and changed the effects to "custom".  When it asked me if I wanted to activate my Nvidia drivers, I said yes.  Although when I restarted, the loading screen was a success, but the login screen never came.  Instead I was greeted with "No signal input".  Would appreciate the help if anyone knows a fix.

---

### Post by schauerlich on 2008-10-09
Try to get into a terminal with Ctrl+Alt+F1. If you can't, then follow the first part of [this guide](http://www.psychocats.net/ubuntu/resetpassword) to boot into recovery mode. Either way, once you get to a command line, run

```

sudo dpkg-reconfigure -phigh xserver-xorg

```

You can leave off the sudo part if you're in recovery mode.

---

### Post by Farajamo on 2008-10-09
Okay I did that... should I be able to turn on the driver now?

---

### Post by schauerlich on 2008-10-09
> **Farajamo said:**
> Okay I did that... should I be able to turn on the driver now?

When you start x you will hopefully have a working xorg.conf

---

### Post by Farajamo on 2008-10-10
When I boot in Ubuntu, it starts in low-graphics mode, and gives me the option to configure my monitor.  Since my brand didn't appear on the menu, I picked generic 1680x1050 widescreen, and hit okay.  It went black for a few seconds, then said "no signal input". It does this until I boot from the liveCD and copy over a fresh xorg.conf.

---

### Post by Farajamo on 2008-10-15
Also, when I go fullscreen in videos, it gets really choppy.

---

### Post by Farajamo on 2008-10-24
I was wondering if upgrading to 8.10 would help fix my problem.

---

