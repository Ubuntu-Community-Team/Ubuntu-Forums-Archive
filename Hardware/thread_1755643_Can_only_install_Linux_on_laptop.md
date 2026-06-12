---
title: "Can only install Linux on laptop"
date: 2011-05-11
forum: Hardware
---

### Post by Ekdulon on 2011-05-11
I have just intsalled Linux to test a laptop I have rebuilt, HP DV2699 Special Edition. 
 
I can install all versions of Linux (well at least 3 or 4) and the laptop works fine, a few problems with the NVidia GPU (problem being it was installed) I can install the 3D Experimental driver but all other version come up as acvtivated but not in use (i get the NVIDIA Splash screen befoe logon).
 
My question is does anybody have a suggestion as to why Linux works fine but WinXP,Vista and Win7 will not install, Win7 installs but I get a flashing cursor on the screen before it shuts down, this always happens but has never occurred on a Linux OS.
 
There is certainly a hardware problem on the laptop which I will resolder when I can be bothered. But has anybody witnessed this before, it seems confusing. The laptop is not overheating and I have ruled out this possibilty.
 
just a quick question and im at work being interupted by morons so may not be easy to read.
 
:confused:

---

### Post by ghostborg on 2011-05-11
The part about the Nvidia saying it's installed but not in use I think is a bug as I have seen many references to it. My system says that and it is actually in use. Have not seen Nvidia logo in a long time maybe because it's experimental or some hidden checkbox or the grub boot quiet option is off. I installed the driver through additional drivers.
I have seen people telling others to search Synaptic for nvidia-current but that seems to do the same thing as additional drivers.

Not sure about the Windows thing other than I would look into your partitions. I have seen in the past, especially if you have been loading several OS  over time, where Windows cannot install it's boot loader properly or points to the wrong one.
Good Luck.

Don't they sell a wrist band to keep those annoying pests away, OH yeah thats for mosquitoes not Morons.

---

### Post by Ekdulon on 2011-05-12
[COLOR=black][FONT=Verdana]Thanks for the reply; I wish I could use wristbands. I had a 'user' who was angry her Wi-Fi Router wouldn’t work at home, she thought the power was wireless too so yeah morons was the correct word.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I was sceptical of the drivers being in use, i can load the full unity desktop using Ubuntu but if i use Ubuntu studio I don’t have the hardware. I can connect my monitor using the HDMI port but the results can be patchy. I will try one more time to install the drivers then I’m going to re-solder the GPU.[/FONT][/COLOR]

---

