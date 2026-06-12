---
title: "Sometimes there is no sound in Hardy"
date: 2008-08-23
forum: General Help
---

### Post by kanesoban on 2008-08-23
Helo,

my problem is, that since i upgraded to Hardy, sometimes when i start it, there is no sound. The only way to get sound back is to restart.

---

### Post by knutschr on 2008-08-23
Hardy uses Pulseaudio as default.
Uninstall it, and choose ALSA.
I think that will help.

---

### Post by carolinason on 2008-08-23
you can check this out too.
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/207883](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/207883)

---

### Post by kanesoban on 2008-08-23
> Hardy uses Pulseaudio as default.
Uninstall it, and choose ALSA.
I think that will help. 

How can i set Hardy to use Alsa instead of Pulseaudio ?

---

### Post by Sinkingships7 on 2008-08-23
> **kanesoban said:**
> How can i set Hardy to use Alsa instead of Pulseaudio ?

System -> Preferences -> Sound

Also, does this happen on a regular boot up, or is it after a suspend or hibernate cycle?

---

### Post by kanesoban on 2008-08-24
I don't use sleep nor hibernate.

---

### Post by kanesoban on 2008-08-25
Okay, here's the problem with uninstalling pulseaudio:
the package manager says, that if i want to remove "pulseaudio", then the "ubuntu-desktop" package will alse be removed. Am i right to think that i don't want that to happen?

---

