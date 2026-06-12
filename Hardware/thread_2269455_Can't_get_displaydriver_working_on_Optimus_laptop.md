---
title: "Can't get display/driver working on Optimus laptop"
date: 2015-03-15
forum: Hardware
---

### Post by Isuru_Daulagala on 2015-03-15
[COLOR=#333333][FONT=UbuntuRegular]I have an acer aspire V5-573G which comes with a NVIDIA OPTIMUS chipset and 750M gfx card. I have a fairly fresh install of 14.04 and I have tried a number of things to install driver and CUDA. In the end nothing seems to work. I will give you a list of things I have done[/FONT][/COLOR]

[LIST=1]
[*]Install open source nvidia-340 driver which comes with prime. Then install CUDA toolkit without NVIDIA's proprietary driver. This works fine for once until you logout/restart. Anytime you switch to your NVIDIA card of prime, display goes black. I have tried a few things :
i. Comment our the gpu-manager.conf file and make the intel gfx card modsetting. Make xorg.conf not wrieable through chattr. This still gives me a black screen.This method is outlined [here]("http://vxlabs.com/2015/02/05/solving-the-ubuntu-14-04-nvidia-346-nvidia-prime-black-screen-issue/").
ii. Try to install the driver that comes with the CUDA toolkit.  I could install the driver and toolkit. CUDA works on tty. But as soon as I start lightdm, everything is blank

[*]Install bumblbee. Installing bumblebee with the driver and then purging prime led to the NVIDIA gfx card working with optirun of glxspheres64. But CUDA doesn't work. Whenever I run sudo optirun ./deviceQuery it gives me an error and tells me that nvidia-uvm isn't found
This led me to believe I don't have the nvidia-340-uvm kernel module. So I used modeprobe to add it to the kernel and it says could not insert nvidia_340_uvm: No such device
[/LIST]
[COLOR=#333333][FONT=UbuntuRegular]This means I don't have 'nvidia'-340-uvm' right? WRONG. I try to install it via synaptic and it's already there part of the 340 probably part of the 340 driver.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]
[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Right now I  have the opensource nvidia 331-updates driver and CUDA 6. I still can't get the display working with the driver. But I can still run CUDA on tty and generate images for my project and then switch to the intel card. This seems to be a painful process, so I'm in need of help[/FONT][/COLOR]

---

