---
title: "Swap Partition Not Automatically Activated After Jaunty Upgrade - How to Fix?"
date: 2009-05-13
forum: Hardware
---

### Post by OzzyFrank on 2009-05-13
Seems that since the upgrade to Jaunty I have to manually mount the swap partition (by setting SWAPON via Partition Editor). While I understand Fstab and have been using Ubuntu since 6.10 so once upon a time had to do edit my Fstab to get the swap to be in use automatically upon boot, I haven't had to worry about that for a while.

Since I swap drives around and things like adding an IDE backup drive can mess up the SATA drive numbers, the fact I didn't have to worry about all that recently has been welcome. So any ideas why it would now not mount the swap upon boot, and how to fix this? I'd prefer not to have to edit Fstab. Is this a Jaunty bug that is to be fixed?

---

### Post by logos34 on 2009-05-13
post your

sudo fdisk -l

cat /etc/fstab

sudo blkid

maybe it's just a wrong uuid

---

### Post by OzzyFrank on 2009-05-19
Here is the relevent info. I don't think it is a wrong uuid issue, but then can't really tell since (as you'll see below) **blkid** doesn't show the swap has one at all. I assume if the other uuids match what is in Fstab, the swap should be fine (can't remember what command I used to get the uuid for the swap, but it supplied the correct ones for the main partitions, and the swap was mounted and activated automatically before the Jaunty upgrade).

[B][COLOR="Red"]sudo fdisk -l
[/COLOR][/B]
[COLOR="#0000ff"][B]Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2101e331

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       45762   367583233+   7  HPFS/NTFS
/dev/sda2           45763       90564   359872065   83  Linux
/dev/sda3           90565       91201     5116702+   5  Extended
/dev/sda5           90565       91201     5116671   82  Linux swap / Solaris[/B][/COLOR]

**[COLOR="#ff0000"]cat /etc/fstab[/COLOR]**

[B][COLOR="#0000ff"]# Ubuntu 64-bit
UUID=daf56d80-15b5-4314-9672-fd91d12a3bd6 /               ext3    defaults,errors=remount-ro,relatime 0       1
# Windows XP x64
UUID=1D3688CD689CA81D /media/Windows-XP-x64     ntfs-3g defaults 0 0
# Ubuntu Swap
UUID=2eefabb9-6ec1-47a2-b357-959763739388 none            swap    sw              0       0[/COLOR][/B]

[COLOR="#ff0000"]**sudo blkid**[/COLOR]

[COLOR="Blue"][B]/dev/sda1: UUID="1D3688CD689CA81D" LABEL="Windows Drive" TYPE="ntfs" 
/dev/sda2: UUID="daf56d80-15b5-4314-9672-fd91d12a3bd6" TYPE="ext3" 
/dev/sda5: TYPE="swap"[/B][/COLOR]

Anything here shed light on what is happening? Cheers

---

### Post by logos34 on 2009-05-19
I guess it could be a bug like you say...Have you searched launchpad?

How about trying the old device format?

> # Ubuntu Swap
**/dev/sda5** none swap sw 0 0

now does it automount?

---

### Post by OzzyFrank on 2009-05-20
Yes, it automounts as **/dev/sda5**, which still begs the question why it won't mount with the uuid (I doubt it has somehow changed since the others are still fine). I would have to say that it is a bug (and no, didn't look it up on Launchpad - I rarely get any answers there, just more questions). The reason I switched to uuids in the first place was because with each kernel update a few versions back my hard drives would get changed from **hda** to **sda** and back again, etc, which would play havoc with things like the swap and storage drives mounting (the system would still boot fine, and no GRUB errors thank the stars, but annoying nonetheless).

By the way, is it normal for **blkid** to give no uuid for the swap when asked? I can't remember what command I used to find the uuids in the first place, but thought it was this one, but now doubt it since it doesn't specify one for the swap.

---

### Post by logos34 on 2009-05-20
no, it's not normal for blkid to not output the swap uuid

yep, uuids helped avoid a lot of grief in the transition to the libata storage driver (which sees everything as 'sdx')

other uuid commands:

sudo blkid -c /dev/null (-->see man page)
sudo vol_id -u /dev/sda5
ls -l /dev/disk/by-uuid

---

### Post by OzzyFrank on 2009-05-20
Well, sudo **[COLOR="Indigo"]blkid -c /dev/null[/COLOR]** gives the same output as before ("swap"), [COLOR="#4b0082"]**ls -l /dev/disk/by-uuid**[/COLOR] does not list the swap partition at all, and [COLOR="#4b0082"]**sudo vol_id -u /dev/sda5**[/COLOR] does absolutely nothing at all but return to the command prompt. That seems a bit weird to me, as I am sure it was either **blkid** or the second command listed above that I originally got the uuid from.

---

### Post by logos34 on 2009-05-20
hmm...maybe something's screwy with the partition...you might try deleting swap and making a new one.

---

### Post by OzzyFrank on 2009-05-20
Well, since the partition seems to be in use and working fine I'd perhaps want to make sure there indeed is something wrong before I do that. Is there any way to check whether the swap is healthy or not? Looking at it via **top** it looks fine.

---

### Post by logos34 on 2009-05-20
dunno know, maybe fsck, but it will probably show up 'clean'.  It's not a bif deal to chuck it and make a new one.  just swapoff, open gparted and delete.  create a new 'linux-swap'

---

### Post by OzzyFrank on 2009-05-26
I deleted the swap and recreated it, and now it has a UUID. I'm gathering that if the swap was successfully mounted with each boot and used without issue/errors (as far as I could see) then it wasn't corrupt, so out of curiosity if anyone reading this in the future knows why this happened, please let us know. Cheers.

---

### Post by OzzyFrank on 2009-06-09
PS: In my opinion, not being able to mark a thread as **[SOLVED]** anymore kinds sucks. It makes such a difference when trying to find a solution in this huge forum.

---

### Post by OzzyFrank on 2009-12-17
I'm just marking this as Solved since that's now allowed again.

---

