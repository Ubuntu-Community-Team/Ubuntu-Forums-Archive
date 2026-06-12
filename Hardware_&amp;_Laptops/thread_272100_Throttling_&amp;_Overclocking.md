---
title: "Throttling &amp; Overclocking"
date: 2006-10-05
forum: Hardware &amp; Laptops
---

### Post by ahaslam on 2006-10-05
Hi, 

I have an old laptop with an AMD Mobile Sempron @ 1600Mhz.
I'm interested in two things:

Firstly I'd like to have better throttling control, at the moment it changes from 800Mhz to 1600Mhz as it's required. I'd like to have more stages to keep it cool & quiet, along with saving power. If this is possible, how would I do it?

Secondly, I'd like to experiment a little with overclocking. Is it possible to increase the frequency of either the cpu or fsb (or anything else) & how would I do this?

Any other options for achieving similar results would also be appreciated.

Thank you,

Tony.

---

### Post by dphipps on 2006-10-05
I would like to know about this too.  I have a laptop with an Athlon4 at 1.2Ghz and it only clocks down to 800Mhz.  If I could get it to clock down to around 500Mhz or so that would realy help with my battery life.

---

### Post by ahaslam on 2006-10-14
Any Ideas :-k

---

### Post by Kateikyoushi on 2006-10-14
I am not sure it works wuth amd processors but I used cpufreq from commandline to set the clockspeed of my cpu.

Try overclocking from bios even in windows there aren't many fsb tweaking softwares.

---

### Post by Frogger on 2006-10-14
How would I use cpufreq and what hardware would it work on?
I have Celeron M laptop that i would like to see better battery life out of.

---

### Post by Kateikyoushi on 2006-10-14
Unfortunately it requires enchanced speedstep to work on Intel Mobile processors, which has been cut off from the celeron models.

[LINK]("http://www.mobilityguru.com/2004/03/09/does_everything_have_to_be_a_centrino/page3.html")

---

### Post by ahaslam on 2006-10-15
Hi, thanks for your reply.

The closest that I found was 'cpufreqd' - I installed this (had to remove powernowd). Could you explain how to configure it?

Cheers.

---

### Post by Kateikyoushi on 2006-10-15
I onnly used it to set my cpu freq to minimum, but seems the recent versions changed and not for the better.

You can get help and read the manual with the following commands.

```
cpufreqd --help
man cpufreqd
```

Or read it [here]("http://cpufreqd.sourceforge.net/manpages/").

Seems creating profiles isn't hard check the cpufreqd-get manual.

The version I still use oonly required me to pass this line and set my cpu to lowest speed. cpufreqd -f 1, now that was more comfy.

---

### Post by ahaslam on 2006-10-15
Thanks for the help, though it seems that I can only set either 800 or 1600MHz, the same as powernowd did on demand.

I guess that these limitations come from the sparse BIOS settings. Overclocking was only an interest, but it would have been nice to have more throttling levels. :(

Tony.

---

### Post by Kateikyoushi on 2006-10-15
Might be that the cpu does not have more multipliers or levels.
I have these multis 6,8,9,10 intel thought 7 is not neceserry and personally I would rather have 7 than 9 the power consumption and heat is almost same on that level.

---

