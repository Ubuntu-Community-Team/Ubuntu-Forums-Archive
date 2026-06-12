---
title: "Thinkpad T40, Ubuntu 9.04: Race condition (cpu 100% )"
date: 2009-05-02
forum: Installation &amp; Upgrades
---

### Post by asbesto on 2009-05-02
Fresh and plain install of Ubuntu Desktop on my Thinkpad T40, Centrino 1.5 GHz, 2 GB RAM. Integrated graphic card is a ATI Radeon Mobility M7 LW 7500.

It was **fast like hell with my Ubuntu 8.10**

Now here's the horror:

[CODE]2706 root      20   0  144m  43m 8344 S 50.8  2.1   6:38.90 Xorg               
 1508 asbesto   20   0  246m 149m  23m S 32.6  7.4   8:01.34 firefox  [/QUOTE]          

Xorg at 50% of CPU Usage just switching from a workspace to another, Firefox 3 munching 30% of the CPU being on Google homepage.

The laptop now is slow as a 486sx-33 without coprocessor using a TSENG LAB ET4000. 

this is a **real horror**.

Someone has the same problems?
Some solutions?

I think I'm going back to Ubuntu 8.10 pinpointing xorg and Firefox 2.

---

### Post by asbesto on 2009-05-02
I found a solution.


Add this in the Device section of /etc/X11/xorg.conf:

```

        Option "MigrationHeuristic" "greedy"

```

It seem to work also for INTEL video cards.

---

### Post by mark.kohler on 2009-05-07
This solution also works great on my Thinkpad R51 which has an ATI Radeon RV250 [Mobility FireGL 9000]. Without that option, Jaunty was unusably slow. Just alt-tabbing between windows would cause rhythmbox to skip.

Thank you for this solution.

---

### Post by asbesto on 2010-02-18
... and really I don't understand why software increase bugs instead of usability; why they had to BROKE STUFF that was working instead of keeping it working!!! O_o

---

