---
title: "No sound Compaq Presario CQ56"
date: 2011-02-12
forum: Hardware
---

### Post by tacobeans1234 on 2011-02-12
Hey there,

I can't seem to get my sound running on my Compaq Presario CQ56. 

lspci output:
```

00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 42)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller (rev 40)
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:16.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:16.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200]
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

```Any ideas? 
Thanks! 
--Tacobeans

---

### Post by gordintoronto on 2011-02-12
This is your sound device:
Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)

Do you use the built-in speakers, or are you plugging in speakers/earphones? Have you run Preferences/Sound? In the Output tab there is a "Connector" drop-down which you might play with.

Which version of Ubuntu? You might find an improvement when the next version is available, in late April.

---

### Post by djeims on 2011-06-06
*I'm running Ubuntu 10.04 LTS, have the same computer, same glitch and this is how I fixed it:*


**[SIZE=2]Install with Synaptic Package Manager[/SIZE]**

 [SIZE=2]**Adding the ppa**[/SIZE] 

[LIST]
[*][SIZE=2]Open up the "Synaptic Package Manager": [/SIZE]
[LIST]
[*][SIZE=2]System -> Administration -> Synaptic Package Manager [/SIZE]
[/LIST]
 
[*][SIZE=2]Bring up the "Software Sources" dialog in the "Synaptic Package Manager": [/SIZE]
[LIST]
[*][SIZE=2]Settings -> Repositories [/SIZE]
[/LIST]
 
[*][SIZE=2]Select the "Other Software" tab in the "Software Sources" dialog. [/SIZE]
[*][SIZE=2]Click the "+Add" button. [/SIZE]
[*][SIZE=2]In the "APT line: " text input box type:  [/SIZE]
[LIST]
[*][SIZE=2]ppa:ubuntu-audio-dev/ppa [/SIZE]
[/LIST]
 
[*][SIZE=2]Click the "+Add Source" button. [/SIZE]
[*][SIZE=2]Close the "Software Sources" dialog. [/SIZE]
[*][SIZE=2]You  may see a dialog box pop up which warns you that your "Repositories  changed". This is a good thing and you can close the dialog. [/SIZE]
[*][SIZE=2]Since  we've just added a new repository we need to update that database that  knows what packages are available and where from. Update the package  information by: [/SIZE]
[LIST]
[*][SIZE=2]Edit -> Reload Package Information [/SIZE]
[/LIST]
 
[/LIST]
[SIZE=2]**Determine the current version of kernel running (via command line)**[/SIZE] 
[SIZE=2]uname -r[/SIZE][SIZE=2][B]

Install the linux-alsa-driver-modules package[/B][/SIZE] 

[LIST]
[*][SIZE=2]Open up the "Synaptic Package Manager" if it isn't already open: [/SIZE]
[LIST]
[*][SIZE=2]System -> Administration -> Synamptic Package Manager [/SIZE]
[/LIST]
 
[*][SIZE=2]Search for the "linux-alsa-driver-modules" package: [/SIZE]
[LIST]
[*][SIZE=2]Edit -> Search [/SIZE]
[/LIST]
 
[*][SIZE=2]In the search results shown, find the package that matches up with the kernel version that you are running. [/SIZE]
[*][SIZE=2]Select the "linux-alsa-driver-modules" package by checking the checkbox in the leftmost column of the search results. [/SIZE]
[*][SIZE=2]Install the package: [/SIZE]
[LIST]
[*][SIZE=2]Edit -> Apply Marked Changes [/SIZE]
[/LIST]
 
[*][SIZE=2]A dialog will come up asking if you want to "Apply the following changes?". Click the "Apply" button. [/SIZE]
[*][SIZE=2]A  dialog will appear showing the progress of applying the indicated  changes. After it's complete another dialog appears stating the changes  have been applied. That dialog can be closed by clicking on the "Close"  button. [/SIZE]
[*][SIZE=2]The "Synaptic Package Manager" can now be closed, the package has been installed. [/SIZE]
[/LIST]
[SIZE=2][B]Note: After installing the linux-alsa-driver-modules package, your system needs to be rebooted.

[/B] [/SIZE][I]
I got these directions from: [COLOR=Blue][https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules)[/COLOR]
They also have instructions there for doing the same thing with terminal commands.[/I]

---

### Post by S_p_or_t_o on 2011-11-13
no modules for 2.6.32-35-generic :(

---

### Post by MoreOrLess on 2011-11-13
[https://wiki.ubuntu.com/Audio/UpgradingAlsa](https://wiki.ubuntu.com/Audio/UpgradingAlsa)

---

### Post by S_p_or_t_o on 2011-11-14
10.04 LTS, 2.6.32-35-generic

thank you, but following that it seems the  Ubuntu Audio Developers Team haven't made available linux-alsa-driver-modules-2.6.32-35-generic

```
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
``` tells me there's an error and couldn't find the module and the synaptic method only has modules listed up to 2.6.32-34

should I wait, use a daily snapshot for now or try the most recent 2.6.32-34-generic?

---

### Post by MoreOrLess on 2011-11-14
Ah, I see. There doesn't seem to be any snapshot for Lucid either. I would try the ALSA upgrade script: [http://ubuntuforums.org/showthread.php?t=1681577](http://ubuntuforums.org/showthread.php?t=1681577)
Make sure you install libsdl1.2-dev before running the script (and remember to close the package manager when you're done).

---

