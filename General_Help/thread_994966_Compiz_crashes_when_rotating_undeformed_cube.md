---
title: "Compiz crashes when rotating undeformed cube"
date: 2008-11-27
forum: General Help
---

### Post by rosyatrandom on 2008-11-27
Hi all.

After a few issues, I've managed to get compiz to work on my system by disabling the bicubic filter plugin. However, I still an issue with it.

If I deselect Cube Reflection and Deformation (or just set the deformation option to 'none') and attempt to rotate the cube, x crashes and restarts. This happens even though I have the crash handler enabled and configured to start metacity.

As I recall, I also used to get this same problem if there was an issue with the number of workspaces set-up (I have 4).

I am rather reluctant to experiment too much with this because a crash of course means losing my session entirely!

My setup is: Acer TravelMate 4230, Ubuntu 8.10 64-bit, Graphics card is some generic Intel 94x series.

---

### Post by eternalnewbee on 2008-11-27
Risking to sound silly, I'll ask: have you enabled the Desktop Cube?

---

### Post by rosyatrandom on 2008-11-27
Ha, yes :D

It works fine when it's deformed to a cylinder shape - not sure about spherical though.

---

### Post by eternalnewbee on 2008-11-27
> This happens even though I have the crash handler enabled and configured to start metacity
maybe the default should be compiz...

---

### Post by rosyatrandom on 2008-11-27
Well, I can use Metacity, but I prefer Compiz (of course) - it's only there in the crash handler (I believe I have 'metacity -replace &&'; I'm currently setting up an XP boot on another partition so can't check) so that if Compiz goes belly-up, Metacity should automatically launch instead.

But that's the theory - what happens is that Compiz crashes, X crashes, and Metacity doesn't seem to get invoked.

---

