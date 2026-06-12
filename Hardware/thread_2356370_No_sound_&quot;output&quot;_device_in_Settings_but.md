---
title: "No sound &quot;output&quot; device in Settings but audio device is recognized"
date: 2017-03-22
forum: Hardware
---

### Post by n2te on 2017-03-22
I'm a relatively new user to Linux/Ubuntu 16.04, and doing my darndest to cut the cord with Mr. Gates' empire and get baptized with the Linux congregation.  I was given a working PC that was previously running WIN-7 and I've since installed 16.04 successfully.  It seems to run great. However I have no sound output. When I go to "Sound Settings" the system does not show any device under the OUTPUT tab *"Play sound through"*. However under the INPUT tab *"Record sound from"* it does show *"Rear Microphone, Built-In Audio"*.  With my limited Linux dexterity, I followed some troubleshooting suggestions online and determined that I have an NVIDIA MCP61 audio device. (lspci -v | grep -A7 -i "audio") I also read a suggestion that I go to a page that listed the ALSA compatability for assorted audio devices and found NVIDIA listed but not my particular MCP61 device. Again, not having a lot of Linux experience I'm not sure what to try next but certainly don't want to give up. Any suggestions? Thanks.
Ed - N2TE (ham radio)

---

### Post by Yellow Pasque on 2017-03-22
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

