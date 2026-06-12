---
title: "Merging Partitions"
date: 2008-08-15
forum: General Help
---

### Post by iamhigh on 2008-08-15
Hello all,

I originally had the Gutsy edition installed. When the Hardy heron edition came out, i downloaded the alternate install to upgrade. The installation didnt go all well as expected and after much trouble I decided to do a clean install of Hardy on a diff partition. Now I have Gutsy and Hardy with all my data on Gutsy.  Here is the GParted screen shot attached for reference and the link.

[IMG]http://tinypic.com/view.php?pic=2wfl1ex&s=4[/IMG]
[http://i33.tinypic.com/2wfl1ex.jpg](http://i33.tinypic.com/2wfl1ex.jpg)

I am able to see my files on Gutsy from Hardy and have copied my backups onto Gutsy.

I would like to delete the Gutsy partition and merge it with Hardy and want to know what steps on Gparted would I need to take to make sure it happens correctly.

Thanks.

---

### Post by ibuclaw on 2008-08-15
Make sure you have moved all precious files/folders onto the hardy partition, then boot into your Ubuntu LiveCD and tell gparted to remove the Gutsy and smaller swap partition, then resize your hardy partition to fit.

It is very simple, just make sure you are removing/resizing the right partitions. :)

[EDIT]
You'll have to resize the extended partition first (sda2) and then resize Hardy to fit into the new extended partition (sda6).
Remove sda5, as you aren't using that swap, and move the other swap partition (sda7) to the end of the partition layout.

Regards
Iain

---

