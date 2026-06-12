---
title: "Ubuntu doesn't show my external hard drive"
date: 2009-05-11
forum: Hardware
---

### Post by Lakeside5 on 2009-05-11
I'm sure lots of people have had this issue, s I shall post here.  I have Hardy Heron 8.04 and it doesn't seem to show my Lacie external hard drive (plugged in right now, and I JUST saw it on the other *cough* Windows computer). I have files I want to transfer to the Windows one from this one, so I'm trying to use the external, but I can't see it listed in 'places'. I must have to configure something? (simple explanations please, I don't know much lol) thanks so much for any help ;)

---

### Post by cholericfun on 2009-05-11
did any error message pop up?
did you "unmount" it in windows?
did you try various USB ports?

plug it out and have a look under 
/dev
and see what entries there are for  sd*.. (sda1,sda2...) and hd* (hda1, hdb) and such like

then plug it in and have another look...

---

### Post by Bucky Ball on 2009-05-11
Ubuntu will read your NTFS drives fine (if you have windoze you probably have them). You just need to mount em perhaps (including your external). Go to Synaptics and search for:

ntfs-3g

Install and run and see how you go. What format is your external drive?

If this fails to find, you can mount manually. With your hard drive plugged in and switched on, go to a terminal and type or paste:

sudo blkid

Does it show up there? Let us know how you go.

---

### Post by Bucky Ball on 2009-05-11
Ubuntu will read ntfs no problem and if you have Windoze installed you probably have a couple of ntfs partitions. Would save using the external. You probably need to mount them and the external drive. Go to Synaptic Package Manager and search for:

ntfs-3g

Install and run and see how you go. If this fails to find, you can mount manually. With your hard drive plugged in and switched on, go to a terminal and type or paste:

sudo blkid

Does it show up there? Let us know how you go.

---

### Post by Lakeside5 on 2009-05-12
Thanks for all your help! This is an awesome forum, I can use my external now.

---

