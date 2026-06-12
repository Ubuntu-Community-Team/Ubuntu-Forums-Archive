---
title: "[SOLVED] 8+ GB of space missing...."
date: 2008-10-19
forum: General Help
---

### Post by brandroid on 2008-10-19
Recently, I went through the process talked about [here]("http://ubuntuforums.org/showthread.php?p=177217") on backing up your Ubuntu system into a tgz file. I let it run overnight, and it seemed to work perfectly, compressing my system into a 8.5 gig .tgz file. I copied the file onto my external HD and went to delete it. It said I didn't have the permissions, so I typed "sudo nautilus" in the terminal, navigated to the folder, and deleted it...it's gone from the folder, but my freespace hasn't increased. I assumed it was just took time to update or something, so I rebooted and still no change.

I also ran the disk usage analyzer, but I couldn't find any unexplained 8.5 gigs.

And before you ask, yes I am sure how much free space I should have. The past couple of weeks I was down to about 1GB, and then I removed a 17.5 GB folder, and increased the partition size by 10GB. I should have about 28.5 GB free, Ubuntu says I only have 19.1.

If the question has already been answered elsewhere, I apologize. Just point me to it.

---

### Post by Elfy on 2008-10-19
I would check rootr's trash - it's probably in there.

[http://ubuntuforums.org/showpost.php?p=5649417&postcount=1](http://ubuntuforums.org/showpost.php?p=5649417&postcount=1)

---

### Post by Fixman on 2008-10-19
> **brandroid said:**
> Recently, I went through the process talked about [here]("http://ubuntuforums.org/showthread.php?p=177217") on backing up your Ubuntu system into a tgz file. I let it run overnight, and it seemed to work perfectly, compressing my system into a 8.5 gig .tgz file. I copied the file onto my external HD and went to delete it. It said I didn't have the permissions, so I typed "sudo nautilus" in the terminal, navigated to the folder, and deleted it...it's gone from the folder, but my freespace hasn't increased. I assumed it was just took time to update or something, so I rebooted and still no change.

I also ran the disk usage analyzer, but I couldn't find any unexplained 8.5 gigs.

And before you ask, yes I am sure how much free space I should have. The past couple of weeks I was down to about 1GB, and then I removed a 17.5 GB folder, and increased the partition size by 10GB. I should have about 28.5 GB free, Ubuntu says I only have 19.1.

If the question has already been answered elsewhere, I apologize. Just point me to it.

```
 
sudo su
cd /root/.local/share/Trash/files/
rm *

```

That will probably free the space.

---

### Post by brandroid on 2008-10-19
Thank you both. The problem did lie in the /root/.local/share/Trash folder. Ahh, it feels so good to have all my space back. Thanks again!

---

