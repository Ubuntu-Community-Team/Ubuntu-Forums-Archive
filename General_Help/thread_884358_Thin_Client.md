---
title: "Thin Client?"
date: 2008-08-08
forum: General Help
---

### Post by Megatog615 on 2008-08-08
My little brother uses another computer with Ubuntu 8.04 on it with a failing hard drive(and I don't have the money right now to buy him a new one). Before all data is lost, I want to know if it's possible to set up a thin client system on my main PC(also running Ubuntu 8.04), and let his computer connect to it. My main PC(which would run the thin client server) is 64-bit so I would probably have to make a 32-bit chroot somewhere on the disk.
For the client I would want to connect to a remote home folder(where I've backed everything up) on the main PC in its real /home directory. I would do this with nfs, correct? Or would I just symlink the /home/user into the chroot?
I also want the client to be able to update the system, add new packages, and generally be able to modify the chroot like he would be able to if it were on a local disk. But I do not want him to be able to modify anything outside the chroot besides his home directory.

A thin client system is a read-only system, right? If a thin client system wouldn't work, how would I get his computer to boot a kernel over the network, then pull a chroot in over NFS? I would think this method would allow persistent changes?

I basically want to set up a system that emulates his old standard hard-disk filesystem in a way that it's fetched over the network, and can save persistent modifications. I've already backed up his data and am ready to start.

---

### Post by dcstar on 2008-08-09
> **Megatog615 said:**
> 
..........
I basically want to set up a system that emulates his old standard hard-disk filesystem in a way that it's fetched over the network, and can save persistent modifications. I've already backed up his data and am ready to start.

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

---

### Post by Megatog615 on 2008-08-09
I'm sorry, I don't have a pendrive large enough to even fit Ubuntu on and as I said I can't afford one. I need his computer to boot using PXE, load a kernel, then mount a chroot on my computer with NFS.

---

### Post by goldfish654 on 2008-08-09
I think this might be what you're looking for:

[https://wiki.ubuntu.com/DisklessUbuntuHowto](https://wiki.ubuntu.com/DisklessUbuntuHowto)

---

### Post by Megatog615 on 2008-08-10
Is it possible to do this behind a router, rather than directly connecting each computer?

---

### Post by BlackRabbit_BE on 2008-08-12
Behind a router?
If his computer is located 'outside' your network (on the 'outside' of your router), you will have to forward some ports.


However, I suppose both computers are 'inside' the same network, and you probably mean: "does it work when both computers are connected on my router (/switch)". The answer is yes, without adjusting any settings.




A small question about PXE (I'm confused reading several reports):
- does it merely boot a window manager towards the server, and from there on, does the server perform all the client's work? (aka: function as thin client)
- or does it rather boot the OS over network, with the OS (after boot) running on the client itself (fat client?)

Or can it do both?

---

### Post by Megatog615 on 2008-08-14
But how does the client machine get the PXE if it doesn't know which machine to get it from? I'm under the impression that the client must be connected to the server directly.

---

### Post by BlackRabbit_BE on 2008-08-22
'directly' yes, as in "on the same network" (e.g.: 192.168.0.xxx).

I haven't used PXE yet, bu I believe you will need to provide this info through your local DHCP server (as PXE uses DHCP-protocol extensions).

---

### Post by ByteJuggler on 2008-08-22
[This]("http://beginlinux.com/server_training/126-linux-terminal-server/1053-ltsp-on-ubuntu-804") is probably relevant.

---

