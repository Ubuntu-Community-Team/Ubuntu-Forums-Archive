---
title: "Cleaned USB with sudo dd, now can't create a partition - &quot;may need to update fstab&quot;"
date: 2015-06-20
forum: Hardware
---

### Post by Northstat on 2015-06-20
I'm not entirely sure what went wrong of if something did go wrong but I dunno what to do now. I'm following this 

[http://askubuntu.com/questions/185815/how-do-i-clear-everything-data-viruses-from-a-thumbdrive](http://askubuntu.com/questions/185815/how-do-i-clear-everything-data-viruses-from-a-thumbdrive)

and I'm at the "Creating partition on the empty disk" step 2. I cleared the drive using sudo dd ... from the above section and now when I try to run "sudo parted /dev/sdb mklabel msdos" I get the error 


"
Warning: The existing disk label on /dev/sdb will be destroyed and all data on this disk will be lost.Do you want to continue?
Yes/No? Yes                                                               
Information: You may need to update /etc/fstab. 
"

If anyone could help me out I would appreciate it. Thank you!

---

### Post by Dennis N on 2015-06-20
The warning is normal. You can do this with gparted from **Device > Create Partition Table** as well (choose MSDos after this). The same warning appears.
The information provided would seem to be for a permanent hard disk drive and not applicable to a flash drive.

---

