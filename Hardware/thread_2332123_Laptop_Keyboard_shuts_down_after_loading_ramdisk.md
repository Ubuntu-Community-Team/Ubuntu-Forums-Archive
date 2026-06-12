---
title: "Laptop Keyboard shuts down after loading ramdisk"
date: 2016-07-28
forum: Hardware
---

### Post by rowbow on 2016-07-28
Hey there,
a few hours ago my Ubuntu has stopped letting me use my laptop keyboard (Lenovo Yoga 13). I suspended it earlier and when I wanted to resume my work I got no input from the keyboard. Touchpad and Trackpoint still worked.
After forcing it to reboot I recognized a very strange behavior:
Before the initial ramdisk is loaded everything works fine. I can use it in the Bios, I can fiddle around in Grub, but the moment I continue booting the keyboard shuts down (FnLock- and microphone-LED go dark)

I did not do a system update before and the system was working fine for months before the incident. Only thing I changed was fs.inotify.max_user_watches, but I doubt that this is the issue. I am using kernel 4.4.0-31 and 4.4.0-24. Same issue in normal mode and recovery mode on both kernels. I get stuck at unlocking my disk...

Unfortunately I cannot try connecting an external keyboard at the moment as I am currently traveling in Thailand and hardware access here is very limited (everyone's using smartphones now...)

So on a scale from 0-10... how screwed am I?

Cheers,
rowbow

---

