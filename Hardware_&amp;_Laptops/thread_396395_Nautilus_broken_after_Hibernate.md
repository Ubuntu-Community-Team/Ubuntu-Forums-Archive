---
title: "Nautilus broken after Hibernate"
date: 2007-03-29
forum: Hardware &amp; Laptops
---

### Post by FuriousLettuce on 2007-03-29
I've had Ubuntu installed on my HP nc4200 for a couple of weeks, and I've been having a couple of problems. I put most of the down to alpha / beta software that I installed immediately after installing Ubuntu. I reinstalled Ubuntu earlier this morning, to try to rid myself of these issues, however one remains: Nautilus really acts up after a hibernate. What happens is that, after the reboot, if I try to access a folder any way (Places -> Home, File -> Open etc), the Nautilus 'shell' opens up (see the screenshot), but the icons take an age to load (~2 mins +) and navigating is a joke.

I just found out, it only happens in my ~/ folder, not even the subdirectories (e.g. ~/images etc). This issue persisted over a reformat. Originally, I had the entire system in one partition, and now I have the system as / and a separate partition for /home/, so I know it can't be a file existing from earlier installations.

After further tests, turns out it's not a Nautilus problem, it happens if I try to 'ls -al' in my home folder in gnome-terminal, but not if I do 'ls' - sounds like it's something to do with one of the filenames of the hidden files within the folder (even though I haven't got Nautilus to show hidden files). As I say, it must be an automatically-made file, as it persisted over a reinstall and reformat, and only after a hibernate/suspend.

There's a file in my home directory, '.gtkrc-1.2-gnome2', which states it was written by gnome-settings-daemon, and it says to include "/home/ben/.gtkrc.mine", which doesn't exist. I did 'touch ~/.gtkrc.mine', but it didn't make a difference. 

UPDATE: Turns out it's to do with my samba mounts, ~/series and ~/films. They automount using fstab, but obviously they're network shares, so I have to be connected to the network for them to be mounted. On initial boot, they only mount once the network is up, but after hibernate/suspend, they don't mount properly (see the second screenshot). The problem goes away after they're unmounted / remounted. 

If anybody has any ideas on what's going on, please give me a shout!

---

### Post by FuriousLettuce on 2007-03-29
Sorry to bump my own post, I just wondered if anybody had any insights now that I've edited the above post to add more info.

---

### Post by CycleGeek on 2007-05-23
I'm not liking it too - hoping that it gets fixed.  In the meantime you can just log on manually to your SMB shares using Places --> Connect to Server if you know your IP.

---

