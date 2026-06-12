---
title: "Name of USB stick"
date: 2010-11-22
forum: Hardware
---

### Post by photoao on 2010-11-22
With Ubuntu Hardy, when I did connect an USB memory stick, it did mount "itself" as /media/disk

With Ubuntu Lucid, when I connect an USB stick, it mounts "itself" as /media/29FD-F6D3 , another USB stick will mount as /media/4804-B57F and so on...

My way of comparing files between HD and USB sticks relies on the fact that whatever stick I am using, it should be available as /media/disk

How can I get Lucid to behave like Hardy did, in that matter ?
Thank you

---

### Post by Fafler on 2010-11-22
You can write a udev rule to fix it and always give it a specific name. There might be a more Ubuntu like approach to it, but here you go:
[http://www.reactivated.net/udevrules.php](http://www.reactivated.net/udevrules.php)

---

### Post by photoao on 2010-11-22
Thank you very much Fafler for your answer

I had a look at the udev documentation, but it looks rather complicated. I fear I will have to define symlinks for each potential USB stick and as soon as I will use a new USB stick, the rules will not work unless being adapted each time, which would not give me back the behaviour of Hardy of course...

Why are software upgrades always braking things that were good and introduce unwanted things that are bad ?...

---

### Post by oldfred on 2010-11-22
Have you tried labeling the flash drive? 

In gparted or Disk Utility as well as command line tools you can add label and then they are mounted by the label.

I gave a label of MC4GB to my MicroCenter 4 GB flash drive.

from blkid:
/dev/sdd1: LABEL="MC4GB" UUID="E489-24AF" TYPE="vfat"

---

