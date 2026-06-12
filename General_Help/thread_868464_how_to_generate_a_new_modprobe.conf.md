---
title: "how to generate a new modprobe.conf"
date: 2008-07-23
forum: General Help
---

### Post by the_real_fourthdimension on 2008-07-23
Hey All

I seem to have overwritten my modprobe.conf file while tweaking some settings.  Strangest thing...  Can anyone tell me how to generate a new one?  Thanks.

---

### Post by iaculallad on 2008-07-23
> **the_real_fourthdimension said:**
> Hey All

I seem to have overwritten my modprobe.conf file while changing the boot concurrency.  Strangest thing...  Can anyone tell me how to generate a new one?  Thanks.

On your terminal:

```
sudo generate-modprobe.conf
```

---

### Post by the_real_fourthdimension on 2008-07-23
> **iaculallad said:**
> On your terminal:

```
sudo generate-modprobe.conf
```

Thanks.  I tried that (I always google before I post), but I only get this:
```
me@my-machine:~$ sudo generate-modprobe.conf
sudo: generate-modprobe.conf: command not found

```

---

### Post by the_real_fourthdimension on 2008-07-23
> **iaculallad said:**
> On your terminal:

```
sudo generate-modprobe.conf
```

I've heard that you have to actually be root in order for this to work...  not just have root privilidges.  Is that right?  Do I need to restart and log into the the recovery terminal?

---

### Post by iaculallad on 2008-07-23
> **the_real_fourthdimension said:**
> I've heard that you have to actually be root in order for this to work...  not just have root privilidges.  Is that right?  Do I need to restart and log into the the recovery terminal?

You could try:

```
sudo -i
```

to invoke your root privilege.

---

### Post by the_real_fourthdimension on 2008-07-23
> **iaculallad said:**
> You could try:

```
sudo -i
```

to invoke your root privilege.

Thanks.  That seemed to make a bit of progress...
```
me@my-machine:~$ sudo -i generate-modprobe.conf
-bash: generate-modprobe.conf: No such file or directory

```

---

