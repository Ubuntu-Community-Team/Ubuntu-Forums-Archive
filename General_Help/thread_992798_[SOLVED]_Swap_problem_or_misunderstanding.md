---
title: "[SOLVED] Swap problem or misunderstanding?"
date: 2008-11-25
forum: General Help
---

### Post by fisherm on 2008-11-25
I've searched thoroughly (I think) to find a satisfying answer or fix and have been unsuccessful. My "problem" is this...my conky keeps me abreast of my Swap usage and after about a 4 day uptime my swap shows 1% used (as opposed to the usual 0%). It sometimes climbs to 7%. What concerns me is that once it goes up it doesn't come down, and I would think that eventually it would come back down. I don't use resource intensive programs to my knowledge and am unable to determine the cause of this swap usage. Once while out of town, I left the machine on but logged off (showing gdm screen). When I logged in the swap usage had gone from 0% at log out to 8%. My machine is an IBM T23 - 1.13Ghz, 1Gb Ram, 512Mb Swap (running 8.04.1). Any help or insight would be greatly appreciated.

---

### Post by regala on 2008-11-25
> **fisherm said:**
> I've searched thoroughly (I think) to find a satisfying answer or fix and have been unsuccessful. My "problem" is this...my conky keeps me abreast of my Swap usage and after about a 4 day uptime my swap shows 1% used (as opposed to the usual 0%). It sometimes climbs to 7%. What concerns me is that once it goes up it doesn't come down, and I would think that eventually it would come back down. I don't use resource intensive programs to my knowledge and am unable to determine the cause of this swap usage. Once while out of town, I left the machine on but logged off (showing gdm screen). When I logged in the swap usage had gone from 0% at log out to 8%. My machine is an IBM T23 - 1.13Ghz, 1Gb Ram, 512Mb Swap (running 8.04.1). Any help or insight would be greatly appreciated.

Well, memory is swapped-out when the amount of available system memory is too short for the allocation the kernel is trying to do. At this time, it moves memory pages that were less used onto the swap space. Usually, these are memory pages that corresponding processes won't touch in the near future (lib initialization code, as constructors code) and are done with. When the memory pressure lowers, it would be a waste o' time if the kernel was to page them out. That's why the kernel pages out only needed pages. So, don't worry if some pages are still in the swap space, it just means you do not need them (but for consistency, there are needed somewhere by the owning process and the kernel for accounting)

---

### Post by mikewhatever on 2008-11-25
I really don't think you need to fix something like that and make an elephant out of a fly. Swap is there to be used, although you can decrease it by lowering swappiness. Setting it to 10 or even 0 would be pretty safe in your case.
[http://ubuntuforums.org/showpost.php?p=1255511&postcount=43](http://ubuntuforums.org/showpost.php?p=1255511&postcount=43)

---

### Post by ibutho on 2008-11-25
The behaviour that you describe is normal and I don't think you need to tinker with anything. This [article]("http://foss.mnit.ac.in:8080/content/sites/gentoo-wiki/FAQ_Linux_Memory_Management.html") may help you get to grips with how Linux manages memory.

---

### Post by fisherm on 2008-11-25
Wow. Great help, and so quick. I guess my only remaining question is this...Will the swap use percentage gradually go back down on its own, or just keep filling up till I reboot (currently at 7%)? Just want to make sure it's safe to leave it up and running.

---

### Post by ibutho on 2008-11-26
You need to stop worrying and leave things as they are. There will be no need for you to reboot (Many linux servers run for months and years without rebots) because the kernel will manage your swap appropriately depending on your system usage.

---

### Post by Greyed on 2008-11-26
> **fisherm said:**
> Wow. Great help, and so quick. I guess my only remaining question is this...Will the swap use percentage gradually go back down on its own, or just keep filling up till I reboot (currently at 7%)? Just want to make sure it's safe to leave it up and running.

It will probably remain there, or increase slightly.  The relevant portion of the article mentioned previous is as follows:

"Swappiness takes a value between 0 and 100 to change the balance between swapping applications and freeing cache. At 100, **the kernel will always prefer to find *inactive pages* and swap them out**"

Key phrases bolded and italicized.  What you're seeing in your swap file are inactive pages, IE, inactive programs, which have not been used in a while and the kernel has determined is safe to swap out so as to free up that RAM for more active applications, buffers or the cache.  This is perfectly normal and desirable.

What programs, you might ask?  Prime candidates would be the 6 gettys set up by default.

```

{grey@igbuntu:~} ps auwx | grep getty
root      4169  0.0  0.1   1780   456 tty4     Ss+  Nov25   0:00 /sbin/getty 38400 tty4
root      4170  0.0  0.1   1780   456 tty5     Ss+  Nov25   0:00 /sbin/getty 38400 tty5
root      4179  0.0  0.1   1780   456 tty2     Ss+  Nov25   0:00 /sbin/getty 38400 tty2
root      4182  0.0  0.1   1780   456 tty3     Ss+  Nov25   0:00 /sbin/getty 38400 tty3
root      4184  0.0  0.1   1780   456 tty6     Ss+  Nov25   0:00 /sbin/getty 38400 tty6
root      5205  0.0  0.1   1780   456 tty1     Ss+  Nov25   0:00 /sbin/getty 38400 tty1

```These correspond with the 6 console sessions you can activate on ALT-F1 through ALT-F6.  If they're not used for a few hours they get swapped out.  If you ever go to one of the consoles they get swapped in.  Simple as that.  Since most people don't use these it's good that they get swapped out.  OTOH if your GUI gets pooched it's good to have them there for recovery.  Though, admittedly, I often pare that down to just two.  Hm, forgot to to it on this VM.

FWIW here's this VM's memory after a few hours of usage as a workstation:
```

{grey@igbuntu:~} uptime
 04:22:41 up  8:26,  1 user,  load average: 0.55, 0.76, 0.75
{grey@igbuntu:~} free
             total       used       free     shared    buffers     cached
Mem:        384376     374176      10200          0       9588     157292
-/+ buffers/cache:     207296     177080
Swap:       401400     138080     263320

```Compare that to my server VM :
```

{grey@olethros:~} uptime
 07:24:03 up 82 days,  9:23,  1 user,  load average: 0.03, 0.03, 0.00
{grey@olethros:~} free
             total       used       free     shared    buffers     cached
Mem:        262312     242492      19820          0      17980      52952
-/+ buffers/cache:     171560      90752
Swap:       524280     219188     305092

```Notice the workstation VM has 177Mb free but 138Mb of swap at 4.5 hours of usage while the server has 90Mb free and 219Mb of swap at 82 days.  Neither really concerns me.  Why?  This workstation VM is perfectly responsive and my server processes the mail/web traffic that it needs to.  Inactive programs being swapped out is what makes both of those possible.  Until you notice performance degradation don't worry too much about what the kernel is doing vis a vis free RAM space, RAM used in buffers, cache and swap.  If you don't notice performance problems then it is doing things right.  ;)

---

