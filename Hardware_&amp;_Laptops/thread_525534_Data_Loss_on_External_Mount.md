---
title: "Data Loss on External Mount?"
date: 2007-08-14
forum: Hardware &amp; Laptops
---

### Post by flipe on 2007-08-14
Hi,

I have a few questions, First can I mount an external harddrive to a location such as /home/local/media/
?

Second is there any possible way i could lose this data if i mount it?


Thanks

(p.s this is in the server edition)

---

### Post by az on 2007-08-14
> **flipe said:**
> Hi,

I have a few questions, First can I mount an external harddrive to a location such as /home/local/media/
?)

Yes.


> **flipe said:**
> 

Second is there any possible way i could lose this data if i mount it?


Thanks

(p.s this is in the server edition)

Sure.  Just don't delete any files you don't want to delete.  As well, unmount the drive(s) cleanly before you unplug the drive.

You can mount the drive read-only, if you want.

---

### Post by flipe on 2007-08-14
in the server mode how would i do this? 

Im used to a gui

---

### Post by az on 2007-08-14
mkdir /home/local/media
(you may need sudo if you are not the user named "local"

sudo mount /dev/scd1 /home/local/media

for read-only:

sudo mount -r /dev/scd1 /home/local/media


To unmount:

sudo umount /home/local/media

To flush out the buffers (unwritten stuff to all drives:

sync; sync; sync

---

