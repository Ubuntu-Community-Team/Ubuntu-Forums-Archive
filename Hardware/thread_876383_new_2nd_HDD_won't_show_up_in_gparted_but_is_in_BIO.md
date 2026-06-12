---
title: "new 2nd HDD won't show up in gparted but is in BIOS"
date: 2008-07-31
forum: Hardware
---

### Post by kimmp12 on 2008-07-31
I recently purchased a second hard drive for storage purposes.  It's a SATA drive with an IDE converter on it.  It shows up in the BIOS as the secondary master and my original drive is the primary.  I can't get the second one to show up in gparted at all.  Any advice to get it working?

---

### Post by kimmp12 on 2008-08-02
Actually let me make an addition to that and hopefully get a reply.  I used gparted live and formatted the new drive, it showed up just fine there, but when I attempt to install Ubuntu on it the drive does not show up.

---

### Post by soxs on 2008-08-02
> **kimmp12 said:**
> I recently purchased a second hard drive for storage purposes.  It's a SATA drive with an IDE converter on it.  It shows up in the BIOS as the secondary master and my original drive is the primary.  I can't get the second one to show up in gparted at all.  Any advice to get it working?

So you finally run it as IDE dev right?
Do you have a slvae attached to your IDE_LANE_1?

---

### Post by kimmp12 on 2008-08-03
The drive does run as IDE.
I had been wanting to add a Windows partition for a few reasons so I did that today.  The second drive works just fine with that, yet I can't do anything with it on Linux.

---

### Post by aisar190 on 2008-08-03
hmm...do you have dual os ?...can u used the drive in windows ?

---

### Post by kimmp12 on 2008-08-03
Yes I can, I just checked to make sure I can save to it and everything went fine.
fdisk does not display the drive at all

---

### Post by soxs on 2008-08-04
Does the drive have any jumper config?

---

### Post by kimmp12 on 2008-08-04
No it does not.

---

### Post by kimmp12 on 2008-08-08
Anyone?

---

### Post by soxs on 2008-08-08
You may update your tags, most people will search according to them (added 2 allready).

Did you try to plug into another machine running linux/preferably ubuntu?

---

### Post by kimmp12 on 2008-08-10
I will try when I see my brother in a bit, however, I'm not sure if it's important to note or not but it does not show up if I use this
```
 sudo lshw -C disk
```

As I said before though, it is working fine under Windows, I just began transferring my music and movies to the drive without a hassle.

---

### Post by kimmp12 on 2008-08-11
It does not show up in another computer running Ubuntu either.

---

