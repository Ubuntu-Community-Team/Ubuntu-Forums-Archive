---
title: "Partitioning Lenovo S10-3T for Ubuntu dual boot"
date: 2010-08-01
forum: Hardware
---

### Post by Factoryworks on 2010-08-01
Hi,
now I also have the nice little Lenovo S10-3T.
It came with Win7 but I want to have Ubuntu on it, same as on my main  machine. I have seen many people using it with Ubuntu but could not  figure, how they solved my issue with the partitioning described below. 

The device has the following partitions:
- 200MB - boot
- 180G - C:
- logical
--- 30G - LENOVO
- 14G - LENOVO PART

What I want to do, is cut C: down (to allow dual boot) for my various Ubuntu partitions (root, home, swap, data, ...). Cutting down is easy.
Since I recall that only 4 partitions are possible, I have to place my  new partition in the logical one already available. Therefore, I would  have to extend it to the left (where the newly generated free space is  located). This is imho not possible.

How did you solve this? Maybe my assumptions are outdated (coming from  my very first days with Ubuntu 06)? Please share your partition scheme  and how you achieved this?

I want to keep Win7 for the moment, until I have Ubuntu touch-screen and  -rotation fully functional (2nd step, I have seen the thread). I could  do without the lenovo-mini-linux they call fast-boot or so.

Thanks in advance
   Dietmar

---
edit: i thought I just give it a trial:
reseized C in Windows to minimum -> gave me 85GB
just played the stupid user and created my partitions with the Ubuntu installer as desired -> surprise, it worked
So it looks like the limit of 4 partitions is obsolete and so were my concerns
Now, Win7 still works, ubuntu works iin recovery mode with a screen issue, but that is another topic

Dietmar

---
yet another update: Ubuntu shows, that it enlarged the logic parition which now also covers my Ubuntu partition.
So it looks like the limit of 4 partitions is still applicable, but Ubuntu installer is so smart to enlarge a logic partition to cover those newly added. Very smart. Of course, this requires that the new partitions are next to the existing logic one.

---

### Post by Paul S on 2010-08-11
I have the same s10-3t and am facing the same problem.  I wonder if the lenovo one-key-recovery has problems with this.

For example, you can create additional recovery backups from windows and backup your files.  Where does OKR put that stuff.  Will it try to write over your linux on that extended partition?  Have you tried anything like creating a backup since you put ubuntu on that extended?

I also am hoping to be able to add additional linux / meego / et.al. distros and multi boot.  As long as the recovery system doesn't mess with those added logical partitions, it should be possible.

---

### Post by Jenopo on 2011-09-24
EDIT: unnecessary, so deleted

---

