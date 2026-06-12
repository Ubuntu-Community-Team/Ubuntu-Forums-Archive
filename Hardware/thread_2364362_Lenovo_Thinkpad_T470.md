---
title: "Lenovo Thinkpad T470"
date: 2017-06-22
forum: Hardware
---

### Post by coverup1128 on 2017-06-22
Any Thinkpad T470 users out there? 

Ubuntu certification page [https://certification.ubuntu.com/hardware/201702-25371/]("https://certification.ubuntu.com/hardware/201702-25371/") warns about slow resume from suspend:
> Certification notes

Slow Resume from Suspend

    This system does not not meet our performance criteria for resuming from suspend, but suspend/resume is functional and other functionality is not affected.
Can anybody confirm that and how serious is the problem?

---

### Post by vocx on 2017-06-22
> **coverup1128 said:**
> Any Thinkpad T470 users out there? 

Ubuntu certification page [https://certification.ubuntu.com/hardware/201702-25371/](https://certification.ubuntu.com/hardware/201702-25371/) warns about slow resume from suspend:

Can anybody confirm that and how serious is the problem?
I have a Thinkpad T450s, so it's a slightly older model. I bought it two years ago. According to the page you provided, the hardware is almost the same: Core i5-5200, GeForce 940M, Intel Broadwell U, Ethernet I218-V, Wifi Intel 7265.

I have no problem with suspend. I never shut down the laptop, I always suspend it when I am not using it. When I want to use it again it I press the power on button and it starts basically immediately. I don't know what they mean by "slow", but it does not take more than 5 seconds to show the desktop with my system.

What may be different for the T470 is the BIOS. Mine came with the legacy BIOS, while the newer one seems to be UEFI. Maybe this affects the way it works at boot time, or how it behaves with Windows, if you plan to dual boot.

Check for the presence of a solid state drive. My computer has a small internal M.2 16 GB drive. As the computer came pre-installed with Windows 7, it was using the SSD in a hybrid mode to cache the RAM, like a Windows version of a swap partition, so Windows would boot and wake from suspend extremely fast. Since I don't really use Windows, I decided to deactivate this mode of operation, and just turned the SSD drive into a regular NTFS partition, so it could be used as additional storage in Windows or Linux. No problems so far.

I've read in Linux you can also set up the SSD in a similar RAM-swap hybrid mode as it was in Windows, but this sounded too much of a hassle, and since I don't have problems with suspend or boot times, I didn't bother.

I love the T450s. It works great. The T-series of Lenovo is supposed to be for professionals, people who want good specs and no hassle. And my experience so far has been good. Before the T450s, I had a T420, running Windows 7 on it. I used it for 5 years straight, and did not have to reinstall it once. It was a workhorse, and I used it with a bunch of scientific software without issues. It would crash occasionally, but that was no problem. I would just reboot and be on my way. I support the T-series, and I feel confident buying the next model, T-510 or whatever they have, in five years.

Two issues I've experienced with the T450s and suspending are related to the Nvidia graphics and Intel Wifi drivers, so they may not be specific to Lenovo computers but to these chipsets in general.

[LIST]
[*]The strange colored borders after suspend was an annoying issue, but it resolved itself after updating the video drivers. I currently use nvidia-375 without problem. [https://askubuntu.com/questions/889166/strange-coloured-border-appearing-around-windows](https://askubuntu.com/questions/889166/strange-coloured-border-appearing-around-windows)
[*]The no-wifi after suspend problem was a bit more annoying because it seemed that the only way to make the wifi work again was to reboot the computer. Eventually my solution was simply to restart the network manager service. [https://askubuntu.com/questions/761180/wifi-doesnt-work-after-suspend-after-16-04-upgrade](https://askubuntu.com/questions/761180/wifi-doesnt-work-after-suspend-after-16-04-upgrade)
[/LIST]
```
sudo service network-manager restart
```

The second issue seems to be related to the Intel "iwlwifi" driver or to other drivers, like the Realtek "rtl8723be". But again, the problem eventually went away after updates, so it was not a big issue for me. One thread suggests adding an option SUSPEND_MODULES="iwlwifi" to the driver module configuration so it suspends and wakes up correctly, but I never had to do this. [https://askubuntu.com/questions/762198/16-04-lts-wifi-connection-issues](https://askubuntu.com/questions/762198/16-04-lts-wifi-connection-issues).

---

### Post by coverup1128 on 2017-06-23
Many thanks for the detailed reply, vocx.

My current laptop is T420/Ubuntu 14.04. Like you I never shut it down, just close the lid. Both suspend to RAM and hibernation work without problem. It's a great PC, everything works, and WiFi is very reliable under Ubuntu. Before that I had T61 and IBM T41, and was running Mandriva/KDE on them. Getting WiFi work always required some black magic, but I suspect that was a KDE problem, since Ubuntu 14.04 works very well on the same PC. 

Indeed, the T470 certified by Ubuntu has UEFI Bios, but so does X470, and the Ubuntu certification page mentions no suspend problems. T470 has NVIDIA graphics though.

---

### Post by vocx on 2017-06-23
> **coverup1128 said:**
> Many thanks for the detailed reply, vocx.

My current laptop is T420/Ubuntu 14.04. Like you I never shut it down, just close the lid. Both suspend to RAM and **hibernation work without problem**. It's a great PC, everything works, and WiFi is very reliable under Ubuntu. Before that I had T61 and IBM T41, and was running Mandriva/KDE on them. Getting WiFi work always required some black magic, but I suspect that was **a KDE problem**, since Ubuntu 14.04 works very well on the same PC. 

Indeed, the T470 certified by Ubuntu has UEFI Bios, but so does X470, and the Ubuntu certification page mentions no suspend problems. T470 has NVIDIA graphics though.
The desktop environment, KDE, Gnome, Unity, etc., is not really a problem. Wifi connectivity depends on: the kernel, the kernel module (iwlwifi), or the application that connects to the router (network-manager). Of course, maybe KDE was using a buggy network manager so using another desktop environment would use a different manager, and solve the problem that way. But really, what you should check for compatibility issues is the kernel module under use (iwlwifi, in this case).

Given the specs of the T470 (video and internet, basically), I'd say it would work just as well as my current T450s, or your T420. Better even. Much faster, and with all the benefits of having more RAM, bigger hard driver, crystal clear screen, mini DP port, etc.

Oh, hibernation. Actually, I think hibernation is disabled by default in Ubuntu. It "still doesn't work right in Linux" is what I hear. Ten years ago I always tried things to make hibernation work. I thought it was useful. Nowadays the benefits of hibernation are not so clear to me so I didn't bother looking to make it work.

---

