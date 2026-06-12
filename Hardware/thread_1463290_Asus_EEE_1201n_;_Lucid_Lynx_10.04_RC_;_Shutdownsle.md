---
title: "Asus EEE 1201n ; Lucid Lynx 10.04 RC ; Shutdown/sleep with fans going to the max"
date: 2010-04-26
forum: Hardware
---

### Post by devicerandom on 2010-04-26
Hi!

First of all, having had to change my laptop, I'm back to Ubuntu after years of using Gentoo (very useful experience btw).

I just bought an Asus Eee 1201n , and I decided to install the 10.04 Lucid release candidate with 2.6.32 kernel. I still have to fix things here and there (wireless, microphone etc.) but overall I am impressed -almost everything I need works like a charm, which is not usual for new laptop models and Linux.
[COLOR="DarkRed"]
However I have a single, very annoying, weird problem when trying to shutdown and/or sleep the machine. More often than not, the laptop seems to shutdown/sleep, but even if anything else looks "sleepy" correctly, immediately the fans turn on and go loudly to maximum speed. Awakening the laptop or rebooting it turns back the fans to normal speed immediately.[/COLOR]

So, to shutdown, I actually have to reboot and then do a cold shutdown from the grub screen (or shutdown from the windows 7 partition). And I can't put the thing to suspend (Well, it worked *once*). Didn't try hibernate (need a larger swapfile).

I looked in the forums, google etc. : I found many notices of the opposite problem (fan not waking up), but nothing about this issue. I think it's an ACPI issue of some kind but I really don't know where to start to debug it. Any hint? Should I file a bug report, and in any case what should I try to troubleshoot?

Thanks a lot!

---

### Post by devicerandom on 2010-04-27
Bump with some update:
- It doesn't happen always (just tried to suspend twice,it worked both times)
- Yesterday night when I tried to shutdown, the fans resumed at full speed. I then restarted pressing the on button on the laptop. The fan went almost quiet back. Then I tried to cold shutdown on the Grub screen. The fans resumed at full speed again, and I had to cleanly shutdown in Windows. It seems therefore that somehow the Linux keeps the ACPI/whatever controls fans in some quirky state.

---

### Post by VeeDubb on 2010-05-09
Have you had this issue since we got to the release version?

I've been running 10.04 on my 1201n since Thursday, and I've not had this problem at all.

---

### Post by devicerandom on 2010-05-11
Yes.

I found it happens if and only if I have my external USB hard drive connected. If not, it doesn't happen. If yes, it is practically guarenteed to happen.

---

### Post by deez on 2010-05-30
I'm having the same issue.  I have no external drives plugged in, but the suspend works once and then no more after that and I must restart to prevent imminent explosion.  Any way to fix this?

---

### Post by pterion on 2011-04-29
same issue here.

I found out that sometimes suspending fails. computers switched off wireless and fans, but stays on and eventually forcefully shut down with a beep due to critical temperature of the CPU.

---

