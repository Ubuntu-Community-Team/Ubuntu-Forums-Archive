---
title: "GRUB editing."
date: 2005-11-23
forum: General Help
---

### Post by Turk on 2005-11-23
Hello.

I want to edit GRUB so that an other os is started up (after 5 sec) defaultly, how can this be done?

Thanks.

---

### Post by aysiu on 2005-11-23
```
sudo nano /boot/grub/menu.lst
```

Change default 0 (which really means default 1) to be default whatever the number you want is (minus one). So if you want the fourth OS to be the default, change it to ```
default 3
```

There's also something there that says ```
timeout 10
``` Change it to ```
timeout 5
```

---

