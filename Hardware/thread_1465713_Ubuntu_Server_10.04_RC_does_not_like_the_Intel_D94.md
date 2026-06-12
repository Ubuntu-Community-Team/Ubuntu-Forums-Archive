---
title: "Ubuntu Server 10.04 RC does not like the Intel D945GCLF mainboard"
date: 2010-04-29
forum: Hardware
---

### Post by fleder on 2010-04-29
Hey guys,

right now I'm in the process of upgrading my file server to higher capacity. It mainly consists of an Intel D945GCLF mainboard that comes with an Atom processor and is equipped with 2GiB RAM, and a hardware RAID system that maps 3 drives to the mainboard.

I've been using this thing with Debian Lenny for over a year now with no problems that would be worth mentioning.

All my data has been moved to a friend's computer so I've got a clean system to go wild with, and seeing that a new Ubuntu LTS Server version is almost done I tought this might come in handy for me. The hardware is nothing anybody would consider cutting edge (hey, Debian Lenny had no problem with it).

I am, however, running into problems with Ubuntu Server 10.04 RC both i386 and amd64 which express themselves in a certain chance of Ubuntu getting stuck during the boot process. In about 40% of all attempts to boot the system it will stall with the following text on the screen (or likewise):
```
fsck from util-linux-ng 2.17.2
fsck from util-linux-ng 2.17.2
dgroot: clean, 49507/1572864 files, 354597/6291455 blocks
dgboot: clean, 206/261120 files, 50298/522081 blocks
init: ureadahead-other main process (647) terminated with status 4
modprobe: FATAL: Error inserting padlock_sha (/lib/modules/2.6.32-21-generic-pae/kernel/drivers/crypto/padlock-sha.ko): No such device

init: ureadahead-other main process (799) terminated with status 4
```It is, however, not completely frozen -- when I press an arrow button I can toggle between this screen and some sort of simple Ubuntu Server boot splash. I also can hit Ctrl+Alt+Del and the computer will reboot in an orderly fashion. I just can't get to any login prompt in those cases.
I also can't pinpoint what may be causing this, it seems to occur completely randomly. Sometimes the computer starts up all right to the login prompt, sometimes it gets stuck with said message.

I have unsuccessfully tried the following things:

[LIST]
[*]Unplug everything that is not needed (in my case, all SATA devices and the rs232 cable to the RAID controller, essentially leaving the system with 2 hard drives (80GB each) as master and slave on the board's single IDE interface)
[*]Flash the BIOS to the latest version, reset it to factory defaults and re-configure it by hand again
[*]After that, disable the onboard audio chip
[*]Disable the onboard NIC (although I sort of need that, seeing that I'm trying to rebuild my file server)
[/LIST]
Does anybody have an idea what this might be about or where I can have a look at (some log files maybe) or what boot options I could play with?

Thanks in advance,
fleder

---

### Post by fleder on 2010-04-30
I've just tried Ubuntu 10.04 alternate i386 and here it pauses at the boot splash with the following message:

```
The disk drive for /tmp is not ready yet or not present

Continue to wait; or press S to skip mounting or M for manual recovery
```My disk drive for /tmp is the partition "sda3" which is set up to be encrypted with a random key during every boot sequence. It is supposed to hold an ext2 file system that should be auto-generated every time.

It seems that this does not work so well with Ubuntu 10.04.

My apologies, this might not be a hardware-related issue after all. Did somebody else run into similar problems?

fleder

---

### Post by ericeclifford on 2010-06-17
I think you are right,

I have a D945GCLF, 2 gig of ram, atom processor(comes with MB), integrated Graphics.

And I can not boot from a CD or USB live cd.

Well, I wont say I cant, sometimes I can.

I got passed the splash screen, and tried to install on a 80 gig WD HD, but it froze during the process with a I/O error.

Anyone having problems or solutions Please report here, I will bump this thread a few times a day until/if things get fixed.

---

### Post by C.S.Cameron on 2010-06-17
I just gave my daughter's DG945GCLF computer a try with a 10.04 32bit flash drive and it booted OK.
This MB has always required funky video drivers due to vertical lines.
I know my DG945GCLF2 works ok with 10.04 32bit flash drive but I normally boot from a XP flash drive so to get Svideo working, (It's an entertainment center stuck inside a muffin tin).

---

