---
title: "Jaunty kernel .28 fails to load but .27 works"
date: 2009-05-05
forum: Installation &amp; Upgrades
---

### Post by govee on 2009-05-05
I have a Emachine D620 that I had$ dual booting to Intrepid on a usb hard drive and after I did the upgrade to Jaunty I can not load the .28 kernel. If I select the .27 kernel it works. I have tried everything I can think of or find in other threads that have been suggested and nothing works. I have added rootdelay up to 300 and about 10 different addtions to the grub. Any help oout there or insight when this will be fixed? I checked Launchpad and I can see a number of reports of this bug. 

On the positive side the .27 kernel had my Atheros wireless up and running out of the box, which was a first for me.

---

### Post by cariboo on 2009-05-05
Can you purge 2.6.28-11, and then reinstall it, to see if it makes a different. the kernel you want to remove is linux-image-2.6.28-11-generic

---

### Post by govee on 2009-05-06
I removed the kernel via synaptic and reinstalled, still no joy. Since I didnt use the purge command in a terminal, I am wondering if the removal was not as complete a removal task as the purge? If so what is the correct syntext to the purge command in the terminal?

---

### Post by pomalin on 2009-05-06
did you try boot the live cd or alternate cd of jaunty ? try it, and tell me, perhaps you have the same bug as mine :

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/343268]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/343268")

---

### Post by govee on 2009-05-06
I haven't downloaded the the live cd yet. I will tonight and report back. I read through the launchpad report and the problem seems similar. I did notice that none listed the "could not locate the hdd and gave up, dropping to shell". warning that I am getting.

---

### Post by ArthurTunstall on 2009-05-07
Thanks for posting the link to launchpad. Some of it looks very similar to the problems I've found - [http://ubuntuforums.org/showthread.php?t=1145427](http://ubuntuforums.org/showthread.php?t=1145427)

---

### Post by blackSP on 2009-05-07
Same here with me: [http://ubuntuforums.org/showthread.php?p=7230485#post7230485](http://ubuntuforums.org/showthread.php?p=7230485#post7230485)

---

### Post by govee on 2009-05-07
Just tried the live cd and I can boot to it. I did a fresh install and I get the same error on boot.

---

### Post by govee on 2009-06-03
I recently found a thread on a different forum and the temporary fix was to do a "modprobe usb-storage" at the prompt and let it run for a few seconds (until it reports back with a few lines), then type "exit" and boot will continue. This works, but I have to do it at every restart. I need to know how to get this applied automatically at startup.

---

### Post by govee on 2009-06-04
Just installed the new kernel from the Jaunty proposed repository and boot now executes with no issues.:guitar:

---

