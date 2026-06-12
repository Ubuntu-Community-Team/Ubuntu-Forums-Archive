---
title: "Power management tools confusion"
date: 2009-03-08
forum: Hardware
---

### Post by arikg on 2009-03-08
Hi all,

I am struggling to improve battery life on my new Thinkpad X200S. It is supposed to be an ultra low power machine and Lenovo claims ~10 hours of battery life with Vista. I am getting far less than that.

There are a lot of useful power related resources on the net such as this forum, lesswatts.org, thinkpad wiki etc, but the overall impression is a total chaos. There are so many tools: APMD (ok, this one is obsolete, I got it), ACPI, pm-tools, laptop-mode-tools, cpufrequtils, and more. How do all these tools coexist (or not) and interact?? What do I need to have a complete solution?

In my Intrepid installation I have laptop-mode-tools, acpi and pm-tools installed. What task each tool is responsible for? Both acpi and pm-tools provide scripts for suspend and hibernation, how do I know which one is actually running? Do I have to keep the other one?

Thanks a lot for your help,
arikg

---

### Post by tchalvakspam on 2009-03-25
I've had some success with powertop.
(i.e. sudo apt-get install powertop )
The only caveat of that is that powertop only puts those power gains in place for the course of a session.

---

### Post by Axx83 on 2009-05-11
I have x60s, two edition earlier than x200s, I'm finally set with laptop-mode and I think that's the easiest way.

If you have Jaunty, modify /etc/default/acpi-support file allowing laptop-mode, modify /etc/laptop-mode/laptop-mode.conf file setting the various thing that you have to set (the file is easy to understand) and then modify the files in /etc/laptop-mode/conf.d/ putting all those powersaving modes on.

I personally have everything from intel, which makes this pc 101% linux compliant probably if you have other components there's gonna be some issues, I don't know sorry.

Anyway with all these tuning now I have more or less 2 hours of battery, the same as on windows xp.

Never believe the crap the manufacturers say about battery life, my notebook SHOULD have had 8 hours of life but never in his life has lasted more than 3, on windows I mean.

good luck, let me know the results of powertop.

---

