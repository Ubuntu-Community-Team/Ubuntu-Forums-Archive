---
title: "ext3 HDD wont mount."
date: 2006-03-20
forum: Hardware &amp; Laptops
---

### Post by nismoskys on 2006-03-20
i just REinstalled ubuntu onto a new 200gig harddrive and everything went smoothly. i have, however 2 identical 40 gig (western digital) harddrives, one that i first mounted from my new installation to copy over JUST videos, the second, that i had my whole old ubuntu on with all my main files on it.

the first hdd, with the vids on it, mounted perfectly, i transferred the files, and it worked and i was happy with it. 
The 2nd, however, refuses to mount. im using the Disks Manager in Sys -> Admin.
I go to the disks, i select the 40 gig disk(it shows up in the menu), go to partitions, select an access path, and click ENABLE. nothing happens. (this is the same thing i did with the 1st 40 gig hdd and it worked fine)..

whats wrong? why wont it mount?.

thanks.

---

### Post by nismoskys on 2006-03-20
*i did open up my comp and double checked the cables, they're in fine

---

### Post by nismoskys on 2006-03-20
hell yeah nvm i figured it out i did it through the terminal though (still unsure why it didnt work through disk manager)
i just typed

```
sudo mount -t ext3 /dev/hdb1 /media/hdb1
```

and it worked perfectly :)

---

