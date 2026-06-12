---
title: "Network Manager errors on shutdown"
date: 2009-01-26
forum: Hardware
---

### Post by tx836519 on 2009-01-26
I installed Ubuntu 8.04 (Hardy-Heron), dual boot with Win-XP.  This machine is networking in both windows and Linux modes with the balance of my network.  It is giving no problem at all in operation, but I consistently get the same error messages on each and every shutdown.  I also get these errors on shutting down from a LiveCD session.  I have two other machines running the same version of Linux - one as my windows network server and the other as my network archiver.  Both of these machines are running flawlessly.

My hardware is as follows:
	PowerSpec 8921
	Processor:  Intel Penium 4
	Core Freq:  2.53 GHz
	System Bus:  533 MHz
	Caches:  8k Level 1 data cache, 512 Level 2 Adv. Transfer
	System Board:  FIC VI-39L
	SiS 962 HyperZip Media I/O Chipset
	Memory:  1 GB

On each and every shutdown, I get these messages:

Network Manager: <WARN>  nm_signal_handler(): Caught signal 15, shutting down normally

Network Manager: <info>  Caught termination signal

Network Manager: <debug> [1233020465.851143] nm_rint_open_socks(): Open Sockets List:

Network Manager: <debug> [1233020465.851349] nm_print_open_socks(): Open Sockets List Done.

Network Manger: <WARN>  nm_hal_deinit(): libhal shutdown failed - Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the replay, the reply timeout expired, 0r the network connection was broken.

Do I have something improperly configured in the OS or am I seeing an OS/hardware incompatibility issue?

---

### Post by ASchweitzer on 2009-01-27
I've gotten similar errors running Ubuntu 8.04 with my wireless card and madwifi(dunno how much of that is relevant), but I've never had any further problems with it.

---

### Post by Yashiro on 2009-01-27
I think it's just an issue with network manager and how it is closed. I have seen that error on my wired lan too. Usually occurs if you shut-down with many connections open.

Log out, then shutdown. See if you still get the error.

---

### Post by tx836519 on 2009-01-27
Yashiro, I did as you suggested:  Logged out and then shut down.  I got exactly the same error messages.  Also, note that I stated that it gave these same errors if I boot LiveCD and then shut down.  So far as connections, the other boxes probably have more than this one and do not have a problem.  -- ken

---

