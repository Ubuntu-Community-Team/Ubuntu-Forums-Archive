---
title: "How should I automount an external drive and ensure auto fsck?"
date: 2008-11-10
forum: General Help
---

### Post by Patb on 2008-11-10
I have an external drive with partitions which I currently auto-mount by including the following (indicative) line in fstab:
```
LABEL=LaCie2 /media/LaCie2 ext3 users 0 2
```
The (minor) problem with this approach is that if I boot while the external drive is removed, I get an error and the systems drops to a root shell before I can continue. I presume the reason is that the routine fsck requested by the "2" in that line cannot assess the mount count for that partition. 

I can of course just leave the line out of fstab and manually mount the partition but I want it auto-mounted at boot time for other reasons (back up related). 

Should I set up an alternative script in /etc/init.d/ somewhere? If so, can anyone suggest a line which would mount the partition and ensure a file system check after say every 30 mounts? And where would I insert the script? 

Thanks in advance and apologies for incompetence - I have searched and googled. 

Cheers, Pat.

---

