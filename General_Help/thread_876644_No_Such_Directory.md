---
title: "No Such Directory"
date: 2008-07-31
forum: General Help
---

### Post by daevyd on 2008-07-31
I've been trying to view my settings for dev/hdc pertaining to DMA to get my DVD playback to work and it's coming up with:  

 
/dev/hdc: No such file or directory


Is this bad and if so how can I correct this?

---

### Post by tuxxy on 2008-07-31
Same here, no file there so I dont think its bad

---

### Post by daevyd on 2008-08-01
But what the heck?  This link here:  [https://help.ubuntu.com/community/DMA](https://help.ubuntu.com/community/DMA)  says it should be there.  Sometimes I feel like pulling my hair out but then I realize that the pain that would cause would totally suck worse than no DVD playback on Ubuntu.

---

### Post by ModelM on 2008-08-01
Udev probably used a different name. Try:

/dev/cdrom
/dev/cdrom1
/dev/dvd

---

