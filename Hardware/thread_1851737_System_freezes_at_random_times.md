---
title: "System freezes at random times"
date: 2011-09-28
forum: Hardware
---

### Post by beboylips on 2011-09-28
Hello forum,

I have a puzzling problem which I need help diagnosing and fixing. 

I have a laptop that has Ubuntu 10.10 Maverick AMD64 running on the following hardware:

CPU: Intel Core i3
GPU: Nvidia 310M

Generic 64-bit kernel. All drivers installed from Ubuntu repositories. 

The system freezes randomly and I can't do anything; can't restart X (I have the Ctrl-Alt-Backspace) enabled, can't switch tty, etc.
The light on the caps lock button keeps flashing (the keyboard has a light on the caps lock button to make the user aware when caps lock is enabled).
It seems like the system crashed and did not recover, and couldn't even restart itself (considering that Linux has the watchdog daemon).

Any comments/suggestions are very appreciated. Please ask if you need more info about hardware, drivers, kernel modules, etc.

Thanks.

---

### Post by diasf on 2011-09-29
first step: Is your machine overheating?

---

### Post by beboylips on 2011-10-01
Nope it's not. GPU is always around 50 degrees.

---

### Post by diasf on 2011-10-01
What about cpu? 
Anything on dmesg?
Try a memtest+ (gotta read the documentation to know how much time you need to let it run).

---

