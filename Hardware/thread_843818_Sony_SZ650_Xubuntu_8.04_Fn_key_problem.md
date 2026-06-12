---
title: "Sony SZ650 Xubuntu 8.04 Fn key problem"
date: 2008-06-28
forum: Hardware
---

### Post by arjunrc on 2008-06-28
Hey folks,
I am facing two wierd problem:

a) When I run acpid -d in foreground mode, all the Fn+Functions keys starting from Fn+F5 to Fn+12 are detected by acpid but the volume control buttons are not detected - Fn+f2 mute , Fn+F3 vol down, Fn+F4 vol up.

b) I figured out a way to make brightness control work when on stamina mode (intel graphics mode) based on tips in this forum, by invoking xbacklight when acpi detects brightness up and down. Interestingly, this only works when I bring down acpid once and restart it again. Any reason why?

thanks

---

