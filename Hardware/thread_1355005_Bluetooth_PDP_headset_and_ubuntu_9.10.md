---
title: "Bluetooth PDP headset and ubuntu 9.10"
date: 2009-12-14
forum: Hardware
---

### Post by niallsc on 2009-12-14
I am having some trouble with my bluetooth headset and ubuntu, I have synced my headset and it says that it is connected but i cant get any audio to come out of it for some reason and I dont know if i am missing drivers or what but I really need to get this headset working and if I could get it to work with linphone that would be Ideal but any suggestions would be greatly appreciated

---

### Post by jwssr on 2009-12-14
I use BT devices on karmic and am just loading 10.04.

I see you are tying the device to a voip app using linphone....I have not had any success with any sw except sflphone (which uses pulseaudio..which ties to BT)...Xten was great up until karmic and it now refuses to work...missing dependencies..which I dont think xten will fix...

to make BT work..make sure that you8 have all of the pulse audio apps installed  paman will install them all for you...apt-get install paman
also insure that pulseaudio-module-bluetooth is installed.

also install gnome alsa-mixer....apt-get install gnome-alsamixer.

Pulse audio works ontop of alsa..so insure that all of you audio inputs/outputs are not muted  by using alsa-mixer...it will be in 
Applications/Sound & Video/Dnome Alsa mixer.

Then, also in Apps/Sound&Video/Volume Control...you can set up your BT device..

if you devices is not alreay showing up in <Output Devices> (tabs across the top)...then click on last tab (Configuration)...it should be there.

depending on the services taht your device supports...ie a2dp for stereo..
HSP/HFP ...you can select type of service.

To see you app working...click on 1st tab  (Playback).  leave this app up on screen while you are using linphone or what ever...it will show you the sound volume using the app.

Hope this helps you...

---

### Post by W. Irving on 2009-12-16
This worked for me - thank you jwssr!
Though I can't get the PulseAudio Device Chooser to start, but it seems I don't need it. After connecting the headset, it appears in the device lists of the hardware, input and output tabs in the volume settings. Absolutely brilliant, and much better implemented than in Windows!

One minor problem I had setting this up was with my headset, a Sony Ericsson HBH IV840, is that the headset service only remains active for a few seconds after starting it, unless it's actually used. The safest way appears to be to start playback first, then connect the headset. Might help someone else being as confused as I was at the time..

I should add that so far I'm only using it to test the battery life of the headset, through looping a song in VLC. Contrary to how it's done in Windows, I did not have to change any settings in VLC to get sound through the headset.
*It just works*

---

