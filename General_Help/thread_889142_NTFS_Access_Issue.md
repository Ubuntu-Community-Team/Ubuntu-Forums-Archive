---
title: "NTFS Access Issue"
date: 2008-08-13
forum: General Help
---

### Post by Marlow12ax7 on 2008-08-13
Hello All,

This question is about accessing NTFS disks from within Xubuntu Linux.

My system has two hard drives: Windows on one, 64-bit Xubuntu on the other. The Windows drive has two NTFS partitions. 

After I installed Xubuntu, I was able to access both windows partitions ... for a while. It was fine for two months, then it became intermittent, and now it's gone entirely. When I click on the /media/winhard1 directory, I get the error "access denied" or words to that effect. Running NTFS config has the same result.

I'm pretty much a Linux noob, but I've done everything I have learned to try. I ran chkdsk /f on the Win partitions, checked the language settings, updated NTFS-3G, and verified fstab against the output of fdiskl. Nothing.

I've done everything I can think of except reinstall Xubuntu ... but if I have to do that, it ain't coming back. I like Linux a lot, but I need it to play with Windows.

Anyone have a suggestion for how to resolve this problem?

Thanks,

Marlow

If it helps, here are my specs
CPU: AMD 5400+ dual-core
Mobo: GA-M55Plus-S3G
RAM: 2 Gig Corsair
Windows HD: 80G Seagate Barracuda ST380811as (two partitions)
Linux HD: 40G Maxtor 6E030L0
Windows XP
Xubuntu/Hardy Heron

---

### Post by pytheas22 on 2008-08-13
If you're being told "access denied," it's probably a permission issue.  I'm not sure why it would have changed suddenly if it worked without authorization before, but try open opening the file browser as root:
```

sudo thunar
```

and see if you can browse to the Window partition that way.  That will at least let us know if permissions are the problem or not.

---

### Post by Marlow12ax7 on 2008-08-14
It now seems to be working. Here's what I did.

I started sudo thunar like you said. Then I navigated to the NTFS partitions, right-clicked, and selected "permissions". Then I changed the permissions group from "root" to "[myname]". I selected recursion, and then rebooted. That fixed it!


Thanks!!!!!

---

