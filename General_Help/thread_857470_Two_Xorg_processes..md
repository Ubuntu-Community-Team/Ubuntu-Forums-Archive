---
title: "Two Xorg processes."
date: 2008-07-12
forum: General Help
---

### Post by coderpp on 2008-07-12
Hi! System Monitor shows two Xorg processes. Is it normal?

---

### Post by PadreSol on 2008-07-12
Can you cut-n-paste what you're seeing? It might be normal. So the answer is "it depends".

---

### Post by coderpp on 2008-07-12
I see this:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=77493&stc=1&d=1215896048[/IMG]

---

### Post by PadreSol on 2008-07-12
open a shell
ps -C Xorg -o args
paste the results here

---

### Post by markharding557 on 2008-07-12
> **coderpp said:**
> Hi! System Monitor shows two Xorg processes. Is it normal?

If you are using the ATI driver then this isn't anything to worry about,i have the same here but only when using ati driver

---

### Post by coderpp on 2008-07-12
ps -C Xorg -o args
COMMAND
/usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
/usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7

Yes, i use ATI driver.

---

### Post by markharding557 on 2008-07-15
I get two xorgs while running ati on debian as well so it's not just ubuntu

---

### Post by ScarySquirrel on 2008-09-26
I have the same problem.  
     Do you use an ATI graphics card?  
     The fglrx driver for it is closed source, and some people report the problem disappearing when they use a different driver, such as the one called "vesa".

---

