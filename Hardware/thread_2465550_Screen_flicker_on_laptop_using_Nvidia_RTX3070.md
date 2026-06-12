---
title: "Screen flicker on laptop using Nvidia RTX3070"
date: 2021-08-04
forum: Hardware
---

### Post by temporos on 2021-08-04
I just bought a new ASUS TUF laptop that has an NVIDIA RTX3070 GPU in it. I have it dual booting Windows 10 Home and Ubuntu 20.04 LTS (I prefer the LTS releases due to longer support, so I don't have to upgrade as often). On Windows, the graphics are working perfectly. But on Ubuntu, when doing something that shows animation or moving images (e.g., playing games, watching videos, web animations, etc.), I get a frequent flicker of the screen. It lasts only a few milliseconds, but it's very disruptive. The whole screen flickers, not just the moving part. And when it flickers, it looks like just random noise, not a distortion of what's on the screen. Has anyone else experienced this behaviour?

Could this be an Ubuntu driver issue? I ran a
```
sudo apt update
sudo apt upgrade
```
shortly after installing 20.04 LTS, and all my software is up-to-date.

---

### Post by temporos on 2021-08-06
NVIDIA has a driver download available [on their website]("https://www.nvidia.com/Download/driverResults.aspx/177145/en-us"), but it says, "...many Linux distributions provide their own packages of the NVIDIA Linux Graphics Driver in the distribution's native package management format. This may interact better with the rest of your distribution's framework, and you may want to use this rather than NVIDIA's official package." Their driver has a date of July 19th, 2021 on it. Should I try installing the driver from NVIDIA's web site? If so, how would I go about removing the current one after installing the new one?

---

### Post by Autodave on 2021-08-06
Do NOT try and install the one from the website or you will just be asking for problems down the road.

Have you gone to Additional Drivers to see if you are actually even using an nVidia driver?  

Doing a quick web search, I see that there are quite a few models of "TUF" machines.  Exactly what model do you have?

---

### Post by temporos on 2021-08-06
I have the TUF Dash 15. I just went to "Additional Drivers," and noticed it says, "This device is using a manually-installed driver." (Screenshot below.) I'm not sure why it says that, because I haven't installed any drivers myself. All the drivers I have right now were installed by the Ubuntu 20.04 installer. Should I be using something different? I notice a bunch of other greyed-out options there (presumably greyed-out because they're absent).

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=288938&stc=1[/IMG]

---

### Post by temporos on 2021-08-12
Here's a quick YouTube video of the issue I'm talking about. I still can't find any mention of something like this on the intarwebz. Does anyone have an idea of what might help?

[https://youtu.be/Tos0Bo06-5o](https://youtu.be/Tos0Bo06-5o)

---

### Post by Autodave on 2021-08-13
Are you absolutely sure that you didn't install a driver??  It sure looks like you did.

---

### Post by temporos on 2021-08-13
> **Autodave said:**
> Are you absolutely sure that you didn't install a driver??  It sure looks like you did.

I'm absolutely sure I didn't install a special driver. I installed Ubuntu 20.04 LTS from [the ISO provided on ubuntu.com]("https://ubuntu.com/download/desktop"); the computer was brand-new, fresh out of the box. Whatever driver is installed is the one installed by that ISO.

Should I have a different one?

---

### Post by Autodave on 2021-08-13
You need to remove whatever driver is already installed and then choose the newest recommended one.

---

### Post by temporos on 2021-08-13
> **Autodave said:**
> You need to remove whatever driver is already installed and then choose the newest recommended one.

Plan of action! I like it. :) I asked my system which video drivers were installed, and it looks like two of them (?). Apparently, this laptop has an integrated Intel GPU as well as the dedicated NVIDIA GPU.
```
user@host:~$ lspci -k | grep -EA3 'VGA|3D|Display'
0000:00:02.0 VGA compatible controller: Intel Corporation Device 9a49 (rev 01)
    DeviceName: VGA
    Subsystem: ASUSTeK Computer Inc. Device 160c
    Kernel driver in use: i915
    Kernel modules: i915
--
0000:01:00.0 VGA compatible controller: NVIDIA Corporation Device 249d (rev a1)
    DeviceName: Second VGA
    Subsystem: ASUSTeK Computer Inc. Device 160c
    Kernel driver in use: nvidia
    Kernel modules: nvidiafb, nouveau, nvidia_drm, nvidia
```
I'm lost at this step. How would I make sure the correct drivers are installed? Also, how do I know I'm using the dedicated NVIDIA card and not the integrated Intel card?

---

### Post by Autodave on 2021-08-15
Sorry, but you need someone else's help right now.  Someone way higher on the payscale than I am. :-)  Sometimes you can disable the onboard one in the BIOS.  You may want to look there first.

---

### Post by temporos on 2021-08-16
Well, I just loaded the BIOS settings, and it shows both the integrated and discrete GPUs, but there's no way to change the order or to disable one. Anyone else have some ideas? I'm just grasping at straws here. It'd be a real bummer if I got one of the best GPUs only to find out I can't play games or watch videos in Linux with it.

---

### Post by Autodave on 2021-08-16
[https://ubuntuforums.org/showthread.php?t=2454399&page=2](https://ubuntuforums.org/showthread.php?t=2454399&page=2)   You may want to check that thread out and see if it applies to you.  (And I inadvertently linked to page 2 of the thread: you can back up to page one and start there.)

---

### Post by temporos on 2021-08-26
@Autodave, I think you were onto something. :) I went into the BIOS and disabled SecureBoot. Then, I opened a terminal and did the following...
```
sudo apt autoremove --purge nvidia-*
sudo apt update
sudo apt upgrade
sudo ubuntu-drivers autoinstall
```
After that, I rebooted, and opened the Software Updater app. In the Additional Drivers tab, it looks (I think) better!

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289056&stc=1[/IMG]

I re-enabled SecureBoot in the BIOS, and...the problem persists. Any time I try to do anything graphics intensive, I still get the flicker. **However!** I noticed that the flicker doesn't occur until (I think) two different Xservers are using different GPU profiles. For example, if I'm running Cities Skylines, that's a graphics-intensive game, so it uses the Nvidia card. But the little indicator that appears when I change the system volume is not graphics-intensive, so it uses the Intel integrated card. Only then does the flickering start. So, this makes me think maybe the two cards aren't communicating properly?

Installing the "recommended" Nvidia driver from ubuntu-drivers also installed an Nvidia control panel app, and the settings look fine. Given this, any ideas on why the flicker might be occurring only after I, say, change the system volume?

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289055&stc=1[/IMG]

---

### Post by Autodave on 2021-08-28
Disable secure boot again and try it.

---

### Post by temporos on 2022-02-16
Still getting the screen flicker while playing certain full-screen games and videos. I've also run into another issue that I feel should be mentioned here. Since I performed [this]("https://ubuntuforums.org/showthread.php?t=2465550&p=14055976#post14055976"), every time one of the NVIDIA packages needs to be upgraded, it will cause all the NVIDIA packages to be held back. The only solution I've found is to purge all NVIDIA packages, and then run [FONT=courier new]ubuntu-drivers autoinstall[/FONT] again. This can't be the best way to go about upgrading these...

---

### Post by temporos on 2022-03-26
Anyone have ideas on this? All Nvidia packages are held back every time I run [FONT=courier new]sudo apt upgrade[/FONT]. This is causing issues like applications opening with invisible windows, and even audio issues. What gives? I *really* don't want to have to reformat this machine only a few months after I installed it, and I *definitely* don't want to go back to using Windows. The only way around this is to purge all Nvidia packages, then autoinstall the Ubuntu drivers again. I have to do this *every time*, and it's a really bad way to do things.

---

