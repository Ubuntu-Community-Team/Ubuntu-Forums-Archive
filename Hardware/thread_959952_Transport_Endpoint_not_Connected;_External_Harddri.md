---
title: "Transport Endpoint not Connected; External Harddrive Connectivity Problems"
date: 2008-10-26
forum: Hardware
---

### Post by lnajt on 2008-10-26
When I copy files over to my Maxtor made NTFS formatted External Harddrive, Ubuntu sometimes stops copying partway through and gives me the error: transport endpoint not connected. This happens most often when I am copying large files (say, several gigabytes or more) and it happens regardless of using cp or the manual drag and drop (a distinction which, incidentally, somehow fixed a copying problem I was having before.)

Previous problems with the hard drive include an instance of presumably spontaneous file corruption and another recurring copying issue - when I manually drag and dropped the entire system would freeze up. I was able to circumvent this last problem through the command line (though somewhat mysteriously, since to the best of my knowledge both do the same thing).

Has anyone encountered, or better yet, solved a problem of this type before?

I running Ubuntu Hardy Heron on my Dell D830 Laptop.

Thanks

UPDATE: rsync also failed: 
     rsync: recv_generator: mkdir "/media/OneTouch 4/Music" failed: Transport endpoint is not connected (107)
     *** Skipping everything below this failed directory ***
     rsync error: some files could not be transferred (code 23) at main.c(977) [sender=2.6.9]

---

### Post by Geochelone on 2009-03-12
Not exactly to revive this old, unanswered thread, however I have a similar problem with my external hard disk. Amusingly, with same brand and maybe the same model, which is Maxtor OneTouch 4 Mini.

I suspect it's caused by the horrendous quality of the hard disk. Mine is hardly a good external hard disk to use. Most of the time it will plugged out itself (not physically though).

To use it, I need to flip it on its face. Else the hard disk won't run. It sadden me as I just bought the hard disk some days ago.

I'm running Intrepid on Lenovo S10.

Or maybe, maybe the lappy has not enough bus power to drive the hard disk. I'm not sure.

---

