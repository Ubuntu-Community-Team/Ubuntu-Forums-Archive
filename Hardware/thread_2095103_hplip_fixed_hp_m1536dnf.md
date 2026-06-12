---
title: "hplip fixed? hp m1536dnf"
date: 2012-12-15
forum: Hardware
---

### Post by pjmlmas on 2012-12-15
I am getting this error:
> failed to open device 'hpaia:/net/HP_LASERJET_M1356dnf_MFP
when using xsane, which sounds as if it has been reported
This thread says that it has been fixed in latest hplip
[https://bugs.launchpad.net/hplip/+bug/1015319]("https://bugs.launchpad.net/hplip/+bug/1015319")
but this one says may need more?
[https://answers.launchpad.net/hplip/+question/152542]("https://answers.launchpad.net/hplip/+question/152542")

My current hplip is 3.12.2-1
so I just need to download from hp and install?3.12.11

---

### Post by agillator on 2012-12-15
That should be all you need to do. However, if your current HPLIP was a package installed from the repos, I recommend purging it first. In my experience my scanner (alll-in-one) does not work well (as in at all) with the Ubuntu version. I have never had a problem with the download/install from HP itself.

---

### Post by pjmlmas on 2012-12-16
I marked complete removal original hplip from synaptic.
I followd hp instructions.
It still found old hplip. I opted for remove and install rather than overwrite (not certain which one to choose)
It asked to check for updates, I did.
It appears to have installed fax driver.

It stated that I would need to reboot and run hp-setup. This appears false.

Duplex printing is working.
Scanning is working.

There are/were other files in synaptic for hp that were at old revision level. I did not mark these for removal, only hplip.

P.S. What happens with auto updates now? Double checked. HPLIP and other packages were removed and no longer listed as installed under synaptic.

---

### Post by agillator on 2012-12-16
Since you have removed Ubuntu's HPLIP the update manager shouldn't do anything about updating it. If it does you may have to go into /var/cache/apt/archives and find the package there that is triggering it, but that probably won't happen. I think HPLIP itself has started letting users know when there is an update. If that happens you will probably have to go through the download/install process again, but that becomes very easy. If you go for six months without an update, then you probably need to start manually checking to see if there is an update. Again, takes a second or two but is no real problem.

Oh, and if this fixes your problem please mark the thread solved. Thanks.

---

