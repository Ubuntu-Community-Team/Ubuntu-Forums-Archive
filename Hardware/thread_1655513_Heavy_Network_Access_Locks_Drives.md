---
title: "Heavy Network Access Locks Drives"
date: 2010-12-29
forum: Hardware
---

### Post by savanik on 2010-12-29
Hey all,

I've got a system we're trying to use software RAID5 on a set of five 1.5 TB drives for a media server. We put it together in March, but recently (for about the last two months) it's been having issues. Whenever heavy network access occurs, the server has issues. Specifically, while processes in memory continue to run, hard drive access is suspended and blocks any process that attempts to access it.

For example, you can type into the login prompt and it will then ask you for a password, but when it attempts to access the disk, the process hangs, waiting for disk access. If you are logged in at the time, you can type in commands into the terminal and it will respond until you attempt to actually run anything.

The primary thing that triggers this is copying files to the server. Network copy via rsync reach about 10.5 MB/s and then the system hangs after about 60 seconds. Streaming video files off the server to another computer also will hang the system.

Local copying of files works fine - I can plug in a USB drive and go to town at full rates all day. It's only when we attempt to copy files via the network that we get these issues. Copying files via network to a non-RAID drive exhibits the same problem.

CPU load drops to 0% when this happens - top continues to run during an event, until you attempt to quit to prompt. Then it hangs.

Things we have tried as troubleshooting:
Replaced ethernet cable. Replaced switch with a managed switch. Replaced WD EARS drives with Seagate drives in order to implement TLER settings. Changed from Gentoo to Ubuntu Server.

We're running out of things to change/replace. I'm about to see about buying a new gigabit network card and see if there's some driver issue with the onboard network adapter that's causing all this. Past that, I can only guess it needs a new motherboard. After that... I don't know, move to a Drobo? :confused:

If anyone has any suggestions or has seen problems like this before, please let me know. The problem is easily reproducable - if there's some command I could run and watch some part of the system to determine what's causing this, please let me know.

For gory dmesg and details, see attachments. If some other output would be more enlightening, let me know.

Savanik

---

### Post by savanik on 2011-01-07
Guess what! I figured out the problem, finally. South bridge was overheating.

Turns out that enough dust had accumulated over time that it was overheating under network load - and south bridge is NOT monitored by lm-sensors, so there were no indications pointing to that as the culprit! Since south bridge was handling both the network traffic AND our SATA bus, overloading one and overheating the chip takes down both.

We blew out the case, installed an ethernet card and disabled the onboard ethernet to reduce load on the bridge, swapped some of the fans for higher airflow, and everything is working just fine now.

---

