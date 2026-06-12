---
title: "brasero - &quot;Unsupported type of task operation&quot;"
date: 2010-08-21
forum: Hardware
---

### Post by BrianMCollins on 2010-08-21
[FONT="Arial"]Hey, not sure if this goes here, but I got the following log when attempting to copy a CD on a Lenovo T61 with 10.04 64-bit.  So far, everything has "just worked" so I"m  little surprised.

Any suggestions?[/FONT]

Checking session consistency (brasero_burn_check_session_consistency brasero-burn.c:1741)
Unsupported type of task operation
Session error : An internal error occurred (brasero_burn_record brasero-burn.c:2839)

---

### Post by bagpussnz on 2010-08-22
Exactly the same here. Exact message was....


$ cat brasero-session.log 
Checking session consistency (brasero_burn_check_session_consistency brasero-burn.c:1741)
Unsupported type of task operation
Session error : An internal error occurred (brasero_burn_record brasero-burn.c:2839)

Ian

---

### Post by Jennifer the Hedgehog on 2010-08-23
Try installing the package "icedax".

---

### Post by Pikiora on 2010-11-10
Worked for me,  Brilliant!  Thanks :)

---

