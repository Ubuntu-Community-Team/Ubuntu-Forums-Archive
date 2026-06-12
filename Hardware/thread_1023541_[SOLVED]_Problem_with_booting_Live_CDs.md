---
title: "[SOLVED] Problem with booting Live CDs"
date: 2008-12-28
forum: Hardware
---

### Post by Nyr on 2008-12-28
Well, this is annoying...

I attempted a bit earlier tonight to boot from my Gparted Live CD, which I have done several times in the past without a glitch. So the Gparted Live CD starts loading, but while it's loading the drivers, it stops and hangs at the line "io scheduler cfg registered". I wait, nothing happens. I reboot - same thing happens. 

I reboot, change the Live CD for a Ubuntu 8.04 Live CD, boot from it. It starts loading properly... then about halfway through, it hangs, and after a while gives me the following error: buffer i/o error on device sr0 logical block 272752. The error repeats itself, again and again, with different logical block numbers.

This has never happened before. Just last week I managed to boot from various Live CDs (Ubuntu, Gentoo). I have searched over the Internet for some help, but didnt find any solutions that worked (one recommended changing the DMA setting in the Bios for the drive - my bios wont even let me do that). Some posts talked about a bad cable, but I hardly think that's the case, partially because, and this is important, the discs seem to load just fine in Ubuntu when I boot from the hard drive (the OS installed on the computer is 8.10).

Anyway, I'm quite puzzled and a bit worried. The computer is a Toshiba laptop (Satellite U300), the optical drive is a HL-DT-ST DVD RAM GSA-U1ON.

Any thoughts? Any input would be greatly appreciated, needless to say.

Thanks in advance!

Nyr

---

### Post by YouSmeg118 on 2008-12-28
Unplug all your USB Devices

I know that sometimes causes startup/installs to fail

---

### Post by linux_tech on 2008-12-28
maybe cd is damaged? try making a new live cd

---

### Post by Nyr on 2009-01-06
Well, I don't know what caused it - could be damaged CDs, as was suggested. I tried with a recent burn of OpenSUSE and Fedora, and they both worked, so I'm going to go ahead and say it was simply a case of old CDs. Now I feel silly lol. Anyway, thank you both for your input.

---

