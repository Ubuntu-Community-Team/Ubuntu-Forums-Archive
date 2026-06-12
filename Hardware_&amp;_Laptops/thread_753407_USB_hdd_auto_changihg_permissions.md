---
title: "USB hdd auto changihg permissions"
date: 2008-04-12
forum: Hardware &amp; Laptops
---

### Post by phlipp on 2008-04-12
My Hard drive is fat32 and will auto mount on boot-up with rw permissions but as soon as i try to edit and save an image with either gimp or f-spot the permissions change to read only and will not revert until re-boot. I'm baffled.:(

---

### Post by prshah on 2008-04-12
> **phlipp said:**
> My Hard drive is fat32 and will auto mount on boot-up with rw permissions but as soon as i try to edit and save an image with either gimp or f-spot the permissions change to read only and will not revert until re-boot. I'm baffled.:(

Are you sure it's mounted rw at boot time? At your next boot try ```
touch /media/whatever/testfile
ls -l /media/whatever/testfile

``` and check if the "testfile" is actually created or not.

---

### Post by phlipp on 2008-04-12
Right now I can create and copy to folders but as soon as I try to save an image I'm back to read only and have to re-boot to get rw.

---

### Post by phlipp on 2008-04-12
I ran your code and was able to write file

---

