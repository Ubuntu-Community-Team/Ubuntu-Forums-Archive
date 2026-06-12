---
title: "Laptop Overheating"
date: 2012-06-02
forum: Hardware
---

### Post by caffeinatedev on 2012-06-02
I'm having issues of my HP G60 experiencing overheating whilst using Ubuntu Precise. I know that it's not a hardware problem because on Windows Vista the laptop operates at an acceptable temperature.

Is there any tweaking that can be done on my part to resolve this? Thanks , happy Linuxing!

---

### Post by Photon89 on 2012-06-03
What hardware does the laptop have? What video driver are you using?

---

### Post by N0oki3 on 2012-06-06
update bios (again, you need windows) and yes...which drivers do you use

---

### Post by caffeinatedev on 2012-06-12
@Photon89: I am using an HP G60-120us and I believe I'm using the proprietary Nvidia driver unless I'm mistaken. How would I check that which drivers I'm using?

@N0oki3 Could you elaborate as to how my current BIOS effects anything? It's the latest firmware from my manufacturer.

Sorry that I took so long to respond, I've been without internet for a while. :-/

---

### Post by itagomo on 2012-06-26
try making your /etc/default/grub:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_aspm=force i915.i915_enable_rc6=1"

got it from here:
[http://www.omgubuntu.co.uk/2011/11/linux-power-regression-overheating-problem-on-thinkpad-fixed](http://www.omgubuntu.co.uk/2011/11/linux-power-regression-overheating-problem-on-thinkpad-fixed)

after reading a lot of posts, i've found out that the kernel has it's problems with some or other hardwares .. even 3.2 update didn't fix it ..

---

### Post by itagomo on 2012-06-26
try making your /etc/default/grub:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_aspm=force i915.i915_enable_rc6=1"

then 'update-grub' from terminal ..

got it from here:
[http://www.omgubuntu.co.uk/2011/11/linux-power-regression-overheating-problem-on-thinkpad-fixed](http://www.omgubuntu.co.uk/2011/11/linux-power-regression-overheating-problem-on-thinkpad-fixed)

after reading a lot of posts, i've found out that the kernel has it's problems with some or other hardwares .. even 3.2 update didn't fix it ..

some useful stuff here:
[http://pastebin.com/BTXKvp6B](http://pastebin.com/BTXKvp6B)

---

### Post by caffeinatedev on 2012-07-02
Thanks for the info @itagomo. That OMG Ubuntu article's grammar made my brain sad. After reviewing the pastebin data, are you sure that would work for my machine? Here's my PC specs for clarification: [http://pastebin.com/dtFFybvv](http://pastebin.com/dtFFybvv)

Thanks for your help guys, I truly appreciate it!

---

### Post by typhoon_tip on 2012-07-02
Have you installed NVidia proprietary video driver or you are simply using the one that comes after install ? To be better detailed, from Unity Dash open "Additional Drivers", and see if anything is "green" there (activated). If nothing appears, then run this command:
```
lspci
```

... and post entire output here.

---

### Post by caffeinatedev on 2012-07-02
@typhoon_tip I've been using a Nvidia Proprietary Driver since the first of my install. Here's my output:
```
00:01.0 ISA bridge: NVIDIA Corporation Device 075e (rev a2)
00:01.1 SMBus: NVIDIA Corporation MCP78S [GeForce 8200] SMBus (rev a1)
00:01.3 Co-processor: NVIDIA Corporation MCP78S [GeForce 8200] Co-Processor (rev a2)
00:01.4 RAM memory: NVIDIA Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:02.0 USB controller: NVIDIA Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:02.1 USB controller: NVIDIA Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:04.0 USB controller: NVIDIA Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:04.1 USB controller: NVIDIA Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:06.0 IDE interface: NVIDIA Corporation MCP78S [GeForce 8200] IDE (rev a1)
00:07.0 Audio device: NVIDIA Corporation MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio (rev a1)
00:08.0 PCI bridge: NVIDIA Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:09.0 IDE interface: NVIDIA Corporation MCP78S [GeForce 8200] SATA Controller (non-AHCI mode) (rev a2)
00:0a.0 Ethernet controller: NVIDIA Corporation MCP77 Ethernet (rev a2)
00:0b.0 PCI bridge: NVIDIA Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:14.0 PCI bridge: NVIDIA Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Link Control
02:00.0 VGA compatible controller: NVIDIA Corporation C77 [GeForce 8200M G] (rev a2)
07:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)

```

---

### Post by typhoon_tip on 2012-07-02
Can you post the content of the XORG file here, use this command:
```
sudo cat /etc/X11/xorg.conf
```

So we are 100% sure of what driver is in use. Moreover, what processor do you have ?

---

### Post by caffeinatedev on 2012-07-04
```
Section "Device"
	Identifier	"Default Device"
	Option	"NoLogo"	"True"
EndSection


```

2.00 GHz dual-core AMD processor

---

### Post by typhoon_tip on 2012-07-05
> **caffeinatedev said:**
> ```
Section "Device"
	Identifier	"Default Device"
	Option	"NoLogo"	"True"
EndSection


```

2.00 GHz dual-core AMD processor

You are definitely not using NVIDIA driver, even if is installed, that file looks wrong to me (it should contain many more references).

Can you open Nvidia Control Panel from the Unity Dash ? It should give you an error that it cannot find the adapter.

---

### Post by msammels on 2012-07-05
And if it doesn't, you can close the control panel, open a terminal and type:

```
sudo nvidia-xconfig
```

To generate a new configuration.

---

### Post by typhoon_tip on 2012-07-05
> **msammels said:**
> And if it doesn't, you can close the control panel, open a terminal and type:

```
sudo nvidia-xconfig
```

To generate a new configuration.

Lolll was googling for the command, which I forgot.

adding: _before restart the system_, post the output of the new xorg.conf file (or any error that nvidia-xconfig would eventually return).

---

### Post by msammels on 2012-07-05
Haha typhoon, it's no problems.

But yes, please do post the output of new config, before you reboot, in case something is overwritten.

---

### Post by caffeinatedev on 2012-07-05
> **msammels said:**
> And if it doesn't, you can close the control panel, open a terminal and type:

```
sudo nvidia-xconfig
```

To generate a new configuration.

I was able to open the control panel but I'm not to sure what you want me to do with that :)

Here's my output from the terminal:

```
Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Default Device" must have a Driver line.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'
```

---

### Post by typhoon_tip on 2012-07-07
Post your new xorg.conf file ! And also, after rebooting, does the computer start ? How's the temperature... ?

---

### Post by caffeinatedev on 2012-07-07
> **typhoon_tip said:**
> Post your new xorg.conf file ! And also, after rebooting, does the computer start ? How's the temperature... ?

Here's the output for the xorg.config file ```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 295.40  (buildmeister@swio-display-x86-rhel47-04.nvidia.com)  Thu Apr  5 22:33:07 PDT 2012


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


```
The laptop boots up normally, except there's now a split second where a Nvidia splash screen appears. I don't know how to check my temperature but it seems a bit cooler from as far as being idle.

---

### Post by 23senick on 2012-07-08
Psensor works for me as a way of monitoring temperatures.  

You could try the Jupiter applet and choose "power saving" mode from performance.  

My laptop (HP dm1) is prone to high temperatures but this seems to have improved with updates to 12.04. Jupiter gained me 2-3 degrees and temp is similar to Windows (tho may tend to be a little higher)

---

### Post by caffeinatedev on 2012-07-08
I installed PSensor and my GPU averages at around 70C....I don't know if that's normal for my laptop but it does seem a lot cooler to the touch.

Any ideas as to how I would get rid of the Nvidia splash screen?

---

### Post by 23senick on 2012-07-08
sorry, no. But another thought - it seemed to help temperature when I moved to proprietary driver for graphics - have you checked if any are available for your machine?

---

### Post by caffeinatedev on 2012-07-08
Ever since I switched to the proprietary drivers, I have been suffering desktop environment stability issues, particularly whenever I open the Unity Dash; I can't open terminal and the console is virtually non-functioning. How do I switch back to the open-source drivers or better yet, check to see if the Nvidia drivers are the problem?

---

### Post by typhoon_tip on 2012-07-09
There is a temperature monitor in NVIDIA configuration application (accessible from DASH).

It is possible that Unity messed up with your previous, broken setup of the driver. Give it a round of reset won't hurt, before tweaking driver install, try this:
```
unity --reset
```

---

### Post by caffeinatedev on 2012-07-11
I ended up reinstalling the Nvidia drivers and I don't have any more graphical problems. I sure do wish I could get rid of that ugly Nvidia splash screen though. :confused:

---

### Post by typhoon_tip on 2012-07-12
[www.google.com](www.google.com)

"nvidia get rid of splash screen"

Search, _first result_:
[ubuntu] disable nvidia splash screen - Ubuntu Forums

[http://ubuntuforums.org/showthread.php?t=918705](http://ubuntuforums.org/showthread.php?t=918705)

:popcorn:

---

### Post by caffeinatedev on 2012-07-12
Basically when in doubt, "Google it". Although I prefer to "Duck Duck Go it" ;)

---

### Post by americanman28 on 2012-07-12
Also try cleaning the computer

---

