---
title: "I want to give ubuntu more space - take space from vista to ubuntu"
date: 2008-10-13
forum: General Help
---

### Post by icrywolf on 2008-10-13
I'm liking ubuntu more and more :D

I"m considering getting  partition some more space to ubuntu by taking away some from vista 

I know how to shrink space away from vista but how would you add the partitioned bit  to ubuntu ???

---

### Post by woodenbrick on 2008-10-13
I assume you are using gparted?
After you shrink the vista partion, just right click on your ubuntu partition and choose resize.  I think the partition might need to be physically next to the freed space for this to work.

---

### Post by shawnrgr on 2008-10-13
sudo apt-get install gparted

GNOME Partition Editor

still best to backup important data before incase something goes wrong. i've done this recently where i resized my os partition to give me more storage space on another, rebooted and everything was fine. again, resize partitions with care. backup important data.

also you wont be able to resize your ubuntu partition when its mounted. so best bet is to load up a ubuntu live cd (already contains gparted) and resize from there. Depending on the size of the partitions this can take a while so be prepared to not use your pc while its running, any interuption WILL damage the disk and it will have to be reformated.

---

### Post by Ms_Angel_D on 2008-10-13
To make the vista partition smaller without risk of damaging it I recommend using it's built in editor to shrink the space. Then using Gparted to make Ubuntu larger.

[LIST=1]
[*]Boot into Windows Vista and go into Disk Management - right-click My Computer, Manage, Disk Management.
[*]Right-click on the main Vista partition and select Shrink Volume - the Shrink tool will assess how much space can be freed up. 
As a rule of thumb Shrink will reduce the main system partition by about 50%. As long as the partition is big enough to begin with (at least 10GB).
[*]Select Shrink and the tool will reduce the volume of the primary partition, leaving the rest of the disk free as unpartitioned space.
[*]Once that's done, shut down the Vista machine.
[*]Boot into your live CD and then use Gparted to "grow" your ubuntu space.
[/LIST]

---

### Post by leehach on 2008-10-15
Possibly stupid question: What partitions can you resize running Ubuntu off the hard drive?  I have:

/windows
/     (this is where ubuntu is installed)
/home
/data

Could I resize /home or /data?  Or should I just run gparted off the Live CD and forget about System/Administration/Partition Manager?

Thanks,

---

