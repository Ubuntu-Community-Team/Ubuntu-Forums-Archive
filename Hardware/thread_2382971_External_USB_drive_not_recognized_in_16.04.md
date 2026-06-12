---
title: "External USB drive not recognized in 16.04"
date: 2018-01-19
forum: Hardware
---

### Post by ruberad on 2018-01-19
Short story: WD My Passport, 2TB, brand new out of box, plug it in, the light comes on, you can feel it spin up, but on the computer side nothing.

Long story: 

SO last year I bought a WD 2TB My Passport external USB drive to do backups and provide PVR storage for Plex. It worked fine (16.04), I reformatted it (ext4?) because that's what Plex said to do, I made a backup onto it, all is cool. (I think it worked before the reformat as well, don't remember exactly). Plex didn't work out because of antenna issues, and the drive sat around for many months. I plugged it in to try to make another backup, didn't work (don't remember the details). Plugged it into windows, it saw something was there, but couldn't use it. Tried to reformat it, windows couldn't figure it out. I had paid for the extended warranty at Best Buy, so I went and replaced it.

So yesterday I take the new one home, take it out of the box, plug it into the USB port of the desktop running Ubuntu 16.04, the light comes on, you can feel it spin up, but on the computer side nothing. No automounted drive, no entry in lsusb, no extra logging from dmesg. It works fine on a Win10 laptop though. I assume it's formatted NTFS. sudo apt-get install ntfs-3g says already up to date.

What else can I try to get this to work? Or if for some reason WD My Passport is not a good match for linux, what other external drive should I exchange for?

---

### Post by Autodave on 2018-01-19
Are you trying on Windows on the same machine that you use for Ubuntu or a different machine?

---

### Post by ruberad on 2018-01-19
Different machine. I haven't had any dual-boot machines for years.

FWIW, Ubuntu 16.04 desktop is an Intel NUC (D34010WYK), the laptop in which it works is a Lenovo Thinkpad/Yoga 11e, win10. On the NUC I am plugging into either of the two front USB ports (which work fine for other things), the ports in the back are occupied -- including an Anker 4-port USB splitter out the back which is fairly new because the previous cheap no-name splitter started not working. Neither splitter had a power cord. The cheap no-name would have still been in use in the back when the previous external drive was working in the front.

Just trying to list all possible usb-related info I can think of.

---

### Post by ruberad on 2018-01-28
Bump.

Anybody got any ideas?

---

### Post by ruberad on 2018-01-28
Bump.

Anybody got any ideas?

---

### Post by litlesam on 2018-01-28
I have one of those and when I plug it into the wall it powers up but will not connect via USB. After it stops spinning ( 15 min later ) it connects without issues when the USB cable is plugged in.

Do to bad power issues here, I keep it unplug until needed. Plug it in 15 min before needed without the USB connected until it stops spinning.

Just something for you to try. lol

---

### Post by ruberad on 2018-02-02
Tried it on a 16.04 laptop, first plugin it didn't work, but there were error messages in dmesg. Yanked it out and plugged it back in again, and it worked!

Went back to the 16.04 desktop, still NOTHING. Light comes on, disk spins up, but nothing added to dmesg, nothing extra in lsusb, etc.

---

