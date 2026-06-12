---
title: "automount internal ext3 with user privilages"
date: 2009-10-26
forum: Hardware
---

### Post by 5mattyb5 on 2009-10-26
I have a second sata internal hard drive formatted as ext3 for the purpose of large file transfer, I say this because I first had it formatted as Vfat or Fat32 and was able to do this with no problem, except I couldn't transfer files greater than 4Gig.  I want to auto mount this disk at boot with user privilages so that I without becoming root can create and delete files.  I am able to automount it using pysdm but for reasons unknown to me I can only mount it with root privilages.  Can anybody open my eyes to a solution whether it be difficult or simple I just want this thing mounted.

Thank-you greatly in advance.

---

### Post by 5mattyb5 on 2009-10-26
I guess I jumped the gun guys, further googling provided me with the knowledge I was seeking.  I had done everything right except claim ownership of the mount point.  Yeah it's that easy.  Really sorry if I waste anybodies time.

---

### Post by iamjakex on 2010-01-06
Could you possibly post the references to how you solved this? I am in the same boat, and unable to find how to auto mount the drive.

:(

---

