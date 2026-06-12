---
title: "Sound problem fixed with sudo pm-suspend command.  Why?"
date: 2016-10-24
forum: Hardware
---

### Post by fresnofred on 2016-10-24
I am running ubuntu mate 14.04 off a little 16 gb thumb drive.  I have a built-in sound card in my Dell PC.  I also have another sound card which I use because the other one in the PC has problems with the microphone.  Anyways, half the time I boot all works except 50% of the time sound does not work.  I check sound settings and sound card is enabled.  It is a VT1720/24 Envy 24PT/HT PCI Multichannel audio controller.  It shows up in aplay -l as device 0 ICE1724 or ICEnsemble ICE1724.  And device 1 same plus IEC 958.  Both card O.
I disable onboard sound in the bios.  Yet sound only works half the time.  If i do the command sudo pm-suspend, sound is restored.  Can anyone explain why this command restores sound and suggest a permanent fix??
Thanks, 
Fresnofred

---

