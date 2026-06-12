---
title: "Move install from MicroSD to mSATA?"
date: 2019-01-24
forum: Hardware
---

### Post by monkeyman_stones on 2019-01-24
Hello,
       I'm creating this post because I could find no other specific to my desire. I placed it in the Hardware section because Hardware is the primary issue. 
I own 2 GizmoSphere Gizmo 2's and I have purchased 2 1TB Samsung 860 EVO mSATA SSDs which I have installed, but I need to move my OS install and all else from the SanDisk Extreme Pro MicroSD to my new SSD.
The Gizmo 2 has a large number of extra requirements for OS files to enable full, easy functionality as well as booting with only a single button press so moving the install rather than a new install will be far faster and easier.
How do I move my install from my MicroSD card to my SATA 3 SSD? What I am aware of is that doing so will require knowing the partition ID (UUID) for the new partitions of the SSD to replace them in FSTAB. 
Is there a way to take the existing MicroSD setup and form an installable OS iso from it? That would make everything a cakewalk.

Thank you for any help you can provide!

---

### Post by #&amp;thj^% on 2019-01-24
There is no such cakewalk,(:D) but with a willingness to learn: [https://elinux.org/Transfer_system_disk_from_SD_card_to_hard_disk](https://elinux.org/Transfer_system_disk_from_SD_card_to_hard_disk)
if you undertake this route, Backups, backups, backups.

---

### Post by monkeyman_stones on 2019-01-24
Some copies of builds of Ubuntu included an application which creates an OS ISO from the install (Pinguy 16.04 had it at least, but I couldn't find it in the installed applications within Synaptic package manager to install it in my installed copy of Lubuntu).

---

### Post by #&amp;thj^% on 2019-01-24
Ahh, I think you are referring to Remastersys also AKA:>> Pinguy Builder is a fork of the well known Remastersys tool that's no longer maintained.
But if your willing to experiment see this:[https://news.softpedia.com/news/you-can-now-create-your-own-ubuntu-18-04-lts-live-system-with-pinguy-builder-520733.shtml](https://news.softpedia.com/news/you-can-now-create-your-own-ubuntu-18-04-lts-live-system-with-pinguy-builder-520733.shtml)

---

### Post by monkeyman_stones on 2019-01-24
I was not referring to the programs that A. Norman made available to turn further versions of Ubuntu to Pinguy like copies. It was an application which was on the desktop that could be used to turn your own copy (your programs, files and so on) of the OS into an iso file to install anyplace else.

---

