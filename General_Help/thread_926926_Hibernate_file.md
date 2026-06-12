---
title: "Hibernate file?"
date: 2008-09-22
forum: General Help
---

### Post by effigies on 2008-09-22
Hey folks. I decided to give hibernate a shot (specifically in KDE, though I suspect it's the same syscall in any event), and the result is that now my computer hangs during boot.

Does anybody know where the file is to which the system stores its state? I would like to delete it, so that I can boot normally again.

Thanks.

---

### Post by mali2297 on 2008-09-22
The state is stored in swap. If you want to clear it, use the commands
```

sudo swapoff /dev/sda?
sudo mkswap /dev/sda?
sudo update-initramfs -u 

```
where /dev/sda? is the location of your swap partition. However, you might also need to edit fstab afterwards.

An alternative to clearing swap might be to use the boot option noresume; when grub starts, press Esc, go to the boot line, press 'e' to edit, add *noresume* to the end of the line, press Enter and then 'b' to boot.

---

### Post by chaime on 2008-09-24
i have some foggy idea of what the fstab is but i do not know WHERE it is. can someone please post the location? thanks!

EDIT : oh. found it in /etc/fstab -- that was easy.

---

