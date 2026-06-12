---
title: "HDD Password vs Full Disk Encryption"
date: 2008-05-23
forum: Hardware
---

### Post by Schalken on 2008-05-23
What is the difference in security between using full disk encryption via dm-crypt or similar, and simply setting a HDD password in the BIOS?

It seems both methods are rock solid, neither having a way to retrieve the data if the drive were to be stolen.

So whats the point of full disk encryption if setting a hard drive password gives equal security?

---

### Post by Steve413z on 2008-05-23
hard drive passwords "lock" the hard drive so it doesn't spin up, but doesn't ENCRYPT the hard drive.  It will deter your average laptop thrive, but not someone determined to get your data.

---

### Post by Schalken on 2008-05-23
But you can't get data off a drive that has been locked with a password, even though the actual data on the drive isn't encrypted, right?

---

### Post by Steve413z on 2008-05-23
your AVERAGE laptop thieve cannot, but someone with a large skill set, who is determined to get your data can access your data can.

---

### Post by gripen40k on 2008-05-23
This might be stretching it, but you can take an identical hard drive (make model and size) and swap the platters of the locked drive into the unlocked drive. There might be easier ways to do it but that is the only one I know of.

---

### Post by Steve413z on 2008-05-23
> **gripen40k said:**
> This might be stretching it, but you can take an identical hard drive (make model and size) and swap the platters of the locked drive into the unlocked drive. There might be easier ways to do it but that is the only one I know of.

i think so, it depends on the model, but like i said, it will stop the AVERAGE laptop thief

---

### Post by Schalken on 2008-05-24
Hmmm. Well this LVM with encryption is turning out to be a bit of a PITA. I think a HDD password in combination with GPG encryption of really sensitive data will be enough.

Thanks for your help!

---

### Post by barry99705 on 2008-06-10
> **gripen40k said:**
> This might be stretching it, but you can take an identical hard drive (make model and size) and swap the platters of the locked drive into the unlocked drive. There might be easier ways to do it but that is the only one I know of.

Easier to just swap out the board on the bottom of the drive.  I've done this to recover info after the chips exploded on a drive.

---

