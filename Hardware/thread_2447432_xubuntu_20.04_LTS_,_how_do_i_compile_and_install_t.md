---
title: "xubuntu 20.04 LTS , how do i compile and install this SSD driver?"
date: 2020-07-18
forum: Hardware
---

### Post by cdoublejj on 2020-07-18
it sucks that in 2020 i still have to compile drives for a years old SSD but, this is the SSD i have and i need to know how to install the drivers, also what kind of issues will i have? i think it patchestthe kernel? what if i install other stuff like VMwarep layer that also patches the kernel?

[https://github.com/snuf/iomemory-vsl](https://github.com/snuf/iomemory-vsl)

---

### Post by pqwoerituytrueiwoq on 2020-07-18
nothing is stopping you form using 2 or more things that make use of dkms like virtualbox and nvidia drivers
What SSD do you have? is it attached via a raid card? or is it something more obscure like a ram based pcie card

---

### Post by cdoublejj on 2020-07-18
> **pqwoerituytrueiwoq said:**
> nothing is stopping you form using 2 or more things that make use of dkms like virtualbox and nvidia drivers
What SSD do you have? is it attached via a raid card? or is it something more obscure like a ram based pcie card



actually neither, it's just an old PCEi SSD, Fusion IO 3.2TB

[https://hardforum.com/threads/3-2tb-ssd-for-240.1991865/](https://hardforum.com/threads/3-2tb-ssd-for-240.1991865/)

[https://www.youtube.com/watch?v=9W7Ifyz5uR0](https://www.youtube.com/watch?v=9W7Ifyz5uR0)

i know it's enterprise but, i don't think it's super obscure, it's said that newer kernels have drivers for it!

EDIT: don't i need some packages installed for the commands to compile and install this driver to work?

EDIT EDIT: okay i&#8217;m confused on how to use the git checkout command, evidently updates would be completely broken without DKMS, using 
git fetch --all --tags brings up nothing

---

### Post by pqwoerituytrueiwoq on 2020-07-18
if it is supported by newer kernels you could get the 5.7 kernel from the mainline, 5.7 does not break the virtualbox dkms stuff
[https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.7.2/](https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.7.2/)
if installing this is compliated there are some tools to make it easy
[https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater](https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater)
[https://www.linuxuprising.com/2018/10/2-utilities-to-install-latest-kernel-in.html](https://www.linuxuprising.com/2018/10/2-utilities-to-install-latest-kernel-in.html)

---

### Post by cdoublejj on 2020-07-24
i can't  seem to mount the drive, the mount option is greyed out. can't format  the drive BUT, it works fine when booted in to windows.

wondering if this is my issue:  [https://superuser.com/questions/278864/cant-mount-hard-drive-ubuntu](https://superuser.com/questions/278864/cant-mount-hard-drive-ubuntu)

[IMG]https://i.imgur.com/dZ6pfdT.png[/IMG]

---

### Post by cdoublejj on 2020-07-25
NAILED IT! had to manual mount it and set up in Disks to auto mount! > $ sudo mount /dev/sda1 /media/openSpaceI

Then had to boot in to windows and convert to GPT disk, THEN format, and finally sudo nano edit my fstab

---

