---
title: "Installed Hardy HDD with files misc. How can I recover my files."
date: 2008-12-20
forum: Hardware
---

### Post by Carlos_444 on 2008-12-20
My master 160 GB HDD went bad during boot and installation of the Ubuntu was made on the 500GB HDD wich I use for files. I dont want to install on the 160 again but want to recover the files that are covered on the ext3 partition.

Any help Ill be very grateful.

---

### Post by cariboo on 2008-12-20
I would suggest booting from the LiveCD and then mount you 160Gb and which ever drive you want to copy the files to, then press Alt-F2 and type:

```
gksu nautilus
```

THis will start nautilus as root, you can then copy the files without having to worry about permissions.

Jim

---

### Post by Carlos_444 on 2008-12-20
Thanks for your response !! Right now Im on the Live Session User. Im a noob and dont know how much can Nautilus do or not.  But what I did was to put on search the type o files I wanted to get wich (Search: *.nef) and it is taking its time.

---

### Post by Carlos_444 on 2008-12-20
Well I finally I installed Ubuntu on the 160 GB disk. And going to investigate mora about HDD recovery.

---

