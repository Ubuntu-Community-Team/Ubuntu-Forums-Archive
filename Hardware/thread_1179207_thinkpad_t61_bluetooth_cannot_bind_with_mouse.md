---
title: "thinkpad t61 bluetooth cannot bind with mouse"
date: 2009-06-05
forum: Hardware
---

### Post by David Shen on 2009-06-05
Hi,

I have a thinkpad t61, with ubuntu 9.04 amd64 installed. the bluetooth wizard can find my bluetooth mouse, but it cannot connect to it.

I have searched the web for a long time, and all the posts tell me to use a hidd command. but i DO NOT have such command. i have tried to apt-get bluez-utils, and the system says i am already having the latest version.

here's the output of the 'hcitool'

hcitool scan:

Scanning ...
	00:1D:D8:91:87:63	Microsoft Bluetooth Notebook Mouse 5000

when i try to use 'hcitool cc' to connect to it, there's no output, and my mouse cannot work.

---

