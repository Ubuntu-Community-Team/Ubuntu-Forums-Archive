---
title: "Twin Ubuntus! (Can I kill one of them?)"
date: 2008-10-22
forum: General Help
---

### Post by academiphiliac on 2008-10-22
I installed with Wubi once. Then I uninstalled with Wubi and installed again. Now I have two ubuntus, or so it seems.

According to GRUB, I have two ubuntu kernels available to me. It goes down like this:

```

Ubuntu 8.04.1 kernel 2.6.24-21-generic
Ubuntu 8.04.1 kernel 2.6.24-21-generic (recovery mode)
Ubuntu 8.04.1 kernel 2.6.24-19-generic
Ubuntu 8.04.1 kernel 2.6.24-19-generic (recovery mode)
...and a few other things...

```

Does anyone know how I might drown one of them, saving the other?

---

### Post by Rayaz on 2008-10-22
Those are the available kernel versions. If you look closely the numbers are different. The recovery option lets you manage your system if anything goes wrong.

If you don't want them showing up, install Startup Manager.Once installed you can change how many kernel versions you want shown at startup.

---

### Post by academiphiliac on 2008-10-22
Can I be sure that one kernel always boots by default? It's a little hard to tell, but I think it varies occasionally.

---

### Post by Rayaz on 2008-10-22
It would only vary if you changed the kernel version yourself. Of course it would also vary if you downloaded a kernel update. You have the latest kernel installed: 2.6.24-21-generic. When you do a fresh Hardy install you start out with a 2.6.24-16-generic. As you get fresh updates the numbers change. It will always be the topmost kernel that will get loaded.

Have you given Startup Manager a try? Use Synaptic Manager and search for startupmanager. Install that and then run it. From the Advanced Tab, you can select "Limit the number of kernels in the boot menu" option to get rid of the extra kernel options.

---

### Post by rune0077 on 2008-10-22
If you only use the one kernel, you can also safely use synaptic to uninstall the other, since it's just taking up space and not really being used (just be sure to uninstall the old kernel and keep the latest :)) Uninstalling with synaptic will also remove it from GRUB.

---

### Post by mickeelm on 2008-10-22
Wow, I'm lucky. This was exactly what I was going to ask. :) I think I've got the answers I needed thanks to the posts in this thread. Just one thing more, does a Kernel take up a lot of space or is it actually a good idea to keep it if one day one of them starts and the other one doesn't?

---

### Post by sethvath on 2008-10-22
Search for linux-headers*, they are about 150mb in total. Keep the latest and n-1 if you are deprived of space. The last known working kernel will help should you experience a kernel upgrade that does not play nice.

---

### Post by gpsblake on 2008-10-22
I am for one grateful for the "twin ubuntus" because when I try to load the 2.6.24-21-generic kernal, it locks up on the splash screen about 1/4th through the progress bar. It loads fine with the 2.6.24-19 kernal. I used wubi to install and don't know why this is happening. Not a big deal though.

---

