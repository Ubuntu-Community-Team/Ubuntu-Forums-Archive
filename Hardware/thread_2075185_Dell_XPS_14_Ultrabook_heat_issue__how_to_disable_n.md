---
title: "Dell XPS 14 Ultrabook heat issue / how to disable nivdia optimus"
date: 2012-10-23
forum: Hardware
---

### Post by npr77 on 2012-10-23
Hi there,

I recently bought a new Dell XPS 14 Ultrabook. I installed Ubuntu 12.10 64bit and it is working fine so far, only issue is the nvidia optimus GPU.

As far as I understand the GPU is in use all the time (without any hacks like bumblebee) - thus consuming power and making my fans go mad after a while. In fact this issue renders the machine pretty much unusable... 

I do not want to use the nvidia GPU at all, the integrated Core i GPU should be enough for me (I am a developer, not a gamer). My BIOS (up to date) doesn’t give me the option to disable the nvidia GPU. Narf.

**Is there a way to completely disable/blacklist/remove nvidia and tell Ubuntu to only use the internal Intel 4000?** :confused:

Regards
Nick

---

### Post by npr77 on 2012-10-24
Hi there, I think I solved the issue. As nobody answered I will outline my  'solution' and hope someone else might find the information useful.

I entered the following stuff into /etc/modprobe.d/blacklist.conf and did an 'sudo update-initramfs -u' after that.

```
blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv
```I expected no more loaded nvidia stuff, yet:
```
$ modprobe -l | grep nvidia
kernel/drivers/video/nvidia/nvidiafb.ko
kernel/drivers/net/ethernet/nvidia/forcedeth.ko
``` :confused:

Anyway, this tells me I am running on my Intel GPU:
```
$ lspci -k | grep -A2 -i vga
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
    Subsystem: Dell Device 054d
    Kernel driver in use: i915
```No more nvidia running as far as I can tell. :razz: Fan has been pretty quiet today as well. :cool:

---

### Post by npr77 on 2012-10-24
Or not. Fans are up and running again. WTF? I wish I knew how to investigate this problem, but my skillz are just not 1337 enough... :(

---

### Post by pablo180 on 2013-02-14
I don't know whether you have resolved your problem, but I have the same laptop and had the same issue so thought that I'd best post how I resolved it for anyone else who runs into the same problem. 

Firstly, Ubuntu 12.10 doesn't recognise the Nvidia card at all, which I thought would be fine, but like the original poster, I discovered this meant that the Nvidia card was on all the time. Battery life was 2-3 hours, it got very hot the longer it was on and when all of the fans are going at top speed it sounded like a jet engine. In Windows it is almost totally silent as the Nvidia card is only turned on when needed. 

I too was planning just to not use or somehow disable the card in Ubuntu and I tried the BIOS/UEFI, nothing there to turn off the card. So as a last resort I tried Bumblebee. Following the instructions located here: [Instructions for installing Bumblee]("http://askubuntu.com/questions/36930/how-well-do-laptops-with-nvidia-optimus-work")

It worked like a charm. Bumblebee automatically turns off the Nvidia card and Ubuntu then only uses the built in Intel by default. To use the Nvidia card you have to run a specific command, which I never do, so problem solved. Battery life now 6-8 hours and the laptop is as silent as in Windows!

---

