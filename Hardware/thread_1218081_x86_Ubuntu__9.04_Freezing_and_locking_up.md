---
title: "x86 Ubuntu  9.04 Freezing and locking up"
date: 2009-07-20
forum: Hardware
---

### Post by perimere on 2009-07-20
I have a Shuttle PC Barebones:
[http://au.shuttle.com/product_detail.jsp?PI=247](http://au.shuttle.com/product_detail.jsp?PI=247)

With a Dual Core Duo, 2GB RAM and a 400GB HDD. When I perform a fresh installation of x86 Ubuntu 8.10, everything goes fine. 

However I noticed that as the system does its initial update after install that it just hung. Picture on the screen, but zero response - no numlock etc. Power On and the Off, and away we go again.

This intermittent system freeze is happening a lot - once an hour if I'm doing stuff - different things were triggering it. If I leave the system unattended but on, it won't last overnight.

This box has happily run both XP and Linux From Scratch 6.3 (no X-windows) without ANY issues. I did a fresh install with x86 Ubuntu 9.04 and have the same freezes.

As a test I installed x86 Ubuntu Server 9.04 and I don't get them as frequently, but if I leave the Shuttle on overnight it's locked up and frozen by morning.

Has anyone else seen these frequent lock-ups?
Any ideas how to isolate and remediate the issue?

I'd really like to be running x86 Ubuntu 9.04 on this as it has a Drobo USB device sharing storage (via SAMBA) for the family which I'd like to be able to leave on.

TIA

Cheers,
Adam

---

### Post by DEagleson on 2009-07-20
I read that Ubuntu 9.04 have some problems with Intels GMA series, and the specs say yours is Intel GMA 950.

---

### Post by perimere on 2009-07-20
Thanks for the advice mate. My first thought was Video related.

Thought running server with no x-windows might have ruled this one out though?

In the mean time will focus my search around known issues on the Intel GMA 950.

Cheers,
Adam

---

### Post by perimere on 2009-07-25
Okay, an update ....

I've dropped a Nvida GeForce 7300 card into the shuttle - there's nowhere in the BIOS to disable the on-board video, and I haven't found if there's a jumper on the MB yet.

Re-installed x64 Ubuntu 9.04, and I'm getting copious amounts of hard freezes now - like every few minutes.

Primarily because I'm trying to use the Update Manager, and I was trying to shift the Video drivers to the NVIDIA accelerated graphics driver (version 180).

I have been unsuccessful in completing an update through the automatic software update prompt as the system freezes.

I have just tried looking through the logs in /var/logs and the system froze again, about 30 seconds into scrolling through the Xorg log.

Currently this system is completely unstable.

Does anyone have any suggestions on how to progress troubleshooting?

Cheers,
Adam

---

### Post by perimere on 2009-07-29
Well I threw XP on as a test and it worked fine.

To be sure I flashed the BIOS with the latest release again, and then for sh*ts and giggles threw 9.10 Alpha 3 on to see if things are likely to improve at all ...

.. and amazingly the freezes have abated. Running the Version 180 NVIDIA driver and currently 2 days up time with Samba and MythTV running with zero issues - w00t!!:popcorn:

---

