---
title: "Ati radeon problem - disable integrated card"
date: 2013-12-27
forum: Hardware
---

### Post by monkeyPlanet on 2013-12-27
Hi,
I moved from Windows to Kubuntu and my system cant detect the Radeon I have.Its a hybrid system so only the Intel card is detected and not the radeon.

```
lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 09)

```

I cant disable the integrated from my BIOS and wud like have only Radeon. I have tried amd website driver, the jockey driver and also I think the open source radeon.

Cant really say if its working or wants to work as I have always booted with the integrated card and dont know to disable it.

All help appreciated.

---

### Post by monkeyPlanet on 2013-12-28
So am I stuck with the integrated card or is there a way.:(

---

### Post by QIII on 2013-12-28
Hello!

You don't mention which version you are using, but if you are using 13.10, you may be in luck.

Uninstall any proprietary driver you have installed and have a look [here]("https://wiki.ubuntu.com/X/Config/HybridGraphics").

Also install fglrx-amdcccle.  You'll need to use the Catalyst Control Center to switch back and forth between integrated and dedicated graphics.

Cheers.

---

### Post by monkeyPlanet on 2013-12-28
Thanks for the reply.
I tried 13.10 and got only a black screen after the kubuntu logo. So I moved to 12.04.
I will try out the solution you  have suggested.

---

### Post by monkeyPlanet on 2013-12-28
Right, I tried doing whats there on the link, jockey-kde shows driver installed.But I cant turn opengl or the AMDcatalyst centre.
Might move to LinuxMint and see if it deals with things differently.

---

### Post by monkeyPlanet on 2013-12-29
Heres the output of   lshw -C display

*-display               
       description: VGA compatible controller
       product: Haswell-ULT Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:62 memory:c0000000-c03fffff memory:b0000000-bfffffff ioport:5000(size=64)
  *-display
       description: Display controller
       product: Sun XT [Radeon HD 8670A/8670M/8690M]
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:16 memory:a0000000-afffffff memory:c0500000-c053ffff ioport:3000(size=256) memory:c0540000-c055ffff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.


So is there no way to disable the intel card just keep the radeon.

---

### Post by Mark Phelps on 2013-12-29
Switchable graphics like these pose serious problems in Linux as the video card manufacturers don't make Linux drivers for them -- leaving us to "hack" around for solutions.  Read through the linked thread to see if anything there helps: [http://askubuntu.com/questions/205112/how-do-i-get-amd-intel-hybrid-graphics-drivers-to-work/288355#288355]("http://askubuntu.com/questions/205112/how-do-i-get-amd-intel-hybrid-graphics-drivers-to-work/288355#288355")

---

### Post by monkeyPlanet on 2013-12-31
I tried that link, very useful , but I am getting  
aticonfig: No supported adapters detected
The open source driver doesnt support 8x cards and the above tutorial doesnt go further cuz of aticonfig error.
This is not going to be as easy as nvidia is it.:D

---

### Post by QIII on 2013-12-31
Intel/Nvidia hybrids are no better.

---

### Post by monkeyPlanet on 2013-12-31
I am leaving it as it for now, did too many installs of ubuntu and nothing seems to work. Fglrx seems to be necessary for video playback so I have fglrx-updates installed for now. If I try to install anything from jockey, it says this driver is activated but not in use right now. So I dont get all the Desktop Effects, no openGL,etc. Dont know if something like Blender will take advantage of the Radeon card at all.

So thanks for the help but it seems there is no straight way to get hybrids working right now.

---

