---
title: "No sound on natty after bios upgrade"
date: 2011-07-18
forum: Hardware
---

### Post by daniel r on 2011-07-18
Hello,

Today, I flashed the bios of my dell XPS m1530 laptop.
Everything went fine, except now I have no sound in natty.

(I tried to boot with a fresh natty from an usb stick, and sound worked, so it looks like a problem in my system setup).


When I launch gnome-alsamixer, the window content is blank. 
If I try to go to the menu "edit > sound card properties" (as my natty is in french, my translation may be not exactly correct), 
the gnome-alsamixer window closes.

Here are the alsa infos of my system:
[http://www.alsa-project.org/db/?f=e3de4ea7d4f2ae6b36bde7651d678ee44bda0eea](http://www.alsa-project.org/db/?f=e3de4ea7d4f2ae6b36bde7651d678ee44bda0eea)

There seems to be a problem with the Driver, as "Driver version" is blank...

What can I do to enable sound again ?

Any idea ?

Thank you very much.

---

### Post by daniel r on 2011-07-18
Additional notes:

```
lspci -v | grep -i audio
```
produces the following output: 
```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
```

And I have:

```
cat: /proc/asound/cards: No such file or directory
cat: /proc/asound/version: No such file or directory

```


And:
```

sudo aplay -l

```
produces: 
```
sudo aplay -l: aplay: device_list:240: no soundcards found...
```

---

### Post by daniel r on 2011-07-18
Ok, problem fixed.

I'm not sure what caused this.

I've tried many things, like uninstalling/reinstalling alsa stuff. 

It seemed not to work, even after reboots.

Then I booted on my old Vista partition.

When I came back to Ubuntu, BAM ! Sound was working again...

Unfortunately, I can't identify what action fixed the problem, or if suddenly Ubuntu just successfully discovered the hardware automatically during last reboot.

---

