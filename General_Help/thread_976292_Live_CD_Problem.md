---
title: "Live CD Problem"
date: 2008-11-09
forum: General Help
---

### Post by Nirva on 2008-11-09
Hay,

Until yesterday I had a very smooth running Ubuntu installation.
But yesterday I decided to give iDeneb a try.  It worked, so now I have a working osx installation on my laptop, but I can't boot into Ubuntu anymore because the Darwin bootloader starts up when I boot.

So I decided to boot from a live CD.  I intended to do the good old trick
```

sudo grub

root (hd0,0)
setup (hd0)

```

But when I run setup hd0, he tells me, he can't find /boot/grub/stage1.

I think the problem has something to do with this :
When I run fdisk -l
There is no output at all ( unless when I atach a USB stick to my computer, then it is recognizd )
Edit : with sudo fdisk -l /dev/sda I have the right output.
But the boot problem isnt solved yet

Does anyone has a solution ?
Thanks

---

### Post by mdurham on 2008-11-09
using "root (hd0,0)" is saying that /boot/grub/stage1 is on partition 1 (the first partition) is this correct?

You can try (in grub) "find /boot/grub/stage1"
this will show you where it is.

---

### Post by Nirva on 2008-11-09
Yes, this is correct.
This is where my /boot directory is

---

### Post by mdurham on 2008-11-09
what does > sudo fdisk -l produce?


what does (in grub)> find /boot/grub/stage1 produce?

---

