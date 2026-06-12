---
title: "How do I report a crash?"
date: 2008-09-16
forum: General Help
---

### Post by serpentine_bull on 2008-09-16
I've recently upgraded to ubuntu 8.04, and everything is pretty stable, except that I've noticed a few crashes. Having worked as a QA tester for quite some time, my reaction was not to complain, but rather to gather as much information as possible and try to repro(duce) the crash as many times as possible. So far, I know that the crash only occurs when audio is playing, and it takes a while to reproduce. (The crash has only occurred while rhythmbox or VLC media player is open, but no short time after either is opened.) This seems to have something to do with having audio play, but I'd like to dig in deeper and get some callstacks or something. Does anyone know what would be useful to the programmers, or how I could get it? Thanks for your time.


Also, in the meantime, are there any alternatives to rhythmbox and VLC that are known for remarkable stability? W/O metal, computing is kind of... boring.

---

### Post by spiderbatdad on 2008-09-16
you should have the program "apport" installed via synaptic package manager. It handles crash detection and reporting. In order to complete a crash report, you need a launchpad account.
[https://launchpad.net/](https://launchpad.net/)

---

