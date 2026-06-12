---
title: "How to set display resolution, colour depth and refresh rate permanently 17.04"
date: 2017-12-02
forum: Hardware
---

### Post by ianmanning on 2017-12-02
I'm running Ubuntu 17.04 and have the HDMI output of my machine connected to a Slingbox. The Slingbox will only recognise a limited range of display settings, and the only one that works well (from testing with Windows 10) is 1920x1080, 32 bit, 30Hz. The graphics card is a Radeon HD 4200. 

I have found the xrandr command for setting the resolution and refresh rate, but can't find where to set the colour depth. Can anyone point me in the right direction? I'm a relative Linux novice, so dummies' instructions would be best!

---

### Post by mörgæs on 2017-12-02
First: Are you sure that you would like to invest time in 17.04 which runs out of support in January? You could also use the occasion to do a fresh install of 17.10 and then people could help you using this version.

---

### Post by ianmanning on 2017-12-02
> **mörgæs said:**
> First: Are you sure that you would like to invest time in 17.04 which runs out of support in January? You could also use the occasion to do a fresh install of 17.10 and then people could help you using this version.

That's the second time I've had an answer like that to a "how to" query in a couple of days. From my perspective there are some important principles here:
(a) if you want to create a "set-and-forget" platform (rather than a development or research platform) there isn't necessarily a need to be using the latest O/S release (particularly when the one you're using is less than a year old). You just need a release that offers the features that you require.
(b) the answer to a "how to" question is often possible to supply without requiring the questioner to upgrade to the latest o/s release
(c) regularly upgrading to new o/s releases as soon as they are available can easily create instability (if it ain't broke don't fix it). One of the easiest ways to introduce a problem to a working platform is to perform a major upgrade on it.

While I appreciate that support  is much easier for O/S providers if all users used the same (latest) release of the O/S, from the users' perspective that is not always feasible or advisable (for reasons (a) and (c) above).

---

### Post by mörgæs on 2017-12-03
> **ianmanning said:**
> That's the second time I've had an answer like that to a "how to" query in a couple of days.
Interesting, isn't it? 

I wasn't 
> **ianmanning said:**
> requiring

anything, it was a suggestion to possibly save you a repeated process in January.

---

### Post by ianmanning on 2017-12-03
I appreciate the feedback. My logic is that if I can find the solution to the problem for my current release then I can implement it now and also have no need for any further work in January (as I don't intend applying regular updates to the platform). If it turns out that this is not possible with 17.04, but I discover that it is possible with a later (or earlier) Ubuntu release, then I would upgrade or downgrade at that time.

---

