---
title: "Bug marked duplicate of a bug it is not a duplicate of and closed as invalid"
date: 2008-12-01
forum: General Help
---

### Post by foxmajik on 2008-12-01
Hello,

I filed this bug report:

[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/302984](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/302984)

It was marked invalid and closed as a duplicate of this bug:

[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/9441](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/9441)

However, they are clearly different issues.

The second bug is marked fixed and was marked fixed before I filed my bug.

If my bug were fixed, I would not have had any reason to file it in the first place, which would result in a vortex of invalid logic and a black hole that would consume the universe.

There does not appear to be a way to change the status of the bug from "invalid/duplicate" to "no it's not/open."

How do I make fixy?

---

### Post by jgoguen on 2008-12-01
The bug in Launchpad may not be the same as what you're experiencing, but the [upstream bug report](http://bugzilla.gnome.org/show_bug.cgi?id=125618) that the second bug links to appears to be the same issue.  Can you please look at the upstream report and confirm whether or not that's close to (or exactly) what you're experiencing?

---

### Post by foxmajik on 2008-12-01
> **jgoguen said:**
> The bug in Launchpad may not be the same as what you're experiencing, but the [upstream bug report](http://bugzilla.gnome.org/show_bug.cgi?id=125618) that the second bug links to appears to be the same issue.  Can you please look at the upstream report and confirm whether or not that's close to (or exactly) what you're experiencing?

The bug report on gnome's bugzilla matches my issue but the bug my bug is marked defendant on does not.

My bug more accurately represents the problem so the other bug should be marked invalid and mine should be kept open.

Also, this begs two questions:

1. The problem has existed since 2003 (five years), why is it not fixed?
2. Why is the package included in the production distribution if it is known to be broken?

It seems like including a known broken package that is supposed to provide visual aid would detract from the user experience in a way that expresses lack of interest in usability and a failure to acknowledge the ergonomic needs of the vision impaired.

---

### Post by jgoguen on 2008-12-01
The reason your bug was marked invalid and duplicate of the other one is most likely simply because the other bug came first.  I've never seen a bug tracker where devs marked the bug that came first as the duplicate.  To attempt to answer your questions:

1. Ask the GNOME developers.  It may simply not be high enough on their priority list.  Like any other large project, they have to make hard decisions about what bugs to push to a later release.  Honestly though, I've never seen the problem and can't reproduce it.  If you can comment on the GNOME bug with exactly how you reproduce the problem, that would be helpful to them.  You could also then subscribe to the bug to get updates from the GNOME bug tracker.
2. Probably because the alternative would be to stick with GNOME from pre-2005, which would be worse.

---

