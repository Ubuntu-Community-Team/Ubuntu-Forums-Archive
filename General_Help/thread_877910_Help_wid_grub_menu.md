---
title: "Help wid grub menu"
date: 2008-08-02
forum: General Help
---

### Post by dinsaurabh on 2008-08-02
hey everyone....cn u help me wid a problem....actually i had windows xp as well as ubuntu installed on my pc ...but due to some reasons i had to reinstall windows  and now the boot menu to select from either of the two is not appearing as i start my computer...directly windows is loading.....cn anyone tell me how to log on to ubuntu......or else how to bring back the boot menu....????

---

### Post by Diabolis on 2008-08-02
You have to reinstall grub from the live-cd

Steps to reinstall grub:
```

sudo grub
find /boot/grub/stage1    It will find all the places **from where** you can install grub.
root (hd?,?)              Select **from where** you want to install grub
setup (hd?)               Select the drive **in which** you want to reinstall grub
reboot
```

So the output of the **find** command is the input of **root**.

---

### Post by dinsaurabh on 2008-08-02
> **Diabolis said:**
> You have to reinstall grub from the live-cd

Steps to reinstall grub:
```

sudo grub
find /boot/grub/stage1    It will find all the places **from where** you can install grub.
root (hd?,?)              Select **from where** you want to install grub
setup (hd?)               Select the drive **in which** you want to reinstall grub
reboot
```

So the output of the **find** command is the input of **root**.

hey i hv done ths and the grub menu has also been loaded....but when i select ubuntu from it....it shows cannot mount from selected partition....pls reply....

---

### Post by Diabolis on 2008-08-02
Remember that the more information you provide the easier and faster people will offer you solutions.

Did you see something like "Error 17", if so: [http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17)

---

