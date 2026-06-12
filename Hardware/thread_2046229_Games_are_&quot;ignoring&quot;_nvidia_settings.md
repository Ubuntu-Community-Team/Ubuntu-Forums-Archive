---
title: "Games are &quot;ignoring&quot; nvidia settings"
date: 2012-08-22
forum: Hardware
---

### Post by alexftw. on 2012-08-22
here's the "situation"
I've got a hybrid notebook with Intel onboard + nvidia 630m and succesfully installed bumblebee and everything works fine, except for...

this problem:
when i open nvidia-settings with ```
optirun nvidia-settings -c :8
``` and change 3D settings like anti aliasing and anisotropic filtering, these settings aren't really applied. for example, if i activate antialiasing 16x and launch a game, nothing has actually changed. Of course, I already searched somewhere else, but I didn't really find a solution. This file, .nvidia-settings-rc, is fine - if i change something with nvidia-settings, the values in it are changed, and even if I try this: ```
nvidia-settings -l
``` ...it doesn't work.

the most frustrating part of it is: in windows 7 (dual boot) the nvidia control center works fine and has more options to change, but i don't want to use windows, i want to use kubuntu.

Every little help is appreciable.

oh, and..I'm sorry for bad grammar or something, not a native english speaker :P

---

