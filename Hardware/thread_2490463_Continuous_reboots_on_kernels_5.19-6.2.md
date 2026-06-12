---
title: "Continuous reboots on kernels 5.19-6.2"
date: 2023-09-05
forum: Hardware
---

### Post by solomax666 on 2023-09-05
Hello,

TLDR;
---------------------------------------------------

After kernel is upgraded to 5.19+ (via HWE or manually) I got constant reboots after any network activity

I can send Laptop to reboot using this simple command: `rm -rf /tmp/* ; wget --mirror -p --convert-links -P /tmp "URL of any static site"`

After 5-10 reboots Wi-Fi disappears from the system, and everything more or less stable until next reboot

Long story:
---------------------------------------------------

I have Lenovo Laptop bought in China: "Legion 5 15ARH7 Laptop (Lenovo) - Type 82RE" [https://pcsupport.lenovo.com/en/en/products/laptops-and-netbooks/legion-series/legion-5-15arh7/82re/82re0001cd/pf3rv11w/](https://pcsupport.lenovo.com/en/en/products/laptops-and-netbooks/legion-series/legion-5-15arh7/82re/82re0001cd/pf3rv11w/)

Memory was upgraded to 2x32GB (64GB total)

OS:
Ubuntu 22.04.3 LTS 

Everything is super stable with kernel 5.15.0 (currently I'm on 5.15.0-83-generic)

Additional drivers: nvidia-driver-535

What I've tried:
---------------------------------------------------

Fresh install of Ubuntu 22.10, 23.04 - continuous reboots, then no Wi-Fi (Wired network is OK)

To localize the issue I did the following:

[LIST=1]
[*] Install Ubuntu 22.04.1 - system was stable
[*] manually update everything but kernel - system was stable
[*] Update kernel (automatically got 6.2)  - continuous reboots etc.
[*] Tryed to find minimum kernel with this problem: minimum 5.19 at apt was 5.19.0-41, so I have installed it using `sudo apt install --install-recommends linux-headers-5.19.0-41-generic linux-image-5.19.0-41-generic linux-modules-extra-5.19.0-41-generic`   - got continuous reboots etc.
[/LIST]

Tried to compare 5.15 and 5.19 using `lspci -k` 
The only difference was "snd_acp_pci, snd_pci_ps, snd_sof_amd_renoir"

tried to drop those with `sudo modprobe -r` with no luck


I have no idea what else can I do :(
I would appreciate any help

---

### Post by Doug S on 2023-09-05
Try the most recent mainline kernel, just as a test. Currently [this one]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v6.5.1/"). The purpose is to determine if the issue has already been fixed upstream.

If not already fixed upstream, the only thing I know to isolate the problem is to bisect the kernel, which is tedious and takes around 20 kernel compiles. Otherwise just use a kernel that works, and eventually your issue should be fixed.

---

### Post by agentl074 on 2023-09-05
5.15 LTS is a very stable kernel -- I am partial to LTS kernels for reliability... may not have all of the bells and whistles, but they have key components backported as needed.

---

### Post by solomax666 on 2023-09-07
> **Doug S said:**
> Try the most recent mainline kernel, just as a test. Currently [this one]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v6.5.1/"). The purpose is to determine if the issue has already been fixed upstream.

If not already fixed upstream, the only thing I know to isolate the problem is to bisect the kernel, which is tedious and takes around 20 kernel compiles. Otherwise just use a kernel that works, and eventually your issue should be fixed.

Thanks for the quick answer Doug,

I've just updated to `6.2.0-32` using: `sudo apt install linux-image-generic-hwe-22.04` and reboot

Surprisingly my network and reboot problems are gone
I can use internet with no restrictions
(pure WiFi was very laggy, but this need to be tested more carefully)

BUT with this kernel I lost my second monitor :(

During upgrade I had nvidia drivers installed

so after reboot with 6.2.0 I had my internal laptop monitor completely white (external was OK)

So I have switched to noveau driver

After reboot I lost my external monitor :(
It is absent in the Settings UI

`sudo ubuntu-drivers devices` is blank :(

I'll try to switch to 6.5.1 and will report back

UPDATE: just have tested 6.5.1 (linux-image-unsigned-6.5.1-060501-generic_6.5.1-060501.202309020842_amd64.deb and friends)

Comparing to 6.2.0 I got:

- my monitors works as expected
- additional nvidia drivers are displayed (haven't try those)
- continuous reboots on wget are back :(((


Shall I start with bisect? (a bit scary, never build kernel so far ...)

Are there any up-to-date instructions? these [https://wiki.ubuntu.com/Kernel/KernelBisection](https://wiki.ubuntu.com/Kernel/KernelBisection) seems to be outdated :(
(at least `git clone git://kernel.ubuntu.com/ubuntu/ubuntu-jammy.git` can't be done :((( )

I found this repo [https://kernel.ubuntu.com/git/kernel-ppa/stable-queue-branches.git](https://kernel.ubuntu.com/git/kernel-ppa/stable-queue-branches.git) but would like to be 100% sure :)

---

### Post by solomax666 on 2023-09-07
> **agentl074 said:**
> 5.15 LTS is a very stable kernel -- I am partial to LTS kernels for reliability... may not have all of the bells and whistles, but they have key components backported as needed.

5.15. is very much stable kernel BUT I believe I need to figure out what is wrong
Or I will stack with 22.04 forever ... :))

---

### Post by Doug S on 2023-09-08
> **solomax666 said:**
> Shall I start with bisect? (a bit scary, never build kernel so far ...)

Are there any up-to-date instructions? these [https://wiki.ubuntu.com/Kernel/KernelBisection](https://wiki.ubuntu.com/Kernel/KernelBisection) seems to be outdated :(
(at least `git clone git://kernel.ubuntu.com/ubuntu/ubuntu-jammy.git` can't be done :((( )

I found this repo [https://kernel.ubuntu.com/git/kernel-ppa/stable-queue-branches.git](https://kernel.ubuntu.com/git/kernel-ppa/stable-queue-branches.git) but would like to be 100% sure :)

I can help you to bisect the kernel, if you are willing to try it. I am a server person and have no idea about nvidia drivers and if that will be an issue or not. I also only ever use the upstream mainline git kernel source tree. Here are my ["how to compile mainline kernel"]("https://askubuntu.com/questions/718381/how-to-compile-and-install-custom-mainline-kernel/718662#718662") notes. While they date back to release version 15.10, I have kept them up-to-date.

If you use LVM and/or have a small /boot partition for some reason, you will have to manage your kernels during this process to prevent filling /boot. (I don't use LVM, and often have more than 50 kernels installed as I have no limit on /boot.) I really really like [this tool]("https://code.launchpad.net/linux-purge") for selective kernel removal.

Finding your bisection starting points: To narrow down your bisection bounds, try [Ubuntu Mainline kernels]("https://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D"), but only original series kernels. What do I mean? I mean 6.5, but not 6.5.1 or 6.5.2. Any RC series kernel is original mainline. and is fine to try.

Now, what is confusing things for this case is that you mentioned 5.19 has the issue but maybe not 6.2 but again with 6.5. Bisection will not converge properly under such conditions.

---

