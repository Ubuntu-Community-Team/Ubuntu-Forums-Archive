---
title: "Help: VMware &amp; performance..."
date: 2005-11-15
forum: General Help
---

### Post by InGearX on 2005-11-15
What kind of performance could I expect from VMware-Workstation-5(.0.0-13124) on Ubuntu-5.10, hosting Win2000 or XP Pro?

All on a Compaq X1000 - 1.3Gh M, 640MB, 1280x800, Ati Radeon 7500

Would Windows be able to play videos/media just fine? over a network?

Thank you all...

---

### Post by suRoot on 2005-11-15
Video performance is never that great in VMWare - at least relative to the video performance you could get directly from the host.  I mean, it's okay, but you're probably not going to be getting great FPS if you're trying to play games, watch movies, whatever.  There are several good how-to's around here for setting up multimedia under ubuntu, so you'd probably be better off trying that.

Other than that, you look a little light on RAM.  I don't know how much memory you plan to give to the guest OS, but you may run in to issues there - especially if you're planning on switching back and forth between the guest & host.

Overall, I find performance to be acceptable.  I'm running VMWare Player on my laptop (2.4ghz centrino / 1gb RAM) and it really never misses a beat (unless I get greedy and try running two or three guests at once!).

You may want to try running your images under VM Player, too.  I've found it to be slightly less of a resource hog than full-blown VMWare, plus it's free.  You can download it from the VMWare website.

---

