---
title: "linksys wireless adapter help..."
date: 2009-09-20
forum: Hardware
---

### Post by alms66 on 2009-09-20
I managed to get someone to give ubuntu a try on his old computer since Windows runs horribly slow on it.  Unfortunately, the wireless internet is not working and I'm still a bit of a noob here, so I haven't been able to get it working in my own searches.

The results of lsusb indicate that the device is detected:
Bus 001 Device 002:ID 1915:2234 Linksys WUSB54G 802.11g Adapter

Can someone give me a hand or point me to a good way to get this thing working.  He already wasn't too impressed with the thought of using Linux, I'd hate to give him (and Windows) a win by not being able to get his internet working.

Thanks.

---

### Post by alms66 on 2009-09-22
*bump*

---

### Post by cariboo on 2009-09-23
Can you post the results of running:

```
sudo lshw -C network
```

This will tell us if the device is detected and athe if the driver is loaded.

---

### Post by alms66 on 2009-09-24
I will do that, but just FYI, I won't be able to get to it until this Sunday, most likely.

---

### Post by alms66 on 2009-09-27
Well, just in case anyone was watching for the output...

Short story:
It turns out that the hard disk died on this computer.  He says it's going to be a while before he goes buy a new one, and likely when he does that he'll just upgrade the whole computer and put Windows on it - or just buy a new one altogether.  Thanks for the offer of help anyhow.

Long story:
I had 9.04 installed.  I decided to try 9.10 to see if it might set up the wireless adapter automatically.  Now when I booted live 9.10, it gave a message that the hard disk was bad (don't remember the exact message).  I tried installing anyway and it failed.  So I try 9.04 again, it failed.  I/O errors both times.  I tried Windows, just to see what would happen...

So Ubuntu gave a warning that the disk was bad and wouldn't install, and Windows just blindly ignored this fact and installed.  Now, had that machine gone into regular use with data that wasn't backed up and it was lost - that would have sucked.  But, from this guy's point of view, and I could just see if from the look on his face when all this occured, "Windows wins, Linux sucks" because Windows installed and Ubuntu failed to.

I'd like to know why that was.  I suspect it's because of the different way the two filesystems (ext3 & NTFS) work, would that be correct?  Anybody experience this before?

---

