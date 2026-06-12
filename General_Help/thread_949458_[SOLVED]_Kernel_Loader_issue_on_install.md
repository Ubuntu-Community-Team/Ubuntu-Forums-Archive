---
title: "[SOLVED] Kernel Loader issue on install"
date: 2008-10-16
forum: General Help
---

### Post by soulrider85 on 2008-10-16
Hi,

I'm new to this forum and to Ubuntu/Linux as well. As you would have guess by the title i have an issue installing the OS. I have created several partitions on my drive, one for xp, one for data both of which are formatted NTFS. I also have one for Ubuntu 20GB formatted to etx3? i think and a 4GB partition for a Linux swap file. However when i boot of the Ubuntu 8.04 hardy heron CD (i have tried two CD's) i click on install Ubuntu or try first. It starts to run the Linux Kernel Loader and will either get stuck at 79% on one CD and 100% on the other. Both times there is HDD activity and CD drive activity, i even left it over night to allow it to finish and was still at 79% in the morning. I have searched this and can only come up with the error occurring when it is already installed and not when trying to install.

Appreciate any help you can provide

Chris

---

### Post by soulrider85 on 2008-10-16
Forgot to add it will also hang if i try disc check on either disc. I'm going to redo the partition in different sectors as a last hope, but any ideas are appreciated.

---

### Post by Rayaz on 2008-10-16
Did you download the .iso? If yes, did you do a md5sum check? What software did you use when burning the .iso?

---

### Post by soulrider85 on 2008-10-17
I managed to resolve this, with some patience the CD Check finally kicked in and found 22 files with errors. I re-downloaded the ISO this time for the 64bit and burnt the image with Nero which seems to have solved the issue.

---

