---
title: "ATI driver works on Unity but not on Kubuntu"
date: 2013-08-14
forum: Hardware
---

### Post by sayakb on 2013-08-14
I have an old laptop with a ATI Mobility Radeon 45xx. I used to run Kubuntu 12.04 and I decided to do a dist-upgrade, although that unfortunately killed the ATI driver (as I understand, ATI does not support it anymore) and I was back to the open source fglrx driver. Now I wouldn't care as I don't use this laptop for anything other than coding, however it would not set my resolution higher than 1024x768 on a 1366x768 screen which was a no-go for me.

So I decided to follow a guide which suggested using an old ATI driver and which apparently worked for many users. When I installed, X would not start at all.

I decided to download Ubuntu 13.04 and it surprisingly not only gave me the desired resolution but also a very working compiz. So my question is, how is it that being the same OS, KDE does not work with it. I mean, it would not be affected by the DE at all. The only thing I can however think of is the update manager I used which removed all obsolete packages in the dist-upgrade where it might have removed some ATI binary. I would like to switch to KDE again and remove Unity. But what I want to make sure is that it does not do the same thing again with 13.10.

Any idea what is going on here?

```
root@FatalException:~# lshw -c video  *-display               
       description: VGA compatible controller
       product: RV710/M92 [Mobility Radeon HD 4530/4570/545v]
       vendor: Advanced Micro Devices [AMD] nee ATI
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:48 memory:d0000000-dfffffff ioport:2000(size=256) memory:fc000000-fc00ffff memory:fc020000-fc03ffff
root@FatalException:~# lspci | grep VGA
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV710/M92 [Mobility Radeon HD 4530/4570/545v]
```

---

### Post by QIII on 2013-08-14
When you installed fglrx, did you do so from the repo or from AMD/ATi's website?

No fglrx version will work with either 13.04 or 13.10 with that card, so you will be limited to the default open source Radeon driver.

It's not the DE that is the issue, but X Server.  The legacy driver for that card does not work with the latest version of X Server.

---

### Post by sayakb on 2013-08-14
Are you referring to my old install? No, I didn't use any third party source for that. So I believe it was the default driver itself, yes, so my bad.
I am just curious how it magically works now!! And I would love to know if someone else shares the same experience as me so that I can go back to KDE without the risk of losing X with the next dist upgrade.

---

### Post by QIII on 2013-08-14
Just to clarify:  When you were running Kubuntu 12.04, did you "dist-upgrade"  (that is, update all of your packages in the context of the current release - 12.04) or "do-release-upgrade" to move from 12.04 to 12.10 or similar?

---

### Post by sayakb on 2013-08-14
I did it via Muon update manager, which runs dist-upgrade internally.

---

### Post by Yellow Pasque on 2013-08-14
> I have an old laptop with a ATI Mobility Radeon 45xx. I used to run Kubuntu 12.04 and I decided to do a dist-upgrade, although that unfortunately killed the ATI driver (as I understand, ATI does not support it anymore) and I was back to the open source fglrx driver. Now I wouldn't care as I don't use this laptop for anything other than coding, however it would not set my resolution higher than 1024x768 on a 1366x768 screen which was a no-go for me.

That means you (and/or the package manager) didn't uninstall fglrx completely. It could have been something as simple as a leftover xorg.conf. (I've seen plenty of people who ended up in the same situation). 

If you install KDE or do a fresh install of Kubuntu 13.04, the default/open-source driver will run at correct resolution with 3D acceleration.

---

