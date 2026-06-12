---
title: "Ubuntu 20.04 is freezing randmply on OMEN by HP Laptop 15-dh0xxx"
date: 2020-07-20
forum: Hardware
---

### Post by romanianborg on 2020-07-20
Hi,
I've install ubuntu 20.04 on a brand new OMEN by HP Laptop 15-dh0xxx with geforce RTX 2060, and ssd SAMSUNG MZVLB256HAHQ-000H1.

Everything is working perfectly, even the RTX demos, wine, etc.. At first I had no sound but after a while it started to work.

BUT..
The system is unstable, because ramdomly is freezing... after reboot doesn't reboot, only after many retries.. and again..freeze, reset ten times, freeze..
No mouse, no keyboard, nothing is working, the image is frozeen, only the power button with x seconds resets.

I've installed windows 10 to test if the freeze is a harware issue, windows works for days, I had no freeze yet.
I've run all diagnostic tools I've got, 

I do not know how to get logs to see if the freeze is caused by someting .. audio seems to work or not after many restarts.

---

### Post by mastablasta on 2020-07-22
what version of nvidia drivers do you have installed? is this a Intel/nvidia combo or ryzen/nvidia?

brand new is not always supported by drivers. you could try and load a newer kernel (testing or similar):
[https://itsfoss.com/upgrade-linux-kernel-ubuntu/](https://itsfoss.com/upgrade-linux-kernel-ubuntu/)

you will need to uninstall nvidia drivers. read carefully:
[https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)

another option is to try a distro with more up to date kernel like Manjaro for example.

---

### Post by romanianborg on 2020-07-26
In ubuntu I've installed latest nvidia driver ~450, and the system is freezing too. (I didn't tried the free driver)


Today I've installed manjaro and system is stable, no freezing yet.. but I didn't had time to test it, I will test next week.

In manjaro nvidia works as free or nvidia 440 drivers.. (latest is >450, but not available in distro)

The only problem in manjaro is that the sound is not working. (maybe the sound drivers causes freezing problems), and the booting takes forever.. ~40sec.. (windows boots in 2seconds)
[http://alsa-project.org/db/?f=c0fdcdaaf090bac74ae5f9eb67f4f0103967e2be](http://alsa-project.org/db/?f=c0fdcdaaf090bac74ae5f9eb67f4f0103967e2be)

I do not know where to report this problem, alsa site says something about launchpad.. 

Thanks.

---

### Post by mastablasta on 2020-07-27
you could try installing Ubuntu and then addign latest kernel (i would say something stable). then if it works, report to launchpad. 

i am not sure what manjaro uses for reporting.

---

### Post by romanianborg on 2020-10-17
I've install ubuntu 20.10 beta, and I got into the same problems.
After that I've check the logs and HDA analog with some text and err -110..with zillion entries.. and that cause all problems.

I've disable module loading for sound:
mv /etc/modprobe.d/alba-base.conf .. somewhere

reboot and I got a stable system and sound works fine, no more freezes.

Maybe the laptop comes with 2 sounds systems, and the GPU one causes all problems.

---

### Post by romanianborg on 2020-10-17
Also nvidia 3d works, system boots in couple of seconds, hdmi works, etc like in windows.

Thanks.

---

### Post by romanianborg on 2020-10-19
For anybody that has the same problem, the solution for me is like this:
add a blacklist module in the file as root (with sudo)
/etc/modprobe.d/blacklist.conf
add line
blacklist snd_sof_pci
and the execute
sudo update-initramfs -u

this will boot with no problems, and no freezing

then to activate sound if needed just run
sudo modprobe snd_sof_pci


the sound will work, and the system is stable,

---

### Post by david-daking on 2020-10-20
> **romanianborg said:**
> For anybody that has the same problem, the solution for me is like this:
add a blacklist module in the file as root (with sudo)
/etc/modprobe.d/blacklist.conf
add line
blacklist snd_sof_pci
and the execute
sudo update-initramfs -u

this will boot with no problems, and no freezing

then to activate sound if needed just run
sudo modprobe snd_sof_pci


the sound will work, and the system is stable,


I have a problem with a laptop with it freezing, using Intel/Nvidia.
Your solution might work, if I can figure out what it is.

Would you please clearly show what file to be edited, what edits to make? What steps to take to get it working, please.

---

### Post by romanianborg on 2020-10-20
Another find is that, if you have no sound and start playing some youtube..
and activate with modprobe the snd_sof_pci, computer freezes instantly, no mouse, no keyboard.. reset from button

Another issues is trying to disable the touchpad from settings while sound active, results in a imediat freeze..,
but the touchpad remains inactiv at next forced reboot.

Otherwise the system is very stable. but this small issues causes a lot of psyhological pain.

---

### Post by romanianborg on 2020-10-20
install ubuntu 20.10 (as it has a better kernel)

choose ubunut recovery mod from the start
- drop to root shell

nice /etc/modprobe.d/blacklist.conf

at the end of the file add the line:
blacklist snd_sof_pci
[save] and exit

excute
update-initramfs -u

to reactivae sound open a terminal and execute
sudo modprobe snd_sof_pci

having no application running that uses sound

All this assuming you have a similar hardware.

---

### Post by david-daking on 2020-10-20
When I enter 
nice /etc/modprobe.d/blacklist.conf
at the root shell, it replies "Permission denied"

---

### Post by david-daking on 2020-10-21
I tried it with vim instead of nice and it worked, but even after making those changes, I still have a laptop that freezes after getting to the desktop.

---

### Post by romanianborg on 2020-11-17
> **david-daking said:**
> I tried it with vim instead of nice and it worked, but even after making those changes, I still have a laptop that freezes after getting to the desktop.

try to black list all modules that can cause the freezing, and activate one by one till you find the one that causes the freezing.

execute:
lsmod

to find all modules

remmember to run 
update-initramfs -u 

to make changes for next boot

---

