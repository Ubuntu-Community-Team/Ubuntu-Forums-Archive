---
title: "[SOLVED] How to recover a DMRAID raid0"
date: 2008-11-01
forum: General Help
---

### Post by tacone on 2008-11-01
Since Intrepid Ibex doesn’t support dmraid, and thanks also to a bug in the bootloader installation at the end of the procedure, my new Intrepid /boot partition wasn’t properly read at startup (the system kept on reading the old hardy partition).

Because of this, I had to find my way manually. But, in the middle of the process, I stupidly executed a command ( dmraid -rE /dev/sda ) which destroyed all my first disk metadata partition.

My raid setup was an Intel based Raid 0.

My /dev/sdb metadata is intact (I have the files generated from dmraid /dev/sdb -rD) , anyone knows a way (or a tool) to restore my raid ? Seems like I lost everything :).

---

### Post by russlar on 2008-11-01
> **tacone said:**
> Since Intrepid Ibex doesn’t support dmraid, and thanks also to a bug in the bootloader installation at the end of the procedure, my new Intrepid /boot partition wasn’t properly read at startup (the system kept on reading the old hardy partition).

Because of this, I had to find my way manually. But, in the middle of the process, I stupidly executed a command ( dmraid -rE /dev/sda ) which destroyed all my first disk metadata partition.

My raid setup was an Intel based Raid 0.

My /dev/sdb metadata is intact (I have the files generated from dmraid /dev/sdb -rD) , anyone knows a way (or a tool) to restore my raid ? Seems like I lost everything :).

Where this was RAID 0 (striping only), I recommend you give this command a shot:

$> sudo prayer

---

### Post by tacone on 2008-11-01
> **russlar said:**
> Where this was RAID 0 (striping only), I recommend you give this command a shot:

$> sudo prayer

$ apt-cache show prayer
[..]
Description: Standalone IMAP-based webmail server
Prayer is yet another Webmail interface.
[..]

Try again.

---

### Post by russlar on 2008-11-01
> **tacone said:**
> $ apt-cache show prayer
[..]
Description: Standalone IMAP-based webmail server
Prayer is yet another Webmail interface.
[..]

Try again.

Well, at least you're keeping a good sense of humor about this.
:lolflag:

---

### Post by tacone on 2008-11-01
Dropbox saved half of my butt :). It's the other half I'd like to recover. Come on, it's < 1kb of metadata. Anyone ?

---

### Post by psusi on 2008-11-05
When you erased the metadata on sda it should have dumped it to a .dat file first.  If you still have that you can put it back with:

sudo if=sda_isw.dat of=/dev/sda seek=`cat sda_isw.offset`

Those are backticks btw, not single quotes.

The metadata for sdb will be different so you can't use that if that's all you have.

---

### Post by tacone on 2008-11-05
Sadly I was on the livecd and I didn't saved the .dat files. My fault. I just resigned , build a new array, and formatted everything.

---

