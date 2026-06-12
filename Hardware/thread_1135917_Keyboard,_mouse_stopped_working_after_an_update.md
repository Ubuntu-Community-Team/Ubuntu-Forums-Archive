---
title: "Keyboard, mouse stopped working after an update"
date: 2009-04-24
forum: Hardware
---

### Post by leonidas300 on 2009-04-24
My keyboard and mouse stopped working after an update.
So I get stack in login screen as I cannot type my password.
How can I fix that problem?
I tried to boot using acpi=off but the problem still persists.
The only keys that works are the combination Ctrl+Alt+Del which restarts my system.
Can I post any log file?Which one?
Thank you for any help!

---

### Post by glenny88 on 2009-04-29
I also have this problem. Can anyone help?

---

### Post by kilgore9 on 2009-05-11
my laptop touchpad also spontaneously stopped working.... would like to have it solved as well!

---

### Post by KagetsukiZero on 2009-05-11
I'm assuming by "login screen" you mean GDM or KDM. First off try hitting ctrl+alt+f1, see if that brings you to a terminal screen. If so you can log in from there and further diagnose and fix the problem. Seeing as to how ctrl+alt+del seems to work I'm guessing this will. Also, if you have a remote login daemon (SSH or Telnet for example) or something enabled you can log in over the network.

Anyway, if you can get to a terminal (where you can use the keyboard) then diagnosing the problem may be a bit easier.

---

