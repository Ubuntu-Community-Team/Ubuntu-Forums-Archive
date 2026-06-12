---
title: "Spontaneous reboots"
date: 2008-08-13
forum: General Help
---

### Post by revolutio on 2008-08-13
For the past month or so Ubuntu has been spontaneously rebooting on me about once a day.  I noticed this trend shortly after replacing the PSU of my computer so I returned that one and got another PSU (I'd had other problems with the replacement as well).  However the problem returned quite promptly.  I'm at a loss for what causes this since it will reboot when under heavy use and then it might also reboot when the machine is idling.

What I've found from troubleshooting:
-twice replaced PSU has ruled that component out
-checking the temperature of the CPU right after rebooting revealed no overheating
-Prime95 for 4 hours showed no instability in the CPU
-video card stress test for about 6 hours showed no errors
-Memtest86+ for 6 hours turned up no errors
-complete diagnostic scans of all 3 of my hard drives showed no errors

Finally, I don't have this problem in Windows XP where I do gaming and thus the most intensive hardware use.  Thus I suspect the issue is related to Ubuntu despite it initially seeming like a stereotypical hardware problem.

Any ideas? What else should I check?  

I'm unfamiliar with the logging system in Ubuntu so I didn't really know what to post from that.  I hadn't seen anything as glaring as "NORTHBRIDGE OVERHEATING" that might give me a clue.  If someone could point me to the correct log file I'd be happy to post the information from right before one of the reboots.

Thanks.

---

### Post by revolutio on 2008-08-15
Advice anyone?

---

### Post by lucho64 on 2008-08-16
Don't have an answer for you, just the same problem...
Are you running Hardy? I'm still running Gutsy. Mi problem started after I started noticing that random programs crashed with signal 6. I ran memtest86 and showed that one of my simm cards was bad. So I took one out and tested the last remaining one and it was fine. But that's when the rebooting started. I've checked also the temperatures and run the WD test program on my hard drives and everything seems OK. Just Googling around I also found some old posts where the voltages could be flaky due to electrolytic capacitors oozing gunk, so I'll check that now. I was trying to figure out where you live, thinking that may be it's got something to do with warmer whether stressing components (capacitors?).
Anyway, I'll keep looking and post back if I found anything

---

### Post by revolutio on 2008-08-16
I'm using Hardy.  I'm somewhere temperature-controlled and ramping up fan speeds in my computer hasn't seemed to affect the problem.  My motherboard is aging (read: four years) so, if this is a hardware problem, it is my prime suspect.  However, none of this explains why no amount of use and abuse under XP will cause the same restarts.  

Again, does anyone know what log file to look in to get information about what happens right before a reboot?

---

### Post by lucho64 on 2008-08-17
Well, you are not using the same hardware in XP and Ubuntu, at least not in the same way. You are probably using different hard drives, and the CPU frequency scaler might not be programmed to run the same way, just to mention two examples that seem the most relevant.
As for your question of which file should have the info on what happened to cause the reboot, I would have to say that probably none, as the reboot happened probably as fast to the kernel as it happened to you, that is, it left no time to do much, like write to the log and sync the filesystem. Linux usually never reboots by itself when it finds an error, you have to have the entry "kernel.panic = 20" in your /etc/sysctl.conf to cause to do that. But you can look into dmesg (or /var/log/kern.log*) for anything unusual (NMI interrupt being stuck seemed to be one to watch for, according to google, but only for 64 bit Linux). The only way to hope for some word from the kernel is to attach a serial console (that way the sync part is not required, but the write to console is) One way that Linux might **shutdown** on its own is by using acpi to avoid temperature meltdown   (look under /proc/acpi/thermal_zone/THRM/), but you said you temps look OK.
For my part, I did go ahead and bought some new memory, and so far so good. And it's not as expensive as it used to be :)

---

### Post by revolutio on 2008-09-08
Dredging this post up because the reboots have increased in frequency to nearly once every two hours.  I'm really at a loss here and my options are drop Ubuntu or replace the motherboard, processor, RAM, and graphics card.

---

