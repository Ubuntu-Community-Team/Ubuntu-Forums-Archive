---
title: "Image of a usb stick"
date: 2008-10-02
forum: General Help
---

### Post by leg on 2008-10-02
How do I create an image from a usb stick so that I can then put that image on other usb sticks in much the same way you do with iso files for cds.

---

### Post by _sAm_ on 2008-10-02
You can make a image file from any partition or folders with:
mkisofs -o /tmp/imagename.iso /source

But you cant "burn/install" this to another usbkey... so, I guess you could get what you want with both dd and rsync.

---

### Post by leg on 2008-10-02
So how do orgs like dsl do it then or is it a decompress sort of process.

---

### Post by _sAm_ on 2008-10-03
You can use dd, rsync and clonezilla(I would try dd first).

I don't know how dsl and so on do it.

---

