---
title: "fsck died with exit status 8"
date: 2009-02-08
forum: Installation &amp; Upgrades
---

### Post by Jeztastic on 2009-02-08
Hi,

I recently upgraded my sister and brother in law's PC to 8.10. All well and good, but I was just about to take it back to her, and turned it on to check a couple of things. I got the above error message.

I have hunted around, and I clearly need to change the UUID in fstab.

```
sudo vol_id -u sdb1
```

However, the system will not recognise the drive to give me the correct UUID.

```

/dev/sdb1: error opening volume
```

Please help! My brother in law has developed a facebook addiction and is hassling me to get it back!

The root partition is fine, it is /home on a seperate hard drive that is the problem. I updated root but did not touch the home partition.

---

### Post by yeats on 2009-02-08
Could you try booting into a live CD?  Perhaps that will grab the right UUID and you can add it to your permanent installation's /etc/fstab while running the CD.  Just a thought . . .

---

### Post by Jeztastic on 2009-02-08
Nice idea, will give it a try... 

edit: grr! Got to spend hours waiting for download now!

---

### Post by Jeztastic on 2009-02-14
I just tried the live CD, and the second HDD was not even recognised. Does this mean it's died? How do I know for sure?

---

