---
title: "How I Used Clonezilla to directly clone HDD to smaller SSD"
date: 2012-09-04
forum: Hardware
---

### Post by monotok on 2012-09-04
Hello,

I searched around the internet and these forums and I didn't quite find what I wanted to achieve. If this is ill relevant then just delete the post :P It is my first post and wanted to contribute my experience which might help someone else.

I had a 500GB hard in my laptop, I decided to buy a SSD which was 480GB. Not much smaller at all but this meant Clonezilla would not directly copy to the small SSD. I didn't want to reinstall etc.

I read around on the internet that you could use Clonezilla in image mode but I didn't want to do that for several reasons. One was that I needed another external HDD to store the images. The other was that I wasn't sure if it would copy the partition MAP correctly as I use GPT.

What I decided to do was burn a live CD of Parted Magic (awesome CD). From this CD I could run many Utilities such as GParted and Clonezilla from the one disc (saves time).


My partitions were as follows (around about): GPT Boot = 1MB, Root = 60GB, Unallocated = 40GB, Home = 380GB and SWAP = 10GB.
Using GParted I reduced the size of the Root partition to 20GB as I was using only 6GB (used to windows where applications were huge :P ). This increased the unallocated space 80GB (this was far another OS that I deleted).

Then I put the new SSD into a USB caddy, used GParted to create the same size 1mb boot partition (needed for GPT disks), created the same size root partition and similar size home partition. The partitions were just created to the same size, no mounting etc.

Then started Clonezilla and selected the device to device option. Then selected the part to local part option. This means that I can directly copy one partition to the same newly created one on the SSD. Pick the local source partition to clone, then select the target partition on the SSD.

I picked the 1mb boot as source and the 1mb partition on the SSD as target. Then I confirmed the settings etc and let Clonezilla do it's thing, I then done the same for the root.

I went to GParted and checked they were the same as the HDD (amount of storage used etc). Then I selected the 1mb partition on the SSD and set it's flag to bios_grub (required for a GPT disc).

I rebooted with the SSD attached in the caddy to see if it booted from the SSD. It DID :D I was expecting it to ask for the /home partition but it mounted the home on the internal HDD while using the root on the external SSD. Then I went back to parted magic and done the same for the home partition. 

All done :D yay!!

Hope this helps some people!

Thanks!

---

### Post by ahallubuntu on 2012-09-04
FYI, you can copy partitions directly with Gparted without even using Clonezilla (since it seems you already reduced the size of your original partitions).  Right-click on the partition in question (assuming you have booted from a live CD so these partitions aren't mounted) and choose "Copy."  Just create the same partitions (or larger if desired) as the originals on the new disk and paste each one.

Sometimes you have to update grub as well after cloning, no matter how you clone.

---

### Post by monotok on 2012-09-04
You learn something new everyday! That may have saved some time! Although both were on the same live CD.

Does GParted copy only the used part of the partition or does it copy it sector by sector?

Thanks!

---

### Post by ahallubuntu on 2012-09-04
> **monotok said:**
> You learn something new everyday! That may have saved some time! Although both were on the same live CD.

Does GParted copy only the used part of the partition or does it copy it sector by sector?

Thanks!

It copies only the used part I'm pretty sure.  You can always use the crude "dd" command to copy everything.

I do know that for NTFS partitions, it uses the "ntfsclone" command - probably same one Clonezilla uses.

---

