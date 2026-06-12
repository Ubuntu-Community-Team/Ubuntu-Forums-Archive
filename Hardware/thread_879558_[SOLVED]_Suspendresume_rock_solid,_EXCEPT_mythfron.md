---
title: "[SOLVED] Suspend/resume rock solid, EXCEPT mythfrontend which freezes after resume"
date: 2008-08-04
forum: Hardware
---

### Post by honda on 2008-08-04
Title says it all.. It's a laptop (fujitsu), since hardy suspend to ram always works (including resume), except I can't start mythtv frontend after resume. It freezes in the startup screen (scaling... progress bar) and nothing works (not even the sys-req-rseiub sequence). I have not found any  other program having problems after resume, and the frontend always works after coldboot. I can even suspend with the frontend running and it works after resume, but then I cant shut it down (freezes computer). What on earth could cause this? Have tried changing various options in /etc/default/acpi-support, didn't help. This is where suspend is configured, right?

---

### Post by honda on 2008-08-05
Found out that it's opengl that kills the computer after resume. Since I don't use any 3d stuff on this machine (too weak, a prosavage adapter), I figured out that it's probably just a matter of disabling all 3d capabilities. Can probably be done by editing xorg.conf, but I figured the easiest way would be lowering the shared memory in BIOS to be unsufficient for 3D. So I changed it from 32M (max) to 8M (min) and now everything I care about runs after resume. (Don't know why mythfrontend uses 3d stuff, I'm using the qt painter, not opengl)

---

