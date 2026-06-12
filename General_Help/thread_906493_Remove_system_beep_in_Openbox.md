---
title: "Remove system beep in Openbox"
date: 2008-08-31
forum: General Help
---

### Post by cchung85 on 2008-08-31
I've scoured the forums and could not find any info on this topic.
I was wondering if there was a way to disable system beep in Openbox so that it is permanently off. I can type the commands in the terminal but it'll only turn it off for the session. Is there a command I can put into my autostart.sh file that will turn it off every time open box is loaded?

---

### Post by eriqjaffe on 2008-08-31
All you have to do is edit /etc/modprobe.d/blacklist in the text editor of your choice (as sudo) and add:

```
blacklist pcspkr
```

When you reboot, the pc speaker (and, thus, the system beep) will be silent.

---

### Post by cchung85 on 2008-08-31
Thank you very much for that tip. I've seen it on the net before but never wanted to black list drivers... But this worked out perfectly.

---

