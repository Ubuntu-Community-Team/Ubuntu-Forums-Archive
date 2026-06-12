---
title: "Nvidia GTX 1650 ti, no HDMI output"
date: 2020-07-21
forum: Hardware
---

### Post by Bucky Ball on 2020-07-21
Hi all,

Just bought a new computer, an Asus Tuf FA506II. It is the one here ...

[https://www.asus.com/au/Laptops/ASUS-TUF-Gaming-F15/Tech-Specs](https://www.asus.com/au/Laptops/ASUS-TUF-Gaming-F15/Tech-Specs)

... and is the version with the Ryzen 5 4600H, the 1650 ti GPU and 8Gb RAM (with 16Gb on the way) and Win 10 installed. The external monitor via HDMI is working fine with Win, BTW.

From the top. I started by installing Xubuntu-core 20.04. No HDMI output to external monitor but laptop screen working fine. Went to Software and Updates > Additional Drivers and there is the nvidia-driver-440 ready for me to select. I do so, reboot, and still no HDMI.

Next, I clone the Xubuntu-core 18.04 install from my old laptop, which was working with this monitor, onto a partition on the new computer. Boot up and the grub comes up fine (but no HDMI external monitor), but when I select Xubuntu, can't get that working at all, not even to get to the login screen. Restart, choose Win and Windows 10 is still working fine (with external HDMI monitor).

Next, I find an old 16.04 Xubuntu-core ISO, burn that to USB, install that, and boots fine, but still no HDMI output. (This time no internal wireless either, but that's another story for another thread.) Thought I might get sneaky and, in a surprise attack, I upgrade via the terminal from 16.04 to 18.04. Still no HDMI (using nvidia-driver-440).

Some outputs.

```
~$ nvidia-smi --query

==============NVSMI LOG==============

Timestamp                           : Wed Jul 22 13:12:23 2020
Driver Version                      : 440.100
CUDA Version                        : 10.2

Attached GPUs                       : 1
GPU 00000000:01:00.0
    Product Name                    : GeForce GTX 1650 Ti
    Product Brand                   : GeForce
    Display Mode                    : Disabled
    Display Active                  : Disabled
    Persistence Mode                : Disabled
    Accounting Mode                 : Disabled
    Accounting Mode Buffer Size     : 4000
    Driver Model
        Current                     : N/A
        Pending                     : N/A
    Serial Number                   : N/A
    GPU UUID                        : GPU-478032cf-a2ee-befc-da9d-96964836c5c4
    Minor Number                    : 0
    VBIOS Version                   : 90.17.42.00.21
    MultiGPU Board                  : No
    Board ID                        : 0x100
    GPU Part Number                 : N/A
    Inforom Version
        Image Version               : G001.0000.02.04
        OEM Object                  : 1.1
        ECC Object                  : N/A
        Power Management Object     : N/A
    GPU Operation Mode
        Current                     : N/A
        Pending                     : N/A
    GPU Virtualization Mode
        Virtualization Mode         : None
        Host VGPU Mode              : N/A
    IBMNPU
        Relaxed Ordering Mode       : N/A
    PCI
        Bus                         : 0x01
        Device                      : 0x00
        Domain                      : 0x0000
        Device Id                   : 0x1F9510DE
        Bus Id                      : 00000000:01:00.0
        Sub System Id               : 0x16DF1043
        GPU Link Info
            PCIe Generation
                Max                 : 3
                Current             : 3
            Link Width
                Max                 : 16x
                Current             : 8x
        Bridge Chip
            Type                    : N/A
            Firmware                : N/A
        Replays Since Reset         : 0
        Replay Number Rollovers     : 0
        Tx Throughput               : 0 KB/s
        Rx Throughput               : 0 KB/s
    Fan Speed                       : N/A
    Performance State               : P0
    Clocks Throttle Reasons
        Idle                        : Not Active
        Applications Clocks Setting : Not Active
        SW Power Cap                : Not Active
        HW Slowdown                 : Not Active
            HW Thermal Slowdown     : Not Active
            HW Power Brake Slowdown : Not Active
        Sync Boost                  : Not Active
        SW Thermal Slowdown         : Not Active
        Display Clock Setting       : Not Active
    FB Memory Usage
        Total                       : 3911 MiB
        Used                        : 0 MiB
        Free                        : 3911 MiB
    BAR1 Memory Usage
        Total                       : 256 MiB
        Used                        : 2 MiB
        Free                        : 254 MiB
    Compute Mode                    : Default
    Utilization
        Gpu                         : 0 %
        Memory                      : 0 %
        Encoder                     : 0 %
        Decoder                     : 0 %
    Encoder Stats
        Active Sessions             : 0
        Average FPS                 : 0
        Average Latency             : 0
    FBC Stats
        Active Sessions             : 0
        Average FPS                 : 0
        Average Latency             : 0
    Ecc Mode
        Current                     : N/A
        Pending                     : N/A
    ECC Errors
        Volatile
            SRAM Correctable        : N/A
            SRAM Uncorrectable      : N/A
            DRAM Correctable        : N/A
            DRAM Uncorrectable      : N/A
        Aggregate
            SRAM Correctable        : N/A
            SRAM Uncorrectable      : N/A
            DRAM Correctable        : N/A
            DRAM Uncorrectable      : N/A
    Retired Pages
        Single Bit ECC              : N/A
        Double Bit ECC              : N/A
        Pending Page Blacklist      : N/A
    Temperature
        GPU Current Temp            : 36 C
        GPU Shutdown Temp           : 102 C
        GPU Slowdown Temp           : 97 C
        GPU Max Operating Temp      : 87 C
        Memory Current Temp         : N/A
        Memory Max Operating Temp   : N/A
    Power Readings
        Power Management            : N/A
        Power Draw                  : 13.61 W
        Power Limit                 : N/A
        Default Power Limit         : N/A
        Enforced Power Limit        : N/A
        Min Power Limit             : N/A
        Max Power Limit             : N/A
    Clocks
        Graphics                    : 1350 MHz
        SM                          : 1350 MHz
        Memory                      : 6000 MHz
        Video                       : 1245 MHz
    Applications Clocks
        Graphics                    : N/A
        Memory                      : N/A
    Default Applications Clocks
        Graphics                    : N/A
        Memory                      : N/A
    Max Clocks
        Graphics                    : 2100 MHz
        SM                          : 2100 MHz
        Memory                      : 6001 MHz
        Video                       : 1950 MHz
    Max Customer Boost Clocks
        Graphics                    : N/A
    Clock Policy
        Auto Boost                  : N/A
        Auto Boost Default          : N/A
    Processes                       : None
```

```
~$ nvidia-smi
Wed Jul 22 13:15:34 2020       
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 440.100      Driver Version: 440.100      CUDA Version: 10.2     |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  GeForce GTX 165...  Off  | 00000000:01:00.0 Off |                  N/A |
| N/A   36C    P0     3W /  N/A |      0MiB /  3911MiB |      0%      Default |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Processes:                                                       GPU Memory |
|  GPU       PID   Type   Process name                             Usage      |
|=============================================================================|
|  No running processes found                                                 |
+-----------------------------------------------------------------------------+
```

Any help greatly appreciated. Any further info required, just ask. In my research, I read one poster suggesting this problem would be taken care of in the 20.04.1 release. Perhaps it comes down to waiting until then. It is very new hardware, after all.

PS: Also, when I launch Nvidia x server settings, I get a small GUI with nothing in it and 'help' and 'quit' buttons at the bottom. That is it. No tweakable anything and no details whatsoever. Just a blank window.

Further info: While I think of it, Fast Boot and Secure Boot are disabled in BIOS and Fast Start is disabled in Win 10, for what it's worth.

---

### Post by mastablasta on 2020-07-22
Ryzen is new. i looked at 3xxx series with 1650 HP but i passed an decided in favour of cheaper one and investing in desktop later on. Does this Ryzen have a GPU chip added as well? 
For 4xxx series i would use latest kernel. these chips just came out. maybe even load a new testing kernel

Anyway strange you don't see nvidia settings. is nvidia chip actually running?

also might not be connected here, but in January we got a desktop with older model of Ryzen 7 and GTX 1650. the motherboard had output for AMD APU, though i used CPU with no GPU on it.  when i plugged in the monitor via HDMI that came, i couldn't get picture on it at all. i tested all components in desktop but it seem all worked. so i took the cable to computer store and asked them to test it. it worked. so it wasn't the cable. then i remembered i have another cable in RPi. i plugged that one in, monitor recognised, i can load the UEFI and OS. then out of curiosity i switched the cables and used the one from monitor. again everything loaded. i have no idea what that was. but still when i boot the first thing is card tries to find VGA plug, but it's not there (this is barely seen). so it switches to  HDMI and loads normally. 

i have similar issue on the old PC. The PC boots to TV (DVI) and then switches it off and turns on the VGA monitor. This happens only on nvidia card. before i had older AMD and it always treated TV as second monitor and always boot to PC monitor.

have you checked the EDID output from monitor? is it read by OS correctly? 

also sweet rig, i hope you make it work well.

---

### Post by Bucky Ball on 2020-07-22
Hi mastablasta and thanks for your comments. Yea, I'm now on Xubuntu-core 20.04 running the 5.4.0-42-generic kernel but will have a look later and see if there is a testing kernel about that has this covered.

And yes, I did try another cable, but no go. Made no difference. It wasn't the cable from my RPi, though (maybe I should try that for good luck!). But it was from a laptop connected to the TV which is definitely working.

> ... have you checked the EDID output from monitor? is it read by OS correctly?

I have no idea how to do this, but will look into it a bit later.

Yes, the Ryzen CPU has a GPU on it and perhaps that is causing some issue(s). I have the nvidia-driver-440 installed. I look for a command that lets me see screens/monitors.

> ... also sweet rig, i hope you make it work well.

I'm hoping that, too! It is lightning fast. Took me about three weeks to settle on something. It is primarily to be used for audio production stuff on the move in Win, so the processor should be perfect for that. But when it's not being used for that, I must have Xubuntu-core on my laptop or life's not worth living! I don't use Win for anything other than audio production (and occasionally a bit of vid). 

Will try some things out later, but for now, to the dishes! Thanks again. Any further thoughts, pitch 'em in.

---

### Post by webaake on 2020-07-22
Some BIOS have a setting for choosing "GPU primary Card". Might be worth checking into.

I can see no reason for your mobo/CPU setup to NOT work with that kernel and that Nvidia driver.

PS. Did you check the settings  "Screen & Displays" (or whatever it's called in your language)?

---

### Post by Bucky Ball on 2020-07-22
Hi webaake.

> **webaake said:**
> Some BIOS have a setting for choosing "GPU primary Card". Might be worth checking into.

Oddly, there is no sign of the Nvidia GPU in the BIOS anywhere, nor can I find anything to do with 'GPU primary card'. Despite this, Ubuntu sees the GPU, installs a driver for it, and Windows has no issue with the screen at all. 

> **webaake said:**
> PS. Did you check the settings  "Screen & Displays" (or whatever it's called in your language)?

It's just 'Display' in Xubuntu, and no sign of the external monitor there. The system just doesn't see it. I had a look using arandr as well. Nothing. All that seems to be picked up is the laptop screen.

It's like the external monitor is in suspend and when I boot Ubuntu, it stays in suspend. Doesn't wake up. The blue light's blinking, but nothing on screen. Monitor set to HDMI, nvidia driver installed, everything looks like it should be working fine to my fairly uneducated eye.

Update: Yea, seems like the laptop is 'seeing' the external monitor, just not waking it up. When I pull the HDMI cable out of the laptop, the monitor flashes then gives me the message that the HDMI cable is disconnected. Plug it back in again, the monitor's blue light starts flashing, but the monitor just doesn't wake.

---

### Post by Yellow Pasque on 2020-07-22
Try 450.57. It had some PRIME/Reverse PRIME improvements
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)

EDIT: Changelog referencek: [https://www.nvidia.com/download/driverResults.aspx/162107/en-us](https://www.nvidia.com/download/driverResults.aspx/162107/en-us)

---

### Post by mastablasta on 2020-07-22
> **Bucky Ball said:**
> 
PS: Also, when I launch Nvidia x server settings, I get a small GUI with nothing in it and 'help' and 'quit' buttons at the bottom. That is it. No tweakable anything and no details whatsoever. Just a blank window.


well this is interesting. i just got this as well after upgrading the kernel. nvidia settings with nothing inside in a small box. but the resolution was off as wlel. i started panicking, but hen i went to see if i can remove drivers. and the drivers manager (Kubuntu) showed i am using 4.35 :O. so i switched to recommended 4.40 and rebooted. suddenly nvidia settings appeared, card recognised etc.

it looks like this happens when you have drivers installed but system doesn't actually see the card or knows how to use it. i am not sure why 4.35 (or whatever it was) were defaulted to as i think you need 4.40 for this chip. and i don't remember ever installing lower version (this PC is on 18.04).


so i remembered this post and i am thinking could it all really be nvidia drivers issue?

also why don't they label these MGTX or something (like MX). they have dedicated RAM, but are they really the same chip? i mean the GTX 1650 on desktop are really big (well let's say medium) cards with plenty or large fans and strong cooling.

----

by the way mobile Ryzen 3xxx series doesn't know how to propperly assign memory (on Kernel 5.4). Issue is supposedly fixed on 5.5 and 5.6 has further power management & fan improvements. I had to boot with kernel switch iommu=soft

some (like mine) wouldn't boot on battery: [https://ubuntuforums.org/showthread.php?t=2446942](https://ubuntuforums.org/showthread.php?t=2446942)
I posted bug on launchpad after seeing many users face this issue and it is hard to find it as it manifests in different ways. A dev made a patched kernel. unfortunatelly i can't try it since it is not actually my laptops and has to remain operational (at leats until end of school holidays :) ) hmm is there a way to try this in live session?

others (like forum member KayaE on Lenovo) could boot, but not always: [https://ubuntuforums.org/showthread.php?t=2447538&p=13974304#post13974304](https://ubuntuforums.org/showthread.php?t=2447538&p=13974304#post13974304)

---

### Post by Bucky Ball on 2020-07-22
Bingo! (Not that I've ever played bingo, but the declaration seems appropriate!)

Installing the 5.6 kernel did it. Rebooted after that and up came the external monitor. Thanks for the tip, mastablasta. The kernel was from here

[https://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D](https://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D)

... and I followed the instructions to install here

[https://itsfoss.com/upgrade-linux-kernel-ubuntu/#install-manually](https://itsfoss.com/upgrade-linux-kernel-ubuntu/#install-manually)

I am now on kernel 5.6.0-050600-lowlatency (low latency for audio stuff as I'll be running [Bitwig]("https://www.bitwig.com/en/home.html") on this machine in both Ubuntu and Win) and everything is now as it should be, except ... Nvidia X Server Settings still a little empty box. I am happy to now try Yellow Pasque's suggestion of installing the 450.57 nvidia-driver and see if that fixes. Not sure how to go about that, though. (I had a look in 'Additional Drivers' to see if the 450 driver was now available with the new kernel, but no.)

Yellow Pasque, would I just install the repo you've suggested and then search for and install the 450.57 driver from Synaptics? Do I need to uninstall the 440 driver first?

Thanks all for all your input. Throwing down bread crumbs gives me a trail to follow and 99% of the time, things get fixed. You know what they say; five heads are better than one! ;)

* Update: spoke too soon. When I close the laptop lid, the external monitor doesn't switch off. Just flashes black for less than a second when I close the lid then reappears again. When I open the lid, the external monitor flashes again, the laptop screen comes up, but the laptop screen now flashes black every second or two. If I then open 'Display', change the laptop screen resolution from 144hz to 60, the flashing on the laptop screen stops. Change back to 144hz, flashing still stopped. Odd. I'll keep digging into this issue later, but this might be the stuff of another thread. 

I'm purely an LTS man and haven't used a release that's less than six months old since I first installed Ubuntu 7.something way back. Using such a new kernel is all new to me as I'm used to stable, but as the hardware's so new and so is the kernel, not surprising there are a few glitches and looks like this is how it's going to be for awhile. All good. ;)

---

### Post by Bucky Ball on 2020-07-23
Just another update on this and perhaps a clue as to why the Nvidia X Settings dialogue is not showing correctly. I notice this.

```
~$ nvidia-smi
Thu Jul 23 15:38:34 2020       
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 440.100      Driver Version: 440.100      CUDA Version: 10.2     |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  GeForce GTX 165...  Off  | 00000000:01:00.0 Off |                  N/A |
| N/A   36C    P0     3W /  N/A |      0MiB /  3911MiB |      0%      Default |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Processes:                                                       GPU Memory |
|  GPU       PID   Type   Process name                             Usage      |
|=============================================================================|
|  No running processes found                                                 |
+-----------------------------------------------------------------------------+
```

No processes found, which means the 5.6 kernel fixed the HDMI output (which the changelog linked to earlier by Yellow Pasque hinted it might) and it is being used by the AMD Radeon GPU on the CPU, not the Nvidia. Which means that the problem outlined in the thread title is half solved: I have HDMI output, but not from the GTX 1650 ti. While the Nvidia driver-440 is installed, the system is not utilising it. Ideally, I would like the dedicated GPU to be dedicated to handling all the graphics and not be using the internal GPU at all, if that is possible.

Perhaps installing the nvidia-driver-450 will fix this, perhaps it is Xubuntu 20.04 and the kernel not being up to handling the situation at this point that is causing the issue. Both screens are being problematic. They keep going to sleep if I leave them for about ten minutes, even though I have Power Manager set to not handle the displays! I had them set to 'never' switch off prior to that and no go. I will keep updating/upgrading and pottering with it.

The other thing to remember is that this is Xubuntu-core 20.04 freshly install. The -core version is very barebones and you need to install things as you go (and as it comes up). The end result is fairly organic, but just how I like it. No fluff! What I'm saying is that it could be something missing that would be there with a full install of Xubuntu that is the issue.

* One question. Looking at 'Install the Latest Nvidia Driver' at this page.

[https://www.maketecheasier.com/install-nvidia-drivers-ubuntu/](https://www.maketecheasier.com/install-nvidia-drivers-ubuntu/)

Should I purge the nvidia-driver-440 before trying this or will installing the 450 driver this way take care of that?

---

### Post by mastablasta on 2020-07-23
purge would be better, just in case there are some "old settings" that could interfere with new version.

yes, on core sometimes things that are needed are missing (have to be added). i once did this in VM and was adding stuff i needed for some time. end result was ligther, but as i remember it needed quite a few installs.

---

### Post by Bucky Ball on 2020-07-23
[QUOTE=mastablasta]purge would be better, just in case there are some "old settings" that could interfere with new version.[/QUOTE]

I followed 'Upgrading Your Nvidia Driver' from here ...

[https://www.maketecheasier.com/install-nvidia-drivers-ubuntu/](https://www.maketecheasier.com/install-nvidia-drivers-ubuntu/)

... and, as it happens, when you install the new driver, it takes care of uninstalling the old one. (I could see it doing away with nvidia-driver-440 in the terminal during the 450 install.) Neat.

I installed the nvidia-driver-450 and Nvidia X Server Settings now works (although it's not showing much and there's virtually nothing tweakable) and it looks like the card is working, too. At least there's a process happening whereas there wasn't one showing previously. 

```
:~$ nvidia-smi
Fri Jul 24 02:01:07 2020       
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 450.57       Driver Version: 450.57       CUDA Version: 11.0     |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|                               |                      |               MIG M. |
|===============================+======================+======================|
|   0  GeForce GTX 165...  Off  | 00000000:01:00.0 Off |                  N/A |
| N/A   39C    P8     1W /  N/A |      6MiB /  3911MiB |      0%      Default |
|                               |                      |                  N/A |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Processes:                                                                  |
|  GPU   GI   CI        PID   Type   Process name                  GPU Memory |
|        ID   ID                                                   Usage      |
|=============================================================================|
|    0   N/A  N/A       982      G   /usr/lib/xorg/Xorg                  4MiB |
+-----------------------------------------------------------------------------+
```

I don't really understand what the process is doing, but from the notes on the new driver, it seems the 450 plays better with xorg than the previous. (There is a good article on that driver [here]("https://9to5linux.com/nvidia-450-57-linux-graphics-driver-improves-support-for-vulkan-apps-adds-new-features")). Despite the process showing, I still have this ...

```
:~$ nvidia-smi --query

==============NVSMI LOG==============

Timestamp                                 : Fri Jul 24 02:17:17 2020
Driver Version                            : 450.57
CUDA Version                              : 11.0

Attached GPUs                             : 1
GPU 00000000:01:00.0
    Product Name                          : GeForce GTX 1650 Ti
    Product Brand                         : GeForce
    Display Mode                          : Disabled
    Display Active                        : Disabled
    Persistence Mode                      : Disabled
    MIG Mode
        Current                           : N/A
        Pending                           : N/A
    Accounting Mode                       : Disabled
    Accounting Mode Buffer Size           : 4000
    Driver Model
        Current                           : N/A
        Pending                           : N/A
    Serial Number                         : N/A
    GPU UUID                              : GPU-478032cf-a2ee-befc-da9d-96964836c5c4
    Minor Number                          : 0
    VBIOS Version                         : 90.17.42.00.21
    MultiGPU Board                        : No
    Board ID                              : 0x100
    GPU Part Number                       : N/A
    Inforom Version
        Image Version                     : G001.0000.02.04
        OEM Object                        : 1.1
        ECC Object                        : N/A
        Power Management Object           : N/A
    GPU Operation Mode
        Current                           : N/A
        Pending                           : N/A
    GPU Virtualization Mode
        Virtualization Mode               : None
        Host VGPU Mode                    : N/A
    IBMNPU
        Relaxed Ordering Mode             : N/A
```

There is more, but you get the idea from 'Display mode: disabled' and 'Display Active: disabled', etc.
 
* I just played a video in Youtube and ran nvidia-smi in a terminal while I was doing it and the output is exactly the same as the output posted above. So I still don't think it's using the card for vid, although I've moved forward a step. There is a process running now at least, whatever it is.

---

### Post by Bucky Ball on 2020-07-24
Quick update. I was in Win 10 and noticed that that is using the Nvidia 451.** driver (can't remember the numbers after the period). Maybe when that pops into Linux things might go more smoothly. But ... in my meanderings I figured something that is possibly obvious if you know what you're doing and know about graphics. Perhaps what's required is to open Nvidia X Server Settings, select 'nvidia-settings Configuration' and 'Save Current Configuration' then tweak the file it creates (.nvidia-settings-rc) until I crack the code to get the Nvidia card as the default and the HDMI output handed over to it. Make sense?

Not that I would have any idea how to tweak that file once created. 

I tried the answer marked '1' from here to try to get the Nvidia card to handle the HDMI.

[https://askubuntu.com/questions/787030/setting-the-default-gpu](https://askubuntu.com/questions/787030/setting-the-default-gpu)

It didn't go well. I made sure to use the correct BusID number for my card, but when I restarted I was greeted with a blank screen with a blinking cursor top left. Restarted to recovery mode, dropped to root shell, edited the file and took out the line with the BusID number, rebooted. Black screen with cursor. Reboot, recovery, root shell, delete  file completely, reboot. Everything working again. 

On a side note, I fixed the suspend issue (external monitor staying on when laptop screen closed) with this.

[https://itsfoss.com/ubuntu-close-lid-suspend/](https://itsfoss.com/ubuntu-close-lid-suspend/)

Any further thoughts on getting the Nvidia card to be the default and take care of the HDMI are welcome and appreciated. While I have HDMI output, pretty sure it isn't coming from the Nvidia card as Nvidia X Server Settings is not showing much action and neither is anything else. As I mentioned earlier, perhaps the working driver/kernel combination to make this work is still in the future.

* Further info: Just had a look in /var/log/Xorg.0.log and I see that there is a ton of information regarding the 'AMDGPU' but next to nothing about the 'Nvidia' GPU because in every instance, it shows as 'disconnected'. There is also evidence in there that the AMD GPU *is* handling the HDMI. So, the Nvidia driver is there, the card is there, no errors showing, but no-one home.

---

### Post by ubfan1 on 2020-07-24
Check frequently for any  firmware updates offered by the vendor too.  New machines typically get a few quick updates to fix problems.

---

### Post by Bucky Ball on 2020-07-25
Thanks ubfan1. Just had a check in Windows then and nothing forthcoming. 

Just an update on where I'm at with things. Have a look at the pic of the Nvidia X Server Settings GUI here under 'Configure Nvidia graphics driver'.

[https://codepre.com/how-to-install-nvidia-driver-on-ubuntu-20-04.html](https://codepre.com/how-to-install-nvidia-driver-on-ubuntu-20-04.html)

In comparison, my options column on the left is missing everything before, in my case, 'GPU 0 - (GeForce GTX 1650 Ti)'. I have no options for Xserver information, X server Display Configuration, X screen 0; none of the options above 'GPU 0'. My options in the left hand column start with 'GPU 0 - (GeForce GTX 1650 Ti)'.

Underneath 'GPU 0 - (GeForce GTX 1650 Ti)' my options are the same as the one at the link above apart from I am missing the 'PRIME profiles' option in the left column. Strange, because I get this in a terminal.

```
~$ sudo prime-select query
nvidia
```

But when I launch 'sudo nvidia-settings' it tells me ...

```
** Message: 00:54:35.204: PRIME: No offloading required. Abort
** Message: 00:54:35.204: PRIME: is it supported? no
```

Prime is not supported? Odd that I can use Prime commands in the terminal and they seem to work. Even this.

```
:~$ sudo prime-select nvidia
Info: the nvidia profile is already set
```

Confused. When 20.04.1 drops on August 6th, maybe I'll get further along the trail with this.

---

### Post by MarvinVzla on 2020-07-25
I have the same issue as you, I have a omen R7 with the same 1650 ti, reading this post It's have been my same path, I also have no control over the brightness on the laptop screen, does you brigtness works fine?,If you have done anything please share it, the screen is leaving me blind,  when I conect another screen it shows on the x server, but there is no way to activated

---

### Post by Bucky Ball on 2020-07-25
Hi Marvin. When you say you have the same problem as me, you mean you have the 1650 ti and you are getting no HDMI output from it? If not, would be better to post a new thread with a title that reflects your issue specifically. If your issue is primarily about the brightness issue (which isn't related to this thread) or the blank screen, you'll get better help on a new thread specifically about that. ;)

Everything I've done is documented on this thread. In a nutshell, install Ubuntu (or whatever flavour you're using) 20.04, make sure you are using the 5.6 kernel ([find it here]("https://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D")) or higher and the latest Nvidia driver (nvidia-driver-450 which you'll need to [install by following this]("https://www.maketecheasier.com/install-nvidia-drivers-ubuntu/")). Install kernel first, Nvidia driver second. That combination fixed some things for me, but not everything. I am now on the 5.7 kernel to see if that gets me any further, but things are exactly the same as they were on 5.6. And that's where I'm up to.

I have no idea whether screen brightness is working or not on my machine. I'm using a reasonably fresh and basic [Xubuntu-core 20.04]("https://xubuntu.org/news/introducing-xubuntu-core/") and have no screen brightness adjuster installed that I can find. You could try adjusting the brightness on the monitor itself, if you are using an external monitor that is.

Try installing the kernel and driver and see if that solves your issue. (If you can't get to a desktop, at the grub screen where you select what to boot, select the 'Advanced' options then the 'recovery' option. There, choose the first option to continue. This might get you to a desktop where you will be able to get online and install the kernel and driver. Then reboot normally and see what happens.)

---

### Post by mastablasta on 2020-07-26
looks like you are close. first the two GPU need to work, then you sort out the switching.

have a look here for similar situation but older Ryzen chip: [https://forums.developer.nvidia.com/t/amd-ryzen-7-integrated-gpu-nvidia-1650-in-same-linux-machine-cause-xorg-to-default-to-outdated-drivers/76183](https://forums.developer.nvidia.com/t/amd-ryzen-7-integrated-gpu-nvidia-1650-in-same-linux-machine-cause-xorg-to-default-to-outdated-drivers/76183)

The person that posted this is on Suse, but Ubuntu/Mint solution is mentioned in the link. as i understand you would need to also setup or fix the xorg.conf file.

and if suggested solution doesn't work post nvidia bug report there in new thread. they might be able to help as i suspect that now Optimus/Prime switching is the issue. hopefully there is support for amdgpu/nvidia switching implemented at least to some extent.

---

### Post by Bucky Ball on 2020-07-26
Thanks for the further info, mastablasta. After following a piece of string starting with your link, I tried this from [here]("https://forums.developer.nvidia.com/t/amd-ryzen-5-mobile-nvidia-gtx-1050-login-loop-ubuntu-18-04/74821/18").

>  ... modify /usr/share/X11/xorg.conf.d/10-amdgpu.conf
replacing only

Driver "amdgpu"

with

Driver "modesetting"

then reboot.

Reboot and all looks good, but no change in Nvidia X Server Settings and no signs of life. So I try the next step on the link.

> Please add

Option "PrimaryGPU" "Yes"

inside the OutputClass of /usr/share/X11/xorg.conf.d/10-nvidia.conf

Not so good. Chose Ubuntu at grub, boots to completely black screen, no blinking cursor, nothing. Into recovery mode and delete the 'Option "PrimaryGPU" "Yes"' line from /usr/share/X11/xorg.conf.d/10-nvidia.conf. Reboot normally and all good again.

So, currently running with the 'Driver "modesetting"' change in /usr/share/X11/xorg.conf.d/10-amdgpu.conf without issue. I can see no difference. AMD GPU still seems to be handling the HDMI and screen still flickers when I open the laptop lid and the machine wakes. Oddly, it didn't do that once this afternoon. Once.

I'll keep digging.

* Just opened the laptop to switch the machine off and ... no laptop screen flicker. Go figure.

---

### Post by Bucky Ball on 2020-08-09
Hi all. Just an update. Haven't forgotten about this thread. Haven't marked solved as, technically, it's not. Still not getting any HDMI out of the Nvidia card even though the card is recognised and the 450 nvidia driver is installed. 

I have my fingers crossed the 20.04.1 point release may help me along as that has some Nvidia server stuff in it, but so far, that point release hasn't come down the line for me. I'll repost any progress once I have that installed and have had a look. So in the meantime, I'll leave this open for now as posting a resolution, if it arrives, may help others. 

Cheers.

* Further update: Now have 20.04.1 and no change. Will leave thread open in case anyone has any further ideas or I figure it out and can post a solution for others. I'll keep trying.

---

### Post by MarvinVzla on 2020-08-29
I haven't also, I am in the same situation as you are

---

### Post by MarvinVzla on 2020-12-25
I do not know if you have found a solution, but I did get help you can see it here [https://forums.developer.nvidia.com/t/no-hdmi-output/164573/8](https://forums.developer.nvidia.com/t/no-hdmi-output/164573/8)

---

