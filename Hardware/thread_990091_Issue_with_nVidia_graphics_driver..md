---
title: "Issue with nVidia graphics driver."
date: 2008-11-22
forum: Hardware
---

### Post by hibbleton34 on 2008-11-22
I'm a complete linux newbie, so please forgive me if I'm a little vague or don't quite know whats going on :)

I installed ubuntu 8.10 on my Samsung R700 laptop, everything works fine except that when in install the graphics drivers for its 8600M GT graphics card I can no longer change the screen brightness (the backlight rather than the image brightness).

Can anyone help me sort this out?

---

### Post by Bruce M. on 2008-11-22
> **hibbleton34 said:**
> Can anyone help me sort this out?

Welcome to Ubuntu.

Did you install: **nvidia-settings** from the repos?

```
Tool of configuring the NVIDIA graphics driver
The nvidia-settings utility is a tool for configuring the NVIDIA
Linux graphics driver.  It operates by communicating with the NVIDIA
X driver, querying and updating state as appropriate.  This
communication is done with the NV-CONTROL X extension.

Values such as brightness and gamma, XVideo attributes, temperature,
and OpenGL settings can be queried and configured via nvidia-settings.

```
Bruce

---

### Post by hibbleton34 on 2008-11-22
> **Bruce M. said:**
> Welcome to Ubuntu.

Did you install: **nvidia-settings** from the repos?

```
Tool of configuring the NVIDIA graphics driver
The nvidia-settings utility is a tool for configuring the NVIDIA
Linux graphics driver.  It operates by communicating with the NVIDIA
X driver, querying and updating state as appropriate.  This
communication is done with the NV-CONTROL X extension.

Values such as brightness and gamma, XVideo attributes, temperature,
and OpenGL settings can be queried and configured via nvidia-settings.

```
Bruce

nvidia-settings are installed properly, it allows me to change the brightness of the image on the screen, just like adjusting the brightness of a photo, but wont let me change the brightness of the LCD backlight which is the issue.

---

### Post by hibbleton34 on 2008-11-24
Reinstall didn't help either...

---

