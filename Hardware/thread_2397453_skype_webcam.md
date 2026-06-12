---
title: "skype webcam"
date: 2018-07-29
forum: Hardware
---

### Post by krssnda on 2018-07-29
To Skype what webcam out of the box will work with Ubuntu 14.04 LTS?

I have a Logitech webcam C270 HD connected.

I get video but no audio.

---

### Post by mastablasta on 2018-07-30
Logitech cams should work without issues.

Audio is provided by speakers or headphone which use a sound card/chip.  

if you mean the microphone, then make sure the correct device (logitech cam) is setup as microphone in skype as well as in the Ubuntu OS

---

### Post by krssnda on 2018-07-30
Hi Mastablasta!

I have installed a G-1050 Multimedia Speaker System. It works perfectly to do YouTube and movies. I have been struggling in the dark. This is what I have tried so far.

 

 I installed the GTK UVC Video Viewer software as well as the Cheese software. With the GTK UVC software installed I got the video and the audio settings but nothing else that I could determine. With the Cheese software installed I got the video but no audio that I could determine.
 

 With Linux Skype installed I got no video or audio that I could determine. Looking at the Linux Skype window I do not see anything on how to integrate either video or audio hardware.

Many thanks for your help.

Kris

---

### Post by mastablasta on 2018-07-30
please identify how your hardware is seen by OS. more info on how to do it can be found here: [https://ubuntuforums.org/showthread.php?t=1422475](https://ubuntuforums.org/showthread.php?t=1422475)

at minimum post output of:
```
sudo lshw -sanitize
```

if you prefer there are also GUI programs that will show hardware and give out a report (*hardinfo* for example or *i-nex*). 

what output do Sykpe settings show?

---

### Post by krssnda on 2018-07-30
Hi Mastablasta!

I am amazed that I was able to do this as computer stuff is basically Klingon to me.
In any case I hope that this is what you meant and that it is useful to solving my problem.

00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (external gfx0 port B) (rev 02)
00:02.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (PCI express gpp port B)
00:04.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (PCI express gpp port D)
00:07.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (PCI express gpp port G)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] (rev 40)
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller (rev 42)
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:16.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 0
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 5
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Turks XT [Radeon HD 6670/7670]
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Turks/Whistler HDMI Audio [Radeon HD 6000 Series]
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
03:00.0 USB controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller

I do not know how to get the Skype settings.

Thanks!
Kris

---

### Post by mastablasta on 2018-07-31
i am not sure but this could be the audio chip or only output on the GPU:
[COLOR=#000000]00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA) (rev 40)

can you check with some system info application to see if this is the device that is not working?

for skype try this:
[/COLOR]> [COLOR=#000000][FONT=&quot]It's done during the call now.  When you are in/starting a call, at the bottom between the hangup icon and the mute item is a + icon.  Click this and you get a pop up menu which has one item called 'Audio and video settings'  this is where you set the inputs for the call.[/FONT][/COLOR]

found at: [https://answers.microsoft.com/en-us/skype/forum/skype_linux-skype_callms-skype_audioms/accessing-sound-settings-in-skype-for-linux-beta/e3fe0e59-016d-4935-b47a-edbbe7ceb489](https://answers.microsoft.com/en-us/skype/forum/skype_linux-skype_callms-skype_audioms/accessing-sound-settings-in-skype-for-linux-beta/e3fe0e59-016d-4935-b47a-edbbe7ceb489)

---

### Post by krssnda on 2018-08-02
August 2, 2018
 

 Hi Mastablasta!
 

 My biggest challenge was finding someone to Skype with.
 

 Making the call I immediately got Video but no Audio. I was able to find and open my Skype Settings and there I found three choices for Audio. One would have been Default which was not working and two other Options. Choosing the one that looked most appropriate I immediately got Audio. I now have complete Skype and it is working perfectly.
 

 I cannot thank you enough for all of your help. Plus it has given me my more confidence to work with Ubuntu.
 

 The first computer was built in 1938 ten years before I was born. I did a bit of Fortran programming as part of my Engineering courses in College but nothing else Computer wise. As I said Computers are pretty much all Klingon to me.
 

 I hate Windows with a passion. I love Linux Ubuntu. Many many thanks for all of your help.
 

 Kris

---

### Post by mastablasta on 2018-08-03
skype has an automated test call available. although you really can't make any conversation with it :)

My grandfather was into technology. Whatever was latest he though he should have it. Colour TV, VCR, Hi-Fi Stereo, Cars. But computers were always a mistery to him. he read about them, but didn't understand them, so he asked questions. finally my uncle bought him one, while i provided "tech support". We would Skype each other weekly, i also prepared him a spread sheet to monitor inventory for his small bar, i showed him how to manage photos and camera, edit photos, check for malware, educate him about e-mail, tough him about word processor (he ran the local veterans organisation and organised trail hikes and festivities)... in the end he became a very good home user. unfortunately, he died before i could introduce him to Ubuntu. But still it shows that it is never too late to learn new things. in fact it is good to keep learning in order to keep the brain going.

---

