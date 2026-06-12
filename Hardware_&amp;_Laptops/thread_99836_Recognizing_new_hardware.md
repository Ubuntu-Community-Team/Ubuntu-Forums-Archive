---
title: "Recognizing new hardware"
date: 2005-12-06
forum: Hardware &amp; Laptops
---

### Post by BrianR on 2005-12-06
I added a TV card and a 2nd hard drive and Ubuntu doesn't see them. Do I need to do something manually to get these two devices to be recognized?

---

### Post by daller on 2005-12-06
Let me see your output from:

```
lspci
```

...and to the harddrive, you should edit "/etc/fstab":

```
sudo vi /etc/fstab
```

You should be able to see your partitions with this command:

```

ls -la /dev/hd*

```

...And then compare it with your fstab!

Please just ask for further help!

---

