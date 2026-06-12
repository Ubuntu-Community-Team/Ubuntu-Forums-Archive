---
title: "Clonezilla issue"
date: 2011-12-31
forum: Hardware
---

### Post by chamber on 2011-12-31
The hard disk in my laptop ran into some issues and appears to be failing.  The Disk Utility in Ubuntu found 1205 bad sectors.  I have order a new hard drive and all important data has been backed up.

I decided to give Clonezilla a go to clone the drive and install it on the new drive when it arrives.  It ran into some issues when cloning the windows partition which is the partition that had the errors.

first error was

> "This partition in the image is broken: sda2"

After it had finished checking the images it said,

> "Broken partition images were found, or some of them are not checkable in the image....."

Will this be able to be restored across to the new drive or will this have the same errors?

---

### Post by howefield on 2011-12-31
If it can't even check the image, what chance is there that you can use it for a restore ?

Probably minimal imho.

---

### Post by chamber on 2011-12-31
Was afraid of that. At least there wasn't anything important on it. Will just get a fresh install on the new drive when it arrives.

---

### Post by Mark Phelps on 2012-01-02
IF you can still boot into Windows, or if you can connect the drive to a Windows PC, you can try either Macrium Reflect or Paragon ToDo Backup -- to see if either of them can image off the Windows partition.  Both of these have free versions available for download.

---

### Post by chamber on 2012-03-30
New hardrive has been configured and windows and linux re installed.  Clonezilla backup taken and everything working grand.

---

