---
title: "Non-destructive move of extended partition?"
date: 2009-05-19
forum: Hardware
---

### Post by durand on 2009-05-19
First of all, I'm not sure where the right place would be to post this, so mods, please move this if needed.

I have a fairly complex partition layout which I've screenshotted and attached to this post. I basically have too many partitions and I've reached the limit of primary partitions and logical partitions inside my extended one. I've also got some extra space on either side of my extended partition. So I need to move it to one end of the drive. The screenshot shows gparted moving my vista partition as well because I pretty much never use it so I've just resized it to be as small as possible.

My question is, would moving my extended partition cause any destruction of my data? I couldn't care less about sda3,9,11 however I really do need to keep the others safe. Is there a recommended way to do something like this? I plan to use dd to image my whole hard drive onto my external drive just in case but I would still like some input before I try something potentially stupid. Oh and if someone knows how to use dd, that would be helpful as well!

Thanks a lot!

EDIT: I just remembered that I can't dd my disk because my big external hard drive partition is FAT32 which doesn't support large files(?). I'll probably just backup my data.

---

### Post by Dark_Stang on 2009-05-19
The last time I rearranged my partitions I just used a gparted disc and I didn't lose any data. However my partition table is nowhere near as complicated as that. And any time you repartition a drive you always run the risc of destroying data so be sure to backup any important things.

Edit: Oh, and FAT32 has a maximum file size of 4gb.

---

### Post by durand on 2009-05-19
Thanks a lot! Resizing and moving the Vista partition went practically flawlessly (had to use the repair tool on the vista disk) but I'm worried if extended partitions are treated in a different way and therefore not have the same positive result.

I might just resize that FAT32 partition and put ext4 on there as well however that's really a last resort since I have quite a lot of stuff on the FAT32 partition which I can't backup. Maybe if I could compress the dd image somehow, then I could put it on my ext2 partition which is also on that hard drive. The only problem is that it's only got about 50GB spare. It's a shame that FAT32 only supports 4GB...

I'm just going to wait for a bit more input from other people and then probably just backup the essentials rather than everything.

---

### Post by durand on 2009-05-20
Well, I just went ahead with it. I couldn't move the extended partition but I could resize it to fill up the space on either side of it. I guess I'll just have to leave it as two partitions or use LVM/raid.

---

