---
title: "Unallocated space problem"
date: 2008-08-22
forum: General Help
---

### Post by Elcid247 on 2008-08-22
hi, ive separated my /usr and /var from the root drive so i can resize them when needed and be able to save data if anything goes wrong.

anyway, i now have 7.6 GB of unallocated space, im not able to increase the size of the extended partition at all (tried using partition magic and Gparted Live)

the screenshot is from Gparted on my ubuntu (tried taking screenshots with Gparted live but when i rebooted, they got deleted :S)

any idea how i can get those 7 GB into my extended?

---

### Post by Diabolis on 2008-08-23
You can't resize a partition if its mounted. Unmount it first and then resize it.

---

### Post by Elcid247 on 2008-08-23
i did and i even used Gparted Live...

---

### Post by Diabolis on 2008-08-23
If you don't see any error messages, then I can only attribute this to the misunderstanding of how to manage the partitions of a drive.

Did you see any warnings or how do you know that you can't resize the partition?

---

### Post by coffeecat on 2008-08-23
I would guess that the reason you can't add the unallocated space to the extended partition is because it is not contiguous. But I'm prepared to be corrected. What I can say is that - forgive my bluntness - your partition layout is a mess. You now have no room for manoeuvre or flexibilty. If I was in your position, I would backup/image every partition, wipe the whole disc clean and start again.

If you do this, consider very carefully what you want on what type of partition. The only restriction is that Windows **must** be on a primary (and active) partition - unless you do some very clever hacking with an extra partition. Your Linux root partition can be a logical one - it doesn't have to be a primary one. And your swap partition can also be logical - at the moment it's a primary, which is a bit of a waste.

If you do backup/image, reformat and restore, all you have to do is to edit fstab and menu.lst to reflect the new partition identities (UUIDs if you use them), and reinstall grub to the mbr if you put your Ubuntu root partition elsewhere than sda1. Since you've been moving /usr and /var around I'm sure you know how to do that.

---

### Post by Elcid247 on 2008-08-23
> **coffeecat said:**
> I would guess that the reason you can't add the unallocated space to the extended partition is because it is not contiguous.

could u elaborate a lil more? and how to avoid this in the future?

> **coffeecat said:**
> If you do backup/image, reformat and restore, all you have to do is to edit fstab and menu.lst to reflect the new partition identities (UUIDs if you use them), and reinstall grub to the mbr if you put your Ubuntu root partition elsewhere than sda1. Since you've been moving /usr and /var around I'm sure you know how to do that.

nice idea thnx

> **coffeecat said:**
> Your Linux root partition can be a logical one - it doesn't have to be a primary one. And your swap partition can also be logical - at the moment it's a primary, which is a bit of a waste.

thnx i had just figured tht out yesterday while reading a wiki on ubuntu.

> **coffeecat said:**
> What I can say is that - forgive my bluntness - your partition layout is a mess. You now have no room for manoeuvre or flexibilty. If I was in your position, I would backup/image every partition, wipe the whole disc clean and start again.

yep ur totaly right, ive been thinking of redoing everything for a while. i was just waiting till i get the Gparted Live USB working, ive done it on my Hard Disk but i cant seem to get the syslinux.cfg right (tried the .iso, .zip and the Live USB versions), all HowTos r outdated, i was thinking of making 1 myself when i get it right.

---

### Post by coffeecat on 2008-08-24
> **Elcid247 said:**
> could u elaborate a lil more?

Contiguous Con*tig"u*ous, a. [L. contiguus; akin to contigere
 to touch on all sides. See Contingent.]
 In actual contact; touching; also, adjacent; near;
 neighboring; adjoining.
 [1913 Webster]

:wink:

> **Elcid247 said:**
> i was just waiting till i get the Gparted Live USB working

You've got Gparted on the Ubuntu live CD. Simply go to System > Adminstration > Partition Editor. It's a slightly older version than the one you can download from the gparted website, but it's perfectly OK to use. Have you tried that?

---

### Post by Elcid247 on 2008-08-24
> **coffeecat said:**
> Contiguous Con*tig"u*ous, a. [L. contiguus; akin to contigere
 to touch on all sides. See Contingent.]
 In actual contact; touching; also, adjacent; near;
 neighboring; adjoining.
 [1913 Webster]

:wink:

thnx for the dictionary output, but wht i wanted to know is wht u mean by contiguous in partioning... is the reason i cant resize the extended partition, tht there is a drive in between the unallocated space and the extended?! or wht did u mean?



> **coffeecat said:**
> You've got Gparted on the Ubuntu live CD. Simply go to System > Adminstration > Partition Editor. It's a slightly older version than the one you can download from the gparted website, but it's perfectly OK to use. Have you tried that?

actually the CD i have is kinda wierd, i downloaded it as an iso from the website right after the release, anyway when i use it, theres no option to go Live! lol! i mean the 1st option is "Install Ubuntu" not try it. so basically i dont have a live CD its merely an installation CD.

---

### Post by coffeecat on 2008-08-25
> **Elcid247 said:**
> i wanted to know is wht u mean by contiguous in partioning

If you look at your Gparted screenshot, you'll see that the 7.36GB unallocated space is 'before' your sda3 extended partition and that there's nearly 13GB between the two. The unallocated space would need to be 'after' the extended partition to be able to add it. That's why I suggested you might need to start over. You had no way to do what you wanted with the current partitions.

> **Elcid247 said:**
> actually the CD i have is kinda wierd, i downloaded it as an iso from the website right after the release, anyway when i use it, theres no option to go Live! lol! i mean the 1st option is "Install Ubuntu" not try it. so basically i dont have a live CD its merely an installation CD.

That sounds like the alternate CD, a text-only CD. When I saw your Gparted screenie I assumed you were using the live CD because this is what most people use. In case you haven't come across this before, you can run a full Ubuntu Gnome desktop from it and there's a graphical installer which most people find more friendly. And, as I said, Gparted is there at System > Administration > Partition Editor. The only real disadvantage is that you need more RAM to run it than you need once you're installed to HD. If you want to try it, download the 'desktop' iso. 

A thought just occurs. Which version of Ubuntu are you running? Is it an older one, because the live CD hadn't been developed for the first few releases? If you are running an old version of Ubuntu and you are going to completely re-organise your hard drive, it might be time to get the latest version of Ubuntu.

---

### Post by Elcid247 on 2008-08-25
im using ubuntu 8.04, i downloaded it 2 days after the release of hardy.


actually i dont need to start over, i found tht when resizing i can select where i want the free space to go, so basically i resized the swap and xp partitions, i didnt actually resize, instead i chose tht the 7 GB free space would be AFTER each instead of before it.


but im having a problem with Gparted when using it ON ubuntu, when i try to unmount any NTFS partition, it gives me the yellow triangle showing tht theres something wrong and remounts the partition, and if i close Gparted and unmount the partition, then open it again, it automatically mounts the drive again! so basically i cant do any operations on my NTFS partitions cause it keeps remounting them. any idea how i can solve this?

EDIT: this was because i didn't have ntfsprogs installed :D dam i was a noob a year and a half ago!

---

