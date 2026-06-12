---
title: "Video only comes up in 640x480"
date: 2015-10-18
forum: Hardware
---

### Post by Icculus on 2015-10-18
I have been running Ubuntu and upgrading without any problems for several years / versions. I recently ran an upgrade and things started going wonky with my video displays. For a while, I would get no boot whatsoever. With some old kernels I could boot, but video would come up in 640x480 with a black border around the outside, and sometimes if I had the Nouveau drivers running, I would be able to boot into full resolution. However, I didn't want this due to the inability to run Steam games.

So, I reinstalled Ubuntu. At first I tried to install everything on top of the installation, but that didn't fix the problem. So I decided to wipe the install and start fresh. Everything was running great until I installed the nvidia drivers (the tested version). The same problems came back.

I've gone through every tutorial I could find to no avail. No matter which driver I have installed, (Nouveau, 340, 346, 352, 304...) I get the same problems.

I'd really like to not have to wipe Ubuntu again... especially considering that it didn't solve the issue the first time. I'm really at a loss here though. I don't know what the next steps should be.

Hardware:
~$ lspci | grep -i nvidia
01:00.0 VGA compatible controller: NVIDIA Corporation GF116 [GeForce GTX 550 Ti] (rev a1)
01:00.1 Audio device: NVIDIA Corporation GF116 High Definition Audio Controller (rev a1)

I have attached the two Xorg.{0,1}.log files. The .0 log file I had to truncate due to size, I don't think I removed any pertinent data, but if there is something missing I can certainly copy the whole thing.

NOTE: I added nomodeset manually on this boot to see if that helped (or had any effect on) the issue.


Any help from the community would be GREATLY appreciated at this point.   Thanks!
[ATTACH=CONFIG]265028[/ATTACH]
[ATTACH]265026[/ATTACH][ATTACH]265027[/ATTACH]

---

### Post by SeijiSensei on 2015-10-19
With the proprietary driver installed, did you run "sudo nvidia-xconfig"?  If not, try that.

---

### Post by Icculus on 2015-10-20
> **SeijiSensei said:**
> With the proprietary driver installed, did you run "sudo nvidia-xconfig"?  If not, try that.

I have tried that, yes. I'll give it another shot. I've noticed that after a single reboot, the nvidia-xconfig tool isn't on my computer anymore.

Also I have tried installing from both command line (via apt-get) and through the additional drivers interface. Just an additional piece of info for the troubleshooting.

EDIT: After running the install "sudo apt-get install nvidia-current nvidia-settings" the nvidia-xconfig tool still isn't installed on my machine :-\

---

### Post by sudodus on 2015-10-20
Is

```
nvidia-settings
```

installed? Try to run it!

---

### Post by Icculus on 2015-10-20
> **sudodus said:**
> Is

```
nvidia-settings
```

installed? Try to run it!

Yes it is. I don't think there is anything there that'll help me.

[ATTACH=CONFIG]265073[/ATTACH]

Also, I'll copy in some of the x11.conf files that are on my computer. I don't think they have ever worked.


I'm not sure if it matters, but I have been connected via HDMI. [ATTACH]265074[/ATTACH]

I believe this is from the only time I was actually able to run nvidia-xconfig.

---

### Post by Icculus on 2015-10-21
So I was able to run nvidia-xconfig after switching:

```
sudo update-alternatives --config x86_64-linux-gnu_gl_conf
```

I still am unable to get any improvements. The 304 driver caused low-graphics mode that wouldn't boot, the 340 driver caused a boot loop at the login screen (still low res) and the 346 driver caused a black screen with a cursor.

I suspect now that the culprit might be lying in the following log file:
```

[    20.008] (II) LoadModule: "nvidia"
[    20.016] (WW) Warning, couldn't open module nvidia
[    20.016] (II) UnloadModule: "nvidia"
[    20.016] (II) Unloading nvidia
[    20.016] (EE) Failed to load module "nvidia" (module does not exist, 0)

```

I don't have the nvidia drivers installed, so I don't know why they would be trying to load.

I'll have to come back tomorrow I guess.

---

### Post by Icculus on 2015-10-22
Update:

I grep'd on /etc for nvidia and found that bumblebee was affecting nvidia, specifically in the modprobe blacklist. 

I removed bumblebee and am back up to normal resolution with the Nouveau drivers, so I guess I'm sorta back to square 1. Hopefully I'll have more luck this time trying to get those pesky Nvidia drivers up.

---

### Post by Icculus on 2015-10-22
Tonight I tried to install the 304, 340, and 346 drivers. After each install (via command line) I ran sudo nvidia-xconfig to create the xorg config file. I rebooted to no avail. I had to remove --purge the drivers in recovery mode.

After installing each driver I tried booting twice, the first with no command line argument and the second with "nomodeset" that I entered in grub before booting. No luck on either front...

---

### Post by SeijiSensei on 2015-10-22
If you can turn off the Intel adapter in the BIOS, give that a try.  I have a hybrid Intel/ATI machine with the Intel adapter turned off to avoid any conflicts.

---

### Post by Icculus on 2015-10-25
> **SeijiSensei said:**
> If you can turn off the Intel adapter in the BIOS, give that a try.  I have a hybrid Intel/ATI machine with the Intel adapter turned off to avoid any conflicts.

I checked and didn't see any options for it. It was running for years without changing the BIOS settings though, so I'm not sure that'll be the problem.

---

### Post by sudodus on 2015-10-26
Sometimes it helps to uncomment, in other words remove the # character, from the line

```
#GRUB_TERMINAL=console
```

in the **/etc/default/grub** file.

```
sudo nano /etc/default/grub
```

Change, save, and run the command

```
sudo update-grub
```

See this link for more details

[/etc/default/grub](https://help.ubuntu.com/community/Grub2/Setup#A.2Fetc.2Fdefault.2Fgrub)

---

### Post by Icculus on 2015-10-30
So I have tried pretty much EVERYTHING at this point. I'd like to confirm my diagnosis.

I have been able to start my machine using Nouveau in full resolution. This is both on 15.04 and now 15.10.
I was having issues with Nouveau when I started this thread. This was due to the bumblebee drivers being installed. 
I have tried some drivers that lead to login loops. I have tried some that lead to seemingly dead systems.
I  have had Nvidia drivers that allow me to get to the point where I can  enter my password via SSH, but then I received no prompt.
I tried to  boot into my ancient Windows 7 partition that, last I know, worked fine.  I see the opening screen, but then when it should be going to a login, I  get "HDMI No Signal" on my monitor. 

To me all signs are  pointing to hardware. As a software engineer, I feel that is a cop-out,  but it really seems to be the case. I haven't looked yet, but if there  is a way to explicitly test this I'd appreciate any advice before I go  out and spend a couple hundred bucks on a new video card that may or may  not solve the problem.

Any thoughts? Is it possible I have a  busted video card that still works with the standard drivers but not  with the Nvidia ones because the damaged portion of the video card isn't  being used? I don't boot into Windows at all anymore, but last I tried  (maybe 6 months ago) everything was working fine there.

---

### Post by sudodus on 2015-10-30
It is rather easy to test the RAM (if you can boot into a live drive in BIOS mode: Select ***memtest***.

It is rather easy to check the S.M.A.R.T. status of the internal drive. Use ***Disks*** (gnome-disks). Install it if it is not yet installed.

You can check the file system including bad blocks with the following command (when booted from a live drive),

```
sudo e2fsck -cf /dev/sdxy
``` 

where x is the drive letter and y is the partition number.

If the power supply unit is failing, it might deliver too low voltage, which can cause various problems.

If there is too much dust inside the computer, it might get overheated, which can cause various problems. (Your problems do not look like they are caused by overheating, but who knows.)

But it can be difficult to identify problems with the motherboard.

---

### Post by Icculus on 2015-10-30
Welp... in a last ditch effort I went to the DVI cable instead of HDMI and all seems to be working at this point.

Ugh.... that was two weeks of headache. At least I have basically a speedy and new OS partition. No clue what is going on with Windows 7, but I'm not worrying about it.

Thanks for the help and more importantly, hopefully this can help someone else.

---

### Post by sudodus on 2015-10-30
Congratulations :KS

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

