---
title: "HP dv6000z hangs on boot after install, X does not appear to load"
date: 2007-01-08
forum: Hardware &amp; Laptops
---

### Post by Tauceti38 on 2007-01-08
I recently got a laptop from HP and have been trying to install Linux on it. I installed it once without any problems other than having to use the alternate install cd, but decided to reinstall it because of some wireless issues that seemed easier to solve from a fresh install. Unfortunately I've been plagued with problems since I tried reinstalling.

I have been using the alternate install cd for ubuntu 6.10 and have checked the cd for errors using the included error checker, and it found none.

Some info about my system:
AMD Turion 64 X2 Dual-Core TL-56(1.8GHz/1MB) 
1 gig ram
80 gb hdd, with a ~20 gb partition for / and a 2 gb swap partition
Nvidia GeForce Go 7200
Broadcom BCM4311 wireless card
I'm uncertain about the motherboard, I'll look for more info about it in a bit.

When ever I boot into the standard kernal I see the Ubuntu splash screen like normal, but after it is completed and gnome should load the screen just goes blank. I've tried letting it sit for a while then getting into a terminal with Ctrl+Alt+F1 but it doesn't work. I"ve tried all the F combinations but none of them have an effect. It appears to me that my computer is hanging right before it loads X, at least thats my best guess.

When I try booting using the recovery kernal I have different problems. It usually hangs at the line:
17179574.1440000] checking TSC synchronization across 2 CPUs:

Sometimes it makes it past that without any problems, but hangs on:
17179574.1840000] PCI: Ignoring BAR0-3 of IDE Controller 0000:00:0d.0

and occasionally I can make it into the command prompt, but that is very rare. It appears that Ubuntu never hangs on the above 2 lines during a normal boot, only on a recovery boot. I've tried starting gdm from the command prompt, but I get the same problem as if I boot with the normal kernal.

I've reinstalled it several times, and I managed to get into gnome after one install, but it hung after I updated everything and restarted to load up the new kernal. 

I just finished a memtest, and it came back with no errors.

Any suggestions? I've checked my xorg.conf and it looks like the resolution and refresh rates are all good, so I don't believe that is the problem.

---

### Post by Tauceti38 on 2007-01-08
Hmm, I just ran a disk check again, and it appears like some files are corrupted after all. I'll try burning a new cd and installing with it.

---

### Post by beniwtv on 2007-01-13
Hi

I own a HP dv6106 and I am getting exactly the same problems as you.

What I found out so far:

When I add rw quiet init=/bin/bash at least I can get into an command prompt.

I will let you know when I find out more.

Has anyone the slightest idea what could cause these problems? Let me know if you find out more about this.

Hint: It is not - so it seems - my instalation CD. It passed the md5sum test, also it passed the CD check & the written data verifying after burning.

---

### Post by Tauceti38 on 2007-01-13
I've discovered so far that I can get into gnome on my first boot if I select the wifi card during the network interface setup instead of the lan. Once I'm in I can get it up and running by installing the nvidia drivers, but unfortunatly I can't get it working with anything besides the 386 kernel, which leaves me with no smp support. I've also tried installing the server edition then adding gnome and ubuntu-desktop, but haven't had much success their either.

I also haven't had any success getting the broadcom card working. rmmod ndiswrapper always returns an error that it can't find the ndiswrapper module, and I get an invalid driver when I setup ndiswrapper from both source and synaptic.

I stumbled across a page dedicated to this series of laptops that has some useful advice, although not much has worked ](*,) 
[https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29](https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29)

I'll try out the tip for booting to command line next time I get the blank screen, I've been looking for something like that.

---

### Post by beniwtv on 2007-01-13
I also tried everything for the wireless card, and I think I can get it to work. 

I am now on Debian Etch - I wanted to know if this was an Ubuntu issue - and to my concern it is,  Debian runs fine until now.

I installed the last Nvidia drivers from nvidia.com and got the card to work also.

Same problem as you: SMP support and frequency scalling is missing. I will see if I can get another kernel.

What I plan to do now is:

1) Install Ubuntu console-only system. This seems to work for me.
2) Update with apt-get and restart
3) Compile own kernel since I think it is a problem of the ubuntu kernel and see if something changes

Cheers

---

