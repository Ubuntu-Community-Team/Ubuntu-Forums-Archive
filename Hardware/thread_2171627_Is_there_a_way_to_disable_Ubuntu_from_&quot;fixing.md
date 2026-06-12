---
title: "Is there a way to disable Ubuntu from &quot;fixing&quot; my video drivers?"
date: 2013-08-31
forum: Hardware
---

### Post by gardengxc2 on 2013-08-31
I have an AMD mid range graphics card and Ubuntu doesn't support it at it's best naively. However AMD has provided some really stellar Linux drivers for it. I install them everything looks great every things all peachy keen. Until Ubuntu updates again and in the process deletes the driver that work well for one that makes my graphics card shudder and makes most of my games crash.

For note I'm running 13.04 and using amd-catalyst-13.8-beta2-linux-x86.x86_64.run for my driver. 

Commands to install,
sudo chmod +x amd-catalyst-13.8-beta2-linux-x86.x86_64.run
./amd-catalyst-13.8-beta2-linux-x86.x86_64.run

---

### Post by alexandari on 2013-08-31
remove the open source drivers packages. they would otherwise conflict from what I understand. If there are no open source drivers,there would be nothing to update next time there is an update

---

### Post by Yellow Pasque on 2013-08-31
No, the open source drivers don't conflict. If you want to have Catalyst automatically update with new kernels, you need to install it using dkms: [http://wiki.cchtml.com/index.php/Ubuntu_Raring_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29_BETA.2FEXPERIMENTAL](http://wiki.cchtml.com/index.php/Ubuntu_Raring_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29_BETA.2FEXPERIMENTAL)

---

### Post by gardengxc2 on 2013-09-21
I don't want ubuntu to touch my graphics drivers at all. The nature of 13.4+ and my drivers seems to be that it'll screw everything up the first chance it gets. I just don't want to have to keep fixing them.

---

### Post by deadflowr on 2013-09-21
The above advice on installing dkms is what you need.
Unfortunately, every time a new kernel is installed, without dkms installed the driver won't be modified to work with the kernel.
Thus a new kernel will bork the driver.
The solution is install dkms, or ignore/avoid all kernel updates.

Ubuntu won't touch or update the actual driver.

---

