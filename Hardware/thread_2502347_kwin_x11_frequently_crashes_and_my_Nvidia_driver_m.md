---
title: "kwin_x11 frequently crashes and my Nvidia driver mystery"
date: 2024-11-10
forum: Hardware
---

### Post by AwaitingUserInput on 2024-11-10
I'm running Kubuntu 22.04. A few months ago after a kernel update, the machine stopped booting and complained about graphics cards. I had to use the grub menu to load an older kernel. Then I updated my Nvidia drivers and I can now boot no problem, but kwin_x11 will randomly spaz out, eat up 100% of CPU and freeze my desktop. My choices when that happens are either to reboot the whole machine, or switch to another terminal with control-alt-f5, kill kwin_x11 from there, restart it, and restart plasma shell. But once kwin crashes, it's much more likely to crash again very soon, even if I restart it.

So I think this crashing is related to the Nvidia drivers since that is when this all started.

I don't remember how I initially installed the Nvidia drivers, but I suspect that I used the "ubuntu-drivers" command.

The Nvidia website recommends a bunch of drivers, but the 3 most recent that they officially recommend are 550.127.05, 535.216.1 and 550.120.

My idea was to try and install one of their official recommendations. I'm currently running 555.42.06, which is not on Nvidia's list.

I don't know what any of the following means, but maybe someone can explain why ubuntu-drivers thinks that the 550-driver is already installed.

```

# Says I'm currently running driver 555.42.06, which agrees with the output of nvidia-smi:
$ modinfo nvidia | grep ^version
version:        555.42.06


# I'm hoping this command will remove 555.42.06 and put this version instead:
$ ubuntu-drivers install nvidia-driver-550
All the available drivers are already installed.


$ ubuntu-drivers list
nvidia-driver-545, (kernel modules provided by nvidia-dkms-545)
nvidia-driver-560-open, (kernel modules provided by nvidia-dkms-560-open)
nvidia-driver-555, (kernel modules provided by nvidia-dkms-555)
nvidia-driver-560, (kernel modules provided by nvidia-dkms-560)
nvidia-driver-550, (kernel modules provided by linux-modules-nvidia-550-generic)
nvidia-driver-555-open, (kernel modules provided by nvidia-dkms-555-open)
nvidia-driver-565-open, (kernel modules provided by nvidia-dkms-565-open)
nvidia-driver-535-server, (kernel modules provided by linux-modules-nvidia-535-server-generic)
nvidia-driver-525, (kernel modules provided by nvidia-dkms-525)
nvidia-driver-545-open, (kernel modules provided by nvidia-dkms-545-open)
nvidia-driver-535, (kernel modules provided by linux-modules-nvidia-535-generic)
nvidia-driver-565, (kernel modules provided by nvidia-dkms-565)
nvidia-driver-535-open, (kernel modules provided by linux-modules-nvidia-535-open-generic)
nvidia-driver-535-server-open, (kernel modules provided by linux-modules-nvidia-535-server-open-generic)
nvidia-driver-550-open, (kernel modules provided by linux-modules-nvidia-550-open-generic)
```

---

### Post by Yellow Pasque on 2024-11-10
```
I'm currently running 555.42.06
```
How did you install 555.42.06 - Package or .run file? Graphics Driver PPA?

---

### Post by AwaitingUserInput on 2024-11-10
I don't remember how I installed it. If I had to guess, I used ubuntu-drivers, but I could be wrong. I once tried to uninstall the drivers with Nvidia's .run script, and it told me, "You used another source to install these drivers, so you shouldn't use this script." So I doubt I got it from a .run file.

Here's the only GPU-related repositories I'm aware of:

```
$ ls -1 [FONT=monospace][COLOR=#5454FF][B]/etc/apt/sources.list.d
[/B][/COLOR][/FONT][FONT=monospace][COLOR=#000000]cuda-ubuntu2204-12-3-local.list[/COLOR]
cuda-ubuntu2204-x86_64.list
[/FONT]
```[FONT=monospace]

I don't think the CUDA repos would be giving me normal GPU drivers, but maybe they are? Is there a way to find out where my drivers came from, since I don't really remember.[/FONT]

---

### Post by Yellow Pasque on 2024-11-10
Synaptic has a filter that tells you the "origin" of your packages and what versions are available. The CUDA repo does indeed have Nvidia drivers in it: [https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2204/x86_64/](https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2204/x86_64/)


If it was me, I would remove anything from the old drivers (double check the proposed list of packages to make sure the wildcards don't end up removing non-nvidia packages with 550/555 in the name) and install nvidia from standard repo. But if CUDA repo has a greater version, it may end up coming from there.
```
sudo apt purge *550* *555*
sudo apt install nvidia-driver-550
```

---

### Post by AwaitingUserInput on 2024-11-10
This is part of why I am so confused. apt doesn't think I have any 550 drivers installed, but as you see in my first post, when I was messing around with the  [SIZE=1][FONT=courier new]$ ubuntu-drivers[/FONT][/SIZE] command it claimed I had all available drivers installed.

At any rate, I'm willing to give your suggestion a try, i.e. [SIZE=1][FONT=courier new]$ apt purge *550* *555*[/FONT][/SIZE] and then install the 550 driver, but why use apt vs. ubuntu-drivers? I am not arguing, just trying to understand how all these different ways of installing packages interact with each other.

Finally, looks to me like I won't lose anything important running your apt purge command. In fact, according to this, apt doesn't think 550 drivers are installed at all, contrary to what [FONT=courier new]ubuntu-drivers[/FONT] thinks (see the first post):

```
[FONT=monospace][COLOR=#000000]$ apt list --installed | grep -e 550 -e 555[/COLOR]

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

libnvidia-cfg1-[COLOR=#FF5454]**555**[/COLOR][COLOR=#000000]/unknown,now [/COLOR][COLOR=#FF5454]**555**[/COLOR][COLOR=#000000].42.06-0ubuntu1 amd64 [installed,automatic][/COLOR]
libnvidia-common-[COLOR=#FF5454]**555**[/COLOR][COLOR=#000000]/unknown,now [/COLOR][COLOR=#FF5454]**555**[/COLOR][COLOR=#000000].42.06-0ubuntu1 all [installed,automatic][/COLOR]
libnvidia-compute-[COLOR=#FF5454]**555**[/COLOR][COLOR=#000000]/unknown,now [/COLOR][COLOR=#FF5454]**555**[/COLOR][COLOR=#000000].42.06-0ubuntu1 amd64 [installed,automatic][/COLOR]
libnvidia-compute-[COLOR=#FF5454]**555**[/COLOR][COLOR=#000000]/unknown,now [/COLOR][COLOR=#FF5454]**555**[/COLOR][COLOR=#000000].42.06-0ubuntu1 i386 [installed,automatic][/COLOR]
libnvidia-decode-[COLOR=#FF5454]**555**[/COLOR][COLOR=#000000]/unknown,now [/COLOR][COLOR=#FF5454]**555**[/COLOR][COLOR=#000000].42.06-0ubuntu1 amd64 [installed,automatic][/COLOR]
libnvidia-decode-[COLOR=#FF5454]**555**[/COLOR][COLOR=#000000]/unknown,now [/COLOR][COLOR=#FF5454]**555**[/COLOR][COLOR=#000000].42.06-0ubuntu1 i386 [installed,automatic][/COLOR]
libnvidia-encode-[COLOR=#FF5454]**555**[/COLOR][COLOR=#000000]/unknown,now [/COLOR][COLOR=#FF5454]**555**[/COLOR][COLOR=#000000].42.06-0ubuntu1 amd64 [installed,automatic][/COLOR]
libnvidia-encode-[COLOR=#FF5454]**555**[/COLOR][COLOR=#000000]/unknown,now [/COLOR][COLOR=#FF5454]**555**[/COLOR][COLOR=#000000].42.06-0ubuntu1 i386 [installed,automatic][/COLOR]
libnvidia-extra-[COLOR=#FF5454]**555**[/COLOR][COLOR=#000000]/unknown,now [/COLOR][COLOR=#FF5454]**555**[/COLOR][COLOR=#000000].42.06-0ubuntu1 amd64 [installed,automatic][/COLOR]
libnvidia-fbc1-[COLOR=#FF5454]**555**[/COLOR][COLOR=#000000]/unknown,now [/COLOR][COLOR=#FF5454]**555**[/COLOR][COLOR=#000000].42.06-0ubuntu1 amd64 [installed,automatic][/COLOR]
libnvidia-fbc1-[COLOR=#FF5454]**555**[/COLOR][COLOR=#000000]/unknown,now [/COLOR][COLOR=#FF5454]**555**[/COLOR][COLOR=#000000].42.06-0ubuntu1 i386 [installed,automatic][/COLOR]
libnvidia-gl-[COLOR=#FF5454]**555**[/COLOR][COLOR=#000000]/unknown,now [/COLOR][COLOR=#FF5454]**555**[/COLOR][COLOR=#000000].42.06-0ubuntu1 amd64 [installed,automatic][/COLOR]
libnvidia-gl-[COLOR=#FF5454]**555**[/COLOR][COLOR=#000000]/unknown,now [/COLOR][COLOR=#FF5454]**555**[/COLOR][COLOR=#000000].42.06-0ubuntu1 i386 [installed,automatic][/COLOR]
nvidia-compute-utils-[COLOR=#FF5454]**555**[/COLOR][COLOR=#000000]/unknown,now [/COLOR][COLOR=#FF5454]**555**[/COLOR][COLOR=#000000].42.06-0ubuntu1 amd64 [installed,automatic][/COLOR]
nvidia-dkms-[COLOR=#FF5454]**555**[/COLOR][COLOR=#000000]/unknown,now [/COLOR][COLOR=#FF5454]**555**[/COLOR][COLOR=#000000].42.06-0ubuntu1 amd64 [installed][/COLOR]
nvidia-driver-[COLOR=#FF5454]**555**[/COLOR][COLOR=#000000]/unknown,now [/COLOR][COLOR=#FF5454]**555**[/COLOR][COLOR=#000000].42.06-0ubuntu1 amd64 [installed][/COLOR]
nvidia-firmware-[COLOR=#FF5454]**555**[/COLOR][COLOR=#000000]-[/COLOR][COLOR=#FF5454]**555**[/COLOR][COLOR=#000000].42.06/unknown,now [/COLOR][COLOR=#FF5454]**555**[/COLOR][COLOR=#000000].42.06-0ubuntu1 amd64 [installed,automatic][/COLOR]
nvidia-kernel-common-[COLOR=#FF5454]**555**[/COLOR][COLOR=#000000]/unknown,now [/COLOR][COLOR=#FF5454]**555**[/COLOR][COLOR=#000000].42.06-0ubuntu1 amd64 [installed,automatic][/COLOR]
nvidia-kernel-source-[COLOR=#FF5454]**555**[/COLOR][COLOR=#000000]/unknown,now [/COLOR][COLOR=#FF5454]**555**[/COLOR][COLOR=#000000].42.06-0ubuntu1 amd64 [installed,automatic][/COLOR]
nvidia-utils-[COLOR=#FF5454]**555**[/COLOR][COLOR=#000000]/unknown,now [/COLOR][COLOR=#FF5454]**555**[/COLOR][COLOR=#000000].42.06-0ubuntu1 amd64 [installed,automatic][/COLOR]
xserver-xorg-video-nvidia-[COLOR=#FF5454]**555**[/COLOR][COLOR=#000000]/unknown,now [/COLOR][COLOR=#FF5454]**555**[/COLOR][COLOR=#000000].42.06-0ubuntu1 amd64 [installed,automatic][/COLOR]
[/FONT]
```

Thank you for your time.

---

### Post by AwaitingUserInput on 2024-11-11
Update: I did apt purge the nvidia drivers, then installed the 550 version that I wanted via $ sudo apt install nvidia-driver-550

For some reason using $ sudo ubuntu-drivers did not work, but apt worked OK.

Based on the terminal output, it looks like it did indeed pull the drivers from Nvidia's repository, but I don't care as long as this solves the kwin_x11 crashing problem. It will take some more time before I'm confident that is fixed but fingers crossed for now!

---

### Post by Yellow Pasque on 2024-11-11
I'm not a fan of ubuntu-drivers and never used it, even when I ran Ubuntu. It never seemed that "smart" to me, and I've seen it get "confused" by external repos like the one you have. So I can't tell you exactly what's going on there.
But fingers crossed for you as well.

---

