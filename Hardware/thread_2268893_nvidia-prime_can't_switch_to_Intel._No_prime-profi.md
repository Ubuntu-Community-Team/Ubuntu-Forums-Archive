---
title: "nvidia-prime can't switch to Intel. No prime-profiles"
date: 2015-03-12
forum: Hardware
---

### Post by mintafrican on 2015-03-12
Hello, perhaps some kind soul can help me get my nvidia-prime functioning so I can switch to Intel. On NVidia my laptop pumps out heat, the fan is always on and the battery dies faster than you can say 'nvidia'

I have a 6 month old Dell latitude 14.04 with NVS 5200M with NVIDIA Driver Version: 346.47 (I have tried all of the options in hardware drivers, 331, 340, etc)

I have purged nvidia and installed again with nvidia-prime & settings

sudo apt-get purge libvdpau-va-gl1 bumblebee* nvidia*
sudo apt-get install nvidia-331 nvidia-settings nvidia-prime

I have also tried this with nvidia-346 which I currently have installed

I don't have a prime profiles option in my nvidia-settings. I have tried blacklisting nouveu as per [https://bugs.launchpad.net/ubuntu/+source/nvidia-settings/+bug/1301490](https://bugs.launchpad.net/ubuntu/+source/nvidia-settings/+bug/1301490) to no avail.

If I try

sudo prime-select intel

I get

update-alternatives: using /usr/lib/nvidia-346-prime/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in manual mode
update-alternatives: using /usr/lib/nvidia-346-prime/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in manual mode

If I then do

sudo update-alternatives --config x86_64-linux-gnu_gl_conf

I get 4 options, but if I select any other than /usr/lib/nvidia-346-prime/ld.so.conf when running the above command it tells me my alternatives are not setup correctly

then if I run

sudo update-alternatives --config x86_64-linux-gnu_gl_conf again. I get

Info: the intel profile is already in use

but the nvidia-settings and the indicator still indicates I am using NVidia

I have logged out / restarted between each step, but it never switches to Intel

Any other ideas, apart from living with a laptop which belches out heat and has no battery life?

---

### Post by efflandt on 2015-03-14
What graphics chip(s) do you have and do you have any remnants from mixed nvidia drivers? Are you sure that you even have hybrid graphics (I am not familiar with NVS 5200M)?```
lspci | grep VGA
lspci | grep 3D
dpkg-query -l nvidia* | grep ii
```

On my laptop with hybrid Intel HD 4600/Nvidia GTX 765m graphics in 64-bit 14.04.1 with **nvidia-331-updates** package from normal repos, I simply go to **NVIDIA X Server Settings**, and in **PRIME Profiles** which was on Nvidia by default, I can chose Intel. It tells me I have to relog in for the change to take effect, I log out of X and back in, and my power LED changes from amber (Nvidia) to blue (Intel). Not sure if 14.04.2 broke anything.

---

### Post by mintafrican on 2015-03-16
Hi, the specs of my computer under settings/ details

Dell Latitude E6530
Intel® Core&#8482; i7-3740QM CPU @ 2.70GHz × 8
NVS 5200M/PCIe/SSE2

here is the output of those commands

lspci | grep VGA
01:00.0 VGA compatible controller: NVIDIA Corporation GF108GLM [NVS 5200M] (rev a1)

lspci | grep 3D
(nothing)

dpkg-query -l nvidia* | grep ii
ii  nvidia-340                                            340.76-0ubuntu1~xedgers14.04.1                         amd64        NVIDIA binary driver - version 340.76
ii  nvidia-340-uvm                                        340.76-0ubuntu1~xedgers14.04.1                         amd64        NVIDIA Unified Memory kernel module
ii  nvidia-opencl-icd-340                                 340.76-0ubuntu1~xedgers14.04.1                         amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                          0.6.2                                                  amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                                       346.47-0ubuntu1~xedgers14.04.1                         amd64        Tool for configuring the NVIDIA graphics driver




I then switch my driver to nvidia-331-updates proprietary from drivers/additional, restart the laptop and then the output of the commands are:

lspci | grep VGA
01:00.0 VGA compatible controller: NVIDIA Corporation GF108GLM [NVS 5200M] (rev a1)

lspci | grep 3D
(nothing)

dpkg-query -l nvidia* | grep ii
dpkg-query: no packages found matching nvidia
dpkg-query: no packages found matching nvidia~

I don't have a "prime-profiles" option in nvidia-settings using either driver

---

### Post by mintafrican on 2015-03-16
ah-ha, one step closer. In another thread I saw someone needing to change their bios settings on a Dell laptop, I went into bios and lo and behold Optimus was not selected - so I enabled it and rebooted.

After enabling this I can't change my drivers under additional drivers (no additional drivers found), also my HDMI external screen doesn't work at all....but I now have Prime Profiles in my nvidia-settings (joy!) 

Done some reading & it looks like HDMI is a big issue with Optimus, has anything improved with the latest drivers or is there a way to get it working (and being able to drag applications between screens?) if not, I'll stay with what works and save on office heating ;)

---

