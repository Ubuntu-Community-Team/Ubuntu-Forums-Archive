---
title: "How to get dmraid to rebuild with a new disk?"
date: 2008-07-11
forum: General Help
---

### Post by skralljt on 2008-07-11
I had a failing raid0 array from a soft raid setup using the "via raid tool", on two sata drives on my motherboard.  Using ddrescue  I copied all but 140 kb onto the new drive, but now I am lost!  The Via Raid Tool says that there is a missing member of the raid0 striping array, even though there is a copy.  I guess it looks at serial numbers rather than the actual data on the drive.  There is no option in the raid tool dialog to replace a member of the array with another one.  Is there a solution with dmraid?
I am convinced that dmraid was what was used because of the naming convention for my raid device; it was named /dev/mapper/via_alsidss.  An mdadm device would be /dev/md0 or something like that.  Is there some file that contains the serial numbers of the dmraid softraid array?  Can I just open vm and edit a config file to replace the serial number of the old member with the new one and then mount the raid array again?  Or is there some esoteric commandline string I can use to specify which members of the array should be booted?  I checked man dmraid but it seems impenetrable.

Does anybody have any suggestions for me?  I am convinced that I still have all the data on both drives, the only thing keeping me from booting the raid array is that the serial numbers don't match the old array.  What should I do arghhh!

---

### Post by skralljt on 2008-07-11
~$ sudo dmraid -r
No RAID disks

---

### Post by HighInBC on 2008-10-22
I would also like the know this. What is the point of a raid array if I cannot rebuild?

---

### Post by fjgaude on 2008-10-22
Is not the fakeRAID created in the BIOS... seems like that would be a place to check on how to replace a bad disk. When you boot up does not a message come up to indicate how to get into the menu for the fakeRAID?

It is likely in the BIOS you will find some way to do what you wish. The program **dmraid** was created to handle fakeRAID but is not that powerful. **mdadm** is used by many who have learned to handle raid arrays.

Did you create the raid array? I guess it is a raid1 array?

---

### Post by jerome1232 on 2008-10-22
Correct me if I'm wrong but raid 0 just strips between two volumes, it's for performance, not reliability. Raid 0 has no way to rebuild if one of the disks fails.

---

### Post by fjgaude on 2008-10-22
Please, is the array raid0 or is it raid1?

Yes, Jerome, you are fully correct. Making a copy of one of the stripped disks that has failed means the copy has also failed. Yes!

---

### Post by daniix on 2009-02-05
Hi,

I've mounted a fakeraid in Mirroring mode (raid1) in ubuntu 8.10 using dmraid. I tried removing one disk and contiunue working with the other one and after a while pluging it again, but they don't get synchronized.

Does anyone know how to solve this?

thanks in advance,

Daniel.

---

### Post by ben1 on 2009-04-26
Hi,

Unfortunately it seems that dmraid command line utility took some time to start support rebuild capability added in 2007.
It seems it's finally possible for "lucky" intel fakeraid owner.
I guess that cover ICHxR chipset family.

If it's your case, you can update dmraid to 1.0.0.rc15 (last available at this date) and try `dmraid -R raid_set /dev/sdX`

Take care to read man page to get all rebuild possibilities !

With ubuntu 9.04, dmraid is already the last one.

---

### Post by sloggerkhan on 2009-04-26
I have software RAID V  on my PC using mdadm, I think it's the way to go. When I had a disk go bad, it dropped from array, array was degraded, I popped a new disk in the slot, formatted it for raid, added it to the array, and it started syncing immediately.

Not to mention if my hardware goes bad I can still use it on any hardware that supports linux and has at least 4 SATA ports.

however, I can't help with dmraid, sorry.

---

### Post by CowEyeball on 2009-06-18
> **daniix said:**
> Hi,

I've mounted a fakeraid in Mirroring mode (raid1) in ubuntu 8.10 using dmraid. I tried removing one disk and contiunue working with the other one and after a while pluging it again, but they don't get synchronized.

Does anyone know how to solve this?

thanks in advance,

Daniel.

I am in a similar situation as this gentleman.  After wrestling with Error messages during bootup, despite what otherwise seemed to be a perfectly functioning RAID1 setup, I resorted to disconnecting each of the drives and booting off of one drive in turn to ensure things were in fact behaving properly.

The good news is that they were, hooray!

The bad news is that now my BIOS is insisting my RAID is "degraded" and I am at a loss as to how to make it happy again.  My Motherboard, an Abit AS8, appears to only have Windows software to perform a rebuild.  Obviously this isn't an option for me, so I'm hoping dmraid can pull off the same.

Trying to rebuild one of the drives through dmraid isn't working for me though, I consistently receive this message:

```
root@cowbox:/dev# dmraid -R isw_cajbjfhdch /dev/sdb
Volume "isw_cajbjfhdch_COWBOX_RAID1" is not in rebuild state (current: 0)
Rebuild: cannot rebuild from current state!
```Any pointers?

---

### Post by kuja on 2009-06-18
> **skralljt said:**
> Does anybody have any suggestions for me?  I suggest not using RAID0 if data integrity is required, and/or if complete backups are unavailable. Maybe look into RAID 5/6 or RAID  0+1 if you want performance and integrity.

---

### Post by madhusker on 2009-07-05
> **CowEyeball said:**
> I am in a similar situation as this gentleman.  After wrestling with Error messages during bootup, despite what otherwise seemed to be a perfectly functioning RAID1 setup, I resorted to disconnecting each of the drives and booting off of one drive in turn to ensure things were in fact behaving properly.

The good news is that they were, hooray!

The bad news is that now my BIOS is insisting my RAID is "degraded" and I am at a loss as to how to make it happy again.  My Motherboard, an Abit AS8, appears to only have Windows software to perform a rebuild.  Obviously this isn't an option for me, so I'm hoping dmraid can pull off the same.

Trying to rebuild one of the drives through dmraid isn't working for me though, I consistently receive this message:

```
root@cowbox:/dev# dmraid -R isw_cajbjfhdch /dev/sdb
Volume "isw_cajbjfhdch_COWBOX_RAID1" is not in rebuild state (current: 0)
Rebuild: cannot rebuild from current state!
```Any pointers?

I have the Asus P6T Deluxe version 2 with the same problem.  It appears that even in 1.0.0.rc15 dmraid does not support a rebuild.  Looks like it's back to software mdadm and md devices.  Bummer...

---

### Post by CowEyeball on 2009-07-05
I wish I knew how to do that!  I ended up using an IDE hard drive and putting Windows on it.  I booted into Windows, installed the Intel RAID garbage, and it rebuilt my RAID something awesome.  When it finished I restarted again, changing the BIOS to never boot into that drive again, and now everything is working great.

I may get my linux license taken away for doing this, but at least the RAID is healthy again.

---

### Post by ronparent on 2009-07-05
CowEyeball

Great!!! It looks like you go lucky, but I'll keep your solution in mind for my own raid0 drives if I run into trouble. You are using raid0 aren't you?

---

### Post by CowEyeball on 2009-07-05
> **ronparent said:**
> CowEyeball

Great!!! It looks like you go lucky, but I'll keep your solution in mind for my own raid0 drives if I run into trouble. You are using raid0 aren't you?

Actually I'm using raid1, but hopefully that wouldn't matter.  Upon installing the Intel RAID manager software it literally took off immediately and didn't ask me any questions.  It found the RAID, saw it was sick, and fixed it.  Lucky indeed. :)

Two things worth noting, the Intel RAID management software on the Abit site was incorrect!  I'd advise anyone interested in going this route to determine the chipset of their board and get the software directly from Intel's site.

Secondly, and this may be a no-brainer for those more experienced than me, it took several hours to rebuild the RAID.  Although not surprised in retrospect, it was a stressor when it was happening.

---

### Post by ronparent on 2009-07-05
Raid1 is a so called mirroring raid and has built in redundancy. If one disk goes bad rebuilding is expected. Raid0 is called stripped array. If one disk goes bad, tough, There is no rebuilding or recovery of data. Your'e lucky. You are using the safer raid alternative.

---

### Post by CowEyeball on 2009-07-05
Ah right, duh.  So on a RAID0 if one disk dies you're starting over anyway?  Seems right.  I chose RAID1 intentionally because of the redundancy.  It makes our family fileserv seem that much more "hardcore", "safe", and "amazing".

---

