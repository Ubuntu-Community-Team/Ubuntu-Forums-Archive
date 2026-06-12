---
title: "t61 hangs on restart"
date: 2008-07-24
forum: Hardware
---

### Post by angrysniper on 2008-07-24
I have a thinkpad t61 running ubuntu studio 8.04 and when I restart it, I see the normal progress bar, and then the screen goes blank and I see another screen with a repeating pattern of colored.. symbols, or something.  I don't know what they are.  After that first pattern, the screen goes blank again, and then another repeating pattern fills the entire screen.  The first one just covers the bottom.  The screen turns blank two more times, and then the computer just hangs and I have to force it to shut off by holding the power button down.  I can boot normally by booting into recovery mode.  I recently installed backports, and maybe that has something to do with it.  However I don't remember what the name of the package exactly was, I just know it had backports in it.  How can I figure out whats causing this problem, or does anyone already know?  Does this happen to other people?  If it is backports, how can I find out the exact package that it was I installed, and how can I remove it?

---

### Post by lionfish on 2008-07-24
Hello, I'm afraid I'm still a bit of a novice with linux, but I think one thing that's useful with stuff like this is to check dmesg.

```
cd /var/log
cat dmesg
```

will hopefully give you a clue as to what broke the previous boot.

Hopefully someone with more knowledge will reply soon ;)

---

### Post by angrysniper on 2008-07-26
bump..

can anyone help me with this?  I'm unable to boot without hanging unless I boot using recovery mode.

---

