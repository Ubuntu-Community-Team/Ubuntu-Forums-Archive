---
title: "Freezing at &quot;Starting up...&quot;"
date: 2008-08-30
forum: General Help
---

### Post by sixfoottallrabbit on 2008-08-30
Hi,

I've been asked to have a look at and attempt to fix a PC.

It's (supposed to be) running Ubuntu 8.04.1 kernel 2.6.24-19-server, but straight after GRUB, when it says "Starting up...", it freezes.

I was wondering if anybody had any general ideas. I can use a copy of the live CD and see what I can do from there, but I was just hoping for some pointers before I have a stab at it.

Is this common or not? Must be quite serious for it to stop straight away, right? Could just a disk check sort it out and does the live CD have such a utility?

Thanks for your help.
-sixfoottallrabbit

---

### Post by Vivaldi Gloria on 2008-08-30
1) Did ubuntu ever work in that computer?

2) What are the specs?

3) Have you tried to choose another kernel in the grub menu? Press ESC at the boot to see the menu.

---

### Post by sixfoottallrabbit on 2008-08-30
> **Vivaldi Gloria said:**
> 1) Did ubuntu ever work in that computer?

As far as I'm aware, no, but I'll have more information on this soon.

> **Vivaldi Gloria said:**
> 2) What are the specs?

Again, more information soon. Sorry about that.

> **Vivaldi Gloria said:**
> 3) Have you tried to choose another kernel in the grub menu? Press ESC at the boot to see the menu.

The only other option in GRUB is to boot the recovery mode of the same kernel, which also does the same thing; freezes at "Starting up...".

Thanks.

---

### Post by EmanresuusernamE on 2008-08-30
Have you tried booting into the Ubuntu Failsafe mode and have it repair your X server settings?

---

### Post by Vivaldi Gloria on 2008-08-30
I'm curious if it has at least 128 MB ram. Otherwise ubuntu won't work.

---

### Post by Vivaldi Gloria on 2008-08-30
> **EmanresuusernamE said:**
> Have you tried booting into the Ubuntu Failsafe mode and have it repair your X server settings?

I'm assuming that it has ubuntu server installed (sixfoottallrabbit, correct me if I'm wrong). So there is no X.

Besides, it cannot pass grub even in recovery mode.

---

### Post by sixfoottallrabbit on 2008-08-30
> **EmanresuusernamE said:**
> Have you tried booting into the Ubuntu Failsafe mode and have it repair your X server settings?

How exactly would I go about doing this? Will I lose any data or configuration settings? Sorry to be a pain.

> **Vivaldi Gloria said:**
> I'm curious if it has at least 128 MB ram. Otherwise ubuntu won't work.

I just opened it up. It has 256MB of DDR PC2100 at 266MHz.

---

### Post by EmanresuusernamE on 2008-08-30
> **sixfoottallrabbit said:**
> Ubuntu 8.04.1 kernel 2.6.24-19-server
My bad, didn't see that it was the server version.

---

### Post by Vivaldi Gloria on 2008-08-30
> **sixfoottallrabbit said:**
> How exactly would I go about doing this? Will I lose any data or configuration settings? Sorry to be a pain.

That works in ubuntu 8.04 desktop systems. You probably have a server system because you have the server kernel. Can you learn if ubuntu ever worked on that machine?

Also, are there any files in it that you need to backup or can you just install a fresh sytem?

---

### Post by linux_tech on 2008-08-30
2 things make sure you are getting correct architecture (i386, amd, powerpc etc.) Make sure you are downloading desktop version.

If it only has 256 MB Ram, use the alternate install method
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Check here if you need the alternate desktop CD. This CD does not include the Live CD, instead it uses a text-based installer.
The alternate install method provides installation on systems with less than 320 MB of RAM.

You may also want to check out xubuntu-http://mirror.anl.gov/pub/ubuntu-iso/CDs-Xubuntu/8.04/release/

You should create a swap partition to help boost performance.
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

---

