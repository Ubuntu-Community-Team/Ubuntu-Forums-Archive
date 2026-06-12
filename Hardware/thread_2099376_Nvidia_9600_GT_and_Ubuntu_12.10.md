---
title: "Nvidia 9600 GT and Ubuntu 12.10"
date: 2012-12-29
forum: Hardware
---

### Post by Adventx on 2012-12-29
So I decided to try coming back to Ubuntu again after my crappy Windows 8 trial experience has run out and still having the same major issues I had with Ubuntu before. My problem is that any Nvidia driver I put onto my system through any methods simply crashes my system and makes it unusable. I've used the methods that Nvidia specifies through their read-me and set everything manually, used Jockey, installed through apt-get and they all just crash the system. I thought in my last attempt that it may have been due to the fact that I accidentally upgraded to xorg 1.13 and couldn't roll back to 1.12, but I just did a full clean install and have'nt upgraded anything xorg related to see if anyone might have some suggestions on what might be the problem before trying to install drivers again. I think one part of the scenario is that my card, although a 9600 GT, is an off brand and may not be like the other 9600 GT sets. I think that because I had issues with running the Nvidia 310 driver update when I was running Windows 8.

Sorry for the long description, I just want my card running on Ubuntu and to be able to play some games nicely so that I don't have to go back to Windows again. Thanks in advance to anyone who can help.

---

### Post by oldfred on 2012-12-29
I upgraded to a 9600GT about 3 years ago when my 7600GS blew out its capacitors. 

I have had no issue with my nVidia other than it needs nomodeset on liveCD/flash and on first boot. 

But with 12.10 I ran into the issue of no kernel headers like many others. Once you install the kernel header then it works. I am using current-updates in 12.04 and primarily use 12.04. But I always install one of the versions offered by Ubuntu.

       [http://ubuntuforums.org/showthread.php?t=2081649](http://ubuntuforums.org/showthread.php?t=2081649)
# You may need headers - meta package for current version:
sudo apt-get install linux-headers-generic
# only reason to purge is there are several versions, if you know you have different nVidia use that:
#To see available  versions:
dpkg -l | grep -i nvidia*
apt-cache search nvidia-sett*
# I used nvidia-current-updates & nvidia-settings-updates, example below is just nvidia-current, use version you prefer
sudo apt-get purge nvidia*
sudo apt-get install nvidia-current
sudo apt-get install nvidia-settings
sudo dpkg-reconfigure nvidia-current
sudo nvidia-xconfig
sudo reboot
May want nvidia-current, nvidia-current-updates or nvidia-current-experimental-XXX for most recent testing version.
apt-cache search nvidia-sett*

---

### Post by Adventx on 2012-12-29
Thank you so much for your reply. I'm trying your instructions now and will post results.

---

### Post by Adventx on 2012-12-29
No luck, computer is unusable again. I'm booting to recovery mode to purge nvidia drivers and then going to try using the nvidia-current-updates.

---

### Post by Adventx on 2012-12-29
Ok so I tried a few different versions and they all failed. Then even tried another setting that I discovered in my research and tried adding "nomodeset" to the grub configuration and updating grub. And then after the boot screen reloaded twice and I started lightdm I was able to boot up and start a game that I downloaded just to test, it loaded and when I tried to make it full screen and at my monitors resolution it crashed the system once again.

---

### Post by Adventx on 2012-12-29
Now the system is completely unusable, boot screen comes up and the wallpaper loads then it crashes and goes back to login screen. I'm at a complete loss of what to do now.

---

### Post by oldfred on 2012-12-29
Which version nVidia did you install?

Mine just works. So I am not sure how to debug. I will reboot back into 12.10 and see that it still works as I have not updated it recently.

---

### Post by Adventx on 2012-12-29
I started with nvidia-current, then nvidia-current-updates, then nvidia-experemental-310. Had to go into recovery mode mount the disk and purge the drivers each time, then ran nvidia-xconfig to update the inframs to the version I was using. Then I realised that my Xorg was on 1.13 so I did a little bit of searching and found the nvidia 304.20 I think it was that supports 1.13 installed that and then was stuck at the continuous lightdm crashing.

---

### Post by oldfred on 2012-12-29
I confirmed I am using current updates. And only ran the settings that I posted as far as I remember. But I was trying several different things until I found what worked.

---

### Post by Calinou on 2012-12-29
> I think one part of the scenario is that my card, although a 9600 GT, is  an off brand and may not be like the other 9600 GT sets.

Which brand is it? I have a 9600M on an old laptop which works fine, zero issues, on Xubuntu 12.10 (Unity might be causing the crashes, who knows!).

---

### Post by Adventx on 2012-12-29
It's a Galaxy 9600GT [http://www.galaxytech.com/__en_gb__/Product74.aspx]("http://www.galaxytech.com/__en_gb__/Product74.aspx") and it could be Unity that is crashing it. Also I tried all the additional drivers and they either crashed the system or would not display full resolution.

---

### Post by dhiru1602 on 2012-12-31
I have run into problems with NVIDIA 9600GT running as SLI. I was unable to get the GPU to work. 

I had troubles with the nvidia-current building the modules since the kernel headers were not proper. For some reason, the linux-kernel-generic doesn't work and I have to specifically download the kernel headers for my kernel version using
```
sudo apt-get install linux-headers-`uname -r`
[COLOR=#008080]*sudo dpkg-reconfigure nvidia-current*[/COLOR]

```

After a reboot, everything was back to normal and the GPU driver worked fine. 

Hope it helps you too. ;)

---

