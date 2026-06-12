---
title: "No USB keyboard, No Network on fresh install!"
date: 2014-10-03
forum: Hardware
---

### Post by mike251 on 2014-10-03
Long time listener, first time caller. I purchased a modest box to be used as a server (Xeon x3220, SuperMicro C2SBE, 4GB). My goal is to use this box as a server for media and a few other things. Nothing extreme, but mostly shares for my home network as well as WAN. Initially downloaded the main Ubuntu Server iso (64-bit), and the install went great. Right now I have only 1 HDD plugged in to avoid any confusion. During install, NIC and USB keyboard both work perfectly. Entire install process takes ~15 min or less. Reboot, neither of those things work. In GRUB (when I can get it to pause at the boot menu), keyboard still works perfectly. As soon as it starts loading the kernel, though, both things seem to stop.

This is first obvious when it tries to start the Samba services. The second service (which I am assuming is the service that actually hosts the shares) fails to start, and then immediately after when the boot tries to load the network configuration settings it fails to do this, as well. It waits the additional 60 seconds with no connection, then just continues to boot. It gets to the login screen, but since the USB keyboard doesn't work I can't log in (or do anything).

Now, I've read there are people that have this trouble when using 64-bit Linux with IOMMU disabled on their mobos, so I tried the 32-bit (just to test). This had the same effect. My motherboard does not have any dedicated IOMMU settings (although the specifications say it's supported), but I did enable VT-d (which is pretty close to the same idea). I also tried adding IOMMU=soft and intel_IOMMU=on to the boot, to no effect.

Any ideas what could be causing this? I'm borrowing a PS2 keyboard to at least see if I can log in, but the bigger issue is the network. I don't really care if USB works (I'm fine disabling it, entirely, in the BIOS), but obviously the network connection needs to work.

---

### Post by mike251 on 2014-10-03
Anyone have any thoughts? Coming up on 100 views but no replies yet. I'm going to also test a PCI wireless card come Monday to see if that works (to see if it's only the onboard LAN that's not working), but was hoping to get some insight about the entire thing.

My dad has a Gigabyte EP35-DS3L at their house that I might try too, but I'm not sure whether it would make a difference or not yet. I mean the weird thing is that everybody I've seen online with this issue just enabled IOMMU or switched to 32-bit and everything worked...in my case the 32-bit piece didn't work, but I don't have a way of actually enabling IOMMU natively. Then again, maybe it's called something else in my BIOS that I'm not able to decipher (I looked through the options and enabled anything that had the same feel to it).

---

### Post by weatherman2 on 2014-10-03
Just a side question: any particular reason you decided to install Ubuntu Server Edition instead of the Desktop edition?  Your board can adequately handle the Desktop edition, I believe.  I usually install that, even on "servers" just because it is much easier to debug stuff.  (I have one server running Ubuntu Server, but that's purposely a bare-bone server running as a web/email server and the less stuff installed the better.)  Some people simply don't want all that extra crap the Desktop edition includes, but if you don't mind extra junk installed that you'll never used, it might be easier to get it going.  You can always uninstall certain things later (e.g. Thunderbird, LibreOffice).

I can't answer your question about the USB keyboard.  There's a chance that if you install the latest updates, it will just fix itself.  But you can't get online yet it seems - so I'd fix the network issue first, with your PS/2 keyboard, and once you do that do updates and then look at the USB keyboard issue.  Even if you want to stick with the Server Edition, I'd still try to boot a Desktop Edition USB or  DVD "live" in "Try It" mode and see if it will come up.  If you can get to a terminal, type

```
sudo lshw -C network
```

to give some information about your network card.  Maybe you need to download/build a driver for it.

---

