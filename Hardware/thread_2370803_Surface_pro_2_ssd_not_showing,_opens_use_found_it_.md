---
title: "Surface pro 2 ssd not showing, opens use found it but I still cannot actually use"
date: 2017-09-07
forum: Hardware
---

### Post by asdfwright on 2017-09-07
Hiya there, I have a surface pro 2 with a 128gb ssd, I have tried using diskpart with windows 10 installer, I've tried using gparted to find the ssd but the two only show the USB drive, and I tried opensuse and I got to the legacy like interface and got opensuse to list all the drives on the surface, it showed the USB drive and the ssd, but it didn't show the size, and it was a litonit model so I can assure it was a ssd. I still can't do anything with it I can't even partition it with opensuse expert partitioner, any clues on what I should do to try and fix this? I plan on dual booting unbuntu and w10, but ubuntu is priority

---

### Post by Autodave on 2017-09-07
I am not an expert here and I expect some one else to jump in, but with the little I do know......

Did you disable *fast boot*? You will need to do that first. Then you will need to use Win10 tools to shrink the main Win partition to free up the space you want to use for Ubuntu.

---

### Post by oldfred on 2017-09-07
Does UEFI/BIOS show drive and show it correctly?

If UEFI does not show drive, then no operating system will see it.

And if shown then using Disks and upper right corner icon is Smart Status. It can run lots of testss, but all I know is if it says drive is good or bad.

---

