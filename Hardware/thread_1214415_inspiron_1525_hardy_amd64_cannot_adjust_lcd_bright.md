---
title: "inspiron 1525 hardy amd64 cannot adjust lcd brightness"
date: 2009-07-15
forum: Hardware
---

### Post by misha680 on 2009-07-15
Dear All:

I cannot seem to adjust screen brightness. Pressing Fn up or down does absolutely nothing in terminal or X, gnome-power-manager segfaults btw:
```

[ 8427.879757] gnome-power-man[16060]: segfault at 0 rip 41141a rsp 7fffb49c5b60 error 4

```
Furthermore if I do:
```

misha@misha-i1525:/proc/acpi/video/VID/LCD$ cat brightness 
levels:  100 100 12 24 36 48 60 72 84 100
current: 100
misha@misha-i1525:/proc/acpi/video/VID/LCD$ sudo echo 12 > brightness 
bash: brightness: Permission denied
misha@misha-i1525:/proc/acpi/video/VID/LCD$ 

```
Am stumped. Any help much appreciated. Thank you

Misha

---

