---
title: "help request: mouse poll rate change?"
date: 2009-04-29
forum: Hardware
---

### Post by H0PE on 2009-04-29
Hi everyone,

I'm new to linux, and setting up my installation in order to utilize my gamer hardware devices. I found a nice detailed page how to change mouse polling rate (I got a microsoft habu, that could push out 1000Hrz instead of 125hz you know).

I'm using linuxmint at the moment, and Im aware that its based on ubuntu thats why im asking here (as well).

The details are here about how to change the mouse polling intervalls
[http://www.linux-gamers.net/modules/wiw](http://www.linux-gamers.net/modules/wiw) ... USBPolling

My only problem is that I1m not sure which file should I modify. Also I was trying to modify the file /sys/module/usbhid/parameters/mousepoll (which is empty surprisingly so maybe thats not even the file I need) but I think I got access denied it says that error happened while trying to modify the file.

I was trying to use the command
sudo pico /sys/module/usbhid/parameters/mousepoll

So I would like to ask two things:
1.) based on the information where to put the modification in linuxmint usbhid please?
2.) how could I modify such system files, seems "root"/sudo didnt give me enough permissions or something.

Waiting for your replies,
H0PE

---

