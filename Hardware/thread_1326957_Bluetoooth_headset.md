---
title: "Bluetoooth headset"
date: 2009-11-14
forum: Hardware
---

### Post by ankman on 2009-11-14
I am trying to get my Motorola headset to work with Ubuntu (Karmic). So far I was able to connect it already to the Bluetooth dongle I have, and Blueman also shows it.

However I seem not to be able to route the audio to it. From some research I did it appears that I am not able to (again) authenticate the computer to the headset via PIN 0000. That might be because, as mentioned here already, there is no hcid.conf and/or passkey-agent to be found. My /etc/bluetooth looks like

audio.conf  input.conf  main.conf  network.conf  pin  rfcomm.conf

and a search system wide for "passkey" just gives

/usr/share/blueman/ui/applet-passkey.ui
/usr/share/gnome-bluetooth/passkey-dialogue.ui

This is probably not what I need.

I guess I installed all with name "bluetooth" or "bluez" I could find with aptitude.

What do I miss?

---

