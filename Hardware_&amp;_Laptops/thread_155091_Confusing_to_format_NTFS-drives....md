---
title: "Confusing to format NTFS-drives..."
date: 2006-04-04
forum: Hardware &amp; Laptops
---

### Post by XPerienced on 2006-04-04
Hi!

I'm having problems here to find how I should format and encrypt my NTFS-drive. It's an encrypted NTFS-drive. The backup is finally done.

Now, I would like to choose the filesystem for the harddrive, but I don't know the differens. This drive is for storing som I think EXT2 might be good.

I would like to access 100% or as much as possible. I don't want to reserve space.

And when I would like to encrypt the storagedrive, but which way is the best? First format, encrypt and the transfer the backup via Samba?

I checked with "sudo -lshw -C disk" and I the system finds the harddrive, but I can't see it anyware else. Not in gparted. 

I have Ubuntu serverinstallation with Xubuntu-desktop. I don't have Gnome at all. I have Thunar, gparted too installed via apg-get.

I'm running out of time so I appreciate alot if I can get helt to make this clear. I found a HOWTO about encrypted drives, but the drives are empty now so there might be a better way? DM-crypt with AES-128 or higher is what I think will be the best.

It must be secure and still be functional and not take to much space.  

XPerienced

---

### Post by renzokuken on 2006-04-04
for the formatting i would suggest using a prog called qtparted (or gparted) which are both in synaptic.

as for encryption, sorry, no idea

---

### Post by XPerienced on 2006-04-04
I checked a last time and I finally found that I could change the harddrive in a list, but I'm not sure which filesystem I should choose for storage only. 

I will encrypt the harddrive after the formating. 

But I don't know how I should do. This is still very, very new for me.

XPerienced

---

### Post by renzokuken on 2006-04-04
for storage only ext3 would be fine

---

