---
title: "Live crashing windows?!"
date: 2005-06-12
forum: Hardware &amp; Laptops
---

### Post by aethiolas on 2005-06-12
Ok, so I'm not sure where to post this b/c I'm freaking out right now.  I just put the hoary live cd into my friends dell laptop running xp and booted off of it.  Just ran the default options and once I got in DONE NOTHING.  I touched nothing, just curious if it would boot w/ sound.  Shut it down and proceeded to boot back into windows.  Apparently somehow someway ubuntu has messed up windows now.  It won't boot at all.  It gives me a BSOD and won't load and I think the error message is something like Page Reload failure or something like that.  Long story short I want to know if anyone else has had issues with this and can anyone please help me!  I will post the exact error if its needed but right now the comp is not in my possesion.

---

### Post by RastaMahata on 2005-06-12
[QUOTE=aethiolas]Ok, so I'm not sure where to post this b/c I'm freaking out right now.  I just put the hoary live cd into my friends dell laptop running xp and booted off of it.  Just ran the default options and once I got in DONE NOTHING.  I touched nothing, just curious if it would boot w/ sound.  Shut it down and proceeded to boot back into windows.  Apparently somehow someway ubuntu has messed up windows now.  It won't boot at all.  It gives me a BSOD and won't load and I think the error message is something like Page Reload failure or something like that.  Long story short I want to know if anyone else has had issues with this and can anyone please help me!  I will post the exact error if its needed but right now the comp is not in my possesion.[/QUOTE]
 im positive that posting the full error would be the best thing to do, so we can help you...

---

### Post by aethiolas on 2005-06-12
It says
"A problem has been detereced and Windows has been shut down to prevent damage to your computer.
PAGE_FAULT_IN_NONPAGED_AREA"
 and then goes on to tell about trying safe mode and such which nothing worked.  Then at the bottom it says:
"Technical information:
*** STOP : 0x00000050 (0xF8701D00, 0x00000000, 0xF86ca051, 0x00000000)"
Don't know if this helps but I really hope so.

---

### Post by msgyrd on 2005-06-13
[QUOTE=aethiolas]It says
"A problem has been detereced and Windows has been shut down to prevent damage to your computer.
PAGE_FAULT_IN_NONPAGED_AREA"
 and then goes on to tell about trying safe mode and such which nothing worked.  Then at the bottom it says:
"Technical information:
*** STOP : 0x00000050 (0xF8701D00, 0x00000000, 0xF86ca051, 0x00000000)"
Don't know if this helps but I really hope so.[/QUOTE]

If you don't know what you're doing and promise that you didn't mess with any files on your hard drive, it's not possible for the Live CD to mess up anything on Windows.  The hard drive isn't mounted as writable under Ubuntu Live, so anything wrong with Windows was probably like that prior to booting a CD.

---

### Post by Seti on 2005-06-13
[QUOTE=msgyrd]If you don't know what you're doing and promise that you didn't mess with any files on your hard drive, it's not possible for the Live CD to mess up anything on Windows.  The hard drive isn't mounted as writable under Ubuntu Live, so anything wrong with Windows was probably like that prior to booting a CD.[/QUOTE]

Agreed. Unless somehow its caused by some change you may have made in the bios, in which case set factory-defaults, reboot and it should be ok.
More likely though, something was already wrong with Windows; rebooting just made the problem come to a head.

---

### Post by KiwiNZ on 2005-06-13
That stop error is indicative of a memory problem , Have you had your box open ?
does the Post screen give a correct Ram count ?

---

### Post by aethiolas on 2005-06-13
Ok guys I owe you a complete and total apology.  This was not at all caused by Linux and to be honest I truly felt that the entire time.  I've worked w/ knoppix quite a bit and never had any issues and this is the first time I've tested this and it had a problem and I immediatley freaked.  After running diagnostics I found out that its actually the ram, and afer changing it out, it works perfectly.  Once again I am truly sorry b/c I usually not one to post until I have tried everything I can think of but this one freaked me out.

---

### Post by tread on 2005-06-13
Been there :) This happening on a friends laptop because of something you did is esp. scary .. if it was your own you prolly wouldn't have freaked out so much.

Still, I'm glad things got sorted out.

---

