---
title: "Windows Boot Problem"
date: 2008-09-13
forum: General Help
---

### Post by questionaire on 2008-09-13
I am dual booting hardy and vista on my hp laptop and it has been working fine for the past week or so, but now when i go to boot windows from the grub screen it says "Starting..." and does not go past that screen. I put in the Vista dvd and had it check the start process, but that did nothing.

The only thing i can think that changed was that I repartitioned the vista partition from a puppy linux liveCD and.  I shrunk it about 8 GB but i'm not sure this would have an effect on the boot.  The partition still contains all its original contents and mounts fine in ubuntu.

any suggestions?

---

### Post by caljohnsmith on 2008-09-13
> **questionaire said:**
> 
The only thing i can think that changed was that I repartitioned the vista partition from a puppy linux liveCD and.  I shrunk it about 8 GB but i'm not sure this would have an effect on the boot.  The partition still contains all its original contents and mounts fine in ubuntu.

any suggestions?
Unfortunately, repartitioning your HDD is most likely exactly the problem. Windows Vista maintains its own partition table outside of the main partition table stored in your HDD's master boot record (MBR). So in practical terms that means if you use anything other than Vista's Disk Management to do your partitioning, you can break Vista. If you have your Vista Recovery CD, the solution is usually as simple as running the following from the command line: 
```
bootrec /rebuildbcd 
```
If you don't have a Vista Recovery CD, you can download one [here]("ttp://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/"). Let me know how it goes or if you need more details/info.

---

### Post by The-Wise-Man on 2008-09-13
nvm

---

### Post by The-Wise-Man on 2008-09-13
nvm

---

