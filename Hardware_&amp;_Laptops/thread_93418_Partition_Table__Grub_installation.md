---
title: "Partition Table / Grub installation"
date: 2005-11-22
forum: Hardware &amp; Laptops
---

### Post by d03boy on 2005-11-22
I have a school issued laptop and they have customized hard drive setups. They are installed with Ubuntu and WinXP Pro. They "imaged" this to my computer so I am not sure how any of it is set up. I did reinstall windows myself because their installation was causing me problems. This overwrote the MBR as you would expect. Before this happened I had Grub working and it had a few options when it came up: WinXP, Ubuntu, Ubuntu safemode, and memtest. I am not sure how this was set up exactly... i'm no expert in stuff like this but I am somewhat computer savvy. I have a copy of my partition table found at [http://www.msoe.edu/~phillijw/partitions.htm](http://www.msoe.edu/~phillijw/partitions.htm) if you would like to see it. From memory, these are the partitions that I know I have:

[LIST]
[*]My winxp installation is NTFS
[*]I store most of my files on a different FAT32 partition
[*]There should be at least one linux partition where ubuntu is installed
[*]there is probably a swap partition
[/LIST]

I am not real sure of any other details. If you need any more information let me know. I simply want to reinstall Grub so that I can have the option of booting up winxp or ubuntu (and safemode and memtest if possible).

I do not currently have any ubuntu liveCDs or anything, but I do have PHLAK and maybe a couple others around. If it is possible to reinstall grub without downloading very much that would be good.

Thanks for any help,
d03boy

---

### Post by adwait on 2005-11-22
If you have any Linux Live CD, boot into that. Get into the terminal and run
```
sudo grub-install /dev/hda
```

ie: run the command "grub-install /dev/hda" as root.

---

### Post by d03boy on 2005-11-23
Does anyone know of a liveCD that is small that I could download and would allow me to do this? My other ones wont let me be root afaik

---

### Post by thtan on 2005-11-24
I did came across a distro called "damn small linux" dsl a while ago. But never tried it before. You could give it a try though.

---

