---
title: "Best Ubuntu version for new Z170 motherboards /w Intel video?"
date: 2015-08-28
forum: Hardware
---

### Post by maurice10 on 2015-08-28
I'm looking to get a new i7-6xxx processor with Z170 motherboard, using the integrated video. 

I'd prefer to use a 14.04 LTS version but I'm concerned about lack of support in the kernel for the new chipset USB 3.1/M.2 SSD/UEFI/Intel HD 530 graphics/Sound/etc.

Is anyone already using one of these? I don't want to have to do sophisticated patching to get things working.  Should I wait for 15.10 to come out? Or is there support in 14.04.03?

If anyone else is using a Z170, it'd be great to hear from you.

---

### Post by oldfred on 2015-08-28
The only info I have seen, so far.
 Skylake needs this boot parameter:  i915.preliminary_hw_support=1

[http://www.phoronix.com/scan.php?page=news_item&px=Intel-SKL-Prelim-Support](http://www.phoronix.com/scan.php?page=news_item&px=Intel-SKL-Prelim-Support)

Very new hardware normally takes a while before it fully works with Linux.

---

### Post by matthew113 on 2015-10-02
I have just installed Ubuntu on my new Skylake build. It took a bit of work initially because the latest 14.04.x release was on a kernel version that the NVidia 900 series really doesn't play ball with. Nomodeset saved me there though - took me a while to get into Grub mind and in the meantime I did a lot of more complex method to fix what turned out to be a relatively simple problem. I found that installing the vanilla Linux kernel 4.2.2 over 14.04.3 is serving me well so far. Before installing the new kernel version, I had no sound coming from my motherboard's line-out, which may or may not be common to the entire Z170 chipset but it is at least something to bear in mind. The obvious issue is that it may not be as stable as sticking to the supported kernel version for Ubuntu - in which case you may want to wait on 15.10 to release later this month, which should bring 14.04.4 with kernel version 4.2 (though maybe you won't hit the same audio issue?).

Linux kernel 4.3 is on RC3 (iirc) about now, so it will be out in a small while and I think is the first kernel version that is intended not to require the boot paramater @oldfred mentioned.

---

### Post by EowynCarter on 2015-10-03
Ah, not alone there.

First try with usb. Worked fine.
And at boot, black screen. Nomodeset, install nvidia drivers.

Still got no sound. I'm updating, i'll see where this go. (i'm on 15.4)
Nope, no dice. I'm clueless on what to try.

Edit : found the solution to the sound problem : 
[https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

---

### Post by gunfus2 on 2015-11-22
I just installed ubuntu 14.04.3 and nothing had worked even after adding the kernel parameters: i915.preliminary_hw_support=1. So kept on reading and trying to figure out... and eventually resolved my problem by installing the Hardware package for ubuntu. 

Here are the instructions: [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)
> 
[h=3]Trusty[/h] The  14.04.2 and newer point release will ship with an updated kernel and X  stack by default. If you have installed with older media you can use the  following to install the newer kernel from 15.04 (Vivid): 
 
[h=4]Desktop[/h]  sudo apt-get install --install-recommends linux-generic-lts-vivid xserver-xorg-core-lts-vivid xserver-xorg-lts-vivid xserver-xorg-video-all-lts-vivid xserver-xorg-input-all-lts-vivid libwayland-egl1-mesa-lts-vivid  
 
[h=4]Multiarch Desktop[/h] If  you run a multiarch desktop (for example, i386 and amd64 on amd64, for  gaming or Wine), you may find you need a slightly more involved command,  like this: 
 sudo apt-get install --install-recommends linux-generic-lts-vivid xserver-xorg-core-lts-vivid xserver-xorg-lts-vivid xserver-xorg-video-all-lts-vivid xserver-xorg-input-all-lts-vivid libwayland-egl1-mesa-lts-vivid libgl1-mesa-glx-lts-vivid libgl1-mesa-glx-lts-vivid:i386 libglapi-mesa-lts-vivid:i386  
 
[h=4]Server[/h] You can install either a kernel from 15.04 (vivid): 
 sudo apt-get install --install-recommends linux-generic-lts-vivid  
Or you can install a kernel from 15.10 (wily): 
 sudo apt-get install --install-recommends linux-generic-lts-wily 


---

