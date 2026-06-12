---
title: "Clean installation: how-to, and why?"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by Brian Vaughan on 2009-04-24
I gather that the conventional wisdom is that it is better to perform a clean install than an upgrade.

My first question is, how is that done? I've got three partitions: one with / mounted, one with /home, and one that's the swap partition. Do I simply delete the partition with / mounted, then use the installer from the CD or flash drive? Or is there more to the process than that?

My second question is, is it really such a good idea to do a clean install, rather than an upgrade? I can see the point of having a consistent set of packages, and the base package setup may have changed. On the other hand, I've installed a lot of optional packages over the last six months, and I don't relish the thought of reinstalling them all piecemeal.

---

### Post by pbpersson on 2009-04-24
Many people just do an upgrade and it runs flawlessly.

You have your personal data on a separate home partition, so do an upgrade and if it does not work, do a fresh install.

What version are you going from and to?  I would not suggest that you skip  versions - for instance, going from Hardy Heron to Jaunty Jackalope.

When you do a fresh install, you would tell it where /, /home, and swap are and tell it to format / but NOT format /home

---

### Post by HPD2 on 2009-04-24
> **Ellen2 said:**
> Have you tried installing it through Wubi. Its a clean way to fresh install Ubuntu. Try it from here: [http://wubi-installer.org/](http://wubi-installer.org/)

unless I am mistaken isn't wubi only for running Ubuntu through windows?

---

### Post by Brian Vaughan on 2009-04-24
I'm currently using 8.10, so I wouldn't be skipping any versions.

I'd started out with 8.04, then did an upgrade to 8.10, with only a few minor difficulties, but I'd been using 8.04 for only about a month at that point, and I'd customized it a lot less than I have since, so I thought that might complicate matters.

The suggestion to simply try an upgrade first makes sense. Of course, I'll burn an installation CD before I do that, as a back up plan.

I'm planning to wait about a week anyway, when the load on the servers will have gone down, and I'll have more time to work on it anyway.

---

