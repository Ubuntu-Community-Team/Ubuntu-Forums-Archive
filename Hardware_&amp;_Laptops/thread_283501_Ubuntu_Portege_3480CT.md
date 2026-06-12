---
title: "Ubuntu Portege 3480CT"
date: 2006-10-24
forum: Hardware &amp; Laptops
---

### Post by tom12519 on 2006-10-24
Okay, the Toshiba Portege 3480CT comes with a rather irritating PCMCIA CD drive.
I can get to the boot menu of what I want it to boot as - but it hardly gets any further, and normally dies around mounting the root filesystem - *before* it seems to have loaded the PCMCIA drivers - so naturally there is no filesystem to mount as the CD drive isn't "there". I have tried installing from within Windows - also to no avail. However I know that some people have managed to get it working (I would also prefer not to install over ethernet, as that will take some more trouble to get working).
Any help would be appreciated.

---

### Post by avc on 2006-10-24
Unfortunately, I've forgotten whether or not I've successfully installed Ubuntu on my Portege 3480CT with just the CD. I know I've installed it successfully using ethernet and another time doing something crazy: copying the Ubuntu CD into its own partition on the HD. That latter method was really hard, involving editing aptget stuff during the install and at least one chroot. I heard it's easier on plain Debian because you can just mount ISOs with the install environment.

Which (major) options did you select as you installed from CD? I think if you do a more customized install versus easy install, you could load the PCMCIA drivers before mounting root.

BTW, it's not that much more of a hassle to install from ethernet because you'll have to spend the same time online anyway to update the software after a CD install.

---

### Post by tom12519 on 2006-10-24
> **avc said:**
> Unfortunately, I've forgotten whether or not I've successfully installed Ubuntu on my Portege 3480CT with just the CD. I know I've installed it successfully using ethernet and another time doing something crazy: copying the Ubuntu CD into its own partition on the HD. That latter method was really hard, involving editing aptget stuff during the install and at least one chroot. I heard it's easier on plain Debian because you can just mount ISOs with the install environment.

Which (major) options did you select as you installed from CD? I think if you do a more customized install versus easy install, you could load the PCMCIA drivers before mounting root.

BTW, it's not that much more of a hassle to install from ethernet because you'll have to spend the same time online anyway to update the software after a CD install.Okay, I should be able to get network booting now - but can you tell me how to do it/give me a link to it, please?

---

### Post by avc on 2006-10-24
A quick search for PXE on [http://wiki.ubuntu.com/](http://wiki.ubuntu.com/) yields [https://help.ubuntu.com/community/Installation/Netboot?action=show&redirect=PXEInstall](https://help.ubuntu.com/community/Installation/Netboot?action=show&redirect=PXEInstall)

---

### Post by nlogax on 2007-10-05
I have always installed the server version of Ubuntu on my Portege 3480CT (and my other laptop, a 3490CT) using a Netboot install.  You need the port replicator's network interface for this to work, I believe.

Once the basic server install is done I add packages for X.org, E17 etc and I have a pretty cool little system, considering the age of the hardware.

There are instructions on setting up a multi-distro/version netboot so that you can just type the name of the distro and version you want to install.

Has anyone else installed Gutsy on their Portege 34x0CT, and did you find, like me, that it runs really slowly?  I believe it is due to changes in ACPI or the CPU frequency governor, but I've not found any fix for it yet except to disable ACPI with the 'acpi=off' kernel boot option.

---

### Post by paradon on 2007-10-13
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/138423](https://bugs.launchpad.net/ubuntu/+bug/138423) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				The first time I installed Ubuntu on my 3480CT (Breezy, I think, or possibly even Hoary), I took the HDD out, plugged it into my desktop with an adapter, and installed it there.  The last time I did a full re-install, I put a net-install initrd in the /boot partition and added it to GRUB.  (That was a while ago, and I can't remember where I got the initrd... I think from the net install iso)

> **nlogax said:**
> 
Has anyone else installed Gutsy on their Portege 34x0CT, and did you find, like me, that it runs really slowly?  I believe it is due to changes in ACPI or the CPU frequency governor, but I've not found any fix for it yet except to disable ACPI with the 'acpi=off' kernel boot option.

Yep, I have exactly the same problem.  Booting the old Feisty 2.6.20 kernel makes it run OK.  I also came across this bug: [https://bugs.launchpad.net/ubuntu/+bug/138423](https://bugs.launchpad.net/ubuntu/+bug/138423) and I'm about to try compiling a vanilla kernel as one comment suggests.

---

### Post by nlogax on 2007-10-15
> **paradon said:**
> Yep, I have exactly the same problem.  Booting the old Feisty 2.6.20 kernel makes it run OK.  I also came across this bug: [https://bugs.launchpad.net/ubuntu/+bug/138423](https://bugs.launchpad.net/ubuntu/+bug/138423) and I'm about to try compiling a vanilla kernel as one comment suggests.

Vanilla kernel worked great for me!  If you're keen to reduce your power/battery consumption you might want to config the tickless kernel option, and also the kernel timer stats option and run Intel PowerTop from [here](http://www.linuxpowertop.org/download.php).

(you'll need to install the libncursesw5-dev package to compile powertop but other than that it's very simple)

---

### Post by paradon on 2007-10-16
> **nlogax said:**
> Vanilla kernel worked great for me!  If you're keen to reduce your power/battery consumption you might want to config the tickless kernel option, and also the kernel timer stats option and run Intel PowerTop from [here](http://www.linuxpowertop.org/download.php).

(you'll need to install the libncursesw5-dev package to compile powertop but other than that it's very simple)

It worked for me, too.  (kernel.org sources, Ubuntu's 2.6.22-14 config because I couldn't be bothered looking through all of menuconfig).  I did add the vesafb driver so I have a full-screen console.

The vanilla kernel seems slightly slower than the old Feisty 2.6.20, and definitely takes longer to boot up, but it's a minor enough difference that I won't bother trying to fix it.  On the plus side, suspend-to-ram finally works again :)

Thanks for the hint about tickless - I usually run on mains, but I'll keep it in mind for my next kernel compile anyway.

---

