---
title: "How to adjust brightness"
date: 2010-07-22
forum: Hardware
---

### Post by gvj on 2010-07-22
Hi all,
I am using Ubuntu 10.04 LTS in Samsung N148. I can't see any option to adjust brightness in System->Preference->monitor. Is there any shell command to adjust brightness ? I have used xgamma -gamma but it change the gamx not brightness.

Cheers

---

### Post by IcarusR on 2010-07-23
Yes it can be done...

```
sudo su
```

enter password

```
 echo -n [COLOR="Red"]100[/COLOR] > /proc/acpi/video/GFX0/LCD/brightness
```

Check to see if the path is correct. [COLOR="Red"]100[/COLOR] is one of the allowed levels listed in the file.

[COLOR="Red"]**WARNING **[/COLOR]

```
sudo su
``` gives you superuser rights in the terminal which is potentially destructive, so close terminal afterwards.

---

