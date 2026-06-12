---
title: "Questions about swapping Nvidia driver with Nouveau driver."
date: 2015-07-16
forum: Hardware
---

### Post by Rytron on 2015-07-16
Hi.

I had the nvidia-331 driver installed. Everything was working fine but I wanted to give the Nouveau driver a try. I just installed xserver-xorg-video-nouveau [image 'Driver Manager.gif'] and so far all seems fine**. Do I need to do anything extra - like edit the xorg file, etc?

I opened Synaptic and saw the package nouveau-firmware is not installed [image 'Synaptic-nf.gif'] - do i need this?
Is there a need to uninstall any of these packages? [image titled 'Synaptic-nvidia.gif']

My graphics card is a GeForce GTX650 - a few year old so I presume it's more compatible with Nouveau.

**
The only problems I've encountered so far is running Euro Truck Sim 2 within PlayOnLinux and Only If within Steam and it forced a re-login when I tried to play a video file on my computer.

Cheers.

---

### Post by dino99 on 2015-07-16
nouveau-firmware (20091212-0ubuntu1) lucid; urgency=low

  * Initial release.

 -- Christopher James Halse Rogers <raof@ubuntu.com>  Wed, 03 Feb 2010 10:13:11 +1100

***** should have been kicked out from archive since ages *******

your card should use nvidia-346 or 352 for better experience (xorg-edgers ppa if not available from your distro)
switching nouveau/nvidia is automaticaly done by jockey; nothing to do on the user side

the actual 'nouveau' driver for your card can handle the 'boost' feature that was only available with nvidia driver a couple months back

---

### Post by dino99 on 2015-07-16
nouveau-firmware (20091212-0ubuntu1) lucid; urgency=low

  * Initial release.

 -- Christopher James Halse Rogers <raof@ubuntu.com>  Wed, 03 Feb 2010 10:13:11 +1100

***** should have been kicked out from archive since ages *******

your card should use nvidia-346 or 352 for better experience (xorg-edgers ppa if not available from your distro)
switching nouveau/nvidia is automaticaly done by jockey; nothing to do on the user side

---

### Post by Rytron on 2015-07-16
Is it safe to remove all packages that refer to just Nvidia and not to Nouveau in Synaptic?

---

### Post by NoWayWin8 on 2015-07-17
> **Rytron said:**
> Hi.

I had the nvidia-331 driver installed. Everything was working fine but I wanted to give the Nouveau driver a try. I just installed xserver-xorg-video-nouveau [image 'Driver Manager.gif'] and so far all seems fine**.

Part of the nvidia installation includes an automatic blacklisting of the nouveau. You should uninstall nvidia-331 the same way you installed it (apt-get or the "additional drivers" tab on Software Sources, depending on which you used) so the configuration changes can be undone correctly. Even then, my experience with the nvidia linux drivers has been mostly negative and reverting back to nouveau results in more problems than would be present if the proprietary driver had never been installed in the first place (I've wiped and reinstalled so many times its not even funny).

---

### Post by tokyobadger on 2015-07-17
Just out of interest have you read [this article (Nouveau and Steam)](http://www.phoronix.com/scan.php?page=news_item&px=Nouveau-CSGO-TF2-Tests) or [this article (Nouveau vs Nvidia)](http://www.phoronix.com/scan.php?page=article&item=nvidia-352-nouveau&num=1) over at phoronix?

Seems to me that you'd be better off with the latest Nvidia driver from a ppa (as suggested above) as opposed to nouveau if gaming performance is what you're after. If you're switching for ideological purposes then [this article might be of interest](http://www.phoronix.com/scan.php?page=news_item&px=NVIDIA-Nouveau-CUDA-Support) <-- while it's not (yet) full open-sourcing of their driver development, assigning resources to CUDA support on Nouveau is an interesting step

---

### Post by Rytron on 2015-07-17
> **NoWayWin8 said:**
> Part of the nvidia installation includes an automatic blacklisting of the nouveau. You should uninstall nvidia-331 the same way you installed it (apt-get or the "additional drivers" tab on Software Sources, depending on which you used) so the configuration changes can be undone correctly. Even then, my experience with the nvidia linux drivers has been mostly negative and reverting back to nouveau results in more problems than would be present if the proprietary driver had never been installed in the first place (I've wiped and reinstalled so many times its not even funny).

Hi NoWayWin8.

I used Driver Manager to install the Nouveau driver, this auto unseleted the Nvidia driver within Driver Manager.

Do you mean manually remove 'nvidia-opencl-icd-331' and 'libcuda1-331' via Synaptic?

---

### Post by Rytron on 2015-07-17
> **tokyobadger said:**
> Just out of interest have you read [this article (Nouveau and Steam)](http://www.phoronix.com/scan.php?page=news_item&px=Nouveau-CSGO-TF2-Tests) or [this article (Nouveau vs Nvidia)](http://www.phoronix.com/scan.php?page=article&item=nvidia-352-nouveau&num=1) over at phoronix?

Seems to me that you'd be better off with the latest Nvidia driver from a ppa (as suggested above) as opposed to nouveau if gaming performance is what you're after. If you're switching for ideological purposes then [this article might be of interest](http://www.phoronix.com/scan.php?page=news_item&px=NVIDIA-Nouveau-CUDA-Support) <-- while it's not (yet) full open-sourcing of their driver development, assigning resources to CUDA support on Nouveau is an interesting step

Hi tokyobadger.

I generally prefer retro and older games. I tried some games with the Nouveau driver yesterday - HL2 and Left4Dead in Steam and they work fine.

Thanks for the links. I am more concerned with ideological purposes than gaming performance.

---

### Post by tokyobadger on 2015-07-17
> **Rytron said:**
> Hi tokyobadger.

I generally prefer retro and older games. I tried some games with the Nouveau driver yesterday - HL2 and Left4Dead in Steam and they work fine.

Thanks for the links. I am more concerned with ideological purposes than gaming performance.
Fair enough. I haven't tried Nouveau recently but when I have previously I didn't get the desktop performance I wanted from the hardware. In some ways I still don't with the nvidia drivers - google nvidia sli linux support ...

---

### Post by Rytron on 2015-07-17
> **tokyobadger said:**
>  ... google nvidia sli linux support ...

[https://duckduckgo.com/?q=nvidia+sli+linux+support](https://duckduckgo.com/?q=nvidia+sli+linux+support) ;)

---

### Post by Yellow Pasque on 2015-07-17
> the package nouveau-firmware is not installed - do i need this?
I think it's supposed to have the firmware needed for VDPAU. You can extract the firmware yourself:
```
sudo apt-get install mesa-vdpau-drivers vdpauinfo vdpau-va-driver
mkdir /tmp/nouveau
cd /tmp/nouveau
wget https://raw.github.com/imirkin/re-vp2/master/extract_firmware.py
wget http://us.download.nvidia.com/XFree86/Linux-x86/325.15/NVIDIA-Linux-x86-325.15.run
sh NVIDIA-Linux-x86-325.15.run --extract-only
python2 extract_firmware.py  # this script is for python 2 only
sudo mkdir /lib/firmware/nouveau
sudo cp -d nv* vuc-* /lib/firmware/nouveau/
```

After next reboot, check vdpauinfo:
```
vdpauinfo
```

The above procedure is based on: [http://nouveau.freedesktop.org/wiki/VideoAcceleration/](http://nouveau.freedesktop.org/wiki/VideoAcceleration/)
How "unfree" is firmware? Well, unless you're RMS and using some obscure laptop, you've already got binary firmware loaded on your system, whether it's for your CPU or Realtek network adapter.

---

### Post by Rytron on 2015-07-18
> **Temüjin said:**
> I think it's supposed to have the firmware needed for VDPAU. You can extract the firmware yourself:
```
sudo apt-get install mesa-vdpau-drivers vdpauinfo
mkdir /tmp/nouveau
cd /tmp/nouveau
wget https://raw.github.com/imirkin/re-vp2/master/extract_firmware.py
wget http://us.download.nvidia.com/XFree86/Linux-x86/325.15/NVIDIA-Linux-x86-325.15.run
sh NVIDIA-Linux-x86-325.15.run --extract-only
python2 extract_firmware.py  # this script is for python 2 only
sudo mkdir /lib/firmware/nouveau
sudo cp -d nv* vuc-* /lib/firmware/nouveau/
```

After next reboot, check vdpauinfo:
```
vdpauinfo
```

The above procedure is based on: [http://nouveau.freedesktop.org/wiki/VideoAcceleration/](http://nouveau.freedesktop.org/wiki/VideoAcceleration/)
How "unfree" is firmware? Well, unless you're RMS and using some obscure laptop, you've already got binary firmware loaded on your system, whether it's for your CPU or Realtek network adapter.

Hi Temüjin.

Thanks for the data. What happens if I don't install those things? I think I will just stay with the Nouveau driver via Jockey for a while and may switch back to the Nvidia Jockey driver in time.

---

### Post by Yellow Pasque on 2015-07-18
> **Rytron said:**
> Thanks for the data. What happens if I don't install those things?

You won't get help decoding video from the GPU. If your CPU is powerful enough to play HD video smoothly, you may not care.

---

### Post by Rytron on 2015-07-18
> **Temüjin said:**
> You won't get help decoding video from the GPU. If your CPU is powerful enough to play HD video smoothly, you may not care.

```
inxi
```

```
CPU~Quad core Intel Core i5-3470 CPU (-MCP-) clocked at 3201.000 Mhz ... 
```

I will switch back to the recommended Jockey Nvidia driver in the next few days. Perhaps one day the Nouveau driver will one day become a viable alternative.

Bye Temüjin. ;-)

---

### Post by Rytron on 2015-07-19
I tried to go back to the Nvidia driver I'd used for over a year but it hangs [see image].

I eventually click cancel and it goes back to the Nouveau driver.

---

### Post by Rytron on 2015-07-20
I did a reboot and this time it worked. :KS

---

