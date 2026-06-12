---
title: "Older ubuntu server breaking hard drives?"
date: 2017-04-11
forum: Hardware
---

### Post by ziphnor2 on 2017-04-11
Hi,

I have a fairly old home server running Ubuntu (originally 14.04 i think).

Its an i3 530 on an Intel DH55TC motherboard, and over its lifetime it has killed off quite a HDDs. Most recently it killed a Seagate 8TB Archive disk after ~6 months of use. Before that it has worn down 3x2TB WD disks, and one other disk i don't remember the exact size of.  I think the only long term survivors are a pair of 1TB WD drives. The load on the disks is not very big, it simply serves as a NAS and Plex media server.

The disks have been running under LVM in case that matters.

I am considering upgrading the hardware (say a G4560 CPU + a B150 mobo), but i would like to understand if my issue is likely to be a hardware or a software issue.

I suppose it must either be a temperature problem (too many disks in a small box), a hardware issue ("stupid" or defective controller) or a software problem (causing unnecessary wear on the disks).

---

### Post by QIII on 2017-04-11
My servers don't destroy disks.

Your most likely culprits are heat or a faulty power supply.

It might be worth your while to install [lm-sensors]("https://help.ubuntu.com/community/SensorInstallHowto") and hddtemp and monitor your voltages and temperatures to see what's up.

---

### Post by Autodave on 2017-04-11
I'm with Qlll here: check the PS voltage and also watch for spiking: preferably do this with everything running as usual. Next, get some more air moving *through *the case: not just around inside the case.

---

### Post by ziphnor2 on 2017-04-11
Interesting point on the power supply, i had not considered that at all actually. I was originally using a good Silverstone PSU, but it got fried when i forgot to disconnect it while an electrician was measuring, so i had to replace it with some old "gaming" PSU i had lying around. I suppose that could be the culprit, or maybe some power supply circuitry on the motherboard was damaged at the same time.

The temps i checked previously a few times, they were not ideal, but still the HGST i replaced the 8tb archive with has recorded max 47C so far. 

I will check the voltages, and if i see anything then probably end up going for some new hardware to ensure there are no PS issues hiding. My plan is to replace it with a case-less server (its already in a small rack cabinet anyway) so temps should improve.

Luckily all but one failed disks so far has been within warranty, and has been replaced for free, but its a huge hassle each time.

---

### Post by efflandt on 2017-04-13
I had a computer at one time that had 4 drives in it and was running SETI@home at low nice, but effectively running the CPU 100% continuously. I forget what the symptom was, maybe I couldn't save a file and logs stopped logging, apparently because the drives overheated. I removed the plastic front of the case and with the PC sitting on a carpeted floor like a vacuum cleaner, the front of the case and inlet fan were totally packed with lint. I cleaned out the lint and everything worked fine.

I currently have a headless Celeron 333 MHz PC in my basement that has been running almost non-stop (only shut down for long power failures) since 2003 with one drive running constantly and the other 2 on standby unless I access them. I forget which of the drives was a warranty replacement, but they are just 20 - 30 GB drives. The only drive I had fail recently was a 1 TB Seagate drive that began failing after 3 years when I started filling the Linux partition at the far end of the drive with Steam games. I replaced it with a WD drive, but currently boot Ubuntu from 512 GB mSATA (from failed laptop) in a SATA adapter. I have never tried lvm or drive encryption, so I don't know if those make minor drive failures more difficult. I have only had a drive fail suddenly once and that was a rarely used Win98 drive, so no great loss. Other failures have been gradual deterioration.

---

