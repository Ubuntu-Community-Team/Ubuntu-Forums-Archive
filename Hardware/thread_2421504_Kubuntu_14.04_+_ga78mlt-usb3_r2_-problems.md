---
title: "Kubuntu 14.04 + ga78mlt-usb3 r2 -problems"
date: 2019-06-22
forum: Hardware
---

### Post by satnrzn on 2019-06-22
Hi! 
I have this fee and extremely disappointed. Solid glitches with &#1093;Ubuntu.Nevertheless, in the Windows - all the rules.
I'm trying to get Kubuntu 14.04 to work normally no longer know which time. 
Unsuccessfully. Today, again, was not a successful attempt. 
But I saw on the network a little, very little, but I saw that people use the Ubunt derivatives on this board.


ZM500LX /16GB Ram / GTX 1050 Ti / FX 4300 / Toshiba HDWD110 1Tb (more than three years). 

After installation, the system behaves simply unpredictable - I have not seen such glitches in the course of using Linux. I use Linux from the output of Ubuntu 10.04. But now I do not know what else to do.

The system is buggy or after installation. Or it seems to be normal, but in the process - again glitches! Here today, I installed it - it seems normal. Updated - and rushed ... But this is not because of the update, that's for sure. It happens while setting up after installation - the same glitches. Just always at a different moment. 
I tried to install from different flash media. Even dvd disk recorded. All the same. 
The system freezes tightly, randomly. After that, it may not load as it should, under the user, but under the ROOT.
Or, when booting and rebooting, after GRUB, the computer dies. After I chose Ubunt 14.04 and pressed enter - very often - everything hangs. Everything is working. Fans and everything. But the PC is dead. Even the disc indication does not blink.Does not react to anything, only - reset. This is the same randomly. 

I do not believe that there may be a problem with the hard drive. Since, before installing Ubunt on this disk partition, it is usually busy with Windows under games. And I in Windows do not have any problems with this disk. Of course, I delete Windows partitions before installing Linux. Gpared And I create anew, with the E&#1061;T4 FS. I am not idiot.


But what is remarkable. I put a very old disk Toshiba 2.5. (he will probably die soon ...) Especially for testing. Kubuntu was already installed there on 14.04, but on a different hardware.
And with this disc for a month somewhere, everything worked perfectly! 

But again, assuming that my hard drive desktop Toshiba is working fine under Windows. I have no reason to believe that the problem is in him. 
Yes, and I have a second PC, FM2 (Biostar MoBo), very old, there are hard drives there - in the trash. And nevertheless, Kubuntu 14.04 works well.

Help. What can be done? Maybe some parameters in the download register? As the same people use Ubuntu on this board.

Please forgive me for my very bad English. And I plus used a translator. Very tired. Over 12 hours trying to configure Kubuntu 14.04 on this PC. Unsuccessfully ...

---

### Post by jeremy31 on 2019-06-22
Unfortunately all 14.04 versions are no longer supported

---

### Post by satnrzn on 2019-06-22
I know. Nevertheless, it fulfills all my needs. It works for me. KDE4! Plasma 5 - just porn. And yet I hope for help. 
And the change of distro on 18.04 - is unlikely to solve these problems. You understand. More than 14.04 is already up and updated. It is necessary to solve the problems here first. And then, in all the weapons already ... I can and update. And I will not be again "at the broken trough" (Russian fairy tale))
You understand, this is life, I just do not have time to rearrange here and there. Let's try to solve it with what we have.

```
System:    Host:  Kernel: 3.13.0-170-generic x86_64 (64 bit) Desktop: KDE 4.13.3 Distro: Ubuntu 14.04 trusty
Machine:   Mobo: Gigabyte model: GA-78LMT-USB3 R2 version: sex Bios: Award version: F1 date: 11/08/2017
CPU:       Quad core AMD FX-4300 (-MCP-) cache: 8192 KB flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 sse4a ssse3 svm) 
           Clock Speeds: 1: 1400.00 MHz 2: 1400.00 MHz 3: 1400.00 MHz 4: 1800.00 MHz
Graphics:  Card: NVIDIA Device 1c82 X.Org: 1.15.1 driver: nvidia Resolution: 1920x1080@60.0hz 
           GLX Renderer: GeForce GTX 1050 Ti/PCIe/SSE2 GLX Version: 4.5.0 NVIDIA 384.130
Audio:     Card-1: NVIDIA Device 0fb9 driver: snd_hda_intel Sound: ALSA ver: k3.13.0-170-generic
           Card-2: C-Media CMI8738/CMI8768 PCI Audio driver: snd_cmipci 
           Card-3: Aveo driver: USB Audio 
Network:   Card: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller driver: r8169 
           IF: eth0 state: up speed: 1000 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 2060.4GB (39.3% used) 1: id: /dev/sda model: SPCC_Solid_State size: 60.0GB 
           2: id: /dev/sdb model: TOSHIBA_HDWD110 size: 1000.2GB 3: id: /dev/sdc model: TOSHIBA_HDWD110 size: 1000.2GB 
Partition: ID: / size: 15G used: 6.8G (49%) fs: ext4 ID: /home size: 276G used: 4.9G (2%) fs: ext4 
           ID: swap-1 size: 5.37GB used: 0.00GB (0%) fs: swap 
RAID:      No RAID devices detected - /proc/mdstat and md_mod kernel raid module present
Sensors:   System Temperatures: cpu: 20.0C mobo: N/A gpu: 43C 
           Fan Speeds (in rpm): cpu: N/A 
Info:      Processes: 172 Uptime: 1:42 Memory: 1644.8/16046.9MB Client: Shell (bash) inxi: 1.9.17
```

---

### Post by jikaczmarski on 2019-06-23
satnrzn; Can you go ahead and run these commands to reinstall the Nvidia drivers, then make sure to reboot. If it's still not working, send over what drivers you are using. In your output there is nothing in the driver section.
```
sudo apt purge nvidia*
sudo apt update
sudo ubuntu-drivers autoinstall
sudo apt full-upgrade
```

---

