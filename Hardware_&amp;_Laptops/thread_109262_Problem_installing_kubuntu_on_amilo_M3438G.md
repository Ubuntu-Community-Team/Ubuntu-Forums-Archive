---
title: "Problem installing kubuntu on amilo M3438G"
date: 2005-12-28
forum: Hardware &amp; Laptops
---

### Post by guillem01 on 2005-12-28
Hi everyone!

I have several problems when I try to install kubuntu on my amilo M3438G. First of all I describe how is now my laptop:

- I have 2 SATA hard-disks in RAID 0
- I have installed Windows XP
- I have installad Instant On (Cyberlink PowerCinema which use a linux mini distribution, I don't if it uses Lilo or Grub)

When I try to install kubuntu my first problem was the two hard-drives in RAID 0 aren't recognized as one. I checked the forums and I found the solution on  [Fake Raid Howto]("https://wiki.ubuntu.com/FakeRaidHowto?highlight=%28raid%29") but when I try to put the LiveCD, it freezes when is activating the hotplug.

If someone nows how to fix it I would be grateful

---

### Post by guillem01 on 2005-12-28
I think I'll try with a knoppix in order to be able to boot the liveCD

---

### Post by guillem01 on 2005-12-29
I still trying to install (k)ubuntu on my laptop. I read some post about the hotplug, but my BIOS has few options and I can't unable anything. Also I re-download Ubuntu and Kubuntu Breezy and there is the same problem with the hotplug.
But I tried with a ubuntu horay liveCD and it works, I think I will try this way.

---

### Post by pelle.k on 2006-01-14
I thought i'd post a suggestion beeing a brand new owner of a Amilo M3438G, with a fresh Kubuntu 5.10 install :)

1. Do a server install. (type "server" when the boot cd ask you for boot options).
2. After first reboot, don't let it load ubuntu, because it will just hang at "starting hotplug". Instead use a live CD (I can highly recommend "KANOTIX Lite") to remove the directory /lib/modules/2.6.12-9-386/kernel/sound/pci/hda, from the root partition of your ubuntu installation.
3. Reboot and continue your installation, i.e. answer a few questions, then at the prompt "sudo apt-get install kubuntu-desktop" :)

To get sound, I chose the driver from [www.alsa-project.org](www.alsa-project.org) instead of the realtek ones, which only caused me grief anyway. I couldn't get them to compile as they should...
Anyway, this guide was pretty straightforward [https://wiki.ubuntu.com/HdaIntelSoundHowto](https://wiki.ubuntu.com/HdaIntelSoundHowto).
I think they left out that you need to "apt-get install gcc-3.4" too though :)

Good luck!
And remember, if you're a n00b (newbie) DONT hesitate to ask, I will make you a "for dummies" guide if thats what it takes ;)

---

