---
title: "Advice about my Asrock mobo?"
date: 2021-08-15
forum: Hardware
---

### Post by nate5 on 2021-08-15
So this is kind of a venting session, but any advice would be appreciated.

I'm building a plex server that will also serve as our home file server, and backup server with the AWS CLI as well to backup files to AWS Glacier storage. Ubuntu server seemed like the perfect option for all this. (I'm a Unix admin by profession, but full disclaimer, my experience has been more Unix, less Linux.)

Anyway, I got my build complete, and got excited to install Ubuntu server. As soon as I pass the grub screen, it all goes black. No video. I was able to bypass the issue with "nomodeset", but obviously that's a temporary thing. And I will be managing this box via ssh 99% of the time, but I can't live without the ability to use a monitor with it. Long story short, from my googling of the issue it looks like my Asrock B560m PRO4 motherboard does not play nice with Ubuntu, specifically graphics drivers and other things,wjo knows what other things.  I haven't been able to find a solid fix for it, except for the fact that 21.04 seems to work fine. Which is not LTS obviously.

So I have a few options. 1 - Run 21.04, hope it's stable and doesn't give me grief until an LTS version comes out proven to work with my mobo. 2 - Return the mobo and rebuild. 3 - use Windows.

I'm leaning towards option 1, but curious what you all think? I really don't want to rebuild, and I really don't want to use windows for this. But it wouldn't be the end of the world. Rebuilding just means I have to wait another week or two to have fun lol.

Any thoughts? Also if anyone has any ideas on how to get an LTS version working on here I'm all ears.

---

### Post by oldfred on 2021-08-16
Which cpu?
Have you updated UEFI, even new systems often need UEFI update.
Using Intel video or do you have video card?

Generally, a Linux distribution is behind hardware. Or it takes a while before kernels & drivers are updated to support latest hardware & then depending on timing of releases a further while for a distribution to include all those new kernels & drivers.
That is why the Ubuntu LTS is now a semi-rolling release where it does update kernel. 20.04.3 will be out soon.
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)
[https://wiki.ubuntu.com/FocalFossa/ReleaseSchedule](https://wiki.ubuntu.com/FocalFossa/ReleaseSchedule)

Or you can install 21.04 and update until 22.04 LTS is released.

Some also add ppa and manually update kernel & drivers.
Squeezing More Performance Out Of Intel Tiger Lake Xe Graphics By Using Mesa Git 21.04 
[https://www.phoronix.com/scan.php?page=news_item&px=TGL-Xe-Graphics-More-Mesa-Git](https://www.phoronix.com/scan.php?page=news_item&px=TGL-Xe-Graphics-More-Mesa-Git)
Gen12 Xe Graphics might not be working out-of-the-box depending upon your kernel. 
Install OEM kernel
[https://forums.linuxmint.com/viewtopic.php?p=2002372&sid=7eab49285b06a0cda51c4ed7ace61615#p2002372](https://forums.linuxmint.com/viewtopic.php?p=2002372&sid=7eab49285b06a0cda51c4ed7ace61615#p2002372)

---

### Post by rsteinmetz70112 on 2021-08-16
That board appears to require either a separate GPU or a GPU integrated into the CPU

From the ASrock site:

> - 11th Gen Intel® Core™ Processors support Intel® Xe Graphics Architecture (Gen 12). 10th Gen Intel® Core™ Processors support Gen 9 Graphics

Which CPU do you have? 

You could always add a separate graphics card. Then take it out when you get to 22.04

Adding the 20.04 HWE stack may help, it uses more modern kernels. I don't know for sure.

There might be a ppa for an updated graphics driver 

Another solution might be to install 21.04 (or maybe 21.10) and upgrade to 22.04 LTS when it becomes available.

---

### Post by nate5 on 2021-08-16
> **oldfred said:**
> Which cpu?
Have you updated UEFI, even new systems often need UEFI update.
Using Intel video or do you have video card?

Generally, a Linux distribution is behind hardware. Or it takes a while before kernels & drivers are updated to support latest hardware & then depending on timing of releases a further while for a distribution to include all those new kernels & drivers.
That is why the Ubuntu LTS is now a semi-rolling release where it does update kernel. 20.04.3 will be out soon.
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)
[https://wiki.ubuntu.com/FocalFossa/ReleaseSchedule](https://wiki.ubuntu.com/FocalFossa/ReleaseSchedule)

Or you can install 21.04 and update until 22.04 LTS is released.

Some also add ppa and manually update kernel & drivers.
Squeezing More Performance Out Of Intel Tiger Lake Xe Graphics By Using Mesa Git 21.04 
[https://www.phoronix.com/scan.php?page=news_item&px=TGL-Xe-Graphics-More-Mesa-Git](https://www.phoronix.com/scan.php?page=news_item&px=TGL-Xe-Graphics-More-Mesa-Git)
Gen12 Xe Graphics might not be working out-of-the-box depending upon your kernel. 
Install OEM kernel
[https://forums.linuxmint.com/viewtopic.php?p=2002372&sid=7eab49285b06a0cda51c4ed7ace61615#p2002372](https://forums.linuxmint.com/viewtopic.php?p=2002372&sid=7eab49285b06a0cda51c4ed7ace61615#p2002372)
Yeah, as for now, I think I'm just going to plan on running on 21.04 and update until 22.04 LTS is released.  

[QUOTE=[COLOR=#000000]rsteinmetz70112[/COLOR]][COLOR=#000000]Which CPU do you have?[/COLOR]

[COLOR=#000000]You could always add a separate graphics card. Then take it out when you get to 22.04[/COLOR]

[COLOR=#000000]Adding the 20.04 HWE stack may help, it uses more modern kernels. I don't know for sure.[/COLOR]

[COLOR=#000000]There might be a ppa for an updated graphics driver[/COLOR]

[COLOR=#000000]Another solution might be to install 21.04 (or maybe 21.10) and upgrade to 22.04 LTS when it becomes available.[/COLOR][/QUOTE][COLOR=#000000]
I am using the Intel i5 10400, specifically because of the integrated graphics and QSV.  Really didn't want to use a separate GPU, which is why I purchased this specific CPU.  Although I suppose I could take the GPU out of my other pc just to test it out.  From my searching, everyone with this board is experiencing this issue, so it's not just me.  I think I won't be the pioneer here.  I'll probably just run on 21.04 until 22.04 LTS is released I guess.  [/COLOR]

---

### Post by rsteinmetz70112 on 2021-08-16
> **nate5 said:**
> Yeah, as for now, I think I'm just going to plan on running on 21.04 and update until 22.04 LTS is released.  

[COLOR=#000000]
I am using the Intel i5 10400, specifically because of the integrated graphics and QSV.  Really didn't want to use a separate GPU, which is why I purchased this specific CPU.  Although I suppose I could take the GPU out of my other pc just to test it out.  From my searching, everyone with this board is experiencing this issue, so it's not just me.  I think I won't be the pioneer here.  I'll probably just run on 21.04 until 22.04 LTS is released I guess.  [/COLOR]

If you do a release upgrade you will need to upgrade to 21.10 before you upgrade to 22.04 then set the relese to LTS, although you could do a reinstall if you wish.

---

### Post by nate5 on 2021-08-16
> **rsteinmetz70112 said:**
> If you do a release upgrade you will need to upgrade to 21.10 before you upgrade to 22.04 then set the relese to LTS, although you could do a reinstall if you wish.
Thanks for the heads up, I may just end up doing a reinstall at that point.  I'm working on a post install script to hopefully streamline the installs of everything on there so rebuilding will be somewhat easier.

---

