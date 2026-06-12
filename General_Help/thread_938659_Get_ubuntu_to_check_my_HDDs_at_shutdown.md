---
title: "Get ubuntu to check my HDDs at shutdown"
date: 2008-10-05
forum: General Help
---

### Post by oblidor on 2008-10-05
Hi

I was just wondering if there is any package or way to get ubuntu to check HDDs at shutdown (not reboot) rather than start up? It is so annoying having to wait 20-60 minutes while one or several HDDs are being examined when you want to boot the PC. I know one can press Esc to skip the test, but if I press Esc every time they will never be tested. NOTE! I'm talking about the regular checks that are scheduled for each partition, not if the system was suddenly turned off or there is a problem.

One solution would be if the computer could test the HDDs on shutdown as well as start up. Then you could skip it on start up and let them be checked when you shutdown for the night.

If there is no solution at the moment for this, I hope it can be incorporated in future releases.

Thanks in advance

---

### Post by niteshifter on 2008-10-05
Hi,

If we're talking laptops, this is a very, very bad idea: Battery failure if fsck is doing something corrective is not pretty. Same reasoning for desktops, btw. Which makes distributions hesitant to do what you ask. A blown up file system is way more than annoying ;)

You can control how fsck works with tune2fs:
```
sudo tune2fs -c 0 -i 30 /dev/sda1
```
Turns off boot-counting control (-c 0) and enables interval control (-i 30), 30 days on the file system on the first partition of the first drive in this example. Set a task in your PIM to warn a day or two in advance, which you use with forcing a fsck:
```
sudo touch forcefsk
```
at the root of each file system you wish to check. It will then happen on the next startup, and resets the count / interval.
Using "-i 6m" will make it every 6 months. Using "-i 10w" makes it every 10 weeks.

Put the two together in a script:
```
#!/bin/bash
cd /
sudo touch forcefsck
sudo reboot

```


You can turn both count and interval control off. But that's living very dangerously. There be dragons ...

---

