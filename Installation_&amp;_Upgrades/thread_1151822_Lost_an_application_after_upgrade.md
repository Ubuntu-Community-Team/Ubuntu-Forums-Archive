---
title: "Lost an application after upgrade?"
date: 2009-05-07
forum: Installation &amp; Upgrades
---

### Post by mahela007 on 2009-05-07
I've lost blender after I upgraded to 9.04. Any way to recover it other than doing a fresh install?

---

### Post by lavinog on 2009-05-07
how did you install it last time? (did you install it manually or with a package manager?)
have you tried reinstalling it using add/remove?

---

### Post by mahela007 on 2009-05-07
I installed using adept. But now I just found out quite irritatingly that there is no adept in kubuntu 9.04 or at least in my PC.

---

### Post by lavinog on 2009-05-07
Can you try
```
sudo aptitiude install blender
```

---

### Post by mahela007 on 2009-05-07
No.. It doesn't work

---

### Post by lovinglinux on 2009-05-07
> **mahela007 said:**
> No.. It doesn't work

That's weird. I did a fresh install of Ubuntu, but generated a script for downloading and installing all my previous applications. Blender was there when it finished. Could it be a Kubuntu repository issue?

---

### Post by lavinog on 2009-05-07
You can download the latest blender from blender.org
It is setup so that you only have to extract the files to a folder and run the executable.

as far as your repository goes can you post your **/etc/apt/sources.list**

---

