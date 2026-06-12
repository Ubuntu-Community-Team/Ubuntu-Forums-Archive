---
title: "Kernel Upgrade Gone Bad (Intrepid running from USB flash drive)"
date: 2008-12-18
forum: Installation &amp; Upgrades
---

### Post by chipmaker on 2008-12-18
Hi all,

I am (actually, seems more like I used to) using Ubuntu Intrepid installed as a persistent USB drive from the LiveCD. Last night, I was trying to install updates using Synaptic Package Manager. I do remember updating the kernel and removing the old kernel, and then i rebooted. 

Now I can't boot into Ubuntu from the USB drive, and I keep getting this message after the startup screen (after the bar at the bottom of Ubuntu splash screen finishes loading):

> * Starting System Tools Backends System-Tools-Backends [Ok]
* Starting Deferred Execution Scheduler ATD [Ok]
* Starting Periodic Command Scheduler Crond [Ok]
* Enabling Additional Executable Binary Formats binfmt-support
Fatal: Could not load /lib/modules/2.6.27-7-generic/modules.dep: No such file or directory
Update-binfmts: Warning: Could not load the binfmt_misc module.
* Checking battery life...

After that nothing else happens and then I have to manually power down.

Is there any way I can save this? Many thanks in advance.

---

### Post by cdtech on 2008-12-18
did you remove the kernel from the "synaptic package manager"? Can you boot from a live cd?

---

### Post by chipmaker on 2008-12-18
> **cdtech said:**
> did you remove the kernel from the "synaptic package manager"? Can you boot from a live cd?

Yes, I used synaptic in downloading the new kernel, as well as removing the existing one.

I can boot from the live cd.

---

### Post by laltopi on 2008-12-19
I have the same problem with binfmt_misc message.
My kernel is on the hard drive - not on a USB. It is on a separate boot partition.

---

### Post by chipmaker on 2008-12-19
:(

unfortunately for me, i think all of the /xxx folders are inside another directory in the usb flash drive and i can't find a way to edit them, like copying the kernels from the cd and pasting them in the usb drive.

---

### Post by Blajano on 2009-02-08
Sorry for bumping this old thread, but i'm also having the same problem :(
Any suggestions?

---

