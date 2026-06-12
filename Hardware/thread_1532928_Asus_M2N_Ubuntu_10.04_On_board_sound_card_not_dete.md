---
title: "Asus M2N Ubuntu 10.04 On board sound card not detected."
date: 2010-07-17
forum: Hardware
---

### Post by bungalallybob on 2010-07-17
Hi there all. 

I decided to get a ubuntu system going better than my windows. 
I did a preview of 10.04 using the live cd. 
A sound card was detected while only providing stereo out-put instead of the 5.1 i should get, is still some sound. 

After installing in permanently on to a hard drive, no sound card is detected by the alsa drivers.

when i run lspci it does find an audio device. listing it as a nvidia mcp61 or something. 

after some research i found that the sound codec should be a AD1988, which doesn't seem to be supported by ASLA but should be since i get sound when using the live cd. 

system specs
Ubuntu 10.04
Asus M2N Motherboard NVIDIA 430MCP
intergrated sound card.  

if anyone has any leads, thanks in advance

---

### Post by lidex on 2010-07-18
It's supported, you probably need latest version. Use the alsa-upgrade link in my sig to get v 1.0.23. Let me know the result.

---

