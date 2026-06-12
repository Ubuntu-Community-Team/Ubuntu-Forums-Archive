---
title: "Laptop/Ubuntu 10.04 - GPU and Disk overheating even when idle"
date: 2010-07-21
forum: Hardware
---

### Post by Elding Nyr on 2010-07-21
I'm looking for some advice from folks who have successfully dealt
with overheating problems on their notebooks running Ubuntu 10.04.
 
My notebook (HP DV6700) is setup to dual boot - Ubuntu and Vista.   When
booted under Windows Vista the internal temperatures are reasonable,
even under moderate load.   When I boot the notebook under Ubuntu the GPU
and disk temperatures climb steadily to very warm, even when the system is
idle.
 
Here are the temperature observations  10 minutes after boot:
 
Windows Vista:
GPU Temp - 54 C
Disk Temp - 41 C
CPU Temp - 36 C

Ubuntu Studio 10.04:
GPU Temp - 60 C
Disk Temp - 61 C
CPU Temp - 43 C

Ubuntu 10.04 Live CD:
GPU Temp - 73 C
Disk Temp - 61 C
CPU Temp - 43 C

Fedora 13 Live CD
GPU Temp - 73 C
Disk Temp - 53 C
CPU Temp - 43 C

Knoppix 6.2.1 Live CD
GPU Temp - 60 C
Disk Temp - 60 C
CPU Temp - 43 C
                                
Here are some other specifics:
 
   GPU temperatures measured via "nvclock"
   Disk temperatures measured via "hddtemp"
   CPU temperatures measured via "sensors"
   All temperatures under Windows measured via "speedfan"
 
   Platform Info
     HP DV6700
     Firmware - F.59
     nVidia G86 - GeForce 8400M GS - Clock speed 33 MHz
 
   Ubuntu Setup
         Kernel - 2.6.32-21-preempt
         PowerMizer - enabled
         Nvidia driver - nvidia-current - 195.36.24-0ubuntu1~10.04
         CPU Frequency - 800 MHz (both CPU 0 and CPU 1)
 
         CPU Load - 97-98% idle
         iostat - 0-6 transfers per second
 
         acpi setup
               /proc/acpi/fan - empty
               /proc/acpi/power_resource - empty
               /proc/acpi/thermal_zone - empty
               acpi flag appears on both CPUs.
               BIOS shows ACPI as "supported"
               power_management.acpi.linux.version = '20090903'
               power_management.type = 'acpi' 
               acpid - Installed and running - V1.0.10-5ubuntu2.1
               acpi-support - V0.136
 
         nVidia configuration
               Kernel driver in use: nvidia
               Kernel modules: nvidia-current, nvidiafb, nouveau

               nvidia-173-modaliases                173.14.22-0ubuntu11
               nvidia-96-modaliases                 96.43.17-0ubuntu1
               nvidia-common                        0.2.23
               nvidia-current                       195.36.24-0ubuntu1~10.04
               nvidia-current-modaliases            195.36.24-0ubuntu1~10.04
               nvidia-settings                      195.36.08-0ubuntu2
 
Here are my specific questions:
 
   1.  I don't have a lot of experience on setting up acpi.
 
         - Should I have to make any changes?
 
         - How can I tell whether acpi is configured correctly on
           this notebook?
 
   2.  Does anyone have a similar notebook setup that is running
       at acceptable temperatures under Ubuntu 10.04?   If so,
       did you have to make any configuration changes?
 
   3.  Does it look like I have two problems here (hot GPU and
       hot disk) or do you think there is a single underlying
       cause?
 
   4.  Can anyone explain why this notebook runs at reasonable
       temperatures under Windows Vista but the GPU and hard
       disk are so warm under all versions of Linux that I have
       tested?
 
   5.  Are there any other suggestions on how I might solve this
       problem?
 
Thank you very much!!!

---

### Post by Elding Nyr on 2010-07-25
Anyone have any thoughts on this?

---

### Post by Elding Nyr on 2010-07-29
Bump

---

### Post by ahoros on 2010-08-02
well - for what it is worth - I seem to have similar problem
my Dell Latitude E6400 (with nVidia graphics)
runs much hotter under Ubuntu 9.10 and 10.4 - than it does under Windows
-- even under moderate load the CPU throttling slows down my laptop considerably 

what I noticed is that CPU fan runs always at single speed setting under Linux
--- to this might be the source of the problem?

Do you notice anything similar?

---

### Post by Elding Nyr on 2010-08-02
Ahoros-

Thanks for the reply! I think we may have different, though possibly related, problems. My fan speed definitely jumps up when the CPU temperatures go up, but doesn't seem to increase as the hard drive/GPU temperatures increase. Have you noticed whether or not your GPU is running particularly hot? Have you checked your /proc/acpi/ folders? It's possible that we both have badly (but somewhat differently) configured acpi settings.

---

### Post by jacobjamesm on 2010-08-07
I am facing exactly the same problem. My processor doesn't actually get very heated up. Its the Hard disk that does. And that gets me worried cause people seem to be claiming that if hard disk temps aren't controlled the disks tend to crash and fail.

---

### Post by tadaskr on 2010-08-07
Same problem with Toshiba satellite a300. fans working, but not going fast or slow. if I boot cold pc fan do not turn on until CPU reaches 70C or more. To go fans faster reboot pc and bios set faster :)

---

### Post by IcarusR on 2010-08-07
Have you tried using acpi_osi="Linux" kernel boot option ??

---

### Post by tadaskr on 2010-08-07
where i can find that acpi_osi?

---

### Post by Elding Nyr on 2010-08-07
@IcarusR- Thanks so much for the suggestion! I just tried it and saw pretty much exactly the same temperature behavior as before. Any other ideas to try?

@tadaskr- You can set this option in your grub configuration file. If you have grub2, this will be /etc/default/grub, and you can read about the basics of working with the configuration file here: [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

@jacobjamesm- Yeah, that's exactly what I'm worried about, too! Would you mind posting some of the details of your laptop setup- brand, model, graphics card, that type of thing? If we end up having to file a bug report on this, I figure the more we know about what type of laptops it affects, the better.

---

### Post by Elding Nyr on 2010-08-09
@tadaskr- Sorry, slight mistake in what I said before. If you have grub, the configuration file will be /boot/grub/menu.lst. If you have grub2, the configuration file will be /etc/default/grub.

---

### Post by TBABill on 2010-08-09
I have a few suggestions, but you may already have them in place. I saw you have the nVidia driver installed, but it also mentions the nouveau. Can you remove any aspect of the nouveau driver? My machine does not have an nVidia card so I can't experiment and explain how. But if you are using the open source driver your GPU will run really hot...using the nVidia driver (exclusively) will gain immediate drops in temps.
 
Other items:
 
1. Remove open source Java and install Sun Java
2. Remove open source flash and install Adobe Flash (still sucks, but better)
3. Make sure you have that proprietary video driver installed and your system is not still using the open source driver
4. Enable CPU frequency scaling to reduce heat, even though your heat does not appear to be from the CPU. Install CPUFREQ via Synaptic and enable via terminal with > cpufreq-set --governor ondemand which will set your CPU at its lowest freq until system demand increases and demands it to step up as required. To verify what you are set to just type > cpufreq-info in a terminal.

---

### Post by Elding Nyr on 2010-08-10
@TBABill- Thanks so much for the suggestions! I first went through Synaptic and searched for anything nouveau related to get rid of, and I removed xserver-xorg-video-nouveau. I then checked to see if the proprietary driver was in fact the driver currently in use. According to the "hardware drivers" GUI under "Administration," the NVIDIA proprietary driver is installed and active. 

Next, I confirmed that I had Sun Java installed, rather than the open-source version, and I installed Adobe Flash and removed the open-source Flash.

Finally, I confirmed that my CPU frequency governor was set to on-demand, as shown by the cpufreq-info command.

After that, I shut down the computer for fifteen minutes, booted it up, and monitored the temperatures for the next ten minutes. The temperatures climbed pretty much exactly as they had before. Any other ideas for me to try?

---

### Post by Elding Nyr on 2010-08-17
Bump

---

### Post by rafalcieslak on 2010-08-18
I had recently a problem that had exactly the same symptoms (and similar temperatures) as yours, none of above solutions worked for me. Yesterday I decided to reinstall my system (from maverick to maverick), and, what is interesting, the CPU temperature lowered from 50 C to 42-41 C when idle, disk and gpu are also not as hot as they used to be. It still is not the 35 C I used to have on karmic, so it is not an ideal solution, but as in my case it helped A LOT, you might want to try (if you are so desperate that you have nothing against reinstalling, I am not going to convince you to remove your system completely and start from the beggining, since I doubt it is an universal solution). I'd love to know WHY it helped me, in order to understand what was the cause of this trouble, so one could repair his ubuntu without the need of reinstalling. Any ideas?

PS. Oh, and maybe you might want to try a liveCD of Ubuntu Studio to check if it's better on a clean system that you use now? As far as I know preempt kernels are quite power-consuming.

---

### Post by Elding Nyr on 2010-08-18
Hmmm... That is interesting. I may eventually try a reinstall, but a Live CD test of Ubuntu 10.04 (non- Studio) showed even worse temperature problems than I'm experiencing with my installed version, so I'm not quite ready to blame it on the preempt kernel yet. Also, I would expect the preempt kernel to cause higher CPU temperatures rather than high GPU/disk temperatures, but in general my CPU temperatures are quite reasonable. Unfortunately, there's no Live CD of Ubuntu Studio, so I can't directly test temperatures with a clean Studio system, but the tests of all of the other distros that I mentioned in my original post showed pretty similar problems.

Would you mind posting some information on the system you were having trouble with- model, manufacturer, GPU, that type of thing? I'm curious whether this problem affects only a particular type of laptop or whether it's more widespread.

---

### Post by tadaskr on 2010-08-18
When I try live CD then fans don't run at all, than mean in live CD laptop is much hotter than installed ubuntu. Now I will try thinkfan maybe that will work

UPDATE: it's doesn't work... I play FIFA 10 temperature up to 69C but fan still working at slowest speed. I agree that is kernel problems

---

### Post by rafalcieslak on 2010-08-23
I use Dell Studio 1773 with Mobility Radeon 3560 HD.

---

### Post by n00pster on 2010-08-29
I too have the same problem and I am tired of it. I am thinking of installing suse to see if its free of these heat problems

---

### Post by Tadcrazio on 2010-08-31
> **n00pster said:**
> I too have the same problem and I am tired of it. I am thinking of installing suse to see if its free of these heat problems

I'm having the same problem with my toshiba laptop, running real hot and under a moderate load has been overheating. Going to try the suggestion from TBABill. I'd love to know how you made out if infact you install Suse.

---

### Post by n00pster on 2010-09-03
i installed suse 11.3, this heat problem is not there. temperature is same as in windows.. maybe someone should port the power management code from opensuse to ubuntu..

---

### Post by Tadcrazio on 2010-09-10
Well i made sort of an improvement..  I was reading a little on here [http://ubuntuforums.org/showthread.php?t=1317507](http://ubuntuforums.org/showthread.php?t=1317507) and i did as ethos101 did and i also added the cpu frequency monitor and put it on powersave, or ondemand when i need it and it runs a lot similiar to windows.

---

### Post by Kernelius Zorg on 2010-09-26
Hi Elding Nyr, after reading your post I've decided to register and reply. I know I'm about to write a long post, but I'm trying to give every detail that might help figuring this thing.

I think I'm having the same problem as you described. I searched the internet and ubuntu-forums to no avail. I hope this thing will be solved, but anyway I'll post my encounter with this problem and maybe that will shed some light.

I have a ThinkPad R60 with ATI radeon mobility x1400 (which I understand it a terrible card that has no linux driver support anymore by ATI). anyway a year ago when I was still using WinXP I had a fan error (I had the laptop for few years and normally it wasn't overheating. When I played games the fan would just work harder and cool it), I gave the PC to IBM service they installed a new fan and a new WD 250GB HD that I bought (SATA if I'm not mistaken). 
So now I had a brand new installation of XP but decided to also check Linux-Mint 8 (which was based on ubuntu 9.10, Karmic). I installed it on an external HD and for months everything was OK. The laptop never got overheated (I assume that not using the internal HD also contributed to that), but even the external HD didn't get overheat.

When ubuntu 10.04, Lucid released I decided to install it on my laptop (the internal HD) and now I have a dual-boot (winxp, lucid). I didn't pay any attention to an overheating issue in the first months, but around june I started noticing it (it's got nothing to do with the summer, I have an air-condition running when it gets hot).
At that time I also stopped using the AC + battery and started using only the AC (I now checked if that might be the cause for overheating - no. I even enabled the "spin down HD when possible" that is in "Power Management "-"On AC Power", didn't change anything)

When I'm in WinXP th temperatures aren't that hot-

WindowXP
Disk Temp - 41 C
CPU Temp - 52 C
GPU Temp - unfortunately I can't measure them for some reason. I tried some softwares and that didn't help.

on the other side, in Lucid, things are different:

Lucid (2.6.32-24, also occurred before this latest kernel upgrade, ext3)
Disk Temp - 51 C (and when not idle it goes up, I use ThinkPad Fan Control at 60-75% of speed so it won't climb higher than 52 C, though when using flash (which is another problem it can get a lot hotter)
CPU Temp - 56-60 C (when idle of course)
GPU Temp - 68-72 C (also when idle)
(when using flash that can jump to CPU-80 C, GPU- 88 C, Disk- 55 C, if not using the Fan Control).

I read a lot of posts about ATI, GPU, radeon, KMS, SGI, Xorg, fan ctrl, overheat, compiz (even tried to turn it off, didn't help), I tried tweaking something like 80% of what I read (I'm not a linux pro, so I didn't want to ruin something). Anyway after giving it a lot of reading and searching, I'm still lost.

I have no idea what to do, it's not the fan (it's new), not the HD (it's also new), it's not happening on WinXP (so it's something to do with Lucid/ubuntu). It might be related to ubuntu<->HD interaction (because when I had an external HD with Karmic on it, it was OK). It might be related to ubuntu<->ATI radeon (x1400) that has no propriety drivers.
I know that when Lucid is idle, the CPU usage is low, so I assume it's not caused by ubuntu<->CPU interaction.

So my layman guess would be ubuntu<->HD or ubuntu<->GPU. (could it be related maybe to not having propriety drives for the ATI card? or now that I think of it, maybe to the fact that I'm using ext3 and not ext4? or maybe because I installed the hdapsd package which enables "Hard Drive Active Protection System" and it interferes with the HD?)
I also noticed that when not turning on the Fan Control the fan speed is always around 2700-2800 RPM. I don't recall ever hearing Lucid turning the fan faster to cool down the machine (not even when using flash and the temps got to 80-90 C), in WinXP I do recall the fan working harder when temps got high.

I really hope someone will solve this, if not now then maybe in 10.10. I want to by another thinkpad but now I fear I should look carefully for a laptop that will fit to ubuntu. :confused:

---

### Post by tadaskr on 2010-09-26
> **Tadcrazio said:**
> Well i made sort of an improvement..  I was reading a little on here [http://ubuntuforums.org/showthread.php?t=1317507](http://ubuntuforums.org/showthread.php?t=1317507) and i did as ethos101 did and i also added the cpu frequency monitor and put it on powersave, or ondemand when i need it and it runs a lot similiar to windows.

yep, this worked for me too, but I don't know how long. Maybe on next restart it will not work :)

---

### Post by c00lwaterz on 2010-09-28
same problem about temperarure but different in fan. my fan is not working so my gpu gets hot or my cpu even in idle state. I tried many distros and some help from advance users. nothing works. I also tried acpi no check .. but did not work.

Toshiba m900 works only on windows. (maybe):(

---

### Post by tadaskr on 2010-09-29
did you try that?
> So here is the recipe:

    * Open a terminal (Applications | Accessories | Terminal)
    * Type:

sudo nano /etc/default/grub

    * Find and Edit the following line:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

    * Add acpi_osi=Linux to the end so it looks like this:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux"

    * Exit Nano editor with Ctrl+X.  Answer "yes" when asked to save the file
    * Update grub: 

sudo update-grub

    * Reboot to make changes effective 			 		

it worked for me and I don't have problem with overheating. How I will try one day to lower GPU clock and will be no problems at all

---

