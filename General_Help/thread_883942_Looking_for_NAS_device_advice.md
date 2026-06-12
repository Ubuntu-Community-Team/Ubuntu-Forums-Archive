---
title: "Looking for NAS device advice"
date: 2008-08-08
forum: General Help
---

### Post by dow mathis on 2008-08-08
I'm looking for a NAS device to put on my home network.  Currently, I've got a desktop PC that's dual booted with Ubuntu and WinXP, and a laptop that's running Vista (at least for now).  The desktop is on its last legs, and will need to be replaced.  However, if I can locate a good, relatively cheap NAS box that will support USB printing, then we can do away with the desktop entirely and go with a second laptop.  This is the solution that will please the wife most, so that's what I'm looking at.  

I've just been looking at the [[color=blue]_Promise SmartStor NS2300N_[/color]](http://www.promise.com/product/product_detail_eng.asp?product_id=198) and a single 500 or 750GB SATA drive now and then add a second one later, as we didn't budjet for this.  What are your thoughts on this solution, and do you know of any potential bugaboos with Ubuntu?

Would you recommend something else?  I really don't have the time or components available right now to build a file server.

Thanks,
dow

---

### Post by y@w on 2008-08-08
If you're going to be running a mix of Windows and Linux, I'd suggest making sure whatever device you choose supports NFS and CIFS, which I didn't see NFS as a feature for the Promise box. There are lots of other features, but those are the two I'd be most concerned with.

I know you said you don't have the time, but I'd suggest checking out the [FreeNAS]("http://freenas.org") project. You can boot it off a CD and configure it, just like you would a NAS you buy off the shelf. The only difference would be that you'd have to assemble the hardware..

---

### Post by dow mathis on 2008-08-08
Thanks for the response.  I'm looking at freenas now.  Do you have any idea if it's possible to expand an array after you create it?  For instance, if you've got a three disk raid5 array, can you add a fourth disk to it?

---

### Post by y@w on 2008-08-08
It looks like that *should* work. You can actually just boot the ISO up in a VM and add disks in and try it :) I'm going to be playing around with it in the future, but don't have a ton of time just like yourself. The feature I like the most of FreeNAS is that you're not locked into a hardware NAS so as long as your motherboard can support more drives, you can keep adding them. I would think that expanding the array would be a core piece of functionality..

---

