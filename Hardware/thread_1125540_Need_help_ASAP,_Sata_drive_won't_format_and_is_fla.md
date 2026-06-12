---
title: "Need help ASAP, Sata drive won't format and is flagged as LBA?!?!"
date: 2009-04-14
forum: Hardware
---

### Post by designer17 on 2009-04-14
I had my htpc dual booted running xp and linux mint. One day I went to use it and neither os would boot.  XP gave a quick blue screen after the splash page then quickly rebooted every time and mint wouldn't get past grub.

Wanting to start over and thinking my sata drive had a bad sector I decided it pop in the UBCD and attempt to wipe the entire drive.  Anyways upon doing so I realized the progress bar said it was going to take a couple days to complete. Me being inpatient decided to restart the pc and look for a quicker solution.  Ever since I tried wiping it I've been unable to format the drive and get errors every time. Gparted won't let me delete any of the partitions or format. XP also gives me an error when trying to format. I've tried every way I can think of to format the drive still getting an error every time.

I noticed last night the bad partitions are flagged as LBA.  I attempted to change them in gparted but I received another error and it wouldn't let me.

So last night I tried installing linux mint and set it to use the entire hard drive.  Mint did install but it didn't use the entire drive like I was hoping.  The LBA partitions remained untouched.  After mint installed I thought xp might install now so I loaded the xp install disk, deleted all the partition, including the LBA partitions then tried to use xp to format it which failed again.



So does anyone know how do I cam I fix my drive so the entire thing is usable and none of the partition are flagged as LBA?

Thanks in advance

---

### Post by cariboo on 2009-04-14
I would go to the hard drive manufacturers web site and download the diagnostic tools and run them to see if your drive is defective. Some manufacturers have a re-certify utility that will repair minor problems.

Jim

---

### Post by designer17 on 2009-04-14
I tried going to the manufactures website a couple days ago and never found anything

---

