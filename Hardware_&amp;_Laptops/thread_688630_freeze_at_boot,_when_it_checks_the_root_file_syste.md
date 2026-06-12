---
title: "freeze at boot, when it checks the root file system"
date: 2008-02-05
forum: Hardware &amp; Laptops
---

### Post by XSC on 2008-02-05
it gets right past the ubuntu boot screen, then says some stuff with        [ OK ] , then says "* checking root file system"
"fsck 1.40.2"
"/dev/sda1 has been mounted 39 times without being checked, check forced"
"/dev/sda1: |===========...(and so on) - 73.4%"
when it gets to 73.4% or somewhere between 73% to 85.7% it just freezes, and i have to hold down the power button, and when i try to start back up it does this whole thing again, but before it was doing this it worked just fine, i could run msn, limewire, firefox, music
PLEASE HELP?
i want to avoid reformatting it but that could be a last resort
thanks.

---

### Post by emitchlpd on 2008-02-18
I'm seeing this problem too. The system is configured to do a disk check after 20 mounts of the root filesystem -- this is a good policy I'm sure but for whatever reason it's not able to complete itself.

I've found that booting either my Ubuntu LiveCD, or another live CD like Knoppix or Puppy Linux, and then running fsck on the drive will get the number of mounts set back to 0 so I can boot my system again.

This isn't ideal though, and I'm worried that I'll be at a client meeting and my laptop won't boot because of this stupid bug -- and I won't have that spare CD with me to save myself.

If anyone has ideas on how to fix this issue please post them!

---

