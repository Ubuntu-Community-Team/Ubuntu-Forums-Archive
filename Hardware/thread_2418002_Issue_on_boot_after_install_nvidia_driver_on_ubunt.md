---
title: "Issue on boot after install nvidia driver on ubuntu 19.04"
date: 2019-04-30
forum: Hardware
---

### Post by hishin on 2019-04-30
Hello dear friends, I hope you guys are ok.

I am trying to install ubuntu 19.04 on my laptop Dell Inspiron 3442 but I am facing issue after I install the nvidia driver.

I've tried install using the "sudo ubuntu-drivers autoinstall". But didn't work.

Then I've tried the tutorial below:

[https://itsfoss.com/fix-ubuntu-freezing/](https://itsfoss.com/fix-ubuntu-freezing/)

The Secure Boot is deactivated, but active or not, the issue persist.
I also tried let the BIOS configuration as "Legacy" instead of UEFI, but didn't work.



525/5000
Description: 3D controller
        product: GF117M [GeForce 610M / 710M / 810M / 820M / GT 620M / 625M / 630M / 720M]
        manufacturer: NVIDIA Corporation
        Physical ID: 0
        bus info: pci @ 0000: 08: 00.0
        version: a1
        width: 64-bit
        clock: 33MHz
        Capabilities: bus_master cap_list rom
        configuration: driver = nouveau latency = 0
        features: irq: 53 memory: f6000000-f6ffffff memory: e0000000-efffffff memory: f0000000-f1ffffff I / O port: d000 (size = 128) memory: f7000000-f707ffff

I hope that you guys can help me out.

Thanks in advance.

Have a good day.

---

### Post by Autodave on 2019-04-30
Kinda confused here.  Do you actually get 19.04 installed completely?  Exactly *what* problem do you have after installing the Nvidia driver?

---

### Post by oldfred on 2019-04-30
With 19.04 when you check install proprietary drivers it now also installs nVidia driver.
So is it already installed?

Can you boot recovery mode from grub menu?
#What is installed
dpkg -l | grep -i nvidia
dkms status
lsmod | grep nvidia
nvidia-smi

Probably better to use UEFI, not legacy/CSM/BIOS mode.
Similar model?
Dell  Inspiron 3670 UEFI update & AHCI worked
[https://ubuntuforums.org/showthread.php?t=2412152](https://ubuntuforums.org/showthread.php?t=2412152)

---

### Post by hishin on 2019-05-02
Hello.
Sorry about my delay.

Yes, I have it completed.

I can't emulate it in this moment, because I don't know how to fix and I'll need to format it.

The issue happens when it is starting the OS. 
The Ubuntu logo is loading;
Then the screen shows the services with an OK and then freezes before the login screen.

I have to press and hold the power button to turn it off and I haven't found a wait to start the computer.

Thanks!

---

### Post by hishin on 2019-05-02
Hello!

In the first time that I installed, the ubuntu had the issue that I described.
I didn't know if I did something wrong and I formated again and tried to install ubuntu and the same issue happened.

Then, I formated it without connect in the internet and worked.

I've updated the OS and restarted to see if something in the update was freezing it and also worked fine.

When I've tried to install nvidia proprietary driver, then ubuntu freezed at the start.

~$ dpkg -l | grep -i nvidia
ii  libcuda1-340                               340.107-0ubuntu3                     amd64        NVIDIA CUDA runtime library
rc  nvidia-340                                 340.107-0ubuntu3                     amd64        NVIDIA binary driver - version 340.107
ii  nvidia-opencl-icd-340                      340.107-0ubuntu3                     amd64        NVIDIA OpenCL ICD
ii  nvidia-settings                            418.56-0ubuntu1                      amd64        Tool for configuring the NVIDIA graphics driver

-----
dkms status
virtualbox, 6.0.6, 5.0.0-13-generic, x86_64: installed

-----
$ lsmod | grep nvidia
(nothing happened)

-----
$ nvidia-smi


Command 'nvidia-smi' not found, but can be installed with:


sudo apt install nvidia-340        # version 340.107-0ubuntu3, or
sudo apt install nvidia-utils-390  # version 390.116-0ubuntu1
sudo apt install nvidia-utils-418  # version 418.56-0ubuntu1


(I am afraid to install it, because I don't have other computer to use)

I am using UEFI right now.

It is a different model from the link that you suggested.

Thanks a lot!

---

### Post by oldfred on 2019-05-02
Dell issues are common across many models.
Bigger differences between AMD & Intel based systems.

Your dkms is not showing nVidia installed. How are you installing it?
Not sure if using virtual install makes a difference or not.

Do not force shutdown with power switch unless nothing else works. That often corrupts file system and you have to run fsck before you can start fixing whatever issue started the problem.

Generally pressing and holding Ctrl+Alt and
then PrintScr, R, E, I, S, U, B (Raising Elephants Is So Utterly Boring)
should do a clean reboot.
R gives back control of the keyboard, S issues a sync, E sends all processes but init the term signal, I sends all processes but init the kill signal, U mounts all filesystem ro to prevent a fsck at reboot, B reboots the system

---

