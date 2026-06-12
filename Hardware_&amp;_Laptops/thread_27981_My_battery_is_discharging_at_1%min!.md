---
title: "My battery is discharging at 1%/min!?"
date: 2005-04-18
forum: Hardware &amp; Laptops
---

### Post by Kryton on 2005-04-18
Hi,
  I've been watching this forum closely lately and have taken much of the advice given yet none of it seems to be working. I have a 1.5 year old laptop (2500+ Mobile Barton core) and am trying to get Ubuntu going on it. So far I have managed to set everything up fine but my problem is as soon as I unplug the AC cord the battery discharges at an alarming rate (1% per minute) and occasionally it will drop from 80%+ to 6% for no apparent reason.
  Reading the threads I have installed powernowd (and the Gnome applet etc. showing it actually working) and laptop-mode-tools (and started it, I think?) but neither have had an affect on this problem. Initally I thought it might have been Beagle running and firing Mono up every couple of minutes but this has been removed yet the problem persists still.  ](*,) 
  The laptop is not 'hot' like the others too. Does anyone know what is causing this usage?

- Kryton

(Edit: I've also tried disabling ACPI with the kernel options but this means that no battery status shows and I am 'always on AC power' so I assume I have ACPI that works?)

---

### Post by soul_rebel on 2005-04-18
i suggest you to monitor anything you can using gkrellm.
try to set an aggressive power saving for the hd with hdparm

It could also be a battery's "physical problem"

---

### Post by Kryton on 2005-04-18
[QUOTE=soul_rebel]i suggest you to monitor anything you can using gkrellm.
try to set an aggressive power saving for the hd with hdparm

It could also be a battery's "physical problem"[/QUOTE]

I doubt it is a physical problem as Windows XP runs happily for a couple of hours (around 4hrs if it's not being pushed). What am I looking for in gkrellm?

- Kryton

---

### Post by soul_rebel on 2005-04-18
in gkrellm you are lookin at disk and cpu usage (maybe ram and swap too)

---

### Post by Kryton on 2005-04-18
Okay I have that installed. It appears as if laptop-mode isn't starting with the laptop and cupsd is preventing the disk from spinning down correctly - watching with top and gkrellm showed a nice correlation in the disk hits  \\:D/ . How can I solve this at boot rather than manually having to sudo laptop-mode start every time, where do I adjust the spin down timings to be faster too? Also I am wondering if I should revert to the original hdpram settings, I have enabled the multi-sector mode as described [here](http://ubuntuforums.org/showthread.php?t=24416).

Thanks for the help.

- Kryton

---

### Post by soul_rebel on 2005-04-18
/etc/hdparm.conf to configure your drives, set an aggressive spindown. Other optimizations should not interfere so much.

You can add this "laptop-mode" at startup if you think it helps. that's not a trivial task and there a lot has been written about.

I want to hear from you the final performances of your battery when everything is set up. :)

---

### Post by Kryton on 2005-04-18
[QUOTE=soul_rebel]/etc/hdparm.conf to configure your drives, set an aggressive spindown. Other optimizations should not interfere so much.

You can add this "laptop-mode" at startup if you think it helps. that's not a trivial task and there a lot has been written about.

I want to hear from you the final performances of your battery when everything is set up. :)[/QUOTE]
 Right I've done some logging. Thanks for the help soul_rebel :) It isn't exactly Windows standard yet but the battery life has improved significantly. I also dropped the /etc/apci/power.sh hdparm -S setting to 3 from 12 (meaning 15secs to spindown rather than 60secs) though the benefit with gkrellm showing little drive I/O is probably not visible.

So far:
  19:30 BST - 100% Battery
  19:45 BST - 85% Battery
  19:50 BST - 80% Battery (Active tasks have been OGL Snakes, gkrellm)

That's extended it to around 100mins battery life but that is still without doing a significant deal. Is there ATI Powerplay support in the drivers, the OGL Snakes might be running in 32bit rather than scaling to 16bit?

Thanks

- Kryton

---

### Post by Kryton on 2005-04-18
Right, was going fine until now... it just jumped from around 55% to 6% and up popped the battery notice. All I tried to do was open Kylix! This caused a bit of high CPU usage for a couple of seconds whilst the IDE started and some disk activity.  ](*,)

---

### Post by armeck on 2005-04-18
I am watching this thread closely as I am having some horrible battery life as well.  A tfirst I though tit was just my imagination but my battery drains in about 1.5 hours as well...:|

---

### Post by Psquared on 2005-04-18
Yet another reason not to upgrade to Hoary.  :roll: 

My laptop works great in Warty and I get the same battery life (even though there is no auto hibernate or suspend) as in XP - about 2.0 hours with moderate-heavy use; 2.0-2.5 hours with light-moderate use; 3 - 3.5 hours with intermittent use.

Toshiba 35X 331 with 1.5 Pent M and 512mb RAM.

Two things that must be a power drain are the size of my monitor (15.5 in.) and that I have wireless running all the time.

---

### Post by gnutux on 2005-04-18
one way to conserve energy is just dim your monitor to the dimmest as possible.

gnutux

---

### Post by soul_rebel on 2005-04-19
I also think that using dark colors can help

---

### Post by Kryton on 2005-04-19
[QUOTE=gnutux]one way to conserve energy is just dim your monitor to the dimmest as possible.

gnutux[/QUOTE]
 Even so, that doesn't explain why the battery usage is so phenomenal. I know that Windows auto-dims the screen but even on the lowest screen brightness the battery usage is still very high!

---

### Post by armeck on 2005-05-02
Maybe one possbility is that the battery actually isn't discharging any faster, but Hoary just *thinks *it is? :???:

---

