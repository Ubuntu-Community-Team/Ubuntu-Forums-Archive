---
title: "Bootproblems please help!"
date: 2006-01-06
forum: Installation &amp; Upgrades
---

### Post by Swiss2K on 2006-01-06
Have Ubuntu running for a week or so and never looked back to Windows. Today I desided to format my Windows D: drive to Fat32 so i can use this space with Linux as well. The result is that Grub is not working (Thanks Bill). I looked into this forum (and others) And i'm at the point of throwing the PC out of my window.

Here is the situation on one 80GB HD
HDA1: NTFS Windows
HDA2: isn't listed ?!?
HDA3: Swap
HDA4: / Unbuntu 
HDA5: Fat32

I have a Knoppix CD an booted it. I've found out that all partitions are in tact. How on earth can I reinstall grub again??

On this forum someone says just boot the Ubuntu CD and 'recover' grub. On my (not live) CD there isn't such an option...


---> Forgot to say hello!! as this is my first post. Been reading this forum for the past week intensively and i like to admosphre here very much !! Ow and pardon my English..:)

---

### Post by Ubluntu on 2006-01-06
Hey, I'm not very good with linux boot partition stuff as I was having a similair problem the other day with a daily build install... I read something about grud-install or grub-installer or something at the command promt.. With the livecd's 'recovery console' you can't execute any shell commands with out entering special commands at the cd's boot menu. or typing it in at the shell promt. It's something like TERM=vt100; display; I can't remember, hopefully someone else does.
Once you get into a shell that you can run commands, that grub-install should help you out.
uhh, good luck I hate when you don't even have a boot menu, keep your patients tho, the worst thing to do is get pissed and makin your problem worse.

---

