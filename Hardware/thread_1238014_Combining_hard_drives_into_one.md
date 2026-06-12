---
title: "Combining hard drives into one"
date: 2009-08-12
forum: Hardware
---

### Post by gardara on 2009-08-12
I am running a fileserver at home that stores a big archive of data (movies and stuff). I have a lot of different type and sized hard drives and I've had them all mounted with nfs which works ok but it would be a lot nicer if I could just mount it as a single drive.. would make finding files easier, etc.

I know I could probably do a hard or software raid but that would mean I have to format all the drives and I would probably have some issues because of the different size of the drives and when adding new disks.

I am actually not sure what I should be looking into, something with nfs probably or maby even some file manager on the client side that would index my files or something.


All ideas welcome.

---

### Post by gardara on 2009-08-13
Nobody?
I could just make symlinks manually I guess but I'd like to have something that would make this possible automatically.

---

### Post by SecretCode on 2009-08-13
Wouldn't just mounting all of them as subfolders of one particular folder address the point of finding things more easily?
/mnt/allmydrives/drive1
/mnt/allmydrives/drive2
etc

---

### Post by markbuntu on 2009-08-13
You can combine drives/partitions into one logical volume with LVM but I think that requires some reformatting. Something to think about for the future anyway.

---

### Post by gardara on 2009-08-14
Good Point SecretCode, it could work... but just isn't easy enough

And about LVM... Does it support easily adding new disks to the one big logical volume?
I could probably get some disks borrowed if a format is absolutely necessary and LVM is a solid solution!

---

### Post by markbuntu on 2009-08-14
I think you can dynamically change the LVM size but as I said, I don't know that much about it and have not really explored it having no need for it myself. I am sure there is a wiki or three around somewhere about LVM.

---

### Post by cariboo on 2009-08-14
Have a look at this [wiki page]("https://help.ubuntu.com/community/SettingUpLVM-WithoutACleanInstall"), it should help you do what you want.

---

