---
title: "SCSI mount issues"
date: 2005-05-05
forum: Hardware &amp; Laptops
---

### Post by Nylira on 2005-05-05
I recently installed ubuntu after being away from Linux for a while but being back I have some small issues with my SCSI system and especially with regards to writing.

Tried a number of progams to write but got odd results. Not in the least that Graveman apparently doesnt detect SCSI drives.

Now Gnomebaker DID detect my drives and after running it with sudo it did finally write the my data to disc. It also complained about a lack of mount point.

So I compared my data in Gnomebaker and FSTab. 
Gnomebaker identifies my cdrom as SR0 and writer as SR1
FStab has mounted my cdrom as SCD0 and writer as SCD1

I was told on IRC that the SR1 is essentially like SCD1 but that SCD was 'newer'. What I then find weird is that it mounted SCD1 (the writer) with the -ro (read only) flag.

Thus I am a bit lost now as to what I can do to resolve this.
Can I blatantly also add SR0 and SR1 to FSTab or will that cause a conflict?

Are there perhaps other programs (yes I have used CDrecord but a GTK style frontend would be preferable) that will work correctly with SCSI writers?

My SCSI writer is a Teac R55S for which the system has a driver. Any help or advise given in this is welcome.
 :?

---

