---
title: "NVidia GTX970: Pulse thinks HDMI audio is unplugged, driver doesn't read 1080p"
date: 2016-01-31
forum: Hardware
---

### Post by 81chevette on 2016-01-31
I have a three OS setup, with Win10, Ubuntu Wily and Mint Rosa. I have an old, cheapo HD TV. I have an Intel i7 Skylake with integrated graphics and an nvidia GTX 970 GPU.
Both 1080p and audio work flawlessly in Windows through both outputs. 
Mint Rosa's stock driver (Nouveaux or something similar) gives me perfect 1080p and audio through the CPU.
Ubuntu Wily's stock driver gives inconsistent results through the CPU. Likely because I've tinkered under the hood too much.
Both flavors of Linux stock drivers boot without HDMI output through the GPU, but will accept a change to tty2 and a reboot command.
Both flavors of Linux with any possible proprietary driver I can get my hands on fail to read 1080 capability in my TV, and will not output HDMI audio. (For the record, BIOS and GRUB also use a lower resolution, but I assume that's normal.)
xrandr reads the TV correctly if I manually set nvidia's control panel to upconvert to 1080p, but I don't get a 1080p signal, only the upconversion.
Pavucontrol reads the HDMI as unplugged.
Aplay lists the GPU correctly, but I'm apparently too stupid to play a test sound. I can play a test sound (inaudible) through the default output. I can play nothing through the dev of my choice. But when I try to play the test sound through the output I want, aplay complains that it's in an unreadable format.
Sound config lists no output options.
Alsamixer shows the GPU sound as present and unmuted, but with no volume options. Only a choice of OO or MM. Alsamixer defaults to onboard 5.1 sound.
I have tried turning various audio and video sources on and off in the BIOS, without much apparent effect.

I've tried about everything suggested here, on stackexchange, on the nvidia forums, and anywhere else I've seen. (Which is probably why Ubuntu won't boot to the CPU properly anymore)
I could just give up on the GPU altogether, I suppose, but the whole point of me building this computer was for gaming, so I don't want to hobble the Windows install.
The funny thing is, the first time I installed Ubuntu Wily from USB, I swear the stock driver worked fine. But not on subsequent installs. Maybe my memory is faulty on that, though.

I can accept one of three options. Best is to just get the sound working through the GPU with a proprietary nvidia driver. Second best is to get HDMI output from the GPU working with the stock driver. As a last resort, if there were a way to have GRUB, Windows, or Ubuntu force video source change without opening the BIOS, I could just change channels when I change OS. But the wife and kid need to be able to operate the computer, and opening the BIOS is beyond them.

---

### Post by 81chevette on 2016-02-02
UPDATE:
Firstly, I noticed that during boot, Ubuntu complains that the hda_intel driver failed to load, and shoots a 3-digit code too quickly for me to read. I think it began with a 9.
Secondly, I discovered today that if I boot up Ubuntu with the TV powered off, everything works fine. Well, fine-ish. I do have to set the resolution manually, and I have to go into my TV's menu to turn overscan on and back off to get it to display properly, but still. I get 1080p picture and audio. This does not work, however, if I boot Ubuntu with the TV tuned to a different input channel. So, clearly the card is failing to read my TV's EDID correctly--or at all. Now, why it just happens to guess correctly I couldn't tell you.
I suspect from what I've read that I need to use the nomodeset option, but I don't know how. Can anyone confirm that this makes sense? And, if you feel like giving me pointers on how nomodeset works, that would be great, too, but I can probably Google that myself.

---

### Post by Vladlenin5000 on 2016-02-02
Skylake CPUs, for the moment, require some additional boot arguments in GRUB:
```
i915.preliminary_hw_support=1
nouveau.modeset=0
```

---

### Post by 81chevette on 2016-02-04
Further update:
I have solved my video issue by adding nvidia.modeset=0 to grub. However, this does not affect the audio issue. If I boot with the TV powered off, I have 1080p video and HDMI audio through the GPU just fine. If I watch a video full-screen on Chrome, X resets itself and loses both 1080p capability and audio function. I am then able to exit fullscreen, perform a manual Xreset, __then open settings__ and X resets to normal capability. This behavior does not occur if I go fullscreen on Firefox. I have not yet tried Chromium, Steam, or Kodi fullscreen. If I boot with the TV powered on and the nvidia.modeset=0 argument, I get 1080p video, the TV reports DVI input rather than HDMI, and pulse reports HDMI as unplugged, so no audio. Fullscreen Chrome video has no effect.
I am now thoroughly confused.
It is clear that I need to figure out a few things. Firstly, does nvidia.modeset=0 mean NO modesetting, or does it set to a "mode 0"? Secondly, while it's now clear that my issues are with X rather than with the kernel, who is checking my output status? Is it an X daemon, or a pulse daemon? And is there a config file somewhere that I can turn that daemon off?

---

### Post by Abdulhadi_81 on 2016-02-05
This might be a long shot but what happens if you do the following ?


[LIST=1]
[*]Execute the command : sudo nano /etc/default/grub 
[*]Add "snd_hda_intel.audio=1 nouveau.modeset=0" to the list of kernel boot parameters (line starting with GRUB_CMDLINE_LINUX_DEFAULT) 
[*]Remove "nvidia.modeset=0" from the list of kernel  boot parameters if you already have it there 
[*]Press CTRL + O to save the file 
[*]Press CTRL + X to exit the file 
[*]Execute the command : sudo update-grub 
[*]Reboot 
[/LIST]
 
If the above does not work, try executing the following commands in the terminal and then reboot:

```
sudo apt-get purge nvida-*
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt-get update
sudo apt-get install nvidia-361 nvidia-prime nvidia-settings
```

---

### Post by 81chevette on 2016-02-07
> **Abdulhadi_81 said:**
> This might be a long shot but what happens if you do the following ?


[LIST=1]
[*]Execute the command : sudo nano /etc/default/grub 
[*]Add "snd_hda_intel.audio=1 nouveau.modeset=0" to the list of kernel boot parameters (line starting with GRUB_CMDLINE_LINUX_DEFAULT) 
[*]Remove "nvidia.modeset=0" from the list of kernel  boot parameters if you already have it there 
[*]Press CTRL + O to save the file 
[*]Press CTRL + X to exit the file 
[*]Execute the command : sudo update-grub 
[*]Reboot 
[/LIST]
 
If the above does not work, try executing the following commands in the terminal and then reboot:

```
sudo apt-get purge nvida-*
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt-get update
sudo apt-get install nvidia-361 nvidia-prime nvidia-settings
```

Well, the grub arguments did nothing. Purging all nvidia junk and installing the 361 driver brought me back to square 1. Now I can't even figure out how I managed to get 1080p video. It must have been some leftover configs from me trying all the various driver releases, because eventually Ubuntu started to boot to 1080p DVI mode, which solved all my problems except audio and full-screen Chrome seizures.
I'm currently working on restoring that functionality. It's possible I may just have to switch to the integrated graphics through the Skylake chip until 16.04 comes out, and hope Fallout 4 isn't too bad through that. Maybe Bethesda has mastered enough DX12-fu to offload to the GPU. I honestly have no idea how that particular voodoo works, so maybe I'll light some candles and say a little prayer.
Of course, since Wily is the last non-LTS release, it's probably using the same kernel as the LTS will, and the same version of nouveau. So maybe 16.04 won't solve anything.

---

