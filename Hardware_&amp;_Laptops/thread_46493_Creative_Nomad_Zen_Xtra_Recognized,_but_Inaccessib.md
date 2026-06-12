---
title: "Creative Nomad Zen Xtra Recognized, but Inaccessible"
date: 2005-07-05
forum: Hardware &amp; Laptops
---

### Post by Flakes on 2005-07-05
It is shown in the device manager, but it doesn't know the vendor, the device, status, etc. it all is listed as unknown... ive re-downloaded and re-installed the proper drivers for it and still am stumped... any ideas?

---

### Post by ulisse on 2005-07-05
I don't own a Nomad player, so I can't help too much, but you should try to apt-get Gnomad2; it seems to be right what you're looking for ;-)

---

### Post by Flakes on 2005-07-05
right, got that... and anything else that has to do with it... when i click "scan for contents", it can't open it... i think it has less to do with the Nomad itself but with the USB... do i need to mount it?

---

### Post by Flakes on 2005-07-05
bump

anyone have any ideas please?

---

### Post by ulisse on 2005-07-06
Try to see if the device can be mounted ad a scsi disc; type:

cat /proc/partitions

in a terminal with the device connected, and look for something like sda1, or sdb4 or similar.
If so, you can try to mount that like an ordinary drive:

mount /dev/sda1 /mnt/yourMountPoint

---

### Post by Flakes on 2005-07-07
[QUOTE=ulisse]Try to see if the device can be mounted ad a scsi disc; type:

cat /proc/partitions

in a terminal with the device connected, and look for something like sda1, or sdb4 or similar.
If so, you can try to mount that like an ordinary drive:

mount /dev/sda1 /mnt/yourMountPoint[/QUOTE]
 major minor  #blocks  name

   3     0   30029328 hda
   3     1   29278431 hda1
   3     2          1 hda2
   3     5     746991 hda5
 254     0   29278431 dm-0
 254     1     746991 dm-1


Which one would it be? my hd is 30 gigs, so is that hda1? or is hda it?

Note that my mp3 player is 30 gig

---

### Post by ulisse on 2005-07-07
Your HD is hda, into your HD you have three partitions: hda1 is the first phisical partition, then you have another phisical partition of 1 block, hda2, and after that the logical partition hda5. (in a disk can be only 4 phisical partition, so if you have some logical ones, the numbers starts from 5).

I don't know what actually are that dm-0 and dm-1, but they seems to be the same partitions of hda... (maybe dm stands for disc-mounts?)

Unfortunately ther is no track of your mp3 reader, so probably it can't be mounted like an HD.
At this point I can't hel pyou anymore, wait for someone more expert.
Sorry.

---

### Post by Flakes on 2005-07-07
[QUOTE=ulisse]Your HD is hda, into your HD you have three partitions: hda1 is the first phisical partition, then you have another phisical partition of 1 block, hda2, and after that the logical partition hda5. (in a disk can be only 4 phisical partition, so if you have some logical ones, the numbers starts from 5).

I don't know what actually are that dm-0 and dm-1, but they seems to be the same partitions of hda... (maybe dm stands for disc-mounts?)

Unfortunately ther is no track of your mp3 reader, so probably it can't be mounted like an HD.
At this point I can't hel pyou anymore, wait for someone more expert.
Sorry.[/QUOTE]
 well thanks a lot for your help though :) im going to try posting at nomadworld, maybe somebody there will have a little more expertise on the subject...obscure as it is ;)

---

### Post by Rippa on 2006-04-24
G'day, I wont have a clue if this helps but I have a zen xtra nomad mp3 player and I used synaptic to install 'Gnomad2' and 'neutrino'. Then I opened a shell window and typed:

'sudo gnomad2' 

and to my bewilderment it worked!

It doesn't work unless I use it under 'sudo'.

Hope that helps!

---

