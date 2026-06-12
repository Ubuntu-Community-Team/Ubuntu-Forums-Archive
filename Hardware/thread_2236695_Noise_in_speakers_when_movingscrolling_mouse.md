---
title: "Noise in speakers when moving/scrolling mouse"
date: 2014-07-28
forum: Hardware
---

### Post by Coder88 on 2014-07-28
I can hear a very in-my-face (ears?) annoying humming and clicking sound when I move my wireless mouse or use its scroll wheel to scroll on a webpage. This happens with my (new) Creative Soundblaster X-Fi Titanium sound card that is in a PCI-e slot; this does NOT happen when I plug my (Klipsch THX) desktop speakers green audio cord into the PC's built-in motherboard audio; this does NOT happen when I boot into MS Windows 7, it happens only when  booted into Linux and using the X-Fi soundcard instead of the built-in motherboard audio-- thus normally I would suspect EMI interference of some sort but the humming/clicking is absent when using Windows 7, so I am not sure if shielding the audio cord or moving the sound card to a different PCIe slot would help. The mouse is wireless, part of a 2.4GHz wireless keyboard+mouse combo made by INSIGNIA (Best Buy's brand).  I have tried disabling the onboard audio in the BIOS when using the X-Fi soundcard, but that made no difference.

Any ideas on what is causing this? I can work around it temporarily by swapping what audio out (green) port I plug my speak jack (green) into when booting into Linux versus Windows 7, but I sure would like to use the X-Fi Titanium sound card as I bought it a week ago so as to achieve better (smaller) latency for audio recording, etc., and because it has good ASIO support for music composition and music sequencing software I use in Windows 7 (would like to transition to doing that in Linux eventually).

---

### Post by Gottier on 2014-10-27
I've noticed something similar on my computer. The computer sounds normal, but then after a while there is a slight whine sound when scrolling, hovering over links, closing windows, or basically anything. Sound goes away for a while if I restart my computer.

---

### Post by tgalati4 on 2014-10-27
The difference between Linux and Windows is often simply a gain level difference.  Can you get sound as loud in Windows as in Linux?  Sometimes Windows drivers use a lower gain setting mask the system noise.  Linux drivers often use a higher gain to get a higher final output, which is useful for driving big headphones or other equipment.  Of course, then system noise is audible, so it is a tradeoff.

I would use a wired mouse and keyboard.  Wireless transmits a microwave signal throughout the area that is uncontrolled.  It's possible your sound card is picking up the microwaves because there is no shielding for this frequency.

Another possibility is differences in the wireless drivers that are causing a higher-level transmit signal, or muting the wireless signal when the mouse is not moving.  This would reduce the noise.  I bet there are some tweaks in the Windows driver to address this.

---

### Post by Gottier on 2014-10-27
I actually found the source of my problem. I used a chopstick (oriental eating utensil) and put one end on my ear, and the other end on various computer components. Doing so allows the vibration of the components to be transferred to my ear. I found that in my case the noise was coming from the graphics card. What was odd was that when I touched the graphics card with the chopstick it would stop the noise. So, I decided that something touching the card was causing the noise. The cable that powers the CPU was touching the card, so I moved it, and the noise went away! I can't say this is the problem that you are having, but at least in my case the problem is solved.

---

