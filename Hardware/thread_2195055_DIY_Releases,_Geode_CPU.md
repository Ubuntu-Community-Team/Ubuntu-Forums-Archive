---
title: "DIY Releases, Geode CPU"
date: 2013-12-22
forum: Hardware
---

### Post by madtom1999 on 2013-12-22
I've got a few old machines - and a very low power server with a geode cpu that wont upgrade to Precise as the cpu lacks a feature. How can I build my own release for it so I can upgrade?

---

### Post by mörgæs on 2013-12-22
Sorry, but I don't think it's worth the effort. The Geode is indeed very low power. 

There's so much used, but newer hardware around. Just take a look at what people throw away after Christmas...

If you really want to try then 10.04 Server is supported through 2015 (but not the desktop packages).

---

### Post by ian-weisser on 2013-12-22
It's possible, but not easy. Part of Ubuntu's simplicity for most users is the tight integration to avoid lots of extra configuration. That integration assumes a minimum level of hardware.
Seems like the minimum CPU requirements have changed to exceed the capabilities of your hardware.
If so, then stock Ubuntu is no longer appropriate for your hardware.

Debian has a wider variety of kernel options. Have you looked at it as an alternative?

Alternately, you can roll-your-own Ubuntu kernel. I've done that for low-power hardware to get a few more years out of it. Bit of a learning curve - you will spend a few days learning the process.

---

### Post by madtom1999 on 2013-12-25
Ian-weisser. Any info you can give from your learning curve please?

---

### Post by madtom1999 on 2013-12-25
There's no need for new hardware - this machine acts as a file server, web proxy and mail server and apt-cacher for 7 other machines on my network and almost never gets cpu bound. It runs on less than 7 kwh per year. Its not even worth investigating other machines.
I may try another distribution but I'd like to keep it ubuntu to keep networking costs down - moving to another distribution would probably cost me more per month in bandwidth charges so I may shift everything over.

---

### Post by ian-weisser on 2013-12-25
> **madtom1999 said:**
> Ian-weisser. Any info you can give from your learning curve please?

Most older hardware I've seen chokes on the pae requirement in the kernel. Current Ubuntu and Debian releases have non-pae kernels in the repositories/archives, and they are easy to install.

My older hardware has has it's share of hardware failures: RAM failures, card-reader failures, USB-port failures, motherboard failures, drive failures, power supply failures, and cable failures. My orientation changed from "Hey, that must be a bug in Ubuntu" to "Hmm, which kind of failure does this look like." 

Backups are vital. Well, backups are always vital.

I found it a great experience for learning the command line, serial port consoles, null modems, how to track and document the services I run, and exactly what I need to backup.

---

### Post by mörgæs on 2013-12-26
Madtom, please post the exact error message you get when trying to run a recent Buntu in a live boot.

---

### Post by madtom1999 on 2013-12-28
mörgæs - I cant remember the exact error message but I was running a do-release-upgrade and it complained of a missing cpu feature (cmov??). It seems to have removed the upgrade option as if I repeat the command I get 'no new release found'.

---

### Post by mörgæs on 2013-12-28
That was as I expected. Not a PAE problem, but CMOV. 

As I mentioned first, your choice of distro is limited and 10.04 server is the only one that comes to mind. You might google your way to another distro not requiring CMOV but don't install an unsupported one.

---

