---
title: "Anyone have experience with a Hybrid (SSHD) Drive?"
date: 2015-05-20
forum: Hardware
---

### Post by SuperKev on 2015-05-20
Hi all,

I bought a new Seagate 1 TB Hybrid SSHD drive recently, dual booting with Linux and and existing Win 7 install on a slave drive, all that works fine after some partitioning hiccups. But from the start my HD activity light has been just steadily glowing, not pulsing on on off as the HD does what it does as normal.

My MoBo and other hardware is not the most recent stuff so could this be the result of the SATA controller maybe not knowing how to handle the SSD part of the drive? SMART and other tests show it to be fine, and I am not seeing any performance hit that I discern even though the light is glowing bright. 

I am just concerned that I might be doing harm to the SSD part of the drive. I have tried to get in touch with Seagate customer support but you know how that goes, online is useless and you sit on the phone for 50 minutes on hold. 

Any thoughts on this would be appreciated.

---

### Post by tgalati4 on 2015-05-21
I do not have one, but my understanding is that the SSD acts as a high-speed cache for the slower spinning disk.  To the operating system, the hard drive is in constant use since data is moved between the SSD and the platters depending on age and frequency.  The light behavior is probably normal until there is a patch submitted that changes it.  How would the operating system know when the SSD is being written or the spinning platters?  Would you want the light to only go on when data is written to the platters?

How does the light behave in Windows?

---

### Post by kurt18947 on 2015-05-21
> I have tried to get in touch with Seagate customer support but you know  how that goes, online is useless and you sit on the phone for 50 minutes  on hold.

And if you had gotten to talk to someone if you told them you were using something other than Windows or maybe OSX you'd probably get a "we don't support that" Click.

---

### Post by SuperKev on 2015-05-21
> **tgalati4 said:**
> I do not have one, but my understanding is that the SSD acts as a high-speed cache for the slower spinning disk.  To the operating system, the hard drive is in constant use since data is moved between the SSD and the platters depending on age and frequency.  The light behavior is probably normal until there is a patch submitted that changes it.  How would the operating system know when the SSD is being written or the spinning platters?  Would you want the light to only go on when data is written to the platters?

How does the light behave in Windows?

Same behavior in Windows as well, that's why I am pretty sure it is a hardware issue. And you may be right, as the SSD is probably constantly doing Read/Write. when I run 'top' and 'iotop' in terminal I don't see anything that strikes as unusual.

---

### Post by kryten35 on 2015-05-25
I have the seagate 2TB hybrid and have noticed this as well.Its just as previous posters have said.There is software built into the disk
that moves files your using into the smaller solid state portion to speed things up.So you get normal activity plus the extra activity
of the hybrid moving files in/out.Its nothing to worry about, its just the hybrid doing its job.

I dont get it so bad now because i only use it as an internal storage drive for large media files etc.Dont have an OS installed on it.
But i still get increased  activity when video editing.The  light is annoying though.

---

