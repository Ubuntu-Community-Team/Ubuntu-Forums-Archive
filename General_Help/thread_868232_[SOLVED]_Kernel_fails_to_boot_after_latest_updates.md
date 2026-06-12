---
title: "[SOLVED] Kernel fails to boot after latest updates"
date: 2008-07-23
forum: General Help
---

### Post by TorqueyPete on 2008-07-23
I had to revert to the previous one. After allowing the most recent software updates. I'm a bit of a numpty so please bear with me if I have to do stuff to my system.
 Took a pic of the frozen screen during boot.

[IMG]http://i81.photobucket.com/albums/j226/chashugh/kernelboot.jpg[/IMG]

 What do I do next?
Any help is thanked in advance! :)

---

### Post by phidia on 2008-07-23
Can you boot in recovery mode? If so when you are able to login you can check /var/log/messages or you can use a livecd to look at your install and /var/log.

I also wonder if this is an actual freeze-when the screen stops can you open a tty by pressing Alt+Ctrl+F1?

---

### Post by Amarsingh0793 on 2008-07-23
Well have you tried booting into another previous Kernel (if you have GRUB, it's easy)?

---

### Post by phidia on 2008-07-24
> **Amarsingh0793 said:**
> Well have you tried booting into another previous Kernel (if you have GRUB, it's easy)?

Originally posted by TorqueyPete;
>  I had to revert to the previous one

---

### Post by danwood76 on 2008-07-24
Im assuming you have the proposed updates repo enabled.
There is a known bug in the -20 kernel so you just have to use the previous one.

---

### Post by TorqueyPete on 2008-07-24
Ah, back home again!
thanks for the replies folks!
 Er, yes , no.
 Yes, it's the 20 kernel, and I tried recovery, but no, to no avail.
If the repo is enabled by default, then it's enabled.

What's grub? I have some on a plate in front of me right now. A delicious spring onion, olive and herb omelette, but I suspect it's not that sort. :)

---

### Post by skankster on 2008-07-24
Grub is the app that lets you boot whichever OS you want from those installed on your system (that reads terribly, but you get the idea). This includes the kernel versions. 

It's probably what you used to select -19 kernel version instead of -20.

---

### Post by coffeecat on 2008-07-24
> **TorqueyPete said:**
> If the repo is enabled by default, then it's enabled.


The Proposed updates repository is **not** enabled by default. You must have enabled it. This is the only way you could have got the -20 kernel.

---

### Post by TorqueyPete on 2008-07-24
Okys, thanks guys.
 I'll just keep using -19 kernel till I hear that the bug's fixed, or the kernel's updated again.

I'll go check for the bug fix right now. Presumably there are reports filed.

---

### Post by skankster on 2008-07-24
> **coffeecat said:**
> The Proposed updates repository is **not** enabled by default. You must have enabled it. This is the only way you could have got the -20 kernel.

It's easy to do then forget. There's many "tips" out there that tell you to turn it on. Some have reasonable caveats, but not all.

Anyway, here's a thread on the boot issue. There's a link to the bug, which has instructions on how to uninstall the update. You'll need to have booted to -19 first though.

[http://ubuntuforums.org/showthread.php?t=868249](http://ubuntuforums.org/showthread.php?t=868249)

---

### Post by TorqueyPete on 2008-07-24
Cool, thanx again. :popcorn:

---

### Post by TorqueyPete on 2008-07-29
Well, the latest updates tonight seem to have taken care of the problem. I'm not aware of the technical side of it all, but this little issue is SOLVED! :guitar:

---

