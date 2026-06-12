---
title: "3870 X2, no amdccle"
date: 2010-12-08
forum: Hardware
---

### Post by jus71n742 on 2010-12-08
I installed the drivers but I am getting some interesting errors

```

root@beastu:/home/jus71n742# fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 3870 X2
OpenGL version string: 3.3.10317 Compatibility Profile Context

root@beastu:/home/jus71n742# aticonfig --initial -f
aticonfig: No supported adapters detected
root@beastu:/home/jus71n742# DISPLAY=:0 amdccle
amdccle: command not found

```

What could be causing this?  I have triple monitors and they worked on 9.04-9.10, but not 10.04 so far. 
Any ideas?  My installation went as follows
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

