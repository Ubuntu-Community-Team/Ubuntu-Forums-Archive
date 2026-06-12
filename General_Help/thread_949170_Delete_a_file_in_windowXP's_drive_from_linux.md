---
title: "Delete a file in windowXP's drive from linux"
date: 2008-10-15
forum: General Help
---

### Post by anshulmalik1987 on 2008-10-15
hi i want to delete the autorun.inf file in a windows drive from linux.
But i am getting an error message that the drive is read only.
when i see the persmission of the drive the user group is plugdev.
please tell me how to do it

---

### Post by Cl0ud9 on 2008-10-15
Did the error message say "failed permissions" or something of that sort?
If so try using sudo.

Otherwise this link may be of use to you:
[http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html]("http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html")

---

### Post by bigbrovar on 2008-10-15
have you installed ntfs-config from the repositories ```
sudo apt-get install ntfs-config
``` once installed the program can be found in Application/Systems/ntfsconfig open it set a name for your NTFS partition make sure its one word .. from there follow the prompts and you should be done

---

