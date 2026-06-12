---
title: "Weird problem using dual monitors"
date: 2011-03-15
forum: Hardware
---

### Post by o0kojiro0o on 2011-03-15
My two monitors are running at different resolutions on an ATI card. The problem I'm having is that the monitor with the lower resolution has an area where the mouse can be moved off-screen, almost like the system is allowing movement of the mouse on both screens as if they were the same resolutions. It's not a major problem but it's getting a little annoying. Any idea on what could be causing this or any kind of workaround?

ATI 5870 on a first gen i7 running Ubuntu 10.10

---

### Post by o0kojiro0o on 2011-03-16
Bump, anyone?

---

### Post by rizky_ghardoe on 2011-03-16
install your VGA driver first.
:D

---

### Post by ptptaylor on 2011-03-17
I think I have the same problem. It's not a major issue since applications know how far to maximise to right? It is much more noticeable on a lower resolution (transition from 1900 + to <1000 pixels.

---

### Post by squaregoldfish on 2011-03-17
I think it's to do with the fact that X needs to work on a rectangle encompassing the maximum resolution of all monitors.

I have two monitors with resolutions 1680x1050 and 1280x800. For X, I have to set up a virtual screen size of 2960x1050, so on the smaller monitor I'm missing 250 pixels.

I've never found it to be a problem, personally.

Steve.

---

### Post by o0kojiro0o on 2011-03-19
> **squaregoldfish said:**
> I think it's to do with the fact that X needs to work on a rectangle encompassing the maximum resolution of all monitors.

I have two monitors with resolutions 1680x1050 and 1280x800. For X, I have to set up a virtual screen size of 2960x1050, so on the smaller monitor I'm missing 250 pixels.

I've never found it to be a problem, personally.

Steve.

Ah I see, I have 2560x1440 and 1920x1080 so that would mean I'm missing just under 400. Slightly bigger gap so sometimes I lose the cursor for a sec. I only really watch videos on the 1080 screen so it's not that big a deal, but it's still a tad annoying at times. I wish there was some kind of workaround that sets the cursor boundary or something.

---

