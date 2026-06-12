---
title: "Installation locking up"
date: 2005-01-22
forum: Installation &amp; Upgrades
---

### Post by LaneRebel on 2005-01-22
I read another thread on a similar problem, but I think mine is slightly different.  

I'm attempting to install the most recent Warty release (downloaded 1/21/05) on my IBM ThinkPad R31 laptop.  The LiveCD works fine, but the installation keeps locking up on me.

My installation is not locking up at a certain point, but after a certain amount of time (seems to be about a minute or so); I can get through as many screens as I want before it locks up.  When I first had the installer running, it went fine until the X screen resolution selection screen.  After that it started this behavior.  Anybody have an idea what might be going on?  I have a feeling it has something to do with acpi and the daemon, but I tried pci=noacpi in my boot options.  Any other ideas?

Thanks!
Joe

---

### Post by thelusiv on 2005-02-17
I am having the same problem with my R31. It definitely seems related to ACPI or APIC, both of which don't really work right in this laptop under Linux. the ACPI BIOS has known issues, bugs in the very firmware. I haven't gotten this problems 100% resolved but I think we need to disable more at boot time. Here's what I have been doing:
```
noacpi noapic pci=noacpi acpi=off
```
I'm not really sure which one it is that does the trick but I do notice when it starts working right, that the modules pciehp and shpchp fail to load at boot.

---

### Post by tkiesel on 2005-02-17
[QUOTE=thelusiv]I'm not really sure which one it is that does the trick but I do notice when it starts working right, that the modules pciehp and shpchp fail to load at boot.[/QUOTE]

I had the same messages on my machine.  There's an [Ubuntu Starter Guide entry](http://ubuntuguide.org/#modprobefatalerror) about those messages and how to remove them from appearing on screen at boot. I think they're harmless for the most part, and shouldn't be causing any boot difficulty.

---

