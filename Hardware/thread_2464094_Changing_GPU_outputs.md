---
title: "Changing GPU outputs?"
date: 2021-06-24
forum: Hardware
---

### Post by almostmatt1 on 2021-06-24
Hello, first post. Sorry if I don't articulate my question correctly, I'll try my best. 

The tldr version is: I have two graphics cards each occupying one slot, and I am looking for a way to manually choose which GPU is the video output device. 

My situation: I have two GPU's, an Nvidia 1060 and 3060ti. My goal is to run Windows 10 in a virtual machine exclusively for gaming purposes (I am aware of proton for Steam and other Linux gaming options, I have decided to go with a Win10 VM instead) and pass through the 3060ti GPU to that VM, while having the 1060 take care of the graphics for the host Ubuntu system.
I have had some success so far. I have set up a Windows 10 virtual machine and successfully passed a GPU to it. So far I'm thrilled with this progress, things are definitely heading in the right direction.

However, I've ran into an issue. My motherboard has two PCI-E slots that my GPU's can slot into, one having 16 lanes and one having 4. Ideally I would like the 1060 in the 4-lane slot with the 3060ti in the 16-lane slot. However, when I boot the computer the card occupying the 16 lane slot becomes the output device, whether it's the 1060 or 3060ti.
- If I place the 1060 in the 16-lane slot, my 3060ti can therefore only occupy the 4 lane slot, which would constrain its potential and limit gaming performance. 
- If I place the 3060ti in the 16-lane slot, it becomes Ubuntu's output device and my 1060 is the only card that is left to be passed through to the VM. This is what I have done with success so far. Obviously, this isn't what I want. 

The solution appears to be having the 1060 in the 4-lane slot and the 3060ti in the 16-lane slot, and somehow be able to make the 1060 Ubuntu's default output device, therefore leaving me the 3060ti to give to the VM. I've tried googling this for a few hours and have unfortunately come up with nothing - sorry if this is a mundane and simple problem! Can anyone help?

Additionally, I should mention I have a CPU with integrated graphics (Intel 8700k), and if I can make this Ubuntu's main video output device I'll do so if it is impossible to use the 1060. This would obviously not be ideal but I'm open to the idea.

Thank you for your time. :)

---

### Post by TheFu on 2021-06-24
This topic is mainly about virtualization.
I don't game and none of my systems have multiple GPUs.

If it were just trying to select the GPU to be used without any GPU passthru, I'd say to manually create an xorg file which specified the exact card to be used and disabled the others.  But when Intel and nVidia are both inside the same system, I think there is some added steps, which I don't know. Sorry. 

My xorg file is mostly about forcing 1200p to be sent on an HDMI output to an DVI-D -to- VGA adapter so it will work with my KVM switch.  You can create a default xorg.conf file using **nvidia-xconfig** with the nvidia-utils/tools.  Store the created file in your HOME, then move it into /etc/X11/xorg.conf.d/ with a filename that ends in .conf after you tweak it for your needs.  Each section provides an "Identifier" which is used as a reference in other sections.  Really there is no way to "wing it" to get a working xorg.conf file.  Every detail needs to be carefully cross-referenced to be consistent within the file.

**xrandr** will list different GPU outputs. 

Also, I know ZERO about how Wayland does these things.   If using Wayland, seek other help.

With GPU passthru, the IOMMU controls would specify which PCI slot to be passed thru for exclusive use. You probably know more about that than I do.

---

### Post by almostmatt1 on 2021-06-24
Thanks for your reply! I'll look into xorg and see what I can accomplish.

I posted the thread here instead of in the virtualisation section because the virtualisation itself isn't the thing I'm having an issue with, it's setting Ubuntu's GPU output prior to doing virtualisation. Although now that you mention it perhaps this is a specific enough issue for me to have posted it there instead.

---

