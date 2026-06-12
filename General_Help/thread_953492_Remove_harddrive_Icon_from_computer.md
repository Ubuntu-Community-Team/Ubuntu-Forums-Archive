---
title: "Remove harddrive Icon from computer"
date: 2008-10-20
forum: General Help
---

### Post by Right Hook on 2008-10-20
Hi,
First time i use ubuntu and i have a 6 TB raid I don't want to mess it or delete any files by mistake. How can i remove the hard drive icon from Computer .when I unmount the drive from partition editor I still see the icon.
Thanks.

---

### Post by theevilhamster on 2008-10-20
Hell of a drive you have there! I'm thinking it may not unmount properly, if it is your boot drive, you can't unmount it. try this

```
sudo umount -f /dev/sdb1
```

obviously replacing "/dev/sdb1" with the drive. This will force unmount it. Be VERY careful with sudo!

Probably wont help but i hope it does! good luck!

---

