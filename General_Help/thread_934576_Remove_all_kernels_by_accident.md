---
title: "Remove all kernels by accident"
date: 2008-09-30
forum: General Help
---

### Post by amedac on 2008-09-30
Hi to everyone. I was cleaning my ubuntu from unneeded stuff, and i was removing old linux kernels from Synaptic. Unfortunate, i done something wrong, i have remove all kernels, and now i can't boot offcourse. Can i repair this somehow without losing my programs and profiles?

---

### Post by ryanhaigh on 2008-09-30
No guarantees that this will work but it's worth a shot:

[LIST=1]
[*]Boot your computer using the ubuntu live cd
[*]Mount your root partition at say /mnt ```
sudo mount /dev/sda1 /mnt
``` *note that you will need to change sda1 to match your system
[*]Chroot to your installed system ```
sudo chroot /mnt
```
[*]Install the kernel and modules ```
sudo apt-get install linux-generic
```
[*]Reboot your system and see if it worked
[/LIST]

I am on a windows system at the moment so I can't check these commands myself but they should at least give you an idea of the procedure I am proposing.

---

### Post by ju2wheels on 2008-09-30
> **amedac said:**
> Hi to everyone. I was cleaning my ubuntu from unneeded stuff, and i was removing old linux kernels from Synaptic. Unfortunate, i done something wrong, i have remove all kernels, and now i can't boot offcourse. Can i repair this somehow without losing my programs and profiles?

That shouldnt be possible... last I recall Synaptic will not allow you to remove the kernel thats currently in use. Are you sure you used Synaptic and werent using the command line and the "rm" command?

---

