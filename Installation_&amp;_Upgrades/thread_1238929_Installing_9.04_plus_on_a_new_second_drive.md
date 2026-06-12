---
title: "Installing 9.04 plus on a new second drive"
date: 2009-08-13
forum: Installation &amp; Upgrades
---

### Post by ubuntu1sttimer on 2009-08-13
Got a new computer that came with Vista on a 320 GB serial drive. I have a new unused 500 GB serial drive that I want to install as a second drive with 9.04 plus one or both of the video versions, Mythbuntu and Ubuntu-Studio. I am new to serial HDs but assume that the 500 GB drive is not formated.

The question is, after installing the new drive, how do I get 9.04 on the new drive. I understand that I must use the Vista disk management program to set things up. Is that true and what questions do I need the answers for to do this? Ubuntu is going to ask how much space for the different partitions, what do I give 9.04 so that I still have room for the additional Ubuntu version on the second drive. It is possible that I will need to share video data files between the different Ubuntu versions. Can I do this without getting into SAMBA or something like that?

Questions, questions, and more questions! Any ideas or suggestions are welcome.

---

### Post by mikewhatever on 2009-08-13
> **ubuntu1sttimer said:**
> Got a new computer that came with Vista on a 320 GB serial drive. I have a new unused 500 GB serial drive that I want to install as a second drive with 9.04 plus one or both of the video versions, Mythbuntu and Ubuntu-Studio. I am new to serial HDs but assume that the 500 GB drive is not formated.

The question is, after installing the new drive, how do I get 9.04 on the new drive. I understand that I must use the Vista disk management program to set things up. Is that true and what questions do I need the answers for to do this? Ubuntu is going to ask how much space for the different partitions, what do I give 9.04 so that I still have room for the additional Ubuntu version on the second drive. It is possible that I will need to share video data files between the different Ubuntu versions. Can I do this without getting into SAMBA or something like that?

Questions, questions, and more questions! Any ideas or suggestions are welcome.

First, I am assuming the computer is a desktop and the new hdd is an internal one, and you plan adding it to the desktop.
I'd also assume that the new hdd is not formatted, which is unimportand because you can both partition and format it.
It's advisable to use the Vista program to manage Vista's own partition, but isn't necessary otherwise. In fact, don't think it can handle creating Linux file system, so the answer is no, you don't need to use it.
Ubuntu needs two partitions, root and swap. You can share the swap partition for all Linux installations and possibly even create a shared home, but since you are new, I'd suggest the following:

swap -- ~ 1-1.5 GB
root -- Ubuntu ~ 20GB
root -- Mythbuntu ~ 20GB
root -- Ubuntu Studio ~ 20 GB
storage ~ the rest of the space

There is no automatic setup for that, so that you'll need to partition manually.

All Linux partitions, as well as the Vista one, will be readable and writable from all *buntu installation, so that you'll only need Samba to share files between computes.

---

