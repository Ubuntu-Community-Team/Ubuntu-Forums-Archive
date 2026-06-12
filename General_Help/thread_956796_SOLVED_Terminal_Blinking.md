---
title: "SOLVED: Terminal Blinking"
date: 2008-10-23
forum: General Help
---

### Post by TheBlueCow on 2008-10-23
I've had a problem with my terminals accessed through Ctrl-Alt-F(#) recently. Not sure when it started, but whenever I start a program like ELinks or screen the text starts blinking on and off at a rate of about once per second. Is this an NCurses problem? It seems to only happen with applications that use color text. Any help?

SOLVED: Wow that was a quick fix... Turns out my terminals don't like having their TERM env var set to xterm-256color for some reason. What are the different options for the term variable?

---

