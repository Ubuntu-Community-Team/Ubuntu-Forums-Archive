---
title: "Please somone can you help. Realtek Hi Def  Drivers on Jaunty"
date: 2009-07-13
forum: Hardware
---

### Post by sieger007 on 2009-07-13
[COLOR="Sienna"]I am running Jaunty as below :
uxxx@ToshDebLX94599:~$ version
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.04
DISTRIB_CODENAME=jaunty
DISTRIB_DESCRIPTION="Ubuntu 9.04"
Linux ToshDebLX94599 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 22:12:12 UTC 2009 x86_64 GNU/Linux
My Windows Partition has Realtek Hi Def Codec installed as the sound driver  and the sound quality of Jaunty is far short of what I am getting in vista. I always believed Linux could a lot better.
PL can someone tell me WHAT the problem is ? I am sure I am missing something there 
My Questions .Please be a bit exhaustive cos I am just  another newbie bloke , poking around Linux now and often.

<>I saw there is a driver available for Linux on Realteks Website.Unfortunately there is no .deb package that I can just install.Its has to be compiled and the directions are even more confusing.** Before I mess around with it** , I would like to verify if the one Jaunty has is the same one as this one or comparable.
**How do I do that ?..verify that  the realteks driver is already installed and if there'd be any need to go through that ordeal? **

<> I can hear some sound on youtube but not the same quality as I can get off Windows using Realteks Hi Def Codec. Is there a parallel Hi Def Codec for Debian ?

<> Finally Skype is just pathetic . I sound like a fisherman , howling the road ( I mean cracked and really lo quality  voice ) or there is no sound heard at the other end  , when I use skype. The only setting that works is Pulse Audio. Does anyone have better luck  getting skype to run .



<> under Sound Devices  there are really a big bunch drop down ones. 
--- Realtek ALC272 ( Does this mean that the original realtek Driver is already installed. No Need to go through all the trouble.
--- Playback HDA Intel ALC272 Analog ( Pulse Audio Mixer ) 
--- Capture  HDA Intel ALC272 Analog ( Pulse Audio Mixer ) 
--- Capture  Monitor of HDA Intel ALC272 Analog ( Pulse Audio Mixer ) 
--- HDA Intel ALSA Mixer

Now are** there supposed to be so **many sound drivers ? and that is why its getting confused ?
.....PL Advice ...
Many thanks 
Sam




[/COLOR]

---

### Post by treesurf on 2009-08-28
I have the same issue, except with a Lenovo IdeaPad Y550.  Also with the RealTek ALC272, though.

The sound is good in Vista, but very quiet in Ubuntu with everything maxed out in alsamixer.  Also I think the built in subwoofer is not working with Ubuntu.  I thought perhaps these driver might solve things but I'm a bit wary about trying to install them.  Does anyone have any advice?

---

### Post by treesurf on 2009-09-06
So on further investigation of the Realtek HD audio drivers I discovered that it's just the ALSA packages.  I upgraded to the latest ALSA (1.0.21) to see if that would help, but the sound is still super quiet in Ubuntu with everything maxed out.  There is no specific model name for the ALC272, but I went ahead and tried a few different model names from similar cards/laptops in the alsa-base.conf file without any luck.

If anyone has any suggestions please, please, please let us know.

---

### Post by ratdog on 2009-09-08
Hello,
Another lenovo y550 owner here.  I would also love some help in this area.  
Thanks!

---

