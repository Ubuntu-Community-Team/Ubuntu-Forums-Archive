---
title: "adding RAM while in hibernated state"
date: 2021-03-20
forum: Hardware
---

### Post by blackbird34 on 2021-03-20
Hi everyone, 

More curiosity than anything else: 
If I put my Ubuntu (20.10 Kubuntu) into hibernate, then open the laptop and add RAM to it, will it start normally and recognize the new RAM stick? Or should I shut down instead (e.g in case the kernel only detects new RAM when the system actually boots)?

---

### Post by ajgreeny on 2021-03-20
Shutdown fully! 

I think you are asking for trouble messing around with hardware when the system is hibernated.
I do not use hibernation any more; I never found it any quicker getting back to a full desktop than a full shutdown though I do use ***suspend*** mostly and only normally reboot when a kernel update demands it, meaning uptime can be s few weeks sometimes.

---

### Post by Autodave on 2021-03-20
+1 with ajgreeny.  NEVER do anything like that unless machine is totally shut down.

---

### Post by grahammechanical on 2021-03-21
What does the instruction manual say? Does it advise removing the laptop's batteries? I have a desktop machine and when I do anything inside the case I switch off the mains power. I also enter the BIOS/UEFI settings utility to see if it detects the new RAM modules before I boot the OS.

---

### Post by blackbird34 on 2021-03-23
> **ajgreeny said:**
> Shutdown fully! 

I think you are asking for trouble messing around with hardware when the system is hibernated.
I do not use hibernation any more; I never found it any quicker getting back to a full desktop than a full shutdown though I do use ***suspend*** mostly and only normally reboot when a kernel update demands it, meaning uptime can be s few weeks sometimes.

Thanks for the replies. I realise it was a dumb question. I will shut down! :)

I was using hibernation for a while because suspend didn't work (i later traced the problem to a UEFI issue and did a BIOS update to resolve it).
I haven't found a manual but there are Youtube repair videos about my laptop model which tell viewers to disconnect the battery.

---

### Post by Tadaen_Sylvermane on 2021-03-23
Not a dumb question. I remember years ago my brother got a video card. The instructions were to put in while the system was live. It worked. But I have no doubt there is a reason that no one does that anymore. Think along the same vein as changing a radiator cap. Off works, but it needs to be completely cooled down to remove any risk (does this make sense?).

---

