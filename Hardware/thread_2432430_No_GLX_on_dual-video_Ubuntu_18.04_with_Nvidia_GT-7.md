---
title: "No GLX on dual-video Ubuntu 18.04 with Nvidia GT-730"
date: 2019-12-02
forum: Hardware
---

### Post by utahul1 on 2019-12-02
I've got an older System76 Jackal Pro that I essentially inherited -- one that has seen almost no use -- and I'm trying to repurpose it as a dedicated OBS Studio box. I've done this before on other systems and my setup and/or workflow work pretty well. I've never done it with this hardware vendor + configuration, however.

The machine has dual video cards. There's the built-in Matrox video card that comes with the system, and then there's a Nvidia GeForce GT 730 (a never-before used one I already had on hand for accelerating OBS). I've got Ubuntu 18.04 installed, and I have the proprietary Nvidia drivers installed via the Software & Updates (Additional Drivers) tool (e.g. nvidia-driver-435). 

Here are some details:

(1) One, I have both video cards attached to the same monitor (VGA to Matrox card, DVI to Nvidia card). Both cards are enabled in the BIOS. The monitor works with the VGA (Matrox) but gets no signal from the DVI (Nvidia). 

(2) The glxgears utility runs as expected. No surprises there.

(3) Three, glxinfo reports that my OpenGL vendor is "VMware, Inc.' and that my OpenGL renderer is "llvmpipe". Tell me if I'm wrong, but that indicates to me that its using software rendering and not utilizing the Nvidia card at all.

(4) The nvidia-settings tool will open, but there are no listed GPUs. 

(5) The 'lshw -C video' command lists both video cards -- "GK20BB [GeForce GT 730" and "MGA G200e [Pilot] ServerEngines (SEP1)". The Nvidia is shown as running the 'nvidia' driver. The only problematic message I see from dmesg is "EDAC sbridge: Failed to register device with error -19"

(6) If I run 'lsmod | grep nvidia' I see nvidia_uvm, nvidia_drm, nvidia_modeset and nvidia all running

(7) I have added nomodeset to GRUB as a kernel parameter and that didn't seem to make any difference.

(8) I have libgl1-mesa-glx, libglx-mesa0, libglx0 and libxcb packages installed.

(9) The gpu-manager.log file reports "Skipping '/dev/dri/card0', driven by 'nvidia-drm'

Any advice on how I can get this Nvidia card working so I can offload video rendering in OBS Studio to the GPU?

---

