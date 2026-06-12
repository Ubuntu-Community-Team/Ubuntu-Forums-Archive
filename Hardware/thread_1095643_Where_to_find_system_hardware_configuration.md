---
title: "Where to find system hardware configuration?"
date: 2009-03-13
forum: Hardware
---

### Post by laughingwiseman on 2009-03-13
I'm new to Ubuntu, so this is probably a total n00b question.

I'm wondering where I go in Ubuntu to find the hardware configuration of my computer. I'm used to using a Mac, where I just go to Apple Menu > About This Mac > More Info. That brings up the System Profiler. Is there anything like that in Ubuntu?

I'm wondering because I'd like to find drivers for my built-in graphics card. (I'm also beta testing Windows 7 on this computer, and it sucks.) Before I can even start looking, I obviously need to know what I'm looking for.

Any help is much appreciated.

(BTW - LOVING Ubuntu so far!)

Thanks!
Isaac

---

### Post by doas777 on 2009-03-13
well the cli command is 'sudo lshw'.

i usually install 'lshw-gtk' to get a graphical interface for it though.

```
sudo apt-get install lshw-gtk
```

and run it with ```
gksu lshw-gtk
``` (you can create a launcher/shortcut so you can launch it with a click)


you'll see 'ls' in a lot of commands. it's short for 'list'. 

there is also 'lspci' which shows you info about all the devices on the PCI bus, and 'lsusb' which shows devices on your usb bus.

---

