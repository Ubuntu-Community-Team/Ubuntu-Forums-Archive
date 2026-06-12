---
title: "[SOLVED] Ubuntu Freeze using USB External Storage, 4-port Hub, Java/Torrent Client"
date: 2008-11-09
forum: Hardware
---

### Post by fitzbuntu on 2008-11-09
Hello,

I am halfway to solving a long standing problem since I upgraded to Hardy.

**Background to the Problem:**

I currently have [COLOR="DarkOrange"]Linux Mint Elyssa[/COLOR] installed on my Packard-Bell desktop system [COLOR="DarkOrange"]2gb ram, Pentium D, nVidia G72 G-Force 7300 SE[/COLOR]. I moved to Mint because I enjoyed Ubuntu (my first love) but at the same time this problem was driving me nuts and I had to try out another distro.

The problem I kept having was [COLOR="DarkOrange"]whenever I plugged in my fat32 500gb external hd and started copying large files the whole system would freeze[/COLOR] - it would not even respond to my attempts to raise Skinny Elephants. Googling this forum produced many different results and theories but I couldn't access logs due to the freeze at the time and I tried some of the solutions but to no avail.

Linux Mint was very good at first, it was working fine when I attached the external drive and would copy many large files. Now the problem has started happening again almost exactly the same...

**The Problem:**

When I plug in my external drive, before it mounts the whole system freezes, just as before on Ubuntu, however I have discovered [COLOR="DarkOrange"]if I log off completely before plugging in the external drive, it will mount and work fine (but will crash if I try to copy multiple files more than ~1.5gb).[/COLOR]

I have done a bit more digging and research and may have discovered the culprits, and this is where I need the help of the brains of this forum.

I have a [COLOR="DarkOrange"]Belkin 4-port usb 2.0 hi-speed hub[/COLOR] attached to my pc which in turn has 6 usb 2.0 ports directly attached to the motherboard. I noticed a number of things:

[LIST]
[*]When I plug in a flash memory stick, the system does not mount/recognise it (previously it did). However if I do the following first it will automount:
```
sudo rmmod ehci_hcd
sudo modprobe ehci_hcd
```
[*]I can mount unmount and plug in the flash memory drive in this way, but as soon as I start Vuze (which is a java based app) I can plug in and mount once but if I remove the flash memory or the hub and plug in again the system will freeze up
[*]Whilst the Belkin hub is plugged in, I have problems with my external HD in that it freezes like this regardless of running Vuze.
[*]When I plug in the flash memory to one of the motherboard usb ports, or unplug the Belkin hub and plug in the external drive then there is no freeze, whether I am running Vuze or not.
[/LIST]

So there appears to be 2 seperate behavioral problems between my flash memory, external hd and Vuze (java) but they both relate to the Belkin 4-port usb hub.

**My questions are these:**

[LIST]
[*]Is there a problem with Belkin 4-port usb 2.0 hi-speed hub and Ubuntu which causes the system to freeze like this?
[*]Is there a way to record the logs like dmesg before a system crash? - I know exactly how to evoke one now. Are there any other logs I can get info from?
[*]Am I understanding right that ehci_hcd is the usb 2.0 module which I am restarting? If I disable this, the usb devices seem to work normal - does this mean I have to use usb 1.1?
[*]Has anyone else experienced this and have a solution other than disabling usb 2.0 or logging off to plug in usb devices and logging back on?
[*]Ideally I'd like to find out why it was working when I first installed Mint but then the problem came back (without doing a fresh reinstall).. does anyone know what I should be looking for?
[/LIST]

Thanks in advance for taking the time to read through this and answer!

---

### Post by peterpan_bz on 2008-11-11
I do experience the same problem, although slightly different. As I was searching on Google many people had problems when having a USB device, such as external HD, plugged in during boot. That is not the case for me. But Ubuntu more or less randomly freezes as well when I use my external HD. It's a 2,5" 320 GB Trekstor that is pretty much brand new. 
My computer is a HP Compaq 6715s with an AMD Turion64 (2x 1,6Mhz) and 4GB RAM. Since it only has two USB plugs, I also use a USB Hub (cannot name it since it's a really cheap, grey plastic thing, it always worked fine, though...it has its own AC-adapter). I haven't really thought about the HUB until I read this post but it is true that it crashes more often with the Hub connected, even though the HD is always directly connected to the Laptop.
The crash happens mostly when I copy files, play files directly from the HD or when I plug it in after I have already used Ubuntu for a while (not start-up).

Has anyone an idea about how to solve this problem? I'm fairly new into this whole Ubuntu, switched from Windows and therefore am a little lost since I cannot just go into my "hardware manager" and fix the problem...8-)

and yes, almost forgot I'm running Ubuntu Studio 8.04.1_i386

I appreciate any help...thanks a lot.

cheers

Jan

---

### Post by fitzbuntu on 2008-11-11
Well, I've done some more testing and I think I can verify the cause of this #-o, but not yet the solution ](*,)

I don't know if this will help **peterpan_bz**.

I removed all my usb devices rebooted my pc and plugged in each one individually. Separately, all of them worked without a problem:

HP Printer-Scanner - uhci_hcd
4gb flash memory - ehci_hcd
ipod shuffle - usb 2.0?
500gb external hd - usb 2.0
Belkin 4-port hub + flash memory - ehci_hcd

This was before I started any applications. Here is the output of usb modules:

```
modprobe -l | grep -i hcd

/lib/modules/2.6.24-21-generic/kernel/drivers/usb/host/ohci-hcd.ko
/lib/modules/2.6.24-21-generic/kernel/drivers/usb/host/isp116x-hcd.ko
/lib/modules/2.6.24-21-generic/kernel/drivers/usb/host/r8a66597-hcd.ko
/lib/modules/2.6.24-21-generic/kernel/drivers/usb/host/ehci-hcd.ko
/lib/modules/2.6.24-21-generic/kernel/drivers/usb/host/uhci-hcd.ko
/lib/modules/2.6.24-21-generic/kernel/drivers/usb/host/u132-hcd.ko
/lib/modules/2.6.24-21-generic/kernel/drivers/usb/host/sl811-hcd.ko
```

I don't know what all these are but I've worked out that ehci-hcd is 2.0 hi-speed, ohci-hcd is usb full-speed(?) and uhci-hcd is 1.0 low speed.

Then I tested my theory about Vuze Bittorrent, bearing in mind the amount of times I can test this is limited as I don't want to bonk my hard drives.

I restarted the PC without any usb devices plugged in, I then started Vuze and plugged flash memory into the one of the motherboard usb ports - Desktop FREEZE - no skinny elephants.

Hard reboot via power switch, and try the same thing again, this time plug in my usb 1.0 printer - Desktop frozen again!

Another Hard reboot and this time I tried the following after starting Vuze and plugging in printer:

```
sudo /etc/init.d/udev restart

sudo rmmod uhci_hcd
modprobe uhci_hcd
```

Which restarts usb services. Plugged in the printer and this time it worked for 1 second... then FROZE AGAIN!

So basically there is a problem when running Bittorrent/Java based client and usb.

Although restarting usb 2.0 seemed to work for other devices, it doesn't seem to be very reliable method. So does anyone have any advice now that I have narrowed it down to Vuze/Azureus application?

One more thing, these devices seem to work, or partially work if I plug in before starting Vuze, it seems to be only when plugging in a device or re-plugging in whilst Vuze is running. Sure it's almost a work-around but hardly practical if I want to keep Vuze running in the background.

Editing to add: I think the 4-port hub was red herring due to the fact that I have always had it plugged in on startup.. which might explain the erratic behaviour plugging in flash memory/external drive because the hub worked as it was plugged in before Vuze started.

---

### Post by maxcelpc on 2008-11-26
I have been experiencing similar problems, which I am now convinced are hardware, i.e. motherboard, specific, since I have 5 computers and only one exhibits the problem. This machine is running, along with others, on an ATEN USB KVM, so the shared keyboard and mouse are connected to the computers USB port.

With nothing other than keyboard and mouse connected, the computer runs all day without problem. If a 1GB Pen Drive is plugged into any USB port it is mounted, but within a few minutes, or immediately if r/w is attempted, all the USB ports on the computer lock out. If a USB DVD drive is mounted, lock out is immediate.

One way around the problem is to disable the USB 2 controller in the BIOS or in the software. The down side to this is that data transfers become painfully slow.

From searches it appears that other distros exhibit the same symptoms, so this appears to be a Linux Kernel/driver problem.

If anybody from the Ubuntu/Linux development team reads this and and is of a mind to finally solve this problem, which exists in at least Gutsy, Hardy and Intrepid, I would be happy to help in any way I can. While this problem exists, my new computer is little more than a very expensive doorstop!

FTR the motherboard which exhibits this problem is a Gigabyte GA-MA78GPM-DS2H with Phenom processor, AMD 780G & AMD SB700 Chipset, 32-bit Ubuntu, installed as Hardy, upgraded to Intrepid. I had also tried AMD64 Hardy, with identical results.

---

### Post by fitzbuntu on 2008-11-26
I haven't posted recently because I last time I tried there was a problem (it would log in but not allow me to post).

I'm now convinced it's to do with Azureus/Vuze, but I haven't tried other BitTorrent clients.

My workaround is this:
Exit Vuze
Restart Hardware/USB:
```
/etc/init.d/udev restart

rmmod ehci_hcd
modprobe ehci_hcd
```

It appears that after a while Vuze starts to error with this message repeated over and over (dmesg):

```
[244076.084280] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
[244076.084282] Please file bug report to http://rt2x00.serialmonkey.com.
```

Which I believe has something to do with my rt61 Belkin Wireless driver.

There were other errors but the logs aren't showing anything untoward now. Not sure what my motherboard is, anyway I can find this out without popping the case open?

---

### Post by fitzbuntu on 2008-12-28
Well I think I have finally solved this problem! :guitar:

I don't know if this will work for others posted here but it was an unexpected proxy solution due to a PSU failure.

My 250w PSU died this weekend and after doing a bit of research on the failure and replacement, I discovered that a failing PSU (or one that does not have enough wattage) may start causing sudden crashes of the PC.

So I bought a replacement 500w PSU, plugged it in. Now I just tested it using the surefire method of crashing my PC by starting Vuze and plugging in the external drive.... Mounted fine and continued working!

The Vuze software and USB issue was a red herring. I figure the problem was either

[LIST]
[*]failing/losing power PSU,
[*]Combination of upgrades, usb devices and apps like Vuze maxed the PSU and caused the crash or
[*]both of the above.
[/LIST]

In the last year I have upgraded my ram from 1gb to 2gb, larger high performance cooler and added USB devices (including 4-port belkin). I wouldn't think this would normally affect power but it seems likely that it did -and attaching the external drive (even with external power) pushed it over the edge.

I hope this helps anyone else experiencing similar problems... and I am glad that it's NOT an Ubuntu issue and I can continue to live a life relatively free from Windows! \\:D/

---

### Post by Rohan Kapoor on 2008-12-29
> **fitzbuntu said:**
> Well I think I have finally solved this problem! :guitar:

I don't know if this will work for others posted here but it was an unexpected proxy solution due to a PSU failure.

My 250w PSU died this weekend and after doing a bit of research on the failure and replacement, I discovered that a failing PSU (or one that does not have enough wattage) may start causing sudden crashes of the PC.

So I bought a replacement 500w PSU, plugged it in. Now I just tested it using the surefire method of crashing my PC by starting Vuze and plugging in the external drive.... Mounted fine and continued working!

The Vuze software and USB issue was a red herring. I figure the problem was either

[LIST]
[*]failing/losing power PSU,
[*]Combination of upgrades, usb devices and apps like Vuze maxed the PSU and caused the crash or
[*]both of the above.
[/LIST]

In the last year I have upgraded my ram from 1gb to 2gb, larger high performance cooler and added USB devices (including 4-port belkin). I wouldn't think this would normally affect power but it seems likely that it did -and attaching the external drive (even with external power) pushed it over the edge.

I hope this helps anyone else experiencing similar problems... and I am glad that it's NOT an Ubuntu issue and I can continue to live a life relatively free from Windows! \\:D/

Yep dead (dying) PSU would do it. My friend had similar problems with windows and his problem turned out to be that his 150 watt power supply couldn't power his system. (He was a really cheap guy).

---

