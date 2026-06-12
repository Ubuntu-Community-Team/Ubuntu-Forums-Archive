---
title: "Trimming down a bloated system."
date: 2009-10-04
forum: Installation &amp; Upgrades
---

### Post by rippin on 2009-10-04
Hey there - thank you for looking at this post.

Been a long-time Debian fan, yet, Lenny has some "features" which made it disappointing even awhile after upgrading (expected them to have corrected certain "problems" by now - no offense Debian!)

That said, I had a system with 68 processes while on my desktop of XFCE4.4. Now that I'm running Xubuntu 9.04 - and not having the prior problems, I am disappointed that this so-called  Xubuntu "light weight desktop" runs 106 procs. Trimmed things down a little bit - 96 procs - by unloading items using rcconf and removing ("A.K.A. "trimming") down the system software services. What I need to is to shell this OS out. leaving the following services availble:

apticron (if I un-install update programs it'll strip xfce4-desktop)
auto-mounting (and umount) of USB sticks, CD's and DVD's
sound system working - including with audio file for newly received email via TBird play back

On a side note: anyone know why gkrellm and conky report 150%  more procs than top?

Again, I appreciate your time,
rippin'

---

### Post by kerry_s on 2009-10-04
like debian you can start from a base install and build up just adding what you want. grab the ubuntu mini.iso, install the cli system.
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

it's as simple as:

**sudo apt-get install xorg gdm xfce4 synaptic**

process showing depends on the setup, programs thread, so it looks like more than there actually is. for example try using htop & put it on tree view. see pic

---

### Post by rippin on 2009-10-04
>  like debian you can start from a base install and build up just adding what you want. grab the ubuntu mini.iso, install the cli system.
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

it's as simple as:

sudo apt-get install xorg gdm xfce4 synapticCapitol idea! Thanks, I was not aware of that ISO. Just downloaded.

> process showing depends on the setup, programs thread, so it looks like more than there actually is. for example try using htop & put it on tree view. see picTried htop once *long* ago ... it's improved a fair bit. Gonna use it more now. Get back to you when done trimming. First, though, I have to go to work.

BTW, I'm envious that you have but 32 procs on a desktop!! Good job!!!

---

### Post by kerry_s on 2009-10-04
> BTW, I'm envious that you have but 32 procs on a desktop!! Good job!!!


thank you, that was my backup rig i was setting up, it's 700mhz 128mb ram, so i got to be tight, i set that 1 up with arch linux.
my usual is this 1, 450mhz 256mb ram running debian lenny custom gnome install.

---

### Post by rippin on 2009-10-05
> **kerry_s said:**
> thank you, that was my backup rig i was setting up, it's 700mhz 128mb ram, so i got to be tight, i set that 1 up with arch linux.
my usual is this 1, 450mhz 256mb ram running debian lenny custom gnome install.

Dang! You gotta tell me how you do this. Put on the new system using the netinst ISO you pointed out in "expert" mode - when it came to packages, I choose none. So, I should have a lean setup - not even a display manager (gdm, etc.). After booting, logging in, and running 'top',  the machine listed 78 procs in tty1. So, I put on rcconf and ended about half the listed services, plus cut gettys down to two. Ran startx and opened xterm with htop and there's 114 procs! Looking closer I learned /usr/sbin/console-kit-deamon is listed 63 times. ps aux | grep console-kit-deamon shows one PID in use. Yet, it has PID's listed in htop anywhere from 1988 to 16600. Bug? So, subtracting 114-63=51 procs?

If you hit F2, then enable Display Options -> Hide Userland Threads,  there's 63 threads while on the desktop ... and I found, after first posting this, there seems to be a bug all right.

[ATTACH]130881[/ATTACH]

[ATTACH]130883[/ATTACH]

---

