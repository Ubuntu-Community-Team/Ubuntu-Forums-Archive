---
title: "Unable to access internal speaker (beep)"
date: 2009-01-07
forum: Hardware
---

### Post by Masterofpsi on 2009-01-07
This is pretty straightforward:

I'm using a Toshiba Satellite A135, running Ubuntu 8.10. I write a few scripts and want to be able to know when and how they exit when they're not called from the command line, so I want to be able to call the internal speaker, or bell (ASCII character 007), which does not depend on the sound card. The command 

```

echo -e \a

```

should do it; however, it doesn't. Does anyone know how to fix this?

---

### Post by cariboo on 2009-01-07
The pc speaker is blacklisted, as it seems to cause problems see bug [# 246969]("http:///bugs.launchpad.net/ubuntu/+source/gdm/+bug/246969"). I would suggest commenting the line out in /etc/modprobe.d/blacklist and see if you have any problems. If you do you can always uncomment it.

Jim

---

### Post by Masterofpsi on 2009-01-08
Why doesn't pcspkr work (as opposed to pcsp, which is what that thread is about)?

---

