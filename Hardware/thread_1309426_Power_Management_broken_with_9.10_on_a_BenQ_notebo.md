---
title: "Power Management broken with 9.10 on a BenQ notebook"
date: 2009-11-01
forum: Hardware
---

### Post by belgianfries on 2009-11-01
Power management worked quite well for me with 9.04 on my BenQ S73G (besides this power-off bug [http://bugzilla.kernel.org/show_bug.cgi?id=8549](http://bugzilla.kernel.org/show_bug.cgi?id=8549)) but it seems completely broken with 9.10:

- It never seems to suspend/hibernate on battery power after the configured idle time
- It often hibernates right after resume on battery power
- The OS often goes completely sideways on battery power after some 10 minutes: It uses 100% CPU and almost freezes, then I can see lots of "pidof" and "killall" processes and eventually the system becomes completely unresponsive
- The system hibernates instantly when connecting or disconnecting it from AC power even if the battery is fully charged

I have created a bug on these issues, originally because of a crash report that I got frequently after resume: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/459830](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/459830)

I'd just like to know if someone experiences similar problems since 9.10?

Cheers,
Torsten

---

### Post by Jere Retzer on 2009-11-10
I'm having a similar problem with an HP L2000 (similar to the DV 2000). I had to disable power management to prevent the laptop from hanging in a non operational state.

---

### Post by belgianfries on 2009-11-15
I created this bug on gnome-power-management bugzilla: [https://bugzilla.gnome.org/show_bug.cgi?id=602009](https://bugzilla.gnome.org/show_bug.cgi?id=602009)

I think I am going to give it a try with KDE/Kubuntu power management.

Torsten

---

### Post by belgianfries on 2009-11-16
Eventually I found out what the problem was for me. The process causing the trouble was lm-polling-daemon which belongs to laptop-mode-tools.

I have now removed laptop-mode-tools and reinstalled gnome-power-manager, and all seems to work fine again. I guess the upgrade to 9.10 somehow screwed up laptop-mode-tools/its configuration and I think it kinda conflicts with gnome-power-manager anyway.

Finally, I can use my notebook on battery power again!

Cheers,
Torsten

---

