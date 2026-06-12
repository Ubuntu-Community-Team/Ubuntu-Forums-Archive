---
title: "ubuntu loading menu has disappeared"
date: 2008-09-13
forum: General Help
---

### Post by fallen seraph on 2008-09-13
so I'm not too sure what I've done; but I've made that loading screen that pops up while ubuntu is loading disappear. Now it just lists what it's doing, and I'd much prefer the pleasant, uncomplicated loading screen :s

any suggestions?

---

### Post by rraj.be on 2008-09-13
Edit ```
/boot/grub/menu.lst
``` change the following line
```

kernel          /boot/vmlinuz-2.6.26-5-generic root=UUID=801683d9-5e74-4ad6-91e9-6f05622ac006 ro 
```

 to

```
 kernel          /boot/vmlinuz-2.6.26-5-generic root=UUID=801683d9-5e74-4ad6-91e9-6f05622ac006 ro quiet splash
```

---

