---
title: "Internal Hard Drive Not Working"
date: 2007-10-15
forum: Hardware &amp; Laptops
---

### Post by Noodels on 2007-10-15
I've had Ubuntu for a while now, and I'm enjoying it very much (If you want to get straight to the problem, skip this paragraph.). There's been a problem I haven't bothered try and fix since day 1 though. My computer has 2 hard drives, a 30gb one, and a 70gb one (the previous owner thought hard drive space was the only limit to things you could do on a computer). The 30gb one is where Ubuntu is installed and still has well over half of the space unoccupied. But recently I decided I wanted to load lots of music onto that hard drive, the only problem being, it doesn't work.

When I mount it from computer, the first odd things is it wants a root password, I type that in and I come to a directory. It has 2 subdirectories, RECYCLER and System Volume Information. If I right click I find I cannot create a new folder nor file. If I try saving something onto the disk, it says that I am trying to save onto a read only disk. If I check the permissions, all three are set to root. I think I've tried changing them from root before by opening Nautilus from the root terminal and going there, when I tried to change them apparently it's a read only disk.

Any ideas anyone?

---

### Post by markusf21 on 2007-10-15
I am assuming this is an old windows drive formatted to ntfs
if so 
1. install ntfs-config from synaptic or terminal
2. under applications go to system tools and click ntfs config tool
3. click appropriate option and click ok

---

### Post by Noodels on 2007-10-15
It did last work on windows, but would formatting it work better? I understand that my working hard drive is something like a ext3 or something?

---

