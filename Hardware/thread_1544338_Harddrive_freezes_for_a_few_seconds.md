---
title: "Harddrive freezes for a few seconds"
date: 2010-08-02
forum: Hardware
---

### Post by JonasDK on 2010-08-02
Hello everyone

Now and then my harddisk freezes up. Usually I'm playing music using Rhythmbox (I'm doing this quite often so don't know if this is the cause) and suddenly the music stops and the harddisk light is continiously on. I have a memory-usage graph in my panel and it says that an I/O-device is on 100% usage, probably my harddisk. The freeze stops after a second or 8 and my GUI is still responsive while this happens. The music continues playing after that and skips those 8 seconds. My laptop freezes about one time a day.

I looked at my System logs and I found this on the time it froze up again:
```
Aug  2 17:08:40 jonas-laptop kernel: [ 6639.000105] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Aug  2 17:08:40 jonas-laptop kernel: [ 6639.000115] ata1.00: failed command: FLUSH CACHE EXT
Aug  2 17:08:40 jonas-laptop kernel: [ 6639.000130] ata1.00: cmd ea/00:00:00:00:00/00:00:00:00:00/a0 tag 0
Aug  2 17:08:40 jonas-laptop kernel: [ 6639.000132]          res 40/00:00:00:4f:c2/00:00:00:00:00/40 Emask 0x4 (timeout)
Aug  2 17:08:40 jonas-laptop kernel: [ 6639.000139] ata1.00: status: { DRDY }
Aug  2 17:08:40 jonas-laptop kernel: [ 6639.000155] ata1: hard resetting link
Aug  2 17:08:40 jonas-laptop kernel: [ 6639.476507] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Aug  2 17:08:40 jonas-laptop kernel: [ 6639.500971] ata1.00: configured for UDMA/133
Aug  2 17:08:40 jonas-laptop kernel: [ 6639.500982] ata1.00: device reported invalid CHS sector 0
Aug  2 17:08:40 jonas-laptop kernel: [ 6639.500999] ata1: EH complete
```

Can anyone help? I've had this on 9.10 also, not on 9.04 but still on 10.04 now.
Thanks,
Jonas

---

### Post by bmillham on 2010-08-02
Get a backup of your system ASAP. It looks to me like your hard drive is failing...

---

### Post by JonasDK on 2010-08-02
My laptop is only a year old? :(

When I had 9.10 I used to have freezes too, but they were more severe. When they happened my system wouldn't recover fully and when I rebooted he couldn't mount my filesystem. I had to preform 'fsck' which fixed bad allocations or something. I can't remember, fsck was like 'counting' something and it counted too many.

I preform backups twice a week so no problem there. I would recall these freezes happening since february when I switched to 9.10.

Thanks for your reply. Not so good news sadly. :|
Any more thoughts?
Jonas

---

### Post by corrytonapple on 2010-08-02
If your computer is under warranty make them replace it or the HDD.:D

---

### Post by JonasDK on 2010-08-02
I kinda need it a lot. But Disk Utility says my drive is healthy.

---

### Post by bmillham on 2010-08-02
> **JonasDK said:**
> My laptop is only a year old? :(

When I had 9.10 I used to have freezes too, but they were more severe. When they happened my system wouldn't recover fully and when I rebooted he couldn't mount my filesystem. I had to preform 'fsck' which fixed bad allocations or something. I can't remember, fsck was like 'counting' something and it counted too many.

I preform backups twice a week so no problem there. I would recall these freezes happening since february when I switched to 9.10.

Thanks for your reply. Not so good news sadly. :|
Any more thoughts?
Jonas
Hard drives fail for lots of reasons. I've seen new drives fail after a few days...

You might try getting a new drive and use Clonezilla to copy your system from the old drive to the new drive (you may also need a usb external drive enclosure to do this)

You could also try re-seating the old drive. Power off your laptop, remove and reinstall the drive. Maybe clean the contacts when you do this. It could be a bad connection,

---

### Post by JonasDK on 2010-08-02
I think I would have to void the warranty if I want to open up my laptop and change the hard drive. I'm now checking my harddrive with HD Tune in Windows (the program sucks actually but anyway) for bad sectors. HD Tune says my HD is healthy also.

I think I'm going to wait and see. If my hard disk fails completely then I'll put it in warranty of course. I have backups all the time so I won't have data loss. For now the freezes maybe happen once a day, but I have to say that I haven't seen them for a few weeks too.

It's possibly like a growing tumor I'm trying to control. :p
My laptop is a Samsung R610 16" with a 500Gb Samsung hard disk, bought 1 year ago.

Jonas

---

### Post by bmillham on 2010-08-02
Replacing the drive (or re-seating it) should not void your warranty. Hard drives in most laptops are easy to replace (Sony laptops are the exception)

---

### Post by JonasDK on 2010-08-02
I think you're right, underneath my laptop is the cover for the HDD which is held in place by just a few screws without a warranty seal or anything (maybe inside?). But as long as they aren't coming very frequently or on timed intervals I cannot see if the problem is resolved by replacing the HDD. Re-seating could do something indeed.

I'm still running HD Tune which will take me another 30 minutes or so. So far no bad sectors, finished for 74,6%.

Greetings,
Jonas

---

