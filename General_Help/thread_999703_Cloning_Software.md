---
title: "Cloning Software"
date: 2008-12-02
forum: General Help
---

### Post by Graham1 on 2008-12-02
Hi

I'm currently testing the following cloning software:-

1. Partimage (from Parted Magic)
2. G4L (Ghost 4 Linux)
3. PING (Partimage Is Not Ghost)
4. Clonezilla

I'm just curious as to what others are using and why. Also, if there is any other software out there that isn't covered above ([COLOR="Red"]see note[/COLOR]). 

Using mainly for cloning Linux distro's but would also be like to know which you think is the best for cloning NTFS partitions.

All comments welcome :D.

:)

[COLOR="Red"]Note:[/COLOR] Live CD's with GUI (*can be text-based but not command line, that's scary for me :D*).

---

### Post by binbash on 2008-12-02
I only tested 1 and 4.I dont like partimage (yes it does its job but i dont like it).I never had problems with clonezilla.

---

### Post by 4t0m1c_w07f on 2008-12-02
I just use gpated live and copy the partitions over...

---

### Post by dchriscoe on 2008-12-02
I just used ddrescue to clone my 60g to 80g- worked great.  I discovered the procedure on [www.linux.com](www.linux.com).  It is written by Keir Thomas and is also in his new book, Ubuntu Kung Fu.

---

### Post by ghostworkz on 2008-12-02
I use clonezilla and a DRBL server.  So far, it's worked great for my baseline images and drive moves.

---

### Post by Graham1 on 2008-12-02
> **binbash said:**
> I only tested 1 and 4.I dont like partimage (yes it does its job but i dont like it).I never had problems with clonezilla.

Hi

From the tests that I have done so far, Clonezilla was the quickest to backup but was the 3rd slowest in restoring. Partimage came last in both backup and restore but that said, it's probably my favourite as it's interface is simple to use (i.e no jumping through menu's, etc). Like you said, it just does the job but unfortunately, worst in performance.

:)

---

### Post by Graham1 on 2008-12-02
> **4t0m1c_w07f said:**
> I just use gpated live and copy the partitions over...

Hi

Could you explain how you do this? I assume I could do the same with Parted Magic? (which includes GParted). 

:)

---

### Post by Graham1 on 2008-12-02
> **dchriscoe said:**
> I just used ddrescue to clone my 60g to 80g- worked great.  I discovered the procedure on [www.linux.com](www.linux.com).  It is written by Keir Thomas and is also in his new book, Ubuntu Kung Fu.

Hi 

I haven't seen/used this one before. Sounds like a command line tool but I'll take a look at this one. Thanks.

:)

---

### Post by Graham1 on 2008-12-02
> **ghostworkz said:**
> I use clonezilla and a DRBL server.  So far, it's worked great for my baseline images and drive moves.

Hi

I wouldn't need the DRBL server part of Clonezilla as I'm mainly cloning from my home computer/laptop. Would you be using this setup with NTFS partitions?

:)

---

### Post by ghostworkz on 2008-12-02
> **Graham1 said:**
> Hi

I wouldn't need the DRBL server part of Clonezilla as I'm mainly cloning from my home computer/laptop. Would you be using this setup with NTFS partitions?

:)
I use the same setup for my home network.  I like using DRBL due to one less cd/usb boot device I have to keep up with.  Set it to PXE boot and bam!, you are backing up and restoring.

I have done a rather large NTFS partition of 300 gigs using Clonezilla.  Took 180 minutes over my network and the restore was roughly the same.  Compare that to a ext3 300 gig done in roughly 30 minutes.

The DRBL server or Clonezilla server let's you "step down" in the backup/restore methods.  You can have it start with NTFS->Partimage->DD and I forget the other of the top of my head.

---

