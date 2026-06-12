---
title: "Ubuntu on an AMD K6-2 without network"
date: 2009-01-20
forum: Installation &amp; Upgrades
---

### Post by night_fox on 2009-01-20
Hi all, I've been trying to install Ubuntu (well xubuntu) on an ancient machine from 1998 with an AMD K6-2 processor. It's x86 architecture and halfway between an i586 and an i686. I've tried all kinds of cds including the alternate install cd. Each live cd I've tried has sometimes crashes when I try to boot from it giving me some kind of "crc error". The cds are not damaged or scratched in any way.

After trying the alternate install cd a few times it managed to install a minimal system but it froze at 6% when trying to install the packages. I managed to make it bootable, but theres no X11, no python, and no man command.

Most of the times it booted from the hard disk it gave me the same crc error. So I compiled a kernel on my laptop- the only option in the "make menuconfig" I changed was the cpu, where I specified the K6/K6-2/whatever. This kept giving me the same crc error but sometimes it booted properly.

I also built gcc on my amd K6 and set the default march and mtune options, and used that to compile a kernel with the same effect.

I also can't get ndiswrapper to work from the command line.

I also don't know how to get the packages from the live cd when running said compiled kernel.

Do you have any suggestions?
How can I find out what else about the kernel needs configured for this machine and what is causing the crc error?
How can I get the packages from the cd or get wireless working so I can apt-get them?

---

