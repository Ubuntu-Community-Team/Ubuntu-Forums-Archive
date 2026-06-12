---
title: "Having trouble installing 9.04"
date: 2009-09-30
forum: Installation &amp; Upgrades
---

### Post by justins1983 on 2009-09-30
When I select install kubuntu my screen loads to a small box with what looks like a drive, a globe, a tools or settings symbol and then goes blank and starts to reload the same screen. I'm trying a fresh installation because my computer has been acting up the last few weeks after some automatic updates. Occasionally it will lock up and force a hard restart where it wont boot the first couple of tries and only then after about 20 minutes being off. I have to go into grub and select kernel 2.6.24.18 (i believe?) otherwise when I attempt to log in the screen simply refreshes instead of going to desktop. The problem with the installation screen is similar except it wont even finish loading. Ive already backed up all of my data so would simply formatting the drive and starting over work? If so, how can I manually format my drive without being able to use the installation disk?

---

### Post by lidex on 2009-09-30
[GParted Live]("http://gparted.sourceforge.net/livecd.php") should work. Can be run from usb or disk.

What do you have currently installed? And you're trying to install kubuntu 9.04? Is that x32 or x64? What are the specs on your PC? Do you have backports enabled in software sources?

---

### Post by justins1983 on 2009-09-30
I installed 7.x a year or two ago and just upgraded since. My upgrades are current but I cant log in with the most recent kernel release. I'm trying to install the x64 version as I have a 64bit processor. AMD3000+, 1gb ram, sata160gb hard drive, liteon 16x cdrw and onboard audio/video/ethernet. I dont know if backports are enabled.

---

### Post by lidex on 2009-09-30
I would go ahead and follow through with your plan since you have backed up your data. GParted live should reformat for you.

---

### Post by rreese6 on 2009-09-30
You problem sound more hardware related.
First is the inside of your computer free of dust.
after that I would run the Memory test from the grub menu.lket it finish at least 2 passes (good to start then go to bed)
once that is done, then we can look to see if you are having hard drive problems....It is acting very unusual.

---

### Post by justins1983 on 2009-09-30
I have run the memory test, no errors after 4 or 5 passes. I have also run the disk check and repair option in recovery mode several times after hard restarts. It occasionally finds orphaned inodes or something like that and repairs them. Never any other errors though. I suspect theres something wrong with my video. When I log in my screen forces me to scroll and the mouse is a big artifact block until I run the screen resize and rotate program. As soon as the program launches my screen and mouse return to normal but I have to do this every time I reboot.

---

### Post by rreese6 on 2009-09-30
Sometimes the Connectors on inserted cards like memory, video, sound, get dirty and that can make your system act crazy. To clean the edge connections use the blank side of a business card or blamk side of a 3x5 card and rub the connectors until the paper is clean. Also make sure the heatsink for the CPU is not clogged with dust..
Check BIOS to see that "Plug and Play OS" is disabled.
as a retired engineer of over 30 years, I have seen systems that display these very same symptoms as you describe above.

Once we have eliminated any possible connection issue, then we will be able to diagnose what device is causing the issue.

also paste here the output of this command:
```
dmesg | tail -n20
```
to see what any errors are present once you boot up.
do this as soon as you boot up the desktop.

---

### Post by justins1983 on 2009-10-01
> **rreese6 said:**
> Sometimes the Connectors on inserted cards like memory, video, sound, get dirty and that can make your system act crazy. To clean the edge connections use the blank side of a business card or blamk side of a 3x5 card and rub the connectors until the paper is clean. Also make sure the heatsink for the CPU is not clogged with dust..
Check BIOS to see that "Plug and Play OS" is disabled.
as a retired engineer of over 30 years, I have seen systems that display these very same symptoms as you describe above.

Once we have eliminated any possible connection issue, then we will be able to diagnose what device is causing the issue.

also paste here the output of this command:
```
dmesg | tail -n20
```
to see what any errors are present once you boot up.
do this as soon as you boot up the desktop.

Ok, thanks for the advice. I will shut down, do a thorough cleaning and restart to get those codes and post them. Currently I am working so perhaps I'll have a chance later tonight. My machine runs fine in windows 2000 but I rarely use that OS and it is on a separate hard drive.

---

