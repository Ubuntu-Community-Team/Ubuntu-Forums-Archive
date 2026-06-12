---
title: "remove kernels"
date: 2009-10-27
forum: Installation &amp; Upgrades
---

### Post by Ubu-freak on 2009-10-27
When my system boots, in the grub menu there are a plethora of kernels to choose from. I was wondering if it was safe to remove these from my system. If so how would you do that in terminal? And is it the same as going to synaptic package manager and "completely removing" the kernels?

---

### Post by gareththegeek on 2009-10-27
[http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/]("http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/")

---

### Post by jheaton5 on 2009-10-27
I just comment out the menu options I don't want in the /boot/grub/menu.lst file.  They don't appear in the menu, but are available if I need them and I don't run the risk of damaging the system by trying to remove them.

---

### Post by drs305 on 2009-10-27
For grub legacy I use StartUp-Manager to change how many kernels to display. These settings change how many you see, but don't physically remove them from your system. SUM has a lot of other tweaks that work well with Grub (1).

I wrote a guide about using StartUp-Manager, and there is also a section on how to remove older kernels.

See the "SUM" link in my signature line.

In a terminal, a sample command would be (tailor to the kernels you want to remove):
```

sudo apt-get remove linux-image-2.6.31-13-generic  linux-headers-2.6.31-13-generic

```
*Please mark the thread solved via the Thread Tools link near the upper right of the original post when you no longer need assistance.*

---

### Post by Lars Noodén on 2009-10-27
If the system recognizes them as redundant, autoremove should get rid of them.

```

sudo apt-get autoremove

```

The reason you get multiple kernels is that when you install a new kernel via an update, you keep the old one until you are sure that you *can* boot with the new one.  If you got rid of the old one and then rebooted only to discover the new kernel doesn't work, life gets more difficult than rebooting and choosing the next oldest kernel in grub.

---

### Post by brouhaha on 2009-10-27
My problem is similar to Ubu-freak's. I upgraded *some* of Linux packages, so I have both, 2.6.24-24 and (half-baked) 2.6.24-25. When I first booted with 2.6.24-25, I was prompted to set up virtualbox again. Perhaps, because I didn't get *all* 2.6.24-25 packages virtualbox didn't work even after recompiling, wifi died too. I booted from 2.6.24-24, and things went back to normal after recompilation of virtualbox.

If I upgrade my kernel will I need to do piece by piece recompilation of all kernel modules? What about all my device drivers? I don't know what all I've got. My drivers came factory-installed with my Dell Studio 15, 8.04LTS.

If answers to the above are "yes", then I don't care for newer kernel. Please advice me how to remove whatever I've got of 2.6.24-25 through Synaptic? If e.g. I "Mark for removal" linux-libc-dev (and other packages), will it revert to older version or will it screw my system?

Thanks for your patience.

---

### Post by Kevbert on 2009-10-27
Through Synaptic search for linux-image-2.6.xx.xx and mark for complete removal (where xx.xx) is the version you want to remove. This will also remove the offending grub menu item. By just commenting out the item in menu.lst will not help as after a while (with updates) the boot sector will become full and you'll have trouble when trying to install new kernels.

---

### Post by phillw on 2009-10-27
Hi,

we had a chat on this a cple of days ago ...

[http://ubuntuforums.org/showthread.php?t=1298247&highlight=phillw](http://ubuntuforums.org/showthread.php?t=1298247&highlight=phillw)

regards,

Phill.

---

### Post by slakkie on 2009-10-27
> **Lars Noodén said:**
> If the system recognizes them as redundant, autoremove should get rid of them.

```

sudo apt-get autoremove

```

The reason you get multiple kernels is that when you install a new kernel via an update, you keep the old one until you are sure that you *can* boot with the new one.  If you got rid of the old one and then rebooted only to discover the new kernel doesn't work, life gets more difficult than rebooting and choosing the next oldest kernel in grub.


Kernels are not autoremoved:

```

cat /etc/apt/apt.conf.d/01autoremove
APT
{
  NeverAutoRemove
  {
        "^linux-firmware$";
        "^linux-image.*";
        "^linux-restricted-modules.*";
        "^linux-ubuntu-modules-.*";
  };

  Never-MarkAuto-Sections
  {
        "metapackages";
        "restricted/metapackages";
        "universe/metapackages";
        "multiverse/metapackages";
  };
};

```

---

### Post by Lars Noodén on 2009-10-27
> **slakkie said:**
> Kernels are not autoremoved:


I stand corrected on Ubuntu.  ;)

---

### Post by Ubu-freak on 2009-10-27
thanks you guys... so in conclusion i used 
```

sudo apt-get remove --purge 2.6.2x-xx-*

```

---

### Post by sgosnell on 2009-10-27
I prefer to do it via Synaptic, so that I can see exactly what I'm removing and what is still there.  It's just a matter of personal preference, though.  If you want newer kernels, you can get them [here](http://kernel.ubuntu.com/~kernel-ppa/mainline/).

---

### Post by drs305 on 2009-10-28
> **Ubu-freak said:**
> thanks you guys... so in conclusion i used 
```

sudo apt-get remove --purge 2.6.2x-xx-*

```

Just a note for others that might use the command line for removing kernels. It is not common for kernels to change from a 2.6.X to 2.6.Y in the same release. In the example above the user (hopefully) had 2.6.3-xx kernels, so getting rid of all 2.6.2-xx would be okay.

Running the "apt-get remove" command with the "-s" switch would display which kernels were about to be removed so the user could check before actually completing the command. You can check which kernel in use with "uname -r".

---

