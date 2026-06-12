---
title: "Can't Write to mp3 Player Samsung Yepp even though I have write permission!!!????!!!!"
date: 2008-03-07
forum: Hardware &amp; Laptops
---

### Post by seismicmike on 2008-03-07
I'm having a very odd problem with my Samsung Yepp player that seems to be different from all the other problems I've seen on here.

It mounts just fine and I can peruse the files. But I cannot write to the disk.

STOP... Before you tell me about write permissions, ownership, chmod, chown and all of that stuff, THAT ISN'T THE PROBLEM.

I have a MemoRive 2GB Thumb drive that I mount and use just like any other thumb drive without any trouble whatsoever, and my mp3 player has the exact same mount options as the thumb drive (except you know... the mount point)...

Furthermore, when I try to add files to the player, I'm **NOT** told that I don't have permission or access. Nautilus simply opens its file transfer dialogue and then sits there and looks at me. The Progress bar stays stuck at 0%. The rate says "Stalled" and the estimated time left taunts me by keeping track of how long it's been since I started the process (it indefinitely counts up)....

At this point if I want control of my computer back, I have to physically yank my player from the USB port......

Does anybody have any idea what might cause this?

EDIT: In case anyone asks, it is not mounted as a read only disk, and no, the hold/write protect button on the device is turned off.

---

### Post by seismicmike on 2008-03-10
bump

---

### Post by seismicmike on 2008-03-12
bump                ba bump    bump
bump                ba bump    bump buuuuuuuuuuuuuuuuuuuuuuuuuuuuump

bump                ba bump    bump
bump                ba bump    bump buuuuuuuuuuuuuuuuuuuuuuuuuuuuump

---

### Post by seismicmike on 2008-03-17
SOLVED!!!!!!!!!!!

Thanks to the guys in the IRC chatroom I figured out that the player uses MTP (media transfer protocol) instead of UMS. This was what caused my problems. There are two potential fixes for this:

1) Configure Amarok to treat it like an MTP (which I would have done all along had I known) and it should work

2) Follow the directions [here]("http://beranger.org/index.php?page=diary&2007/12/10/15/14/55-make-your-samsung-yp-u3-j-linux-") to change the firmware on the device to UMS instead of MTP. BE VERY CAREFUL THOUGH BECAUSE A WRONG STEP RUINS THE DEVICE!!!

I chose #2 b/c I don't only add files in Amarok. Sometimes I go through Nautilus and wanted that flexibility. It works perfectly now. Thank you IRC guys, specifically Scunizi!!!

---

