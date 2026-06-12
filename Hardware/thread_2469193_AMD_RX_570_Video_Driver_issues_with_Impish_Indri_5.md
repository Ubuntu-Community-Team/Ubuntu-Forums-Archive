---
title: "AMD RX 570 Video Driver issues with Impish Indri 5.13/5.14"
date: 2021-11-22
forum: Hardware
---

### Post by shadowfactor on 2021-11-22
Very new to Ubuntu so please excuse my overall lack of knowledge about Ubuntu.

I was using The Hirsute Hippo 21.04 and was prompted to upgrade to 21.10 Impish Indri so I performed the upgrade and it broke my computer. It would boot into a Black screen after the update. I did a bunch of googling and figured out that I could boot into TTY mode and the computer wasn't actually bricked as previously thought. I tried a few various things off google and managed to reset the GUI manager thing I think It may have had something to do with Wayland ( Cant quite remember) anyway I performed a simple CLI instruction and it allowed me to get the GUI interface back and the computer booted up to the usual home screen although at a terrible resolution.

I performed a lshw -c video and it shows that my graphics card is unclaimed. I googled various steps and re-installed the graphics drivers or atleast attempted too but I get a package error when installing AMDGPU. I thought it may be a issue with the kernel based on further googling so I installed 5.14 but encountered the same results. The resolution is not able to be changed the the graphics card is still unclaimed. 

I have spent alot of time googling and haven't been able to get the graphics to work on anything higher than 5.11.038 Kernel. I had this kernel installed from 21.04 and it works so I have currently been using this but lately I am getting some performance issues that I wasn't experiencing before upgrading to 21.10 Impish. Was hoping to resolve the issues and get Impish working

Does Anyone have a solution about how to get a AMD GPU to work with Impish.

MB: Gigabyte B550 Aorus Master
GPU : AMD XFX RX 570 8GB

Thanks

---

### Post by Tadaen_Sylvermane on 2021-11-24
Are you using the drivers from AMD or the built in from the Mesa package?

---

