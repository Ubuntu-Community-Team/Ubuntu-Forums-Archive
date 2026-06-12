---
title: "External audio device - Fractal FM3 - partial function?"
date: 2023-04-27
forum: Hardware
---

### Post by acharlespossum on 2023-04-27
Hello gurus, 


I've got a piece of audio equipment, the FM3 by Fractal Audio. It's a USB device that can be used for capturing audio in a DAW and does its own on-board processing. Furthermore it also has some control software, and it works as a USB sound board with OS's. 


I'm running 22.04 LTS and fortunately it detected the FM3 right off the bat and it functions as a sound card. Yee haw. Following that, 
1) I used Wine to install the Windows version of the control software, FM3-Edit, and it opens. Then I downloaded the USB driver bundle from Fractal Audio, and then also using Wine:
2) From the driver bundle, I installed the *Serial* drivers using that specific .exe installer. It completed successfully.
3) From the driver bundle, I tried to install the USB Audio drivers using that specific .exe installer. It started, but said the OS was not supported and quit. 

When I open the FM3-Edit control software, it opens as normal but says it can't detect the unit. This is how it looks if USB is unplugged. 

Now, I imagine that since system audio playback is working fine, Ubuntu is using a generic driver for system audio. All well and good. But I also figured that if the Serial driver installs fine, then the control software should be able to communicate with the FM3 unit over USB as well. Is that a false assumption?

Any ideas on things I should be trying to get the software to talk to the device?

This whole shebang is my last gasp for leaving Windows where all of the software and devices play nicely together with native support. I looked at other threads but this whole thing seems different because there's nothing available or interesting in Software & Updates.

Thank you for any thoughts!

---

