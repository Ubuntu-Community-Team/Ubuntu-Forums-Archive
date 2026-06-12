---
title: "Intel microcode update for meltdown - old processor shows new microcode version"
date: 2018-01-18
forum: Hardware
---

### Post by mikechant on 2018-01-18
I just upgraded the Intel microcode package (along with a load of other updates) to this version:
intel-microcode (3.20180108.0~ubuntu16.04.2) xenial-security

I wasn't expecting this to have any effect on my system because my CPU is long unsupported by Intel - it's about 10 years old, a core2duo E4500 Conroe architecture. Intel say not microcode fixes will be issued for systems older than about 5 years if I remember correctly.

However, I noticed that in /proc/cpuinfo I now get
microcode	: 0xa4
and before the microcode upgrade I was getting
microcode	: 0xa3

Does anyone know why this would happen? I'm a bit concerned because I know the microcode updates have been causing system instability in some cases and I thought I wouldn't be affected. (I haven't noticed any ill-effect so far though).

Later: OK, no problems actually. The microcode version was a3 when I was running a live usb version of Ubuntu for testing. I checked my old boot logs for 16.04 and actually I've been using version a4 all along.
Sorry to waste anyone's time, it's just that all the problems people have been having with the microcode changes have made me a bit jumpy!

---

