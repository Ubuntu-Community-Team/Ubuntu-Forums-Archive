---
title: "Elecraft K2 needs configured com port"
date: 2008-12-25
forum: Installation &amp; Upgrades
---

### Post by Arthur73 on 2008-12-25
The Elecraft K2 (& KIO2) ham radio tranceiver requires the com port connection to be configured 4800 N8 with 2 stop bits in order to connect to this Ubuntu 8.10 computer.

I have tried using the "serial" command as root but the response is always the same - no such file

The typical command has been

serial:/dev/ttyS0?baud=4800+parity=none+stop=2

I see the ttyS0 file has 0 size - might this mean that the file does indeed not exist? If so, how does one create an appropriate ttyS0 file? Is this the real problem or is the command sintax incorrect?

Your help is appreciated

Arthur

---

