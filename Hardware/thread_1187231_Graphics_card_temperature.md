---
title: "Graphics card temperature"
date: 2009-06-14
forum: Hardware
---

### Post by j-g-faustus on 2009-06-14
Hi,

I'm trying to monitor hardware temperatures with a scheduled script, including graphics card temperature.

I can get it to work if I log in to the desktop and execute the script as the logged-in user:
```

sudo -u faustus nvidia-settings -c :0 -q GPUCoreTemp
  Attribute 'GPUCoreTemp' (server:0.0): 40.

```
But X11 must run for this to work, and I must be logged in to the desktop.

This is slightly impractical for 24x7 operation. I would be happy with any of these alternatives:
[LIST]
[*]Read temperatures without X11 running (best)
[*]Read temperatures without logging in
[*]Auto-login at bootup
[/LIST]

Does anyone know of a way to do either of these?

Or is this a question for the Nvidia forum?

---

