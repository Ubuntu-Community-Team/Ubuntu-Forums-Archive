---
title: "APIC woes, starting in Intrepid"
date: 2008-11-12
forum: General Help
---

### Post by jpardey on 2008-11-12
Hello,

I updated to the Intrepid release candidate (amd64 SMP, dual core) a few days before the official release, figuring it would be fine. After a bunch of strange dependency problems, I managed to get everything working (of note, my GeForce 8600GT, which was conflicting with mesa libGL or something, but that's all fixed now).

Anyway, recently when some flash game or video has been running, the sound would sometimes start to loop (about a quarter of a second or less, I'd guess the buffer on the sound card). The system would slowly become less responsive. I couldn't switch to a virtual console (to do the "magic sysgr" shutdown), and trying to shut it down with the power button just makes the system bell beep. Sometimes I was able to start up the system log viewer, or a terminal, but that would shortly become impossible. Anyway, it turns out the error was ```
APIC error on CPU1: 00(80)
``` This log is saved to disk, so it's not one of those total disk failure errors.

Right now I'm running xfce, flash disabled. KDE4 seems to be pretty bad for it, and GNOME with compiz and all disabled has problems too. I haven't had any problems so far, but I'm barely doing anything on it.

Perhaps the upgrade to Flash 10 was a problem, but there are many times it hasn't been related to flash at all (nor should a user app crash the system). The sound card is a crappy Cirrus Logic CrystalSound or something equally hideous, running Sound Fusion CS46xx drivers (or at least reporting itself as such).

Can anyone help me? I should try disconnecting the sound card and seeing if it's related to that, and the noapic boot option doesn't seem to help. I can reflash my bios, but the problem only seems to have started with Intrepid. Any other things I should test for diagnosis?

Thanks in advance!

---

### Post by Yellow Pasque on 2008-11-13
Perhaps try some of the other APIC boot parameters:
[http://www.mjmwired.net/kernel/Documentation/x86_64/boot-options.txt](http://www.mjmwired.net/kernel/Documentation/x86_64/boot-options.txt)

---

### Post by jpardey on 2008-11-13
Thanks for the suggestion, I'll give those a shot... but there are a few things I'm still curious about...
Why would upgrading my OS make boot parameters like these necessary? I wasn't having these sorts of problems with 8.04 (nor with Windows). I would really rather find the problem than disable the more advanced interrupt settings.
Are there any other tests I can do to tell what might be wrong? It always gives an error 00(40) on CPU1. What does that code mean? Would it be related to an interrupt vector, and if so is there any way to decode what driver/component? Could it be a flaky bios, or is Linux not so great with the newer interrupt controllers?

---

### Post by Yellow Pasque on 2008-11-14
> Why would upgrading my OS make boot parameters like these necessary?
It's probably something that changed from the 2.6.24.x kernel to the 2.6.27.x kernel that Intrepid uses. If you still have the old kernel installed, you can try booting from it.

---

