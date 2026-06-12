---
title: "Nvidia driver with a laptop video card with custom firmware."
date: 2017-07-17
forum: Hardware
---

### Post by mobilejad on 2017-07-17
Hello I installed Ubuntu 17.04 on a Clevo laptop with a GTX 970m and it has been flashed with custom firmware to allow overclocking. 
When I used this laptop and video card under Windows, the only driver that I could use was a custom driver provided by Sager that has a custom device id list.
When I use lspci command to look at my video cards info, the results look familiar to what I was using under the Sager driver. 
How ever when I switch from nouveau to the Nvidia driver under proprietary drivers, the Nvidia driver does not seem to be engaging. 
The Nvidia settings app is empty, and running the Heaven benchmark app provides same results under both drivers. 
I am pretty sure that what needs to happen for me with Ubuntu with the Nvidia driver is similar to what I have to do with Windows, the driver needs the correct device (under windows the driver has a list of device ids in a inf file) id to be able to install correctly. 
But so far I'm having trouble finding out exactly what I need to do to get the Nvidia driver in Ubuntu to work correctly with my customized video card. 

Any help will be appreciated! 
Thank you, 
Jonathan Duncan.

---

### Post by Autodave on 2017-07-17
According to Nvidia's website, 375.66 is the driver recommended for that card. Have you tried that yet? If not, you probably need to. Do NOT get it from the website! Go to Settings -> Additional Drivers and get it.

---

### Post by mobilejad on 2017-07-17
Yup that's the method that I used to install the Ubuntu provided driver, I believe it was version 375, I can double check when I get off work though.
Yup when I check the Additional Drivers it says version 375.66 Proprietary. 
I currently have the proprietary selected by Heaven runs slow and if I try starting a game from my Linux Steam, like Borderlands 2, the game will start, but no textures are applied to any of the 3D objects...
Well I am learning more and more about Linux and 3D rendering, right now I have the nouveau driver enabled, found about driconf and the S3TC feature, switched S3TC on and relaunched Borderlands 2,
Wolla! Textures are now being rendered! Makes sense that S3TC was described to me as a proprietary texture compression feature. However using nouveau there is still lots of rendering glitches, but at least my games should be _playable_
And from what I understand the current version of nouveau is Alot better than what it used to be...
I would still like to figure out how to get the proprietary Nvidia driver running if its possible to do so, without resorting to reflashing my 970m back to stock firmware... (If I can even find it, Prema mod seems to be going through some troubles...)

---

