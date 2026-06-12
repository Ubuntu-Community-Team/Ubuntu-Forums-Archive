---
title: "CUPS 1.3.9-2 downgrade"
date: 2008-11-26
forum: Hardware
---

### Post by timboellis on 2008-11-26
How can i either downgrade or reinstall cups with an older version?

---

### Post by tgalati4 on 2008-11-26
How did you install the 1.3.9-2 version in the first place?

If you added a new repository, then you should be able to do the following:

>sudo apt-get remove cupsys

Go into synaptic repositories and uncheck or remove the offending repository.

Then add cups back through synaptic or close synaptic and:

>sudo apt-get install cupsys

This should restore cups to the default, supported version of cups.  Remember, cups is closely tied to your kernel.  Change one or the other and breakage occurs.

---

### Post by timboellis on 2008-11-26
Well the problem is that the version of cups does not work on my PC as get a child error 1 .

However been looking around and found that going to a previous version wil resolve the issue

---

