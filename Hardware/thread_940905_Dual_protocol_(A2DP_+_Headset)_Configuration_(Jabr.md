---
title: "Dual protocol (A2DP + Headset) Configuration (Jabra BT8010)"
date: 2008-10-07
forum: Hardware
---

### Post by AcIDx0 on 2008-10-07
Hi all,
This is my first post, since I have found a solution to every problem so far, until this came up.

I have a Jabra BT8010. This is a headset that supports both A2DP and Headset protocol. 
The main difference between them: 
A2DP is one-way (device to headset) stereo link. Basically used for music.
Headset (maybe there is a better name for this) which is two way (mic and headphone) mono protocol. It is used for phone calls.

There are numerous headsets, like Jabra BT8010 which combine those two features.

I have successfully synced the headset to my computer and configured the .asoundrc file.

Whenever I play a sound to the headset (skype or music), it shows a small icon that it is receiving music.

I was unable to use the microphone in any way. Skype says "problem with audio capture"

I am 99% sure this is because Ubuntu is trying to communicate using the A2DP protocol, which simply does not support a mic.

Question:
How do I make alsa (or any other thing for that matter) use a specific protocol?

What I tried:
1.Wrote the headset 2 times into .asoundrc, and manually defined a profile (tried "a2dp", "headset, "voice") instead of "auto".
Each time restarted the alsa service and skype and tried to make a call.
No banana so far.

Will appreciate any help.
Thanks.

---

### Post by AcIDx0 on 2008-10-08
*BUMP* Please help, this is the last issue that keeps me from ultimate system.

---

### Post by nermaljcat on 2008-10-13
I have a Jabra BT8040 and experience the same problem. If I find a solution I'll post it here. Can you please also do the same?

---

### Post by nermaljcat on 2008-10-15
If it helps at all, I'm running Ubuntu 8.04 on a Thinkpad T60. I'm pretty sure it's a problem with the Jabra headset not connecting in it's 'minor' headset mode.

I've tried some of the python code in the bluez Audio Guide to setup a 'Headset' connection, but it hogs the device (eventually dies) so Skype cannot connect. I've also tried connecting in BlueMan under: Services->Audio->(configure button) as 'Headset' instead of 'Sink' (a2dp I believe), but it also hogs the connection and Skype cannot access it.

Querying the Jabra headset for services (python script or in BlueMan) returns nothing.

As for your .asoundrc config, I think that 'audio' also handles headsets. Look at /etc/bluetooth/audio.conf and there is a section for configuring [Headset] mode. Bluez also says that it's Audio service manages the Headset interface (looking at some of the python code confirms this).

---

### Post by fatski on 2008-10-26
Sad to say it's a known kernel bug:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/211893](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/211893)

As of now many bluetooth headsets just don't work in linux.

---

### Post by AcIDx0 on 2008-11-06
Upgraded to intrepid in hopes that this will be resolved here, yet now i can't even start blueman, only the standard bluetooth manager. The situation is basically still hte same. I read the proposed kernel bug, and it does not seem to be the issue. The headset works, just not as SCo but as A2DP. 

@nermaljcat: Could you elaborate on that? How do you scan for services in ubuntu? I did that with my WM6 phone and it discovered the services alright

---

### Post by Nate53085 on 2008-11-13
I have the same headset, running 8.10

Bluemon will not start:
Error querying status: The name cx.ath.matthew.bluemon.server was not provided by any .service files


Tried hidd --search for the device, but it doesn't pick it up.

The gnome bluetooth applet will see the device, but the only options are to send file or browse device.

I'd be happy if I could just get the thing to pair with my computer.

---

### Post by AcIDx0 on 2008-11-13
The headset pairs alright, but is only recognized as A2DP device (only after I manually specified it as one in .asoundrc). I just bought a simple unbranded a2dp and sco receiver and guess what? same story. a2dp work good after some tweaks, but headset profile does not with same issues. 
Any gurus to help us?
Question is simple: how to make devices with dual protocol (a2dp and sco headset) support, use the sco protocol and not a2dp?
thanks

---

### Post by giovannif on 2009-01-19
I have just bought the Jambra BT8040 headset. I tried to connect it following these instructions: 
[http://forums.overclockers.com.au/showthread.php?t=694010](http://forums.overclockers.com.au/showthread.php?t=694010)

My OS is Ubuntu 8.10 and I have got the same problem. Audio is OK but my microphone does not work. Then I tried to reboot my laptop with windows XP and I had the same problem once the heaset was paired. For Windows XP I found this solution:

[http://forum.skype.com/index.php?showtopic=184761](http://forum.skype.com/index.php?showtopic=184761)

but I could not make it work cause the bluetooth application gives me only the stereo option. I am very new with ubuntu but if somebody found a solution with windows, is it possible to do something similar with ubuntu? Is it possible to exclude the "stereo" option or something like that?

Thanks
Gio

---

### Post by vavatl on 2009-01-21
You actually can make it work as headset by setting ```
profile "voice"
``` in your .asoundrc configuration. You can even make two different configuration, one for a2dp and one for headset, and they will both kind a work. What you can't do is to switch the headset from one configuration to another easily. That is, if you start a music player and headset goes into a2dp mode, Skype won't work with it. Sometimes restarting bluetooth services helps, sometimes you have to also switch headset off and on again, sometimes nothing helps. As far as I know there's no solution for that yet which is why I still using that damn Windows.

---

### Post by AcIDx0 on 2009-01-21
> **vavatl said:**
> You actually can make it work as headset by setting ```
profile "voice"
``` in your .asoundrc configuration.

Dude, read the first post. I did that, but no banana. The headset still receives the sound through a2dp despite what you specify. I am waiting for BlueZ 4.0 and compatible blueman. I think they might solve the problem. Somehow though, it seems none of these projects are advancing. I'd say bluetooth in linux if pretty much crippled as of today. 

I am using a wired usb headset for my calls meanwhile. streaming music to my headphones works good, so I am not pressed or something. I just think that a BT headset is much better for skype calls. I might buy a separate cheap headset just for this....

---

### Post by giovannif on 2009-01-30
thank you vavatl. I made it work with skype, modifying the file ~/.asoundrc with:


ctl.bthandset {
  type bluetooth
  device XX:XX:XX:XX:XX:XX
  profile "voice"
}
pcm.bthandset {
  type bluetooth
  device XX:XX:XX:XX:XX:XX
  profile "voice"
}

thank you
gio

---

