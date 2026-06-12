---
title: "How to setup 2 GPUs but use the built-in GPU"
date: 2022-03-06
forum: Hardware
---

### Post by couzin2000 on 2022-03-06
I have this Z90 ASUS mobo running Ubuntu. I don't currently have a video card installed inside - I'm using the video output from the built-in GPU on the motherboard (Intel I think).
I need to install a video card inside so that I can take advantage of its hardware acceleration - this is to transcode video on-the-fly. However I do NOT want to use its output - the computer is currently not even hooked up to a monitor. I run that PC headless, with a dummy plug in the DisplayPort output, and I can log into the pc with Teamviewer which runs great form me. So I need to keep all that setup that way.

Is it as easy as just popping the card into the PCIe 16x slot, and installing the latest Nvidia driver, but letting the BIOS know I'm using the built-in car as the output? Will the outboard GPU be recognized and used? I need to be able to use the outboard GPU for other stuff that actual video output.

---

### Post by Autodave on 2022-03-06
On most motherboards (I am not sure about yours) the built-in GPU is disabled when any GPU is added.  There may be an option in you BIOS to run both at the same time, but then you will have another bag of worms to deal with since they take different drivers for each GPU.

---

### Post by couzin2000 on 2022-03-06
> **Autodave said:**
> On most motherboards (I am not sure about yours) the built-in GPU is disabled when any GPU is added.  There may be an option in you BIOS to run both at the same time, but then you will have another bag of worms to deal with since they take different drivers for each GPU.

I'm aware. But I'm looking for the actualy way to do just that. 
I was able to install a PCIe GPU on my motherboard, yet run the onboard GPU, which went pretty smooth. I haven't gotten any further than installation, however, so I need to know how it's possible to have both running at the same time. As stated above, the onboard GPU is Intel and the PCIe GPU would be Nvidia, possibly a Quadro. Just wanna know how it's possible to be running the INTEL output, yet use the NVIDIA card as a on-the-fly transcoder.

---

### Post by mIk3_08 on 2022-03-07
> **couzin2000 said:**
> I'm aware. But I'm looking for the actualy way to do just that. 
I was able to install a PCIe GPU on my motherboard, yet run the onboard GPU, which went pretty smooth. I haven't gotten any further than installation, however, so I need to know how it's possible to have both running at the same time. As stated above, the onboard GPU is Intel and the PCIe GPU would be Nvidia, possibly a Quadro. Just wanna know how it's possible to be running the INTEL output, yet use the NVIDIA card as a on-the-fly transcoder.
Just curious, What is exactly your plan of doing this? What is exactly your purpose on this? regards.

---

### Post by couzin2000 on 2022-03-08
> **mIk3_08 said:**
> Just curious, What is exactly your plan of doing this? What is exactly your purpose on this? regards.

My plan is that I currently am running (as said previously) a sort of "headless" server. I had a hard time removing the PCIe GPU for the PC to still run... but I was able to get into the BIOS and setup the built-in discrete GPU. By booting into the PC with a monitor attached, I was able to force the BIOS into recognizing that the output I wanted to use was the DisplayPort, Once that worked, I rebooted. As the PC rebooted I removed the monitor and put in a DP dummy plug. Now the server runs as if I had a monitor connected.

I would like to keep the PC this way. I would also like to harness all the power of a video card (say a Quadro P400 as an example), BUT I don't want to have to buy an extra dummy plug, run through all the hassle of forcing the pc into using a certain out, BIOS settings and all that... I was a hassle to begin with, and I find    this method of working pretty bad because it's all trial and error, hope for the best kinda deal. I would rather find the proper wat ron install the card without having to connect anything to it at all. 

The usage I will get out of this card is Plex hardware transcoding on-the-fly. The reason I didn't mention it is because I am trying to configure Ubuntu for this, not Plex. So I don't wanna be told "you should go to Plex Forums". I know the answers I need are here.

Please let me know if there is a way to set this up.

---

