---
title: "Firefox maxing out an 8 core?"
date: 2017-12-26
forum: Hardware
---

### Post by Autodave on 2017-12-26
Second time in the last few days this has happened. On Firefox, one tab only, suddenly hear CPU fan revving up. Psensor shows 98% usage. Stacer shows all 8 cores running wide open. Wassup with that?  8 core, 3.5, 8 gig RAM. Only thing running was Firefox.

---

### Post by QIII on 2017-12-26
Hello!

What does top say?

---

### Post by vasa1 on 2017-12-26
See also:
[https://www.reddit.com/r/firefox/comments/7g6k9n/firefox_quantum_is_eating_your_cpu_help_us_debug/](https://www.reddit.com/r/firefox/comments/7g6k9n/firefox_quantum_is_eating_your_cpu_help_us_debug/)
[https://www.reddit.com/r/firefox/comments/7knnn4/firefox_quantum_is_eating_your_cpu_help_us_debug/](https://www.reddit.com/r/firefox/comments/7knnn4/firefox_quantum_is_eating_your_cpu_help_us_debug/)

---

### Post by Autodave on 2017-12-27
*What does top say? *

I am lost. What is top?

---

### Post by QIII on 2017-12-27
Top is a command-line package to show system resource  use.

Just issue

```
top
``` in the terminal.

Watch what is going on just as the system freezes.

---

### Post by Autodave on 2017-12-28
Understand that it does not lock up or even slow down: at least not that I can see. Just now, running *top*, I saw CPU usage peak at 750.5% for Firefox. It was hovering between 720% and 750%.

---

### Post by vasa1 on 2017-12-28
Have you altered any defaults? Have you increased "core processes" from the default? What do you see in *about:performance*?

---

### Post by Autodave on 2017-12-28
Bone stock 57.0.1.  Where do I find the ```
about:performance
```?

---

### Post by #&amp;thj^% on 2017-12-28
Hi Autodave.
You put that in the address bar or URL window.

---

