---
title: "Black and white lines flash across ThinkPad screen"
date: 2010-08-01
forum: Hardware
---

### Post by Recursive Acronym on 2010-08-01
Occasionally, black and/or white lines will appear across my laptop's screen for a split second. Is this likely to be a driver issue, or is the screen going bad? They appear only occasionally, and they seem to have worsened somewhat since they started. My computer is a Lenovo T500 has an integrated Intel graphics card.

---

### Post by Recursive Acronym on 2010-08-03
Bump.

---

### Post by tgalati4 on 2010-08-03
I presume it doesn't happen in Windows.

Open a terminal:

```

dmesg | more
```

Spacebar to move forward, q to quit.

Look for any errors related to graphics.

Also check .xsession-errors in your home directory and /var/log/Xorg.0.log

```
cd
more .xsession-errors
more /var/log/Xorg.0.log
```

---

### Post by dgaud on 2010-08-04
I've seen them in an old lenovo t45 my girlfriend uses. I did not see them in Windows. I updated her to 10.04 and it still happens. I'll try the messages / log file tonight and report back. I was wondering what was that about. Thanks for starting the topic.

---

