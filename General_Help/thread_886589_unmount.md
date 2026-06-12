---
title: "unmount"
date: 2008-08-11
forum: General Help
---

### Post by demon_hunter on 2008-08-11
I have mounted an ISO file using furius ISO mount yet cannot unmount it. i hace tried right clicking on the file and pressing unmount . but it comes up with this message.'umount: /home/lukas/BCDisc1_iso is not in the fstab (and you are not root)'.Anybody able to help .thanks:confused::confused:

---

### Post by tarps87 on 2008-08-11
Try using this command:
```

sudo umount /home/lukas/BCDisc1_iso

```
You may need to use:
-d     In case the unmounted device was a loop device, also  free  this loop device.
```

sudo umount -d /home/lukas/BCDisc1_iso

```
I hope this helps

---

### Post by demon_hunter on 2008-08-11
thanks .it worked:)

---

