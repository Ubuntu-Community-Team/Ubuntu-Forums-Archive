---
title: "Micorphone woes"
date: 2008-05-07
forum: Hardware
---

### Post by xcelman on 2008-05-07
I've just installed Hardy Heron (on my Lenovo Desktop) and my goal is to use Skype on it.  I have installed skype (with help from several forum threads), video is working, but am having NO luck with the microphone. I've read several posts on microphone issues/fixes but none seems to help.

lsusb -> Bus 005 Device 007: ID 046d:0990 Logitech, Inc. 
Bus 005 Device 004: ID 054c:01bd Sony Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 005: ID 04b3:310c IBM Corp. 
Bus 001 Device 004: ID 04b3:3025 IBM Corp. 
Bus 001 Device 001: ID 0000:0000  

In volume control I see three devices in Volume Control and have tried each with no success
. HDA Intel (Alsa mixer)
. USB Device 0x46d:0x990 (Alsa mixer)
. Analog Devices AD1988 (OSS Mixer)

I have also made sure that vi alsamixer that all of the channels are running max gain and have made sure that they are not muted.

I getting ready to pull the plug on trying to fix this and install a 3rd party sound card, which I hope will resolve my problem.  Any suggestions on a sound card that works with ubuntu?

---

