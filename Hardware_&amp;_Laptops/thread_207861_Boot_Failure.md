---
title: "Boot Failure"
date: 2006-07-02
forum: Hardware &amp; Laptops
---

### Post by gibbylinks on 2006-07-02
Help Please

I don't know if this is a coincidence or what (I think it is). I installed wine this afternoon. Not having touched it before and was trying to get EAC working with it. Gave up after a while and shutdown the machine.

I now have a huge problem (not bragging here)

When I try to boot I get 

Searching For Boot Record From IDE-O OK
Boot Failure From Previous Device

And get prompted to insert a floppy or disk with a Boot Record

I'm typing this using the 6.06 LTS Live/Install CD

I can mount my disk /dev/hda1 and mooch around in it, but it won't boot.

I only have Ubuntu on it with 3 kernels and just two partitions Ext3 and a swap partition.

It was a fresh installation about 3 weeks ago and has been running fine, xgl, compiz and all.

Can anyone rescue me from the mud

Cheers :confused:

---

### Post by gibbylinks on 2006-07-03
C'mon guys please.

I finish work in a few hours and was hoping one of you heroes would have had some pointers for me !!

---

### Post by gibbylinks on 2006-07-04
Well thanks guys, your policy of leave it long enough and he'll get there worked (lol) :-) !!!

I followed this thread [http://ubuntuforums.org/showthread.php?t=24113&highlight=mbr+problem]("http://ubuntuforums.org/showthread.php?t=24113&highlight=mbr+problem")
but had to use the setup (hd0) option rather than (hd0,0) that I'd used previously with no joy.

When I changed it re-wrote the sectors and installed OK. Now it boots fine.

Hope this helps other folk

\\:D/

---

