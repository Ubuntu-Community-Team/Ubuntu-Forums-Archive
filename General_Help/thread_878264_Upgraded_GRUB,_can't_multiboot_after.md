---
title: "Upgraded GRUB, can't multiboot after"
date: 2008-08-02
forum: General Help
---

### Post by kulturloseramerikaner on 2008-08-02
I've been trying to get my system to multiboot Win, 'Buntu, and PCBSD for the past week.  I've been dual-booting 'Buntu and Windoze for year and a half now and decided I'd like to play with BSD too.  Finally just got PCBSD to install to a third drive but could not for the life of me get grub to load it; nothing I tried worked, always "error 17."  I found GRUB 2 in the repos and discovered that it had much better ufs (the native BSD filesystem) support so I installed it using Synaptic.  Now my GRUB menu's messed up and I can't boot BSD or Windoze.  Can someone that knows a little about GRUB 2 help me get multibooting again please?

Thanks in advance.

p.s. If worst comes to worst, how would I go about reverting back, or am I hosed now?

---

### Post by Diabolis on 2008-08-02
Error 17
[http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17)

If you want to give another try to grub, steps to reinstall grub:
```

sudo grub
find /boot/grub/stage1    It will find all the places **from where** you can install grub.
root (hd?,?)              Select **from where** you want to install grub
setup (hd?)               Select the drive **in which** you want to reinstall grub
reboot
```

So the output of the **find** command is the input of **root**.

---

### Post by kulturloseramerikaner on 2008-08-08
So then I'd reinstall GRUB from my linux drive to the windoze drive, is that correct?

---

### Post by caljohnsmith on 2008-08-08
Kulturloseramerikaner, you weren't exactly clear in your original post--do you have three drives, one with Windows, one with Ubuntu, and one with PCBSD? Please post the output of:
```
sudo fdisk -l
```

---

