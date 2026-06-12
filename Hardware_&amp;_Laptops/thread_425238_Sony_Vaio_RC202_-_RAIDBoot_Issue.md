---
title: "Sony Vaio RC202 - RAID/Boot Issue"
date: 2007-04-27
forum: Hardware &amp; Laptops
---

### Post by Mrs Harris on 2007-04-27
Hey all,

I've got a bit of an issue.  I got a Sony Vaio RC202 Media Centre and planned to put ubuntu on it and after having a nightmare trying to install feisty (had issues with the SCSI drives being seen as removable media) I now cannot boot it.

Essentially it gets to the "GRUB loading, please wait" and then hangs.  I think it may be to do with my RAID settings but sadly there is no BIOS option to turn the raid off.  Is it likely that this is the issue?  I called Sony and they said that there is no option to turn off the RAID.

I've also tried Edgy and this gives me a GRUB error 17.

I bought this from play, do you think it's likely they'll refund me?

---

### Post by soapytheclown on 2007-04-27
Ive been trying to get around the problem which you described, as soon as id install feisty on my friends sony vaio VGN-AR11S it would come up with grub error 2. 

i thought id try out a copy of edgy (here at uni however i only had beta knot 2) which took a good hour to install. After booting for the first time it just hangs at "GRUB loading please wait..."

I took the raid thing into account that you mentioned, Put on the network boot options to be on in the bios, and when i booted up again, it gave me a quick option for about 5 seconds to enter raid setup (ctrl-i) where i took off the raid features and now i can boot into this version of edgy, 

im seeing if i can drop a copy of fiesty back onto the same partition (doing an entire disk wipe)

will report back if there are problems

---

### Post by dj_flx on 2007-07-01
> **soapytheclown said:**
> I took the raid thing into account that you mentioned, Put on the network boot options to be on in the bios, and when i booted up again, it gave me a quick option for about 5 seconds to enter raid setup (ctrl-i) where i took off the raid features and now i can boot into this version of edgy, 

im seeing if i can drop a copy of fiesty back onto the same partition (doing an entire disk wipe)

will report back if there are problems

I unknowingly stumbled into this trying to install Feisty onto a VGN-AR370 this weekend. How exactly did you do the BIOS/RAID setting thing? Did it eventually work out?

---

