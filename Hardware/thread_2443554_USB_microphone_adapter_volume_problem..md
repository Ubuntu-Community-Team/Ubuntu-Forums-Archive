---
title: "USB microphone adapter volume problem."
date: 2020-05-17
forum: Hardware
---

### Post by ipmungam on 2020-05-17
Hi All, new to the forum, hope I'm in the right place.

I recently bought a cheap "3D SOUND" USB audio adapter I would like to use for a microphone project:

[https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=8&cad=rja&uact=8&ved=2ahUKEwi8rY3e6LrpAhUpQxUIHQuUBm0QFjAHegQIAhAB&url=https%3A%2F%2Fwww.ebay.co.uk%2Fitm%2FExternal-Virtual-USB-3D-5-1-Channels-Stereo-Sound-Card-Audio-Adaptor-Converter-%2F171898196952&usg=AOvVaw2-NJdGQxESqNepdU8qfElf](https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=8&cad=rja&uact=8&ved=2ahUKEwi8rY3e6LrpAhUpQxUIHQuUBm0QFjAHegQIAhAB&url=https%3A%2F%2Fwww.ebay.co.uk%2Fitm%2FExternal-Virtual-USB-3D-5-1-Channels-Stereo-Sound-Card-Audio-Adaptor-Converter-%2F171898196952&usg=AOvVaw2-NJdGQxESqNepdU8qfElf)

It is recognised in Ubuntu 18.04.4 LTS as: 

Manufacturer=C-Media Electronics Inc.      
Product=USB PnP Sound Device

in a USB2.0 port with the snd-usb-audio driver.

It functions, however the mic level is too low -- much lower than the same mic using the motherboard's 3.5mm mic port (Realtek ALC221).  I have maxed out everything I can see in sound settings, pavucontrol and alsamixer, to no avail.  I notice that in alsamixer's capture list this USB device has only one level -- in particular, "mic boost" is absent.  My question is:** is this just a driver issue with this USB device, or is there really no way to boost this mic adapter in software?** (Without destroying the audio quality.)


More if helpful:
I'm trying to get an old iMac microphone working over USB.  I assume I've wired it correctly because it works in the 3.5mm port.  The USB adapter's mic level is actually tolerable if you use a headset with the microphone beside your mouth, but for the iMac obviously the mic is several feet away.  I assume this is where one needs the "boost", because the mic works alright using the 3.5mm port which does have a "mic boost" level in the alsamixer capture list.

In case anyone is familiar with this bug ([https://forums.linuxmint.com/viewtopic.php?f=48&t=183740#p952175](https://forums.linuxmint.com/viewtopic.php?f=48&t=183740#p952175)), I tried to reconfigure pulseaudio to "un-merge" the mic channels, but the USB mic is recognised as Mono so there is only one channel as far as I can tell.

I have also read that one can force pulseaudio to amplify the signal with
$ pacmd
>>> set-source-volume 1 250000
However the audio quality is already not great at pavucontrol's current 153% level, so I'd prefer not to just crank this up and make it even worse, if possible.  Presumably "mic boost" does something better than this.

---

### Post by TheFu on 2020-05-17
> bought a cheap "3D SOUND" USB audio adapter
That's the problem.  What's the saying, "you can put lipstick on a pig, but it is still a pig."
Did the microphone ever work well on any computer?  Not sure what you expected for $3.50.  Low levels is always an issue.

I can recommend a Samson Go Mic for $35. [https://www.amazon.com/Samson-Mic-Portable-Condenser-Microphone/dp/B001R76D42](https://www.amazon.com/Samson-Mic-Portable-Condenser-Microphone/dp/B001R76D42) Relatively cheap, sounds better than most mics. Has always been plug-n-play on all my Linux systems. It isn't a Blue Yeti, but still pretty good for 1/3rd the cost.  I've seen it for $25 before, but the pandemic has really caused a run on webcams and microphones.

---

### Post by ipmungam on 2020-05-17
Thanks for the reply.  That mic does look good, but the goal here is to get the original iMac microphone to work -- doesn't have to sound great, but the volume at least needs to be useable!  Is there a better analog to digital USB adapter out there maybe?

---

### Post by ipmungam on 2020-06-19
In case anyone comes across this, I tried another (not quite as cheap) USB audio adapter, and after some messing around in alsamixer this one does give usable mic levels -- so I guess it was a problem with the previous device.

---

### Post by TheFu on 2020-06-19
> **ipmungam said:**
> In case anyone comes across this, I tried another (not quite as cheap) USB audio adapter, and after some messing around in alsamixer this one does give usable mic levels -- so I guess it was a problem with the previous device.

Bet people would love to learn the specific device, cost paid and a comment about the quality of the recorded audio.  Options are good.

And if you could please mark this thread as **SOLVED** - Thread Tools button at the top of the page. That would help the community both people looking for answers and people looking to help.

---

