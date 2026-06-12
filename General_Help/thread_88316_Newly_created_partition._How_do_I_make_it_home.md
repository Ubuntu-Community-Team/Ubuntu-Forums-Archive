---
title: "Newly created partition. How do I make it /home?"
date: 2005-11-10
forum: General Help
---

### Post by poopdog on 2005-11-10
So... I had a little problem when trying to adjust the partition size on my disk.

Long story short, my 60gig NTFS partition is now a 60gig ext3 (/dev/hda1)

How do I go about making this my /home directory?

Is it possible to do post-install?

[IMG]http://x11.putfile.com/11/31223033860.jpg[/IMG]

---

### Post by Remmelas on 2005-11-10
[QUOTE=poopdog]So... I had a little problem when trying to adjust the partition size on my disk.

Long story short, my 60gig NTFS partition is now a 60gig ext3 (/dev/hda1)

How do I go about making this my /home directory?

Is it possible to do post-install?[/QUOTE]
well, here's what i would do
```

sudo -s
mkdir /mnt/hda1
mount /dev/hda1 /mnt/hda1
cp -ax /home/* /mnt/hda1
umount /mnt/hda1

```
That will get your current home directory duplicated on your new partition
then, add the following line to your /etc/fstab
```
/dev/hda1       /home        ext3    defaults        0       0
```

then, to be clean, you can either reboot(that's the easy way), or,
ctrl+alt+f1 to get to a console window
```

sudo /etc/init.d/gdm stop
sudo mount -a
sudo /etc/init.d/gdm start

```
that'll get you up and running with the new home partition.

---

### Post by poopdog on 2005-11-10
This worked perfect!

Thanks so much for the help.

I'm now 100% Ubuntu on my home computer.  :D

---

