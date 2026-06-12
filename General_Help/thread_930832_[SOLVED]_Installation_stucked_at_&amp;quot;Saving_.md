---
title: "[SOLVED] Installation stucked at &amp;quot;Saving VESA state..&amp;quot;"
date: 2008-09-26
forum: General Help
---

### Post by tnylsej on 2008-09-26
I was installing ubuntu using wubi on verbose mode.
The installation was stucked at "Saving VESA state.." I waited for more than an hour and it was still at "Saving VESA state.."
I tried the other installation modes and the same problem occurred.
Would appreciate if anyone can advise me on this. 
Thanks.

---

### Post by jimmyhacker on 2008-09-27
and my installation freezes at "removing temporary files"

---

### Post by jarven on 2008-11-03
> **tnylsej said:**
> I was installing ubuntu using wubi on verbose mode.
The installation was stucked at "Saving VESA state.." I waited for more than an hour and it was still at "Saving VESA state.."
I tried the other installation modes and the same problem occurred.
Would appreciate if anyone can advise me on this. 
Thanks.

I had same problem so I used the alt CD and I could complete the installation. I could also start Ubuntu once but after I ran update manager and reboot I'm back to "Saving VESA state...". Pretty frustrating.

---

### Post by jarven on 2008-11-04
Well, well.

I have solved the problem.
If you edit /etc/default/acpi-support
and change SAVE_VBE_STATE=true to false your Ubuntu should boot without freeze.

[FONT="Courier New"]**sudo nano /etc/default/acpi-support**[/FONT]

If there is a better solution, please let me know.

---

