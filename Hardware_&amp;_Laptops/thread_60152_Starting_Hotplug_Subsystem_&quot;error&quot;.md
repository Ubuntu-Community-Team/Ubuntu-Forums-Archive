---
title: "Starting Hotplug Subsystem &quot;error&quot;"
date: 2005-08-26
forum: Hardware &amp; Laptops
---

### Post by Comp_Lex on 2005-08-26
Hello,

i'm using Ubuntu for some time now and I must say that it is a very capable Linux Desktop OS and as a development platform as well. However, I bought a new graphics card (Geforce 6600) a few days ago, i plugged it in my computer and now i'm stuck with some kind of bad hotplug manager. Every time Ubuntu boots it hangs at "Starting hotplug subsystem..." and it doesn't boot further. Neither X nor GNOME loads and there is no way I can get to the console. I've tried everything I've found here and with google. Ctrl+C, nohotplug, single mode, switch AGP to Primary in BIOS.... nothing works! I find this very frustrating and I must say that this is a very SERIOUS bug! 
I also tried to boot my system with Breezy, but when it gets to "Starting hotplug subsystem..." I get a kernel panic with a some kind of stacktrace. I saw that it tried to assign some kind of IRQ to my hardware ("do_irq") before it panicked.I also tried a 2 (!) year-old Morphix LiveCD and that boots perfectly! No problem with the hotplug manager, not at all! Now I'm on the brink of giving up and I'm planning to use a another distro. When I installed Debian some time ago i came across some kind of question to use hotplug or not. I think that this should be intergrated in the Ubuntuinstaller as well.

Can someone help me to fix this problem?

My hardware specifications:

Motherboard: ASRock P4i45GV (82845) with 533 MHz FSB
CPU: Celeron 2.4 GHz
Memory: 256 MB
Sound: Onboard chip
Graphics: XpertVision Geforce 6600 256 MB AGP  and Intel onboard chip 64 MB max (shared)
Network : Realtek PCI card 100 Mbps
USB: 2 x 2.0 and 4 x 1.1

(Please don't give me a answer like: "Why don't you boot Ubuntu without your Geforce card!", because I like to play a few games once in a while and I can't play games with the onboard chip @ 200 texels.)

---

