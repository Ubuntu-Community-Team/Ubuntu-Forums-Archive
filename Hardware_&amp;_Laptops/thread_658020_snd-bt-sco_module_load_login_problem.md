---
title: "snd-bt-sco module load login problem"
date: 2008-01-04
forum: Hardware &amp; Laptops
---

### Post by JoshHendo on 2008-01-04
Hi,

I am trying to get my bluetooth headset working to a point where I can turn it on, and it be recognised and enabled, and the opposite when I turn it off.

In order to do that, I decided to follow the guide at [https://help.ubuntu.com/community/BluetoothAudio](https://help.ubuntu.com/community/BluetoothAudio) , as it seems to be the only one that I can get working.

It says, to load the kernel module snd-bt-sco at startup, to add a line containing it's name (just snd-bt-sco) to the /etc/modules file. When I do this, I am unable to login, even in fail safe. The furthest I get is the wallpaper, and that always doesn't happen! To be able to login again, I need to remove it form the file and restart the computer.

I am able to add it using modprobe, and I also need to run the command 'btsco -v 00:1A:0E:29:19:49', and it will work how I want it. If there is a way to get it working how I mentioned above, that would be great.

When I follow the instructions at [http://wiki.bluez.org/wiki/HOWTO/AudioDevices](http://wiki.bluez.org/wiki/HOWTO/AudioDevices) for the most recent version (which I have from the repositories), it doesn't seem to work at all. If there is something I need to do to make that work easily, I would rather use that than what I am currently using.

Thanks, Josh.

---

### Post by BoardDWorld on 2008-01-09
It's only **btsco** that you want to type into a line of its own in /etc/modules

---

