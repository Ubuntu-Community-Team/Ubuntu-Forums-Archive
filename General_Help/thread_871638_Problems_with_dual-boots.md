---
title: "Problems with dual-boots"
date: 2008-07-27
forum: General Help
---

### Post by Kover on 2008-07-27
People here my story,

I have installed Ubuntu 8.04 and then I have installed windows on it. The problem was that I must reinstall grub. I have used a guide with the command line thing ( gksudo, (hd0) ) you probably now what I talk about. Now I will switch over to windows by the countdown of grub I press escape. But I see only my kernels that I can boot. Not windows or something. This is my first time on Ubuntu after fighting with Slackware that is to old school for me :) . Can anybody help me I don't understand anything of it.

Thanks buddy's

---

### Post by lisati on 2008-07-27
> **Kover said:**
> People here my story,

I have installed Ubuntu 8.04 and then I have installed windows on it. The problem was that I must reinstall grub. I have used a guide with the command line thing ( gksudo, (hd0) ) you probably now what I talk about. Now I will switch over to windows by the countdown of grub I press escape. But I see only my kernels that I can boot. Not windows or something. This is my first time on Ubuntu after fighting with Slackware that is to old school for me :) . Can anybody help me I don't understand anything of it.

Thanks buddy's
If you run ```
fdisk -l
```in a terminal and post the output, maybe someone will be able to guide you through fixing this.

---

### Post by Kover on 2008-07-27
I cant give you the output now I am now on the live cd. I have another problem with my drivers (Low graphics mode problem) sorry mate I give you later the information :(

---

### Post by geirha on 2008-07-27
Doesn't starting in safe graphics work? Anyway, the fdisk command requires root privileges, so ```
sudo fdisk -l
```

---

### Post by Kover on 2008-07-27
dam very stupid of me !

Output:

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7173    57617091    7  HPFS/NTFS
/dev/sda2            7174        7186      104422+  82  Linux swap / Solaris
/dev/sda3            7187       19457    98566807+  83  Linux

```

---

### Post by geirha on 2008-07-27
```
gksudo gedit /boot/grub/menu.lst
```
Adding the following section to the end of that file should add an entry for windows.
```

title       Microsoft Windows
root        (hd0,0)
savedefault
makeactive
chainloader +1

```

---

