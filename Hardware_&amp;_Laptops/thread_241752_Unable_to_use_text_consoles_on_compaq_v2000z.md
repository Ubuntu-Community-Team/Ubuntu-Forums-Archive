---
title: "Unable to use text consoles on compaq v2000z"
date: 2006-08-22
forum: Hardware &amp; Laptops
---

### Post by evillawngnome on 2006-08-22
Heres the problem: I get a black screen any time i try to go to a console (ctr-alt-f1). Also, on boot, i dont get to see the startup messages. Do i need some kind of "cheet code" in grub to fix this?


I wasnt really worried too much about this until today, when i had to do the xorg downgrade. I had to find a CRT monitor to plug into my laptop to do the job.

---

### Post by evillawngnome on 2006-08-22
Did some searching, found this problem is related to the ati driver. The solution is to add vga=768 (for my 1280x768 widescreen). All is well now.

---

### Post by ÄlveKatt on 2006-08-25
I also have his problem. Could you post a more detailed description of how you solved it?
Thank you.

Or some links.

---

