---
title: "umount user partitions not working"
date: 2008-10-09
forum: General Help
---

### Post by SteelWo1f on 2008-10-09
Hi

I have some entries in my fstab that have the user option set. So when I do 'mount -aO user' it mounts all those partitions. According to the man page I should be able to do 'umount -aO user' to then unmount them, but this doesn't seem to do anything. It doesn't even give me any warnings. The drives are not  in use when I try this. I do it immediately after the mount.

Any ideas?

Thanks

---

### Post by jerome1232 on 2008-10-09
Generally if the command doesn't give any output that means it was successful. Are you sure it didn't unmount? (the folder will still be there but nothing should be in the folder)

---

### Post by SteelWo1f on 2008-10-09
Yah its definitely still there. I check using df. To double check I just mounted it, wrote a file to the partition, unmounted it, and the file was still there.

---

### Post by mixmaster on 2008-10-09
Can you successfully unmount it as root?

---

### Post by SteelWo1f on 2008-10-09
If I just do a normal 'umount /var2' then it works.

---

