---
title: "Cannot unmount USB drives"
date: 2008-09-04
forum: General Help
---

### Post by 50words on 2008-09-04
I have set myself up as an unprivileged user on a file server. Under User Privileges, I do have the ability to access external storage devices automatically.

When I insert a USB drive, it pops up on the desktop and Nautilus displays the contents of the drive.

However, when I right-click the drive icon on the desktop and select "Unmount," I get a pop-up error dialog that says "Cannot unmount volume." Under Details, it says "Cannot remove directory."

However, the drive icon disappears, and I go ahead and disconnect the drive, anyway.

I have not used this drive in any computers with Windows.

Any ideas how to fix this problem?

---

### Post by AhJah on 2008-09-24
hi,
I have exactly the same issue, since a day when my pc freezed because of thermal issue while a USB drive was connected. Now my usb devices are umounted correctly, as the icons disappear and the mount directories are not present anymore, but I get the same pop-up errors.

Did you manage to solve?
Thanks
 Leo

---

### Post by 50words on 2008-09-24
I haven't managed to solve it, no. I cleared out all the . folders, thinking that might do it, but I still get the same error every time.

---

### Post by AhJah on 2008-10-23
Just to provide my final 2 cents, I managed to solve the issue by deleting .hal-mtab and .hal-mtab.lock in /media

regards
leo

---

### Post by jamarsa on 2009-08-21
Thanks Leo, you solved my day :)

---

