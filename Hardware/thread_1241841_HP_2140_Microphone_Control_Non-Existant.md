---
title: "HP 2140 Microphone Control Non-Existant"
date: 2009-08-16
forum: Hardware
---

### Post by Bungo Pony on 2009-08-16
I'm running Xubuntu 8.04. I know there is a bug where the internal Microphone on this machine doesn't work, but that's not my problem.

If I plug a microphone into the input jack, it works, but is extremely quiet. There is no microphone control that shows up in alsamixer. How can I get the microphone volume control? I tried upgrading the version of alsamixer to 1.0.20, but that did not fix the issue.

The only controls I have are "Master" and "PCM"

---

### Post by Bungo Pony on 2009-08-16
Found the problem... The Mic control is labelled "digital" and was not enabled.

---

