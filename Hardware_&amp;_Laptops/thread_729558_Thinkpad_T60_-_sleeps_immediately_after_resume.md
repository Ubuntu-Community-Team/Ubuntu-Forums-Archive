---
title: "Thinkpad T60 - sleeps immediately after resume"
date: 2008-03-20
forum: Hardware &amp; Laptops
---

### Post by amd-64 on 2008-03-20
Thinkpad T60 8744-5BU ATI X1400 graphics - fglrx driver, atheros A/B/G/N wireless and Intel T7200 Dual Core CPU. Running Kubuntu Gutsy with 2.6.22 64-bit kernel and Hardy with 2.6.24 64-bit kernel (dual boot). 

Everything works, really. One annoyance is resume from suspend, on resume the machine immediately goes back to sleep. I suspend from the command line, Fn-F4 or kde menu. This repeats for one or two cycles and then the machine stays up as intended. 

I would like to know why this is happening, if there is a solution, and how to debug this problem. 

Any help is appreciated.

---

### Post by amd-64 on 2008-04-19
Update

Now running Hardy, and figured out how to suspend and resume. I copied the hal file from gutsy to hardy and now hardy suspends really well, and fast too. After 20 suspends, I have not seen anymore cycling through suspend and resume this far. 

Simply copy 

/usr/share/hal/fdi/information/10freedesktop/20-video-quirk-pm-lenovo.fdi 

to hardy and try it yourself. If you do not have Gutsy installed, download the deb for hal-info, uncompress it using dpkg -x, and then copy the file.

---

### Post by phiral on 2008-04-25
Hi!
i'm also running hardy on a t61, with the intel X3100 adapter and cant make this problem go away.

it suspend nicely, but on "lid open" or "fn" it resumes
and immediately suspends again.

i remember reading something about acpid receiving a lid event or something that was issued on suspend but got received only on resume. either way it happens, on lid open or on fn (to resume).

tried copying 20-video-quirk-pm-lenovo.fdi from gutsy, which is quite different from the one in hardy, but got no success.

any idea or update on this problem?

Thanks!

---

### Post by paulderol on 2008-04-26
i was under the impression that the flgrx driver did not support suspend/resume. are you using the ati binary, because there is a known, heavy duty issue with 3d acceleration and suspend/resume in this situaition...

---

### Post by amd-64 on 2008-04-26
Looks like the lid event is kicking in. Check the log files and see if this is true. Sometimes using more than one suspend package is the culprit. Use only one at a time.

I am using the latest drivers from ati. There are no issues with suspend/resume in the binary fglrx.

---

### Post by phiral on 2008-04-26
i have acpi-support and pm-utils currently instaled. 
triggering suspend trough fn+f4 [which causes it to suspend after resume, even without closing the lid] gives this in pm-suspend.log : 
```

Sat Apr 26 21:44:41 BRT 2008: running suspend hooks.
===== Sat Apr 26 21:44:41 BRT 2008: running hook: /usr/lib/pm-utils/sleep.d/00clear =====
===== Sat Apr 26 21:44:41 BRT 2008: running hook: /usr/lib/pm-utils/sleep.d/05led =====
===== Sat Apr 26 21:44:41 BRT 2008: running hook: /usr/lib/pm-utils/sleep.d/10NetworkManager =====
===== Sat Apr 26 21:44:41 BRT 2008: running hook: /usr/lib/pm-utils/sleep.d/20video =====
kernel.acpi_video_flags = 0
===== Sat Apr 26 21:44:41 BRT 2008: running hook: /usr/lib/pm-utils/sleep.d/49bluetooth =====
===== Sat Apr 26 21:44:41 BRT 2008: running hook: /usr/lib/pm-utils/sleep.d/50modules =====
===== Sat Apr 26 21:44:41 BRT 2008: running hook: /usr/lib/pm-utils/sleep.d/90clock =====
===== Sat Apr 26 21:44:43 BRT 2008: running hook: /usr/lib/pm-utils/sleep.d/94cpufreq =====
===== Sat Apr 26 21:44:43 BRT 2008: running hook: /usr/lib/pm-utils/sleep.d/95led =====
===== Sat Apr 26 21:44:43 BRT 2008: running hook: /usr/lib/pm-utils/sleep.d/99video =====
Sat Apr 26 21:44:43 BRT 2008: done running suspend hooks.
Sat Apr 26 21:44:59 BRT 2008: running resume hooks.
===== Sat Apr 26 21:44:59 BRT 2008: running hook: /usr/lib/pm-utils/sleep.d/99video =====
===== Sat Apr 26 21:44:59 BRT 2008: running hook: /usr/lib/pm-utils/sleep.d/95led =====
===== Sat Apr 26 21:44:59 BRT 2008: running hook: /usr/lib/pm-utils/sleep.d/94cpufreq =====
===== Sat Apr 26 21:44:59 BRT 2008: running hook: /usr/lib/pm-utils/sleep.d/90clock =====
===== Sat Apr 26 21:45:01 BRT 2008: running hook: /usr/lib/pm-utils/sleep.d/50modules =====
 * Reconfiguring network interfaces...
   ...done.
===== Sat Apr 26 21:45:01 BRT 2008: running hook: /usr/lib/pm-utils/sleep.d/49bluetooth =====
===== Sat Apr 26 21:45:01 BRT 2008: running hook: /usr/lib/pm-utils/sleep.d/20video =====
===== Sat Apr 26 21:45:01 BRT 2008: running hook: /usr/lib/pm-utils/sleep.d/10NetworkManager =====
===== Sat Apr 26 21:45:01 BRT 2008: running hook: /usr/lib/pm-utils/sleep.d/05led =====
===== Sat Apr 26 21:45:01 BRT 2008: running hook: /usr/lib/pm-utils/sleep.d/00clear =====
Sat Apr 26 21:45:01 BRT 2008: done running resume hooks.

```

but i found that running pm-suspend from a konsole makes it suspend/resume normally, no suspend after resume!

any hints about which file in /etc/acpi could contain the culprit procedure?
i have a intel video based t61 [x3100] btw.

thanks!

---

### Post by phiral on 2008-04-27
while reading the /etc/acpi/sleep.sh, i noticed that it does explicit checks for running gnome-power-manager or klaptopdaemon, so it let for them to handle suspend/resume, but it does not check for kpowersave.

i added a explicit "exit;" before those checks, and its working perfectly now. :D

however i suspect that the culprit is in the resume code of acpi-support. further investigation needed..

---

