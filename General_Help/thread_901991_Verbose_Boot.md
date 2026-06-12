---
title: "Verbose Boot"
date: 2008-08-26
forum: General Help
---

### Post by Marantz on 2008-08-26
Call me old school, but I really miss the verbose boot with the green [ OK ]... how would I go about getting this all back? I found it an easy way to troubleshoot any problems that came up and see just how everything is starting.

---

### Post by iaculallad on 2008-08-26
Remove the 'quiet' from defoptions & your kernel entry lines in your menu.lst file.

```
# defoptions=quiet splash
```

To:

```
# defoptions=splash
```


Then change:

```
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hda3 ro quiet splash

```

To:

```
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hda3 ro splash

```

NOTE: Kernel versions above are just for illustration.

---

### Post by -Zeus- on 2008-08-26
anywhere is says "splash" in your /boot/grub/menu.lst, change it to say "nosplash"

EDIT: forget it!  iaculallad's advice is way better.

---

### Post by Marantz on 2008-08-26
> **iaculallad said:**
> Remove the 'quiet' from defoptions & your kernel entry lines in your menu.lst file.

```
# defoptions=quiet splash
```

To:

```
# defoptions=splash
```


Then change:

```
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hda3 ro quiet splash

```

To:

```
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hda3 ro splash

```

NOTE: Kernel versions above are just for illustration.

Thank you much!

---

