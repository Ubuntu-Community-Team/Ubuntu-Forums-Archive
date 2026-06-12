---
title: "Sandisk SD card won't mount in Gutsy"
date: 2007-12-01
forum: Hardware &amp; Laptops
---

### Post by A-dogg on 2007-12-01
I've seen a similar problem randomly mentioned in the forums, but haven't seen any answer. I have a sandisk ultra II (the SD card that you can snap open and plug directly into the USB drive) that I use in my treo. Obviously, in XP the card mounted fine. In Gutsy, though, if I have the "Computer" window open, I can see an icon show up ("MsMount" or something?) for like a split-second. And then it's gone. So the card won't mount. I have no idea if the card is FAT32 (I think it is, actually) or NTFS, but... can anyone advise? If it's a matter of buying a $12 card reader, I totally would -- I just don't know which way to go.

Thanks!

---

### Post by heatpumpcontrol on 2007-12-01
you probably will be better off just getting an all-in-one card reader. It will save you headaches.

---

### Post by A-dogg on 2007-12-01
so it IS a matter of gutsy not being able to read a sandisk card plugged directly into the USB?

any particular cheap card reader you recommend?

---

### Post by A-dogg on 2007-12-08
Hi, I was finally able to manually mount my SD card tonight. I created a folder in /media called "SanDisk" and then, in a terminal, typed "sudo mount /dev/sdb1 /media/SanDisk -t vfat".

The device mounted and I can copy things from the card to my hard drive. But I cannot alter anything on the card. When i try to, it tells me that:

Error while copying to "/media/SanDisk".
You do not have permission to write to this folder.

I'm new to linux and am just learning the terminal commands.

Can anyone help me with getting permissions?

Also, now that I can actually mount the device, is there a script I can write, or something I can edit so that it will automatically mount upon hotplugging (if I'm even using that jargon right...)?

Thanks!

---

