---
title: "kernel requires 0:6"
date: 2009-03-28
forum: Installation &amp; Upgrades
---

### Post by Thasaidon on 2009-03-28
Hi all,

I tried to install Ubuntu 8.04.1 LTS Server Edition
on my Dell Latitude D500 laptop.

The install went just fine and everthing seemed ok.
But when the install is finished, it askes to reboot the system.
I did, but now every time the laptop boots and tries to start Ubuntu (Grub seems to work just fine), I get the following error:
```
Starting up...
Thes kernel requires the following features not present on the CPU:
0:6
Unable to boot - please use a kernel appropriate for your CPU
```

The laptop is a Dell Latitide D500
Latest BIOS revision A10
Intel Pentium M 1,3Ghz/600Mhz
512Mb SDRam
Intel 855GM video chipset
Sigmatel 9750 audio chipset

The strange thing is... Ubuntu 8.04 desktop edition works just fine when running from the live cd.

Does anyone know how I can get the server version running on my laptop?
I've found some threads mentioning I need a PAE/NX supporting CPU?
But those threads were talking about running in virtual machines.
And why would the server edition need this enabled whilst the desktop edition just runs fine without it?


Eventually I want this laptop to run as a router/firewall, with some services like mail, web and ssh, etc...

Thanx in advance

---

### Post by Thasaidon on 2009-03-29
anyone?

---

### Post by namaku0 on 2009-03-29
How about trying this: [http://www.rasyid.net/2009/01/28/the-kernel-requires-the-following-features-not-present-on-the-cpu-06/](http://www.rasyid.net/2009/01/28/the-kernel-requires-the-following-features-not-present-on-the-cpu-06/)

This is just a guess: A server usually have a large RAM, like
4 GB or more. So to make use all of them on 32-bit CPU you need
PAE. Hence the server version developers decided that PAE is
a must.

[http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)

---

### Post by Thasaidon on 2009-03-29
Thanx for the link, but where would I enter the commands as suggested in your link?

> That message show up when I try to install Ubuntu Server 8.04.2

Looking around, the solution :

    apt-get update
    apt-get remove linux-server
    apt-get install linux-386
    apt-get install linux-server

or change linux-386 with linux-generic

will solve that problem.
The Linux won't start and I can't run those command during setup.

Anyway, I think this might be a no-go on my laptop, since the CPU doesn't support PAE.

But thanx for the input.

---

### Post by Thasaidon on 2009-05-01
I found this on PAE, maybe others find this info usefull.
> In computing, Physical Address Extension (PAE) is a feature of x86 and x86-64 processors that enable the use of more than 4 gigabytes[1] of physical memory to be used in 32-bit systems, given appropriate operating system support. PAE is provided by Intel Pentium Pro and above CPUs (including all later Pentium-series processors except the 400 MHz bus versions of the Pentium M), as well as by some compatible processors such as the Athlon and later models from AMD.
Quoted from: [http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)

My problem lies in the fact that the laptop has the 400 MHz bus versions of the Pentium M CPU.
Bummer...

---

