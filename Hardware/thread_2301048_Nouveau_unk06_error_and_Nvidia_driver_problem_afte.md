---
title: "Nouveau unk06 error and Nvidia driver problem after clean installing 15.10 willy"
date: 2015-10-30
forum: Hardware
---

### Post by Sohan_Chowdhury on 2015-10-30
I have a Asus K550JK (Ubuntu shows X550JK) with a intel hd 4600 and nvidia 850m.
When trying to install Ubuntu 15.04, the same error nouveau unk06 used to flood,
I would just set nomodeset to the kernel parameters and install 15.04 and then Just install bumblebee.
After that nomodset would not be needed and my laptop worked fine on ubuntu.

But when 15.10 came out, I tried to setup and same nouveau error unk06 started flooding. 
From experience I just added nomodeset to boot parameters and installed.
Then I tried installing bumblebee and after reboot the screen went black after the ubuntu bootloader/loading little circles animation.

So I though bumblebee isnt compatible with 15.10 so I clean installed again using nomodeset. Then went in and installed a propeitory driver from ubuntus Additional drivers section. Upon reboot, same problem, black screen. I tried different drivers and the results were same.
Black screen. Some older drivers give a purple screen, nvidia optimus gives a login loop.

I'm not sure what logs I can/need to post since I cant access the laptop as it goes black screen.
But I'm sure with instructions I can do it.(It starts fine on recovery mode on a low resolution. )
As I use ubuntu just for programming and web browsing and other simple non graphical tasks, I would be happy if I could just use the intel gpu and ubuntu would turn off the nvidia alltogather(if that was a solution that is). But the bios does not have any option for disabling the nvidia gpu.

Please help.

---

