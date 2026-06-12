---
title: "how can i remove my ubuntu partition?"
date: 2009-03-08
forum: Installation &amp; Upgrades
---

### Post by JZeFF on 2009-03-08
On my laptop (Toshiba satellite l305d)  I decided to try installing ubuntu.  It installed fine, its just not what i need for school right now.  How can i get the partition back to Vista?

I do not have a recovery disk (dont think it came with one when purchased new?).. and i obviously dont want to delete everything i have on here..

So what do i do?

---

### Post by Neo_The_User on 2009-03-08
Open up a terminal

Option 1
```

sudo fdisk /dev/sda
l

```

Now press d and enter, then press the number after sda the partition that ubuntu is stored on.

OR

Option2
```

sudo cfdisk

```

And delete the ubuntu partition (ext3 probably marked as linux) and then press write and type yes.

OR

Option3
```

sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get install gparted && gksudo gparted

```


PLEASE NOTE THAT THAT WILL DELETE ALL DATA ON THE UBUNTU PARTITION AND IF YOU ARE NOT CAREFUL, YOU CAN END UP DELETING THE WRONG PARTITION AND... YEAH.

---

### Post by Mark Phelps on 2009-03-08
> **JZeFF said:**
> On my laptop (Toshiba satellite l305d)  I decided to try installing ubuntu.  It installed fine, its just not what i need for school right now.  How can i get the partition back to Vista?

I do not have a recovery disk (dont think it came with one when purchased new?).. and i obviously dont want to delete everything i have on here..

So what do i do?

Before you do ANYTHING ... did you install dual-boot, or did you install inside Vista (using Wubi)?  If the latter, you can remove Ubuntu just like any other Windows app.

---

