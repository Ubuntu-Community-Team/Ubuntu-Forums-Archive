---
title: "Can someone recommend a good RAID 5 controller card?"
date: 2010-03-05
forum: Hardware
---

### Post by diablo75 on 2010-03-05
I am wanting to build a NAS with Ubuntu on it and I'd like to go with a hardware managed RAID 5 array.  I read an article on Tom's Hardware that uses one from LSI, but they are pretty dang expensive so I was trying to find something cheaper.

---

### Post by paulisdead on 2010-03-05
If I don't have the budget for a 3ware or Areca card, I don't bother with hardware and just do software Linux RAID, which actually has pretty decent performance.  An added benefit, is you can plug the drives into another linux box, and bring the array up, even if the disk controller is completely different, just in case the controller or motherboard in the main machine dies.

I know LSI owns 3ware now, but I've not liked their cards.  It has been over 4 years since I played with them, but they had pretty sub-par performance under Linux then.  It's probably improved, but I'd still rather have the 3ware brand and utilities over LSI.

For a real hardware RAID card you're probably looking at at least a few hundred bucks.  Until I managed to get myself a couple 3ware cards, I just used a motherboard that had 8 sata ports and soft RAIDed them.  You'll need the alternate install CD to install Ubuntu onto a software RAID array.

---

### Post by IcarusR on 2010-03-06
3ware cards always. Been using one in my server, mirror, for 3 years now with no issues. Can control via web page & command line.

---

