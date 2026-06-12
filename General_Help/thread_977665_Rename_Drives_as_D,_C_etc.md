---
title: "Rename Drives as D:, C: etc"
date: 2008-11-10
forum: General Help
---

### Post by iampriteshdesai on 2008-11-10
I have Vista and Ubuntu. I have been used to Vista's drive nameing and want to follow it in Ubuntu. How to do that? Instaed of the space available I get in Nautilus?

---

### Post by cariboo on 2008-11-10
You can use e2lablel on ext3 partitions:

```
e2label device [newlabel]
```

The above command has to be done in a Applications-->Accessories-->Terminal.

Jim

---

### Post by scouser73 on 2008-11-10
Here's a tutorial to help you rename HDDs; [https://help.ubuntu.com/community/RenameUSBDrive]("https://help.ubuntu.com/community/RenameUSBDrive")

---

