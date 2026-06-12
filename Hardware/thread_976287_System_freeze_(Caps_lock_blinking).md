---
title: "System freeze (Caps lock blinking?)"
date: 2008-11-09
forum: Hardware
---

### Post by Nixie Pixel on 2008-11-09
Hi, I recently installed Ubuntu 8.10 on a Compaq Presario A909US (dual-booting with Vista).  At the moment I am having an easier time of it than I did with 8.04 which I gave up on a while ago, aside from some Broadcom wireless issues (who hasn't had those?? =D).  

However my system has frozen twice now in the four days I have had it installed - a hard freeze that I needed to hit the power button to get out of.  My Caps Lock indicator was blinking on and off after the freeze happened, both times.

Does anyone know what this means or could be?

Thanks!

~Nix

---

### Post by sroland81 on 2008-11-09
It happened to me one time.... the system freezes and the caps lock LED is blinking... i heard that this happens because of some hardware problem... is this correct? after rebooting the system, in there any system log file that remains after rebooting? thanks

Also using Intrepid Ibex 8.10 i386 on Compaq Presario F700 notebook

---

### Post by sgleo87 on 2008-11-09
I used to have that problem in Hardy...happened to me maybe once or twice a month, but now that I have upgraded to Intrepid a week ago it hasn't happened to me so far. I did try to find the cause of it at the time by searching the forums and google, but unfortunately I never really found any satisfying answer.

---

### Post by Nixie Pixel on 2008-11-09
I wish I could answer - I am sort of new to this and wouldn't know where to look for log info about what caused the crash.

If anyone could help, I would appreciate it!

---

### Post by RavUn on 2008-11-10
I've had this problem with 8.04 for a while on my laptop; I have not had any issues on my desktops before.  I read somewhere (can't remember what forum) that it's not a hardware issue but is something with Ubuntu.  Someone recommended adding:
```
ro quiet splash noapic nolapic pci=noacpi acpi=off
``` to the kernel when booting in grub/menu.lst.  So, I added it and then my laptop froze up a few hours later (caps lock/num lock flashing).  I rebooted and it wouldn't boot up with that added...  I don't know what's wrong, I guess I'll try updating to 8.10 or try a different linux distro.

Some others recommended checking the keyboard, making sure there's no dust in the computer and running a memtest.  My laptop is a dell inspiron i1318 and it boots and runs Vista just fine.  I've had this issue in Ubuntu since I bought it (a few months ago).  I doubt it's a hardware issue, but who knows... ubuntu apparently doesn't like something with my hardware, though.  I don't think there'd be any dust inside a new laptop and I don't know how to check the keyboard and memtest checks out fine.  I'd love to hear if anyone has a solution.

---

### Post by towe on 2008-11-10
This happens all the time to my Asus V2S after upgrading to 8.10. It didn't happen a single time on 8.04. 

The laptop freezes up totally with the screen stuck on whatever it showed at the time. The caps-lock led is flashing and there is no response to any input. 

The time before it occurs seems random, but is has never happened during active use which makes me suspect that it is related to some power saving feature.

There is nothing in the logs indicating the cause.

---

### Post by Nixie Pixel on 2008-11-10
Hmm, I might say you were on to something - the very first time it happened to me was during the installation process for 8.10 itself!  I had left it unattended expecting the process to complete and leave me with the "please eject the disk" notice, only to come back to it completely frozen with Caps blinking on and off.  

However, I recently had this happen while opening a new Firefox browser session, so for me at least I don't think it is completely consistent with it being some sort of power save issue.  

Isn't there some sort of system log or something we can view to see what happened to cause the crash?

By the way, I recently completely cleaned the laptop, opened it up and made sure there was no dust and such, so cleanliness is not an issue...

---

### Post by Nixie Pixel on 2008-11-11
Can anyone help here?

As it is now, it seems like XP would have more diagnostics available to it than Ubuntu/Linux.  Surely if there was some tool available to help determine the source of this problem, someone would have posted about it by now?

---

### Post by Izkata on 2008-11-11
If you look in other threads, it has been confirmed that this is a problem with the driver for Broadcom wireless cards.

The Windows Broadcom drivers are stable, but the Linux ones are not.  That is the problem as far as anyone can seem figure out.

---

### Post by sgleo87 on 2008-11-12
I did a google search and the problem seems to be kernel related, not hardware related: [https://answers.launchpad.net/ubuntu](https://answers.launchpad.net/ubuntu) and [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/231376/+question/5529](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/231376/+question/5529)
So are your running the latest kernel (which I believe is 2.6.27-8-generic)?

On launchpad there is also a bug report relating this to 802.11n wifi: [https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.27/+bug/276990](https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.27/+bug/276990)

Like I stated before, I used to have this problem in Hardy but after upgrading to Intrepid on Nov 2 it has not happened so far (current kernel: 2.6.27-8-generic)

---

### Post by Nixie Pixel on 2008-11-13
I had been running 8.04 Hardy Heron without this issue cropping up (though I had other issues with Heron).  

My uname -a info:  2.6.27-7-generic #1 SMP

I'm not sure how to update my kernel...is that anything like apt-get update or apt-get upgrade?  (If not, what do those do, anyway?)

Sorry for my noobishness...

Thanks again!

Edit:  I figured out how to upgrade to the 2.6.27.8 kernel...I'll see if that helps...thanks again...

---

### Post by sgleo87 on 2008-11-13
how to upgrade kernel: [http://www.cyberciti.biz/faq/linux-kernel-upgrade-howto/](http://www.cyberciti.biz/faq/linux-kernel-upgrade-howto/)

---

### Post by gjohn2 on 2008-11-14
I had upgraded everything. removed programs blah blah.

finally in my syslog i found, something about wireless
event too big, and about 2 mins later i get the freeze.

this is on a dell d420  with an intel 3945 abg wireless,
 which ran flawlessly under the last two ubuntus. so after 
having 3 freezes in one hour at work(out of about 10 for the
day), i reboot and and turned my wireless off.....come in 
today and still no freeze.i think the freezes increased after
running a script to keep my wifi from blinking incessantly. 
gonna remove that and see what happens.

---

### Post by gjohn2 on 2008-11-14
So after being on for over 12 hours with no freeze (with wifi off) i removed the stop blinking script(so its back to install state) and started up the wireless. 2-3 hours in, FREEZE. thanks 3945 driver. any ideas? in ibex. please help, this makes me want to die.

---

### Post by Nixie Pixel on 2008-11-16
Ok, after upgrading to the latest kernel, I had another system freeze tonight.

*sigh*

---

### Post by Nixie Pixel on 2008-11-16
Well, I appreciate the attempts to find a solution to (or at least information about) the problem online, but the first step for me would be to use diagnostic tools to determine the source of the problem.

Unfortunately, it seems no one knows of diagnostic tools to be found within Linux that are equivalent to the types of tools one can download for Windows to at least pinpoint the sources of problems?

---

### Post by quad65 on 2008-11-16
Maybe this will be helpful:

[http://users.bigpond.net.au/hermanzone/p8.html#Hardware_Detection_and_Testing](http://users.bigpond.net.au/hermanzone/p8.html#Hardware_Detection_and_Testing)

---

### Post by Nixie Pixel on 2008-11-17
Thank you for that list, it has introduced me to a number of commands that I was not familiar with.

However, what I am really trying to do is this:

Run some sort of diagnostic tool or admin log that can tell me when I reboot the frozen computer exactly what was happening when the computer crashed.

For instance, under Windows XP I can go to the Event Viewer, and while not perfect, get an idea of what caused a system crash.  Nothing like this exists in Linux?

---

### Post by sgleo87 on 2008-11-17
What about System > Administration > System Log?

---

### Post by mumurlen on 2008-11-17
Hi 

Verify you don't have Intel 4965 wireless chipsets

If so follow the release notes for 8.10 and install linux-backports-modules-intrepid

```

sudo apt-get install linux-backports-modules-intrepid
```

[https://wiki.ubuntu.com/IntrepidReleaseNotes#System%20lock-ups%20with%20Intel%204965%20wireless](https://wiki.ubuntu.com/IntrepidReleaseNotes#System%20lock-ups%20with%20Intel%204965%20wireless)

Hope it helps.

---

### Post by sgleo87 on 2008-11-17
Well...should always read those release notes...I definitely have the Intel 4965 wireless chipset. Although Intrepid hasn't crashed on me yet it never hurts to install it. Thanks so much for your post mumurlen!

---

### Post by larnal29 on 2008-11-17
Hello!
I have the same freezing, blinking problem with 8.10 running on dell xps 1012. I suspect that there may be some trouble with firefox, it usually happens when Firefox has been opened.

---

### Post by larnal29 on 2008-11-17
Globally my 8.10 is much more unstable than my Hardy config I have to say. I had repeated crash of open office as well.
Is there a particular log I can check to understand the sequence leading to crash?

---

### Post by Nixie Pixel on 2008-11-17
I don't think I have the Intel 4965 wireless chipset, I have a Broadcom 43xx in this machine.

I too have had this crash often with Firefox open, but since I almost always have Firefox open for one reason or another, I don't know if this is relevant.  It certainly didn't cause my crash when I was first installing Intrepid.

The suggestion System->Administration->System Logs should help determine what happened next time it happens.  Thank you!

I will report back here with the log of the time when it crashed.

---

### Post by MarkM06 on 2008-11-17
Hey Nix,

I've heard that this can be caused by a motherboard failure or a faulty gfx card. Apparently flashing the bios can (sometimes) fix it. That seems a little drastic to me, though.

There is a thread here about flashing the bios in Ubuntu though [http://ubuntuforums.org/showthread.php?t=318789](http://ubuntuforums.org/showthread.php?t=318789)

Mark

---

### Post by Nixie Pixel on 2008-11-17
Thanks, I will check this out.

However, I did have Hardy on the machine for a couple of weeks before I gave up on it, and never had a problem with these system freezes.  Given their frequency in the latest release I would have to think that I would have seen a problem in 8.04 if it were some sort of hardware failure, wouldn't I?

---

### Post by VraiChevalier on 2008-11-17
I am having the same problem on a Dell desktop with a P4 tri booting XP Home and Hardy and Mint Elyssa. I have several other machines running various versions of Ubuntu but this is the first time I have had crashes like this. I hadn't thought of the wireless card, will try disabling that. Somewhere I saw something about the Nvidia drivers causing a problem like this. Anyone else heard of that?

I am wondering if it is a recent kernel version causing the problem.

My system locked up twice while trying to do updates. No Firefox running. When running XP the machine does not have any problems so I do not think it is a hardware issue.

---

### Post by MarkM06 on 2008-11-17
Good point, it probably isn't a hardware issue if everything was okay with 8.04.

I just looked around on Google, and keeping in mind I'm not a Linux guru, it could be a Kernel panic. [https://answers.launchpad.net/ubuntu/+question/5529](https://answers.launchpad.net/ubuntu/+question/5529).

Have you tried reinstalling 8.10?

---

### Post by Nixie Pixel on 2008-11-18
I have not tried reinstalling 8.10, but I did upgrade the kernel to the 27-8 version, which did not help the problem.

I have not yet seen the freeze since learning about the system logs, so I don't have any further information at the moment.

I read in another thread about using CTRL-ALT-F1 and logging in, to watch and see if any output is displayed when it freezes.  Is there any way to have this open in a window rather than full screen, so that I can be working in other windows while this is running?

Edit:  Well, I could try reinstalling - with three partitions (swap, /, /home) including /home, what is the easiest way to reinstall?  With Windows I would just save my data and reformat the whole thing, copying my data back when I had a fresh install.  I set up a /home partition for a number of reasons, one of which being that I could supposedly reinstall rather easily while keeping all of my data, configuration and applications.

---

### Post by wyth on 2008-11-19
Seen this?
[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=944123](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=944123)
Same issue you're having with the same card, but on Hardy

---

### Post by kuhlbeans on 2008-11-19
This is a known problem with Hardy and it is what is called a kernel panic (as MarkM06 noted).  If you search google for "hardy kernel panic" or "hardy caps lock" or various other combinations you can find many people having this issue and a few bug reports.  Intrepid also has kernel panic issues but I am not seeing situations described like yours and the Hardy panics.

Though this may be a hardware related issue, I am not sure of the common denominator.  My guess is that is has something to do with wireless, though not a particular manufacturer, because Intel, Broadcom, etc. all seem to have occasional problems.  When I first installed Hardy I would get this problem several times a day that required a hard off/on cycle to get the system back up.  With subsequent updates this problem has mostly gone away, with kernel 2.6.24-19 I have had almost no problems; I've yet to upgrade to Intrepid.  

Did you do a fresh install of Intrepid or an upgrade, Nixie?  Also, the system logs would be helpful, keep us informed!

To answer your question about a reinstall, if you have a /home partition it is very easy to do.  Just run the install like normal but when the hard drive partitioning section comes up you will have to select manual rather than guided.  It should list the partitions you already have, just select the existing / to be formatted with whatever FS you prefer and be mounted as / again.  Also, make sure /swap and /home are set to mount as /swap and /home, but make sure /home is NOT SET TO FORMAT, otherwise you *will* loose your data.  There should be plenty of guides out there that could help you (and provide screenshots) about this, or feel free to PM me.

---

### Post by Nixie Pixel on 2008-11-20
It was a fresh install of 8.10.  Though I had to go through the procedure twice - the system crashed during the file copy portion of installation the first time I tried it.

It is weird that you saw this on Hardy, and I did not, but now I do.  If the problem is wireless-related, that could make sense, as I went through more than a few iterations of trying to get my Broadcom card working...using fwcutter, ndiswrapper, and so on.  I got it working, but never experienced a system crash during all the troubles.

Anyway, I haven't had a crash for several days, so hopefully the problem has been solved somehow?  :P

---

### Post by Zetheroo on 2008-11-28
I have the R61 Thinkpad which was working well with Hardy. Then I went for the automatic upgrade to Intrepid which in tern led to all sorts of issues, most of which I have worked out .... except the freezing and flashing CAPS Lock LED indicator ... all I can do is hold the power button down for a hard reset -- very unimpressive!
 
Anyhow, I decided to do a fresh install of Intrepid but this did not solve the issue. It does not happen the often ... but often enough to make me wonder what is going on with Linux that every new release brings with it more and more issues?!?

So now I hear that this is a Kernel Panic (due to some hardware issue?) ... what does one do to locate the cause? 

In Windows XP Pro is was pretty easy to find the cause of a system hang etc ... but in Linux it seems to be something only "the gods" can do ... and even then ...

Here is the read out of lspci:

```
xxxx@xxxx-xxx:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
03:00.0 Ethernet controller: Atheros Communications Inc. AR5212 802.11abg NIC (rev 01)
04:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
15:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
15:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
15:00.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
15:00.3 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev ff)
15:00.4 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 11)
15:00.5 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 11)
```

Here is my lsusb output:

```
xxxx@xxxx-xxx:~$ lsusb
Bus 003 Device 005: ID 046d:c505 Logitech, Inc. Cordless Mouse+Keyboard Receiver
Bus 003 Device 004: ID 03f0:0c17 Hewlett-Packard LaserJet 1010
Bus 003 Device 003: ID 04b4:6560 Cypress Semiconductor Corp. CY7C65640 USB-2.0 "TetraHub"
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0a5c:2110 Broadcom Corp. Bluetooth Controller
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

---

### Post by wyth on 2008-11-28
Okay, so I had a bit of a breakthrough today.

**The Problem**
Like many of you, I've been getting some random lock-ups; kernel panic with a hard freeze I could only end with a hard reset. This seems had something to do with the wireless card, in my case iwl3945 -- it really didn't like one of the networks at my university, and whenever I got on that network, it crushed my system.

I read in a number of places that in order to fix this, you needed to install linux-backports-modules-intrepid. Okay, why not. But that introduced the other problem; the hard freezes may have stopped, but it broke wireless. No networks could be seen, and the module couldn't be modprobed. Of course it fixed the problem -- how can the wireless card bring down the system if it's broke? 

Removing the backports fixed the wireless, but left the freeze problem.

The problem has persisted up to the most recent kernel, which jumped to 2.6.27-10-generic in my updates, skipping 2.6.27-9-generic.

**The Fix**
After some more research, I found some references to "proposed" as a possible culprit, although I couldn't find enough to tell me what they meant. So I experimented. I commented out the proposed repositories in my sources.list and did all the updates and autocleans..  

The first thing I noticed was that the 2.6.27-10-generic kernel was no longer available, but the 2.6.27-9-generic was. I added the 2.6.27-9-generic kernel, made sure I had the backports installed, the headers, restricted modules, all that stuff, and rebooted.

AND WIRELESS WAS THERE. AND IT WAS GOOD.

So far no freezes (although it's a U.S. holiday and I'm not on my university's network), wireless is working fine, and everything seems happy.  I ran this laptop for over 18 hours now without a problem.

So if you're having any hardware woes, consider commenting out the intrepid-proposed lines, re-installing some things, and it may solve some of your issues.

---

### Post by RavUn on 2008-11-28
I've updated to 8.10 and kernel 2.6.27-7-generic.  So far the issue has stopped, so hopefully it was an issue with the older kernel.  I never did actually figure out what caused the issue, but I saw in logs one time that I had a kernel panic.  That time it happened when I was restoring from sleep mode, but most of the other times it would just randomly happen while I was working.

If the issue arises again I'll check out removing the "proposed" items.

---

### Post by Zetheroo on 2008-12-01
Still having system lockups with the 27-9 kernel. No answers in sight ... 

Many people talk about the Intel Wireless being the issue ... but mine is Atheros and I too have the problem with kernel panics ... so its a bit more than that I think ...

---

### Post by Andrade on 2008-12-01
Same problem here with 27-9 and a BCM4312.

---

### Post by ildella on 2008-12-01
In my system kernel panic seems to happen under some conditions. 

It just happens when laptop (dell xps 1530) is connected via VGA to a LCD monitor (benq 24). It never happened when no external monitor is attached. 

With that configuration, the rate of kernel panic is very low but when I play music, particulary with elisa media center, the kernel panic is more frequent. 

It could be related to elisa itself or the fact I am using a USB external soundcard (foobar 2, plug and play perfectly). 

Or can be related to a wireless dirver error, in fact I always stream my music from a NAS. 

Here is my lspci, this evening will post lsusb, when all peripheral will be attacched. 

Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 005: ID 0a5c:4503 Broadcom Corp. 
Bus 006 Device 004: ID 0a5c:4502 Broadcom Corp. 
Bus 006 Device 003: ID 413c:8126 Dell Computer Corp. Wireless 355 Bluetooth
Bus 006 Device 002: ID 0a5c:4500 Broadcom Corp. 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 004: ID 046d:c521 Logitech, Inc. MX620 Laser Cordless Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
della@della-laptop:~/projects/work/loginet/petrol$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GT (rev a1)
03:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
0b:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)

---

### Post by Mizzou_Engineer on 2008-12-01
I have a Dell Latitude E5400 with a Broadcom BCM4312 card and kernel 2.6.27-9-generic using the wl driver. It performs fine when connected to unsecured, WEP, or standard WPA2 but causes a kernel panic immediately on connecting to a WPA/WPA2 enterprise (MSCHAPv2) network. 

I have confirmed this as the cause of the panics by restarting the machine with the BCM4312 card active and noting the computer panicking as soon as a connection is made every time I connected to the AP. With the wireless disabled via the hardware switch, the computer is fine and does not panic. Turning on the switch causes a panic as soon as the BCM4312 connects to the AP. I replaced the BCM4312 with an Intel 3945 WLAN card and I can successfully connect to the WPA enterprise/MSCHAPv2 networks with no issues whatsoever.

---

### Post by the_tazinator on 2008-12-01
I am having the same problem as Mizzou_Engineer. I have reinstalled 8.10 several times trying to narrow down the issue. I have a Dell Precision M4300 with a Broadcom BCM4328. When I was running 8.04, the directions that are [here]("http://ubuntuforums.org/showthread.php?t=297092") worked for me. Now I can't get it to work, even with the patched that was suggested [here]("http://ubuntuforums.org/showthread.php?t=972415") due to not being able to compile on 2.6.27 kernel. I tried using the ndiswrapper that is on the repositories and that doesn't work either. If I use the restricted drivers that Ubuntu say works and has been tested, my wireless works on WEP networks fine. When I try to connect to a WPA2 Enterprise network, as soon as it connects, it locks up. A couple seconds later the num lock light starts flashing. I am forced to power cycle the laptop to fix the issue. This has become very frustrating.

---

### Post by Zetheroo on 2008-12-01
Well for me it happens so irregularly that I have no idea what may be causing it. 

Following is my Network Device info:
```

03:00.0 Ethernet controller: Atheros Communications Inc. AR5212 802.11abg NIC (rev 01)
04:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
```


Thing is that I never use the Broadcom Netlink LAN as I am always on the wireless network which btw is completely unsecured with no encryption.

Could the Broadcom Netlink device be causing kernel panics even if its not being used?

I left my laptop on through the night with it booted up into console in hopes that the system would freeze and spit out he error ... but alas it did not freeze!

---

### Post by wyth on 2008-12-01
Just curious if any of the people still having problems tried commenting out/removing intrepid-proposed from their sources.list and reinstalled the kernel, along with backports.  I've had no problems since I did that.

---

### Post by Zetheroo on 2008-12-01
I never had proposed enabled. 

BTW I just rebooted from a kernel panic. What should I do? Where should I look for the cause?

UPDATE: I just did a memtest and it finished with no errors .... no surprises there ....

---

### Post by Mizzou_Engineer on 2008-12-01
the_tazinator, newer Dells and most other laptops have a spare full-length mini-PCIe slot in the bottom and spare antenna leads in case somebody wants to put in a cell modem (aka WWAN card.) Those slots fit a standard mini-PCIe WLAN card and I used mine to install an Intel 3945 WLAN card, which fixes the issue. 

However, you will want need to do a few things to ensure that this works:

1. DO NOT go into the BIOS and shut off the built-in WLAN card. Doing so shuts off the second WLAN card you installed as well. I know this happens on new Dells, not so sure about other machines.

2. Disable the other wireless card by switching off the WLAN switch, booting the computer, and then blacklisting the Broadcom card's driver. You will need to add the line "blacklist wl" less the quotes to /etc/modprobe.d/blacklist to prevent the Broadcom driver from loading on boot and potentially hanging the system if it finds and tries to connect to a WPA Enterprise network before you can stop it.

3. Load the drivers for the wireless card you installed and any firmware, if needed. 

4. Turn on the wireless switch. Note that the "WiFi" light probably will not turn on, but this does not mean that the new card is not recognized or non-functional. The card you installed should show up in NetworkManager and successfully connect to the WPA2 enterprise network. if not, reboot and it will then. You should also not see the Broadcom card in NetworkManager.

---

### Post by sergiom99 on 2008-12-02
It happened to me only twice (I use Kubuntu HH): when I tried to connect to an unsecured wifi network at my brother's building. I can connect to any WPA/WP2 netkwork, but the only time I tried to use an open network it froze.

---

### Post by RavUn on 2008-12-02
Are you using a Broadcom card?

---

### Post by sergiom99 on 2008-12-02
BCM4328  with linux driver working perfectly.

---

### Post by VraiChevalier on 2008-12-02
To follow up:

I was having the hard freeze problem with the blinking keyboard lights just as others have described in this thread.

I fixed it by replacing the PCI wireless card. The card causing the problem was a Rosewill. I'm sorry to report that I neglected to get the chip info prior to removing it. I replaced it with a different PCI wireless card which was known to work well with Linux. Voila! Issue resolved.

If it is possible to remove or disable the wireless card in your machine and then connect via ethernet cable try that. For me it was an easy way to eliminate one possible culprit.

---

### Post by Zetheroo on 2008-12-02
I reformatted and returned to Hardy and I am already noticing the benefits. My sound is no longer distorted like it was in Intrepid and my wireless works out of the box with much better reception than in Intrepid.

Also no more freezes!!! 

People should not have to be changing their hardware "to make Intrepid work" which is what many people seem to be suggesting. If your hardware worked in Hardy and its not working in Intrepid you should return to Hardy until Intrepid gets a serious batch of fixes or until the next release.

IMO Intrepid was not a "good release" since I have experienced many major issues with it on a variety of machines ... issues which were NOT present in Hardy!

Some people say that we should give Intrepid time to have its bugs fixed since it was just released. But the bugs in Intrepid are obviously pretty deeply ingrained ones that will most likely take months to fix .... if at all. So best to just revert to Hardy which has matured in the time its been around -- Unless all you want to do is file bug reports and play around with acquiring new hardware etc ... :lolflag:

---

### Post by kitchensink on 2008-12-02
Hi,
   I have a acer aspire one 110 with intreprid with kernel linux 2.6.27-9-generic.  I am getting a freezing when connected to network using remote desktop or VNC.  Can someone suggest how to fix this issue.  


Thanks

---

### Post by kitchensink on 2008-12-02
Hi,
   Is there a way to go back to previous version of kernel.  I have not had any issues in the previous version of the kernel..

---

### Post by ryclegman on 2008-12-02
Hello,

Iv been having similar problems. Yesterday i was downloading something from the internet and it froze completely, my lights on my keyboard just flashed ect. I rebooted and went back to firefox and it crashed again because the file stated to download again. So another reboot and by now im pissed, so i let it do it again so i could see my system log with the error. I found this, not sure if it was to blame, but here it is....

> 
Dec 1 15:45:14 ryan-desktop avahi-daemon[5252]: Withdrawing address record for ******** on wlan0.
Dec 1 15:45:14 ryan-desktop avahi-daemon[5252]: Leaving mDNS multicast group on interface wlan0.IPv4 with address *********.
Dec 1 15:45:14 ryan-desktop avahi-daemon[5252]: Interface wlan0.IPv4 no longer relevant for mDNS.
Dec 1 15:45:14 ryan-desktop avahi-daemon[5252]: Withdrawing address record for fe80::218:f8ff:fe2d:f0f4 on wlan0.
Dec 1 15:45:14 ryan-desktop avahi-daemon[5252]: Joining mDNS multicast group on interface wlan0.IPv4 with address ************.
Dec 1 15:45:14 ryan-desktop avahi-daemon[5252]: New relevant interface wlan0.IPv4 for mDNS.
Dec 1 15:45:14 ryan-desktop avahi-daemon[5252]: Registering new address record for ******** on wlan0.IPv4.
Dec 1 15:45:15 ryan-desktop NetworkManager: <info> Clearing nscd hosts cache.
Dec 1 15:45:15 ryan-desktop NetworkManager: <WARN> nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))


Im not sure if this is to blame but thats it... It seems thats whats always in my sys log when my sys crashes

Here are my specs**

500 gig sata HD Western Digital
4 gigs of DDR2 ram
64 bit intel core 2 quad
MSI mother board
MSI N9600 gt - i believe its Nvidia chip based...

---

### Post by Zetheroo on 2008-12-02
Switch back to Hardy. :KS

---

### Post by the_tazinator on 2008-12-03
I gave up. I wiped out 8.10 and installed 8.04. Everything is working fine, including the wireless with no issues. I did have a PCM/CIA wireless card to use, but that defeats the purpose of getting an internal card. It works fine in 8.04, why not in 8.10? It seems like development is going backwards. I have this machine set for dual boot between Vista and Ubuntu and having to carry around an additional card for wireless use in Ubuntu is annoying. I had to do that with my old laptop.

---

### Post by davidschein on 2008-12-03
This started for me after letting the update manager upgrade, among other things, my kernel.  Running 64-bit 8.10 on a Dell D830 so it upgraded to 2.6.27-9-generic.

I have had to wire myself to the network and switch off the wireless switch.

This does kind of suck.

---

### Post by RavUn on 2008-12-03
Weird.  Switching TO 8.10 from 8.04 seemed to have fixed it for me.

---

### Post by ryclegman on 2008-12-03
Im actually using _Hardy_ and it happens a lot for me....I believe my networking card is a Ralink? not sure

---

### Post by Zetheroo on 2008-12-03
> **ryclegman said:**
> Im actually using _Hardy_ and it happens a lot for me....I believe my networking card is a Ralink? not sure

You can check with a simple lspci in the terminal. If its USB than do lsusb.

---

### Post by pah99 on 2008-12-03
Hi. I have a Dell Studio 1535 with 8.10 installed. This thing crashes on me every single day. I have looked into the System Log, and in particular the auth.log. When looking at it, the last thing mentioned before the crash is the following:
Dec 3 20:58:07 pasha-laptop gdm[15026]: )gnome-keyring-daemon: couldn't lookup pkcs11 component setting: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details - 1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified.

This error pops up a lot in this log. I have looked at that website but couldn't figure anything out.

This only happens when wifi is on.

---

### Post by Zetheroo on 2008-12-03
> **pah99 said:**
> Hi. I have a Dell Studio 1535 with 8.10 installed. This thing crashes on me every single day. I have looked into the System Log, and in particular the auth.log. When looking at it, the last thing mentioned before the crash is the following:
Dec 3 20:58:07 pasha-laptop gdm[15026]: )gnome-keyring-daemon: couldn't lookup pkcs11 component setting: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details - 1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified.

This error pops up a lot in this log. I have looked at that website but couldn't figure anything out.

This only happens when wifi is on.

Well the obvious question is "What wireless chipset are you using?"

---

### Post by pah99 on 2008-12-03
Broadcom corp BCM 4332 802.11 a/b/g/n Wireless LAN controller (rev 01)

pasha@pasha-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 04)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 04)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 04)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 04)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f4)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 04)
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3400 Series
01:00.1 Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
0c:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)

---

### Post by Zetheroo on 2008-12-04
> **pah99 said:**
> Broadcom corp BCM 4332 802.11 a/b/g/n Wireless LAN controller (rev 01)



Then your most likely one of the many with Broadcom wireless devices that are experiencing Kernel Panics.
So far the choices are to either replace your hardware or revert back to Hardy. ;)

---

### Post by ryclegman on 2008-12-04
I figured it out its a wireless issue, and i used [https://help.ubuntu.com/community/Wi...er/Ndiswrapper](https://help.ubuntu.com/community/Wi...er/Ndiswrapper) .... We will see if it works
!!!

---

### Post by the_tazinator on 2008-12-05
Well... giving up didn't work either, but I am getting closer. I currently have 8.04 installed. The base kernel version that is installed when you install 8.04 is 2.6.24-16. Everything works fine. All wireless connections fuction properly with no system lockups. After doing a system update, the kernel version is upgradede to 2.6.24-22. The system boots fine and I am able to connect to a WEP wireless network. However, when I try to connect to a WPA2 network the machine locks up while attempting to connect. I have rebooted several times and by picking different kernel versions in the grub menu, I was able to easily reproduce the issue. Somewhere between 2.6.24-16 and 2.6.24-22 something changed that causes these errors.

If you are having this issue in 8.04 try using a older kernel by selecting it from the grub menu and see if it fixes the issue. Go back to atleast 2.6.24-16. I have not installed any version inbetween the two to see exactly what version causes these errors. That will be my next step. I am not sure if you can downgrade the kernel verion on 8.10 or not. I never had to try it before. I would be interesting to know if it would work.

---

### Post by ryclegman on 2008-12-05
well reverting back to hardy wont do anything.... My method did connect the hardware, but never would actually allow access to the internet. THE problem is the WIRELESS DRIVER! linksys does not provide linux drivers

---

### Post by ryclegman on 2008-12-05
i switched to Linux mint and i haven't had any more problems!

---

### Post by math_phy on 2008-12-08
linux mint 5 is based on hardy. I have not had any problems after reverting back to hardy. BTW I have an intel wireless chipset

---

### Post by trumpeteersman on 2008-12-09
I have Hardy and having the same problems.
/var/log/messages tells me nothing, just --marks-- at the time it happened.  Even more strange is it still writes the --mark-- every 20 minutes even after it has frozen.  Tried ctrl+alt+del, sysrq+b, ctrl+alt+f1.  Nothing works but a hard reset.  Happens 2-4 times a week.

I have:
Core 2 Duo T7100
Intel GMA X3100 video
1G RAM
Intel 3945ABG Wireless

Kubuntu Hardy
KDE 3.5.10
Vanilla 2.6.24-21-generic
xserver-xorg-video-intel 2.2.1 (-1ubuntu13.7)
iwl3945 ?? -Built into kernel?

---

### Post by Nixie Pixel on 2008-12-10
Well, it happened last night, for the first time in weeks.  It happened while the laptop lid was closed and nothing was going on (I left it on but shut for the night).

Here are the relevant (I think) log outputs:

Syslog

Dec  9 21:40:17 raptor kernel: [24077.015271] eth0: link up, 10Mbps, half-duplex, lpa 0x0000

Dec  9 21:40:17 raptor kernel: [24077.016264] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

Dec  9 21:40:17 raptor NetworkManager: <info>  (eth0): carrier now ON (device state 2) 

Dec  9 21:40:17 raptor NetworkManager: <info>  (eth0): device state change: 2 -> 3 

Dec  9 21:40:17 raptor NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0' 

Dec  9 21:40:17 raptor NetworkManager: <info>  (eth0): device state change: 3 -> 4 

Dec  9 21:40:17 raptor NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 

Dec  9 21:40:17 raptor NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 

Dec  9 21:40:17 raptor NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 

Dec  9 21:40:17 raptor NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 

Dec  9 21:40:17 raptor NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 

Dec  9 21:40:17 raptor NetworkManager: <info>  (eth0): device state change: 4 -> 5 

Dec  9 21:40:17 raptor NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 

Dec  9 21:40:17 raptor NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 

Dec  9 21:40:17 raptor NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 

Dec  9 21:40:17 raptor NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 

Dec  9 21:40:17 raptor NetworkManager: <info>  (eth0): device state change: 5 -> 7 

Dec  9 21:40:17 raptor NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 

Dec  9 21:40:17 raptor NetworkManager: <info>  dhclient started with pid 11578 

Dec  9 21:40:17 raptor NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 

Dec  9 21:40:17 raptor dhclient: Internet Systems Consortium DHCP Client V3.1.1

Dec  9 21:40:17 raptor dhclient: Copyright 2004-2008 Internet Systems Consortium.

Dec  9 21:40:17 raptor dhclient: All rights reserved.

Dec  9 21:40:17 raptor dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Dec  9 21:40:17 raptor dhclient: 

Dec  9 21:40:17 raptor NetworkManager: <info>  DHCP: device eth0 state changed (null) -> preinit 

Dec  9 21:40:17 raptor dhclient: Listening on LPF/eth0/00:1b:38:fc:19:20

Dec  9 21:40:17 raptor dhclient: Sending on   LPF/eth0/00:1b:38:fc:19:20

Dec  9 21:40:17 raptor dhclient: Sending on   Socket/fallback

Dec  9 21:40:18 raptor dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4

Dec  9 21:40:18 raptor dhclient: DHCPOFFER of 192.168.0.146 from 192.168.0.1

Dec  9 21:40:18 raptor dhclient: DHCPREQUEST of 192.168.0.146 on eth0 to 255.255.255.255 port 67

Dec  9 21:40:18 raptor dhclient: DHCPACK of 192.168.0.146 from 192.168.0.1

Dec  9 21:40:18 raptor NetworkManager: <info>  DHCP: device eth0 state changed preinit -> bound 

Dec  9 21:40:18 raptor NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 

Dec  9 21:40:18 raptor NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) started... 

Dec  9 21:40:18 raptor NetworkManager: <info>    address 192.168.0.146 

Dec  9 21:40:18 raptor NetworkManager: <info>    prefix 24 (255.255.255.0) 

Dec  9 21:40:18 raptor NetworkManager: <info>    gateway 192.168.0.1 

Dec  9 21:40:18 raptor NetworkManager: <info>    nameserver '192.168.0.1' 

Dec  9 21:40:18 raptor NetworkManager: <info>    domain name 'wavecable.com' 

Dec  9 21:40:18 raptor NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 

Dec  9 21:40:18 raptor NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) complete. 

Dec  9 21:40:18 raptor dhclient: bound to 192.168.0.146 -- renewal in 1663415 seconds.

Dec  9 21:40:18 raptor NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started... 

Dec  9 21:40:18 raptor avahi-daemon[4759]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.0.146.

Dec  9 21:40:18 raptor avahi-daemon[4759]: New relevant interface eth0.IPv4 for mDNS.

Dec  9 21:40:18 raptor avahi-daemon[4759]: Registering new address record for 192.168.0.146 on eth0.IPv4.

Dec  9 21:40:18 raptor avahi-daemon[4759]: Registering new address record for fe80::21b:38ff:fefc:1920 on eth0.*.

Dec  9 21:40:19 raptor NetworkManager: <info>  Policy set 'Auto LOOMIS' (eth1) as default for routing and DNS. 

Dec  9 21:40:19 raptor NetworkManager: <info>  (eth0): device state change: 7 -> 8 

Dec  9 21:40:19 raptor NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS. 

Dec  9 21:40:19 raptor NetworkManager: <info>  Activation (eth0) successful, device activated. 

Dec  9 21:40:19 raptor NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 

Dec  9 21:40:19 raptor kernel: [24079.022638]  CIFS VFS: Error connecting to IPv4 socket. Aborting operation

Dec  9 21:40:19 raptor kernel: [24079.022657]  CIFS VFS: cifs_mount failed w/return code = -111

Dec  9 21:40:20 raptor ntpdate[11641]: adjust time server 91.189.94.4 offset -0.144365 sec

Dec  9 21:40:27 raptor kernel: [24087.428047] eth0: no IPv6 routers present

Dec  9 21:42:27 raptor NetworkManager: <info>  (eth1): supplicant connection state change: 7 -> 0 

Dec  9 21:42:28 raptor NetworkManager: <info>  (eth1): supplicant connection state change: 0 -> 4 

Dec  9 21:42:28 raptor NetworkManager: <info>  (eth1): supplicant connection state change: 4 -> 7 

Dec  9 21:56:38 raptor NetworkManager: <info>  (eth1): supplicant connection state change: 7 -> 0 

Dec  9 21:56:38 raptor NetworkManager: <info>  (eth1): supplicant connection state change: 0 -> 2 

kern.log

Dec  9 21:36:58 raptor kernel: [23878.600220] usb 1-1: USB disconnect, address 4

Dec  9 21:37:15 raptor kernel: [23895.424808] CPU0 attaching NULL sched-domain.

Dec  9 21:37:15 raptor kernel: [23895.424828] CPU1 attaching NULL sched-domain.

Dec  9 21:37:15 raptor kernel: [23895.428188] CPU0 attaching sched-domain:

Dec  9 21:37:15 raptor kernel: [23895.428198]  domain 0: span 0-1 level MC

Dec  9 21:37:15 raptor kernel: [23895.428205]   groups: 0 1

Dec  9 21:37:15 raptor kernel: [23895.428216]   domain 1: span 0-1 level CPU

Dec  9 21:37:15 raptor kernel: [23895.428222]    groups: 0-1

Dec  9 21:37:15 raptor kernel: [23895.428233] CPU1 attaching sched-domain:

Dec  9 21:37:15 raptor kernel: [23895.428238]  domain 0: span 0-1 level MC

Dec  9 21:37:15 raptor kernel: [23895.428244]   groups: 1 0

Dec  9 21:37:15 raptor kernel: [23895.428253]   domain 1: span 0-1 level CPU

Dec  9 21:37:15 raptor kernel: [23895.428259]    groups: 0-1

Dec  9 21:38:41 raptor kernel: [23981.292933] CPU0 attaching NULL sched-domain.

Dec  9 21:38:41 raptor kernel: [23981.292953] CPU1 attaching NULL sched-domain.

Dec  9 21:38:41 raptor kernel: [23981.312147] CPU0 attaching sched-domain:

Dec  9 21:38:41 raptor kernel: [23981.312161]  domain 0: span 0-1 level MC

Dec  9 21:38:41 raptor kernel: [23981.312167]   groups: 0 1

Dec  9 21:38:41 raptor kernel: [23981.312182] CPU1 attaching sched-domain:

Dec  9 21:38:41 raptor kernel: [23981.312187]  domain 0: span 0-1 level MC

Dec  9 21:38:41 raptor kernel: [23981.312196]   groups: 1 0

Dec  9 21:39:33 raptor kernel: [24033.289061] usb 1-2: new low speed USB device using uhci_hcd and address 5

Dec  9 21:39:33 raptor kernel: [24033.469090] usb 1-2: configuration #1 chosen from 1 choice

Dec  9 21:39:33 raptor kernel: [24033.526022] input: Microsoft Microsoft Wireless Optical Mouse&#65454; 1.00 as /devices/pci0000:00/0000:00:1d.0/usb1/1-2/1-2:1.0/input/input11

Dec  9 21:39:33 raptor kernel: [24033.555252] input,hidraw0: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Mouse&#65454; 1.00] on usb-0000:00:1d.0-2

Dec  9 21:40:17 raptor kernel: [24077.015271] eth0: link up, 10Mbps, half-duplex, lpa 0x0000

Dec  9 21:40:17 raptor kernel: [24077.016264] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

Dec  9 21:40:19 raptor kernel: [24079.022638]  CIFS VFS: Error connecting to IPv4 socket. Aborting operation

Dec  9 21:40:19 raptor kernel: [24079.022657]  CIFS VFS: cifs_mount failed w/return code = -111

Dec  9 21:40:27 raptor kernel: [24087.428047] eth0: no IPv6 routers present

If there are any other diagnostics I can run, I would appreciate it if someone would post them.  From all the people complaining that such diagnostics can happen in Windows, you would think someone with the relevant Linux knowledge would step up and let us know.  Unless it just doesn't exist in Linux?

Thanks again!

---

### Post by the_tazinator on 2008-12-10
Has anyone tried an older version of kernel? As I mentioned before, my machine works fine with the kernel Hardy was shipped with (2.6.24.16) but fails after I go through all of the upgrades and it updates the kernel to 2.6.24-22. As long as no mods have been done with the grub menu, you should be able to revert to an older kernel version easily.

---

### Post by math_phy on 2008-12-10
@ nixie pixel 
try adding
```
blacklist ipv6
```
to the blaclist file in /etc/modprobe.d
and reboot your system once.
the last entry mentions ipv6, so just a hunch.
else install hardy. I have not had any problems with both the old and new kernels in hardy.

---

### Post by ryclegman on 2008-12-10
Im using hardy and i still get the freezes.  downgrading or upgrading wont do a thing.

sorry

---

### Post by Nixie Pixel on 2008-12-10
It happened again this afternoon.  I had not read the suggestions here yet.  Here are some logs:

daemon.log

Dec 10 16:19:01 raptor dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
Dec 10 16:19:01 raptor dhclient: DHCPOFFER of 192.168.0.141 from 192.168.0.1
Dec 10 16:19:01 raptor dhclient: DHCPREQUEST of 192.168.0.141 on eth1 to 255.255.255.255 port 67
Dec 10 16:19:01 raptor dhclient: DHCPACK of 192.168.0.141 from 192.168.0.1
Dec 10 16:19:01 raptor NetworkManager: <info>  DHCP: device eth1 state changed preinit -> bound 
Dec 10 16:19:01 raptor NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) scheduled... 
Dec 10 16:19:01 raptor NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) started... 
Dec 10 16:19:01 raptor NetworkManager: <info>    address 192.168.0.141 
Dec 10 16:19:01 raptor NetworkManager: <info>    prefix 24 (255.255.255.0) 
Dec 10 16:19:01 raptor NetworkManager: <info>    gateway 192.168.0.1 
Dec 10 16:19:01 raptor NetworkManager: <info>    nameserver '192.168.0.1' 
Dec 10 16:19:01 raptor NetworkManager: <info>    domain name 'wavecable.com' 
Dec 10 16:19:01 raptor NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled... 
Dec 10 16:19:01 raptor NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) complete. 
Dec 10 16:19:01 raptor dhclient: bound to 192.168.0.141 -- renewal in 1745879 seconds.
Dec 10 16:19:01 raptor NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) started... 
Dec 10 16:19:01 raptor avahi-daemon[4889]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.0.141.
Dec 10 16:19:01 raptor avahi-daemon[4889]: New relevant interface eth1.IPv4 for mDNS.
Dec 10 16:19:01 raptor avahi-daemon[4889]: Registering new address record for 192.168.0.141 on eth1.IPv4.
Dec 10 16:19:02 raptor NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS. 
Dec 10 16:19:02 raptor NetworkManager: <info>  (eth1): device state change: 7 -> 8 
Dec 10 16:19:02 raptor NetworkManager: <info>  Activation (eth1) successful, device activated. 
Dec 10 16:19:02 raptor NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete. 
Dec 10 16:19:03 raptor ntpdate[16444]: adjust time server 91.189.94.4 offset -0.390474 sec
Dec 10 16:46:43 raptor chipcardd[4974]: devicemanager.c: 3373: Changes in hardware list

kern.log

Dec 10 16:19:02 raptor kernel: [44539.085460]  CIFS VFS: Error connecting to IPv4 socket. Aborting operation
Dec 10 16:19:02 raptor kernel: [44539.085472]  CIFS VFS: cifs_mount failed w/return code = -111
Dec 10 16:46:42 raptor kernel: [46199.104053] usb 1-3: USB disconnect, address 5

Does this help narrow it down at all?

---

### Post by math_phy on 2008-12-11
well here is something that seems to be working on intrepid for intel chipset.
1]go to synaptic, 
2]enable the "proposed" repositories. 
3]hit reload.
4] search for linux 2.6.27-10 and install (better still to upgrade all packages).
5] reboot.
has not given me trouble for some time now.

---

### Post by math_phy on 2008-12-11
@ryclegman
try installing nscd . I looked at your logs and that is the last entry "failed to execute nscd"

---

### Post by ryclegman on 2008-12-11
hey thanks i installed it. Ill let you know if anything else happens !

---

### Post by Morty007 on 2008-12-11
I had my first kernel panic last night, and it happened twice actually. I'm using Linux Mint 6.

 The first time was watching a video on CNN, and the 2nd time was while listening to internet radio. 

What does that mean, it has to do with flash?

---

### Post by Morty007 on 2008-12-11
OK, I think I'm on to something. The panic happens when I listen to internet radio.


The Kernel Log

Dec 11 19:07:11 marc-laptop kernel: [ 5901.860729] compiz.real[5787]: segfault at 40563 ip 08055c8c sp bfc50da0 error 4 in compiz.real[8048000+34000]


Here is the system log- 1st line looks scary. 

Dec 11 19:07:11 marc-laptop gdm[5369]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
Dec 11 19:07:11 marc-laptop kernel: [ 5901.860729] compiz.real[5787]: segfault at 40563 ip 08055c8c sp bfc50da0 error 4 in compiz.real[8048000+34000]
Dec 11 19:07:11 marc-laptop bonobo-activation-server (marc-14309): could not associate with desktop session: Failed to connect to socket /tmp/dbus-4dFskkfnLG: Connection refused
Dec 11 19:07:14 marc-laptop acpid: client connected from 14361[0:0] 
Dec 11 19:07:17 marc-laptop acpid: client connected from 14361[0:0] 
Dec 11 19:07:18 marc-laptop gdmgreeter[14380]: GdkPixbuf-CRITICAL: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed 
Dec 11 19:07:18 marc-laptop gdmgreeter[14380]: GdkPixbuf-CRITICAL: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed 
Dec 11 19:07:18 marc-laptop gdmgreeter[14380]: GLib-GObject-CRITICAL: g_object_unref: assertion `G_IS_OBJECT (object)' failed 
Dec 11 19:07:18 marc-laptop gdmgreeter[14380]: GLib-GObject-WARNING: invalid (NULL) pointer instance 
Dec 11 19:07:18 marc-laptop gdmgreeter[14380]: GLib-GObject-CRITICAL: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed 
Dec 11 19:07:18 marc-laptop gdmgreeter[14380]: GdkPixbuf-CRITICAL: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed 
Dec 11 19:07:18 marc-laptop gdmgreeter[14380]: GdkPixbuf-CRITICAL: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed 
Dec 11 19:07:18 marc-laptop gdmgreeter[14380]: GLib-GObject-CRITICAL: g_object_unref: assertion `G_IS_OBJECT (object)' failed 
Dec 11 19:07:18 marc-laptop gdmgreeter[14380]: GdkPixbuf-CRITICAL: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed 
Dec 11 19:07:18 marc-laptop gdmgreeter[14380]: GdkPixbuf-CRITICAL: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed 
Dec 11 19:07:18 marc-laptop gdmgreeter[14380]: GLib-GObject-CRITICAL: g_object_unref: assertion `G_IS_OBJECT (object)' failed 
Dec 11 19:07:18 marc-laptop gdmgreeter[14380]: GLib-GObject-WARNING: invalid (NULL) pointer instance 
Dec 11 19:07:18 marc-laptop gdmgreeter[14380]: GLib-GObject-CRITICAL: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed 
Dec 11 19:07:18 marc-laptop gdmgreeter[14380]: GdkPixbuf-CRITICAL: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed 
Dec 11 19:07:18 marc-laptop gdmgreeter[14380]: GdkPixbuf-CRITICAL: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed 
Dec 11 19:07:18 marc-laptop gdmgreeter[14380]: GLib-GObject-CRITICAL: g_object_unref: assertion `G_IS_OBJECT (object)' failed 
Dec 11 19:07:18 marc-laptop gdmgreeter[14380]: GdkPixbuf-CRITICAL: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed 
Dec 11 19:07:18 marc-laptop gdmgreeter[14380]: GdkPixbuf-CRITICAL: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed 
Dec 11 19:07:18 marc-laptop gdmgreeter[14380]: GLib-GObject-CRITICAL: g_object_unref: assertion `G_IS_OBJECT (object)' failed 
Dec 11 19:07:18 marc-laptop gdmgreeter[14380]: GLib-GObject-WARNING: invalid (NULL) pointer instance 
Dec 11 19:07:18 marc-laptop gdmgreeter[14380]: GLib-GObject-CRITICAL: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed 
Dec 11 19:07:30 marc-laptop pulseaudio[14498]: ltdl-bind-now.c: Failed to find original dlopen loader.
Dec 11 19:07:30 marc-laptop pulseaudio[14501]: pid.c: Stale PID file, overwriting.
Dec 11 19:07:30 marc-laptop pulseaudio[14501]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Dec 11 19:07:30 marc-laptop pulseaudio[14501]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Dec 11 19:07:31 marc-laptop x-session-manager[14410]: WARNING: Unable to find provider 'gnome-wm' of required component 'windowmanager' 
Dec 11 19:07:41 marc-laptop x-session-manager[14410]: WARNING: Application 'gnome-wm.desktop' failed to register before timeout 
Dec 11 19:07:51 marc-laptop x-session-manager[14410]: WARNING: Application 'libcanberra-login-sound.desktop' failed to register before timeout 
Dec 11 19:07:51 marc-laptop x-session-manager[14410]: WARNING: Could not launch application 'emerald--replace.desktop': Unable to start application: Failed to execute child process "emerald--replace" (No such file or directory) 
Dec 11 19:07:53 marc-laptop pulseaudio[14501]: module-x11-xsmp.c: X11 session manager not running.
Dec 11 19:07:53 marc-laptop pulseaudio[14501]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Dec 11 19:07:55 marc-laptop anacron[14783]: Anacron 2.3 started on 2008-12-11
Dec 11 19:07:55 marc-laptop anacron[14783]: Normal exit (0 jobs run)
Dec 11 19:07:55 marc-laptop kernel: [ 5945.793341] CPU0 attaching NULL sched-domain.
Dec 11 19:07:55 marc-laptop kernel: [ 5945.793354] CPU1 attaching NULL sched-domain.
Dec 11 19:07:55 marc-laptop kernel: [ 5945.829162] CPU0 attaching sched-domain:
Dec 11 19:07:55 marc-laptop kernel: [ 5945.829169]  domain 0: span 0-1 level MC
Dec 11 19:07:55 marc-laptop kernel: [ 5945.829172]   groups: 0 1
Dec 11 19:07:55 marc-laptop kernel: [ 5945.829178] CPU1 attaching sched-domain:
Dec 11 19:07:55 marc-laptop kernel: [ 5945.829180]  domain 0: span 0-1 level MC
Dec 11 19:07:55 marc-laptop kernel: [ 5945.829182]   groups: 1 0
Dec 11 19:08:57 marc-laptop modprobe: WARNING: Not loading blacklisted module ipv6 
Dec 11 19:09:03 marc-laptop modprobe: WARNING: Not loading blacklisted module ipv6

---

### Post by Nixie Pixel on 2008-12-11
I am running on 2.6.27-10, and update every day...

---

### Post by ions on 2008-12-12
I have the hardlock with flashing lights as well.

Dell Inspiron running 8.10 with updates installed as they come upgraded from 8.04(which was far more stable and faster).  

```
$ lspci | grep 4965
0c:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)

```

I've noticed that in syslog the last thing that occurs before a lockup is this:

```
Dec 12 11:05:05 laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 7 -> 6 
Dec 12 11:05:05 laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 6 -> 7
```

Although there isn't a lockup after everytime this occurs.  

I'm curious if anyone else who has this problem also has the klogd and dd bug where it maxes out the cpu?  Just in case they're related.  There's a bug about this on launchpad but I cant find it right now.

---

### Post by pah99 on 2008-12-12
Updating to 2.6.27-10 has, I guess, fixed the problem. Haven't had a kernel panic since upgrading.

---

### Post by ions on 2008-12-12
How long ago did you install that kernel?  I've gone days without a lockup then had 5 in 24 hours.

---

### Post by pah99 on 2008-12-12
Since last week sometime. I can't recall having a lockup since. What type of wireless card do you have?

---

### Post by Nixie Pixel on 2008-12-12
When I first installed 8.10 I would crash about twice a day.  I upgraded to the latest kernel (-10) and had no change.

Then a few days later, mysteriously it stopped happening.  This lasted for about two weeks.  Now I've crashed twice in the last two days, without touching the kernel.

So I have no idea what is causing this, but for me a kernal update did me no good.

---

### Post by ions on 2008-12-12
> **pah99 said:**
> Since last week sometime. I can't recall having a lockup since. What type of wireless card do you have?

[Post #80](http://ubuntu-virginia.ubuntuforums.org/showpost.php?p=6355841&postcount=80)

Kernel being used:
```

$ uname -a
Linux laptop 2.6.27-9-generic #1 SMP Thu Nov 20 22:15:32 UTC 2008 x86_64 GNU/Linux

```

---

### Post by pah99 on 2008-12-12
I'm thinking it may be with the type of wireless card you have. 
Anyone here have a Broadcom card that used to cause this problem, but stop after kernel update to Linux 2.6.27-10-generic?

---

### Post by pah99 on 2008-12-12
Okay, forget what I've said. It just happened three times in a row. 
Good news is, I have a new idea: Hardware. If you could, please list out all of your hardware specs and we'll see if there is any correlation between us. I recommend you use Sysinfo for this. Also, please tell what you were doing at the time it happened. For example, when it happens to me, I am using Firefox and either listening to music, or watching a movie.
The reason why I think it may be something other than problems with wireless is because we all have different types of wifi. It has to be something else plaguing us.

Please use the following format: 

Version (of Ubuntu): 
Kernel: 
Processor:  
Memory: 
Hard drive: 
Host Bridge:
PCI bridge:
USB Controller:
ISA bridge: 
Graphics Card:
Multimedia audio Controller: 
Wireless card:
Ethernet: 

So, for example, my setup is the following:

Version: Ubuntu 8.10 (intrepid) x64
Kernel: 2.6.27-10-generic 
Processor:  Core(TM)2 Duo CPU     T9300  @ 2.50GHz
Memory: 4 GB. ddr2 800
Hard drive: 250 GB WDC WD2500BEVS-7
Host Bridge, PCI bridge, : Intel Corp. Mobile PM965/GM965/GL960 
USB Controller, ISA bridge: Intel Corp 82801H
Graphics Card: ATI Mobility Radeon HD 3450 
Multimedia audio Controller: HDA Intel- STAC92xx 
Wireless card: Broadcom Corp. BCM4322 802.11 a/b/g/n 
Ethernet: Broadcom Corp. BCM5784M

I am actually thinking its the hard drive, but thats just me.

---

### Post by ions on 2008-12-12
Did you check out the first 6 pages of this thread?  Pretty sure it's not hardware.  In fact I'm pretty much convinced it's the wireless driver.  For my PC anyway.

---

### Post by jron on 2008-12-12
I just purchased a Lenovo S10 and installed Ubuntu 8.10 on it. The wireless card causes the system to lock. This happens almost 3-5 seconds after it connects to my access point. The system must be hard reset to recover. If I disable the wireless, the problem goes away. I should also mention that I'm running OpenWRT 8.09 RC1 on my router.

The wifi card is a BCM4312.

---

### Post by pah99 on 2008-12-12
> **ions said:**
> Did you check out the first 6 pages of this thread?  Pretty sure it's not hardware.  In fact I'm pretty much convinced it's the wireless driver.  For my PC anyway.

If it were the wifi, then why is it affecting ALL types of wifi? Why is it affecting different brands of wifi cards? If it were a wifi problem, it would affect only one type of brand, and no others. Problem is, their all screwed. Intel, broadcom, etc. I realize that the problem only shows up when wireless is being used. Thus, I think that the problem is that there is a conflict between the wifi and some other hardware.

At least check to see if you have any similar hardware specs as I do. If not, we rule out my idea and start from square one again.

---

### Post by networm1230 on 2008-12-13
Cool! what i mean bye that is that you and i have the some computer type. not the crashing and freezing. my computer is a Compaq Presario SR1103WM Desktop PC 

um.. will the crashing and freezing may be cussed bye many reasons. on you post you sad that you duel boot different operating systems that may be the problem  some time when booting more than one OS is overkill for pc hardware and software to handle. splashily the possessor and the hard drive. in stead of running all operating systems on one drive try to run theme on spirit drives. or you can us VMware (virtual machine) install your operating systems on a virtual machine instead of on you have physical hard drive running vmware is safer on your hard drive because you do not need to duel boot your pc and all of you operating systems well be running on a virtual machine so you do not need to weary about data loss or messing up you physical hard drive in any way.

possible reason 1. your pc may be over heating. due to dust on the hardware some computers today have a tempter threshold if a computer over heats it some time acts crazy and lights start to blink telling you some thing is wrong with the computer = clean your hardware 

possible reason 2. your possessor can some time crash and freeze if you are running a low level possessor like intel celeron  possessors doing a lot of multitasking some times crashes the possessors try not to run a lot of graphics like stuff on this  possessor. I am going to give you small tip on monitoring your computers systems monitoring. lift click on moues on your tool bar (panel) and click on add to panel scroll down to you see systems monitoring and add it to your panel now you can see what is going on in your computer.

I hop this helps you

note: (VMware) Virtualbox is free and open source

---

### Post by ryclegman on 2008-12-13
alrighty had another crash downloading something...

Heres the code > Dec 13 10:33:43 ryan-desktop modprobe: WARNING: Not loading blacklisted module ipv6 
Dec 13 10:33:41 ryan-desktop ntpdate[7404]: step time server 91.189.94.4 offset -2.655412 sec
Dec 13 10:33:42 ryan-desktop kernel: [   90.711716] /dev/vmmon[0]: HostIF_ReadUptime: detected settimeofday: fixed uptimeBase old 18445514891330892843 new 18445514891333548262 attempts 1
Dec 13 10:33:48 ryan-desktop modprobe: WARNING: Not loading blacklisted module ipv6 

---

### Post by Nixie Pixel on 2008-12-13
I guarantee you that the problem is not my wireless driver.  Why?  Because the first time I had this problem -I was in the middle of installing Intrepid from CD-.  It was literally in the middle of copying files from the CD to my laptop.  No wireless was running, and though I don't know the install process, I doubt the driver was even loaded.  I had used the Live CD to boot right to the install process, not even load Ubuntu first. 

My system:

Version (of Ubuntu):  Intrepid Ibex 8.10
Kernel:  2.6.27-10-generic (#1 SMP Fri Nov 21 12:00:22 UTC 2008)
Processor:  Intel(R) Pentium(R) Dual  CPU  T2330  @ 1.60GHz
Memory:  2 GB
Hard drive:  Fujitsu MHY2120B 120GB
Host Bridge:  Intel Mobile PM965/GM965/GL960 
PCI bridge:  Intel 82801H PCI Express & 82801 Mobile PCI Bridge
USB Controller:  Intel 82801H
ISA bridge:  Intel 82801HEM
Graphics Card:  Intel Mobile GM965/GL960 
Multimedia audio Controller:  Intel 82801H HD Audio
Wireless card:  Broadcom BCM4311 802.11b/g rev 02
Ethernet:  Realtek Semiconductor RTL-8139/8139C/8139C+ rev 10

I also had this USB device plugged in each time the system crashed:
Microsoft Wireless Notebook Optical Mouse 3000

I just purchased this replacement:
Kensington Slimblade Presenter Mouse

What I am doing at the time it crashes is random:
-Installing Intrepid
-Browsing with Firefox
-Laptop is idling
-Laptop is idling with screen saver
-Laptop is idling with monitor shut off
-Laptop is idling with lid closed

I'm wondering if it is a problem with my USB mouse, given some of the info that came out of the logs during the crashes.

---

### Post by pah99 on 2008-12-13
PCI bridge: Intel 82801H PCI Express & 82801 Mobile PCI Bridge
USB Controller: Intel 82801H
ISA bridge: Intel 82801HEM

I see something similar. And NixiePixel said that it only happens when the mouse was plugged in. Perhaps a USB conflict?

---

### Post by networm1230 on 2008-12-13
> **Nixie Pixel said:**
> Hi, I recently installed Ubuntu 8.10 on a Compaq Presario A909US (dual-booting with Vista).  At the moment I am having an easier time of it than I did with 8.04 which I gave up on a while ago, aside from some Broadcom wireless issues (who hasn't had those?? =D).  

However my system has frozen twice now in the four days I have had it installed - a hard freeze that I needed to hit the power button to get out of.  My Caps Lock indicator was blinking on and off after the freeze happened, both times.

Does anyone know what this means or could be?

Thanks!

~Nix

in stead of running duel boot maybe look in to Vmware (virtual machine) VirtualBox is free and open sours 

I hop you find this us full    gamer4life!!

---

### Post by Nixie Pixel on 2008-12-13
Well, thank you, but I already have a Vista license (it came with the laptop) and I am not sure of what the benefit of doing so would be.

But was that a suggestion to try and help with the problem we are having in this thread?  If not, PMs are a great way to get in touch with me.  :)

Regarding the issue at hand, I have three USB ports on this laptop.  It is possible that the problem corresponds to a particular port, but I'm not sure as I haven't been paying attention...

---

### Post by pah99 on 2008-12-13
Hold on for one second on the USB thing. So far three of us say we are dual booting (well, counting me). What if this is an issue with dual booting? How many other people are dual booting and have this issue?

---

### Post by ryclegman on 2008-12-13
Im duel booting as well and have this problem. Mine will crash with or without anything plugged into a usb port.

---

### Post by RavUn on 2008-12-13
I dual boot and was having the problem frequently.  After upgrading to 8.10 (kernel 2.6.27-9-generic) the issue has stopped.  Now I just have more issues with firefox freezes and flash problems... but that's a different thread.

---

### Post by pah99 on 2008-12-13
Yeah. I am having the same problem: I dual boot with Vista. And I've never had a kernel panic being USB related.

---

### Post by Zetheroo on 2008-12-14
My system:

Version (of Ubuntu): Intrepid Ibex 8.10
Kernel: 2.6.27-8-generic + 2.6.27-9-generic
Processor: Intel(R) Core(TM)2 Duo CPU     T9300  @ 2.50GHz
Memory: 3 GB DDR2
Hard drive: HITACHI HTS72201 100GB 7200 RPM
Host Bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
PCI bridge: Intel 82801H (ICH8 Family) PCI Express (rev 03)
USB Controller: Intel 82801H (ICH8 Family) (rev 03)
ISA bridge: Intel 82801HEM
Graphics Card: Intel Mobile GM965/GL960
Multimedia audio Controller: Intel 82801H HD Audio
Wireless card: Atheros AR5212 802.11 abg NIC
Ethernet: Broadcom Netlink BCM5787M Gigabit Ethernet PCI Express

Dual Boot: Yes! Windows XP Pro/Ubuntu Intrepid

I reverted back to Hardy and now an "triple" booting with Windows XP Pro, Ubuntu Hardy and Kubuntu Intrepid. Interesting tidbit is that I have gone for 3 days without a kernel panic in Kubuntu Intrepid.

---

### Post by gillmt on 2008-12-14
This will not help you at all I'm afraid but I wanted to add my concerns about 8.10 (and the Mint equivalent). I run two desktops - AMD64x2 and an Intel - both from a KVM switch. For six months I had no issues at all using Hardy.

When I tried upgrading to Intrepid, both machines ran hot, froze and logs showed i/o messages being repeated on desktop 800000 times - means nothing to me and I am still struggling to improve my understanding.

When I went back to Hardy and Mint 5 - everything waas just fine - low CPU use, no thrashing, no freezes.

---

### Post by pah99 on 2008-12-14
Okay, so now we have three people with the same things in common.

PCI bridge: Intel 82801H (ICH8 Family) PCI Express (rev 03)
USB Controller: Intel 82801H (ICH8 Family) (rev 03)
ISA bridge: Intel 82801HEM
Multimedia audio Controller: Intel 82801H HD Audio

Now, I have never had the problem being USB, and the PCI and the ISA I doubt are a problem... so perhaps this is an audio problem?

---

### Post by Zetheroo on 2008-12-14
pah99: This is indeed interesting.

Just wanted to mention here that my wife has the HP Pavilion dv5-1002 with all AMD and ATI components as well as Atheros wifi, and I upgraded her to Intrepid about 2 weeks ago and she has not had a single kernel panic or freeze-up at any time.

gillmt: Can you help by posting the hardware info on your systems?

Btw, has anyone opened a bug on this issue yet?

---

### Post by pah99 on 2008-12-14
> **Zetheroo said:**
> 
Just wanted to mention here that my wife has the HP Pavilion dv5-1002 with all AMD and ATI components as well as Atheros wifi, and I upgraded her to Intrepid about 2 weeks ago and she has not had a single kernel panic or freeze-up at any time.



I'm guessing because its all AMD, then there are no lockups. The way things are going, looks like Intel is to blame.

---

### Post by Zetheroo on 2008-12-15
Hmmm ... it does seem to be look that way for now. I just am puzzled that I have not had any issue with Kubuntu 8.10 ... :confused:

---

### Post by pah99 on 2008-12-15
Well, anyway, I have been turning more and more to Vista, and to be honest, I like it. I'm tired of dealing with all the issues with Ubuntu, and this one has finally pulled the plug. I always will like Ubuntu, and maybe some day I'll try it again, but for now, I'll just run my virus scans at night, and enjoy the stability of Vista during the day. So, good bye, and best of luck to you all.

---

### Post by Zetheroo on 2008-12-15
pah99, can I ask you if you were ever fully setup in Ubuntu and using it as your main OS? 

Reason I ask is because its my guess that Ubuntu was never your main (95-99%) OS but that you more or less used it here and there and toyed around with the idea to finally move to it altogether. That's just my guess ... 

I, on the other hand have been using Ubuntu as my main OS for 2+ years and only use Windows XP Pro (NEVER Vista) in VirtualBox as part of my client support so that I can follow along with them while on the phone or chat troubleshooting etc...
In the case of Intrepid being a real genuine let-down I just reverted back to Hardy and am as productive as ever after only about 2 hours of reinstalling Hardy and all (30+) applications that I use, as well as restoring all my mail, browsing and other data backups.

I think in some ways the Ubuntu Linux "balloon" is blow-up a little to much and people are easily disappointed because the impression they have got from other Ubuntu Linux users is somewhat slanted and not altogether truthful. Due to this I have seen many individuals put-out by bugs or issues, such as the one we are experiencing with Intrepid, and they usually end up reverting to MS Windows because that is their "comfort zone". But those who stick around get to actualyl understand that its not always a must (in fact it is never a must) to upgrade every 6 months to a new release of Ubuntu if the release you have currently on your PC is working to your satisfaction.  

Imagine is MS was turning out a new release every 6 months ... ha ... talk about issues and bugs ... it would be complete chaos and anarchy. :lolflag:

It takes MS 6 years to come up with a bulky piece of sh*t called Vista and Ubuntu has caught up with all the Windows versions including Vista in just 4 years!!! That is awesome imo!

Anyhow, sad to see you "bite-the-dust" but hey ... good luck! ):P

---

### Post by ExemplarUbuntu on 2008-12-16
I am experiencing lots of freezes (lock-ups) on a Toshiba Satellite laptop that I upgraded to Ibex about 2 weeks ago. It worked brilliantly with Heron but release this is just awful. It will only work for about 15-20 minutes before going sluggish with lots of disc thrashing and then becomes completely unresponsive and requires a powerdown. I haven't noticed any caps-lock flashing but I will look for it.

The laptop will boot and run for hours as long as you don't do anything but try to do anything and it quickly dies. Main culprits seem to be Synaptic PM and Firefox but TBH I haven't done much else with the laptop because Ibex is so bad compared to Heron.

It does not have wireless so I can rule that out.

---

### Post by TpyKv on 2008-12-16
I am having the exact same issue, this is my thread and I have not had any fix suggestions as of yet...

[http://ubuntuforums.org/showthread.php?p=6378633#post6378633](http://ubuntuforums.org/showthread.php?p=6378633#post6378633)

Hardy was fine, perfect in fact, yet Intrepid is, erm, for want of a better word - PAINFUL.

As has been mentioned before, I now have to use Vista regularly rather than once in a blue moon, and I am most upset by it.

I used to think that Ubuntu could do everything I needed it to, with the exception of MS Flight Sim and my blackberry software.

Now I am not so convinced - no one can help and I cannot use a laptop that crashes after 10 minutes use. 

Back to Hardy then, everyone :lolflag:

---

### Post by Zetheroo on 2008-12-16
TpyKv & ExemplarUbuntu ...

Can you both please post here your system hardware information asap?
Thanks

My system:

Version (of Ubuntu):
Kernel:
Processor:
Memory: 
Hard drive:
Host Bridge: 
PCI bridge: 
USB Controller: 
ISA bridge:
Graphics Card: 
Multimedia audio Controller: 
Wireless card: 
Ethernet: 
Dual Boot:

---

### Post by david.birch on 2008-12-16
This only seems a recent thing for me - i also get the virtual freeze up loads of disc thrashing on a t400, i'm going back to kernel 2.6.27-7 which didn't have this issue - or at least i hope it is just a kernel issue.

---

### Post by TpyKv on 2008-12-16
I would be happy to, would the results from HardInfo be enough for you? (sudo apt-get install hardinfo)

I am on a conference call now :roll:, will post this up in half hour or so...

---

### Post by Zetheroo on 2008-12-16
> **TpyKv said:**
> I would be happy to, would the results from HardInfo be enough for you? (sudo apt-get install hardinfo)

I am on a conference call now :roll:, will post this up in half hour or so...

Use whichever tools you can or want ... so long as you con get the info I posted earlier.

---

### Post by Zetheroo on 2008-12-16
> **david.birch said:**
> This only seems a recent thing for me - i also get the virtual freeze up loads of disc thrashing on a t400, i'm going back to kernel 2.6.27-7 which didn't have this issue - or at least i hope it is just a kernel issue.

Hi there, could you be a bit more specific about your problem?

When did it begin? (in relation to the release of Ubuntu you were using at the time etc ...)
Also ... what do you mean by "disc thrashing"? Is that like the head parking and unparking?

Thanks

---

### Post by david.birch on 2008-12-16
Hi,
   as far as recent - i didn't get this issue prior to grabbing updates last weekend (i have updates on manual).
I did actually find this in messages log (an di guess those messages don't look pretty...):

Dec 16 15:47:51 lenny -- MARK --
Dec 16 15:49:36 lenny kernel: [18135.068277] thinkpad_acpi: unhandled HKEY event 0x6030
Dec 16 15:52:46 lenny kernel: [18324.962666] hpet1: lost 1 rtc interrupts
Dec 16 15:52:48 lenny kernel: [18326.988578] hpet1: lost 1 rtc interrupts
Dec 16 15:52:48 lenny kernel: [18327.393266] hpet1: lost 1 rtc interrupts

after this i hit the power button - if i wait long enough the laptop does shutdown, but it takes 10-15mins. Though - this is not something i can say happens often, i had used the laptop for about 6 hours with fairly high usage (weblogic chewing fairly hard on my box) today, and only had one crash this morning & one this afternoon.

cheers

---

### Post by ExemplarUbuntu on 2008-12-16
I don't have the laptop with me today, it's not worth carrying around at the moment. I'll get what info I can, I am not familiar with the tools needed to find the information.

"disc thrashing", the disc led is on permanently which suggests that the disc is being accessed permanently. The HD is being thrashed.

---

### Post by Zetheroo on 2008-12-16
I would suggest that if your HDD led is on non-stop (aka hard drive thrashing) that you disable Tracker and Tracker Applet from starting up at login. Tracker basically indexes the data on your HDD for faster search ... I turn it off and still get pretty fast search results.

---

### Post by ExemplarUbuntu on 2008-12-16
Is this something new to Ibex ? I didn't have the problem with Heron.

The laptop works fine for 15-20 minutes and then nearly always crawls to a halt, thrashing the HD.

---

### Post by TpyKv on 2008-12-16
My system: Sony Vaio VGN-NR10E

Version (of Ubuntu): Intrepid Ibex 8.10 (Fresh install)

Kernel: Linux 2.6.27-9-generic(i686)
Processor: 2 x Intel Dual CPU T2310 @ 1.46 GHz
Memory: 2063 MB
Hard drive: SCSI0 ATA ST9160821AS Seagate 160 GB
Host Bridge: Intel Corp Mobile PM965/GM965/GL960 
PCI bridge: Intel Corp 82801H
USB Controller: Intel Corp 82801H
ISA bridge: Intel Corp 82801H
Graphics Card: Mesa DRI Intel 965GM 2006102 x86/MMX/SSE2
Multimedia audio Controller: HDA Intel 
Wireless card: Atheros AR5007
Ethernet: Marvell Technology Group Ltd 88E8039 PCI-E Fast Ethernet Controller / Atheros Communications Inc. AR242x 802.11 abg Wireless PCI Express Adapter (This is really AR5007)
Dual Boot:[/QUOTE] Vista Home Premium & Intrepid 8.10


Thank you, and sorry for the delay, work tends to get in the way every now and then :p

---

### Post by ryclegman on 2008-12-16
all right, i had wireless, but took it out and ran Ethernet to it. Ill let you know if this is actually the problems. If not then we need to try some other things.

---

### Post by pah99 on 2008-12-16
No, I have been a full blown Ubuntu user for some time, and have used it as a primary (100%) os for well over 3 years. I'm just bummed out with all the crashes, and so I started using Vista and realized, hey, why switch back and forth when I can just get stability on Vista. Now, I'm not saying Vista is better. Its not. I just know how to keep it clean and unbloated. Thats why it works for me. And like I said, maybe someday I'll go back to Ubuntu. But for now, I'd rather prefer not crashing every ten minutes.

---

### Post by pah99 on 2008-12-16
I keep seeing the same hardware for the motherboard- INTEL!!!

Something fishy is going on here.

---

### Post by Zetheroo on 2008-12-16
Yes, there we have it again ... its the same Intel Chipset.

**Please can everyone who is experiencing Kernel Panics in Intrepid post their hardware info.**

---

### Post by RavUn on 2008-12-16
Well, after nearly a month of no issues it happened just now.  I installed some updates last night (some were pulseaudio and I've ben having a lot of pulseaudio issues recently) and then the laptop froze up today.

I also have an intel chip... I believe it's the Intel core 2 duo T5800.

lspci:
```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

```

---

### Post by pah99 on 2008-12-16
> **RavUn said:**
> 

I also have an intel chip... I believe it's the Intel core 2 duo T5800.


Its not the processor. Its the Intel chipset on the motherboard, which is the 82801H.

---

### Post by Zetheroo on 2008-12-16
pah99, look at that ... its that same Intel 82801 chipset again ....
at the end of the day I just want to know if anyone is having this issue with a different chipset.

**ryclegman: whats your hardware? **

---

### Post by pah99 on 2008-12-16
I think its time for the dev's to start looking into this as its probably too complex for us (or at least for me).

---

### Post by Zetheroo on 2008-12-17
Has anyone tried or is anyone currently using Kubuntu 8.10? If so how is it going?

---

### Post by Zetheroo on 2008-12-17
Hey **sroland81**, could you post your system hardware info please? Thanks

---

### Post by raylu on 2008-12-17
I think there is some confusion in this thread.

Having your system perform sluggishly or lock up is *not* indicative of a kernel panic. You're debgging multiple issues here (and going about it the wrong way, too). Your Num Lock and Caps Lock lights should flash when you have a kernel panic.

Comparing hardware will likely get you nowhere. I suggest poking around in /var/log/ immediately after a kernel panic. Specifically, dmesg*, kern.log*, syslog*, and possibly debug*. "zless" will help you. Posting things that look important from there is likely to get you to a solution faster.

---

### Post by Zetheroo on 2008-12-17
I think you are right that there are some ppl posting here who are not experiencing kernel panics. However I do think it is still interesting that all those who posted their system specs which show the INTEL 82801H chipsets all have kernel panics, myself included.

I have tried looking through my logs right after a kernel panic and have showed them to others as well ... and basically got nowhere at all. Most people also say that a kernel panic and the cause for it would not be visible in the logs ... but that you would have to be logged into the command prompt to see the kernel panic output etc .. I for one do not have the time to sit around waiting for my computer to crash in the prompt ... 

Then again others (such as yourself) tell us to look into the logs ... so its a real puzzle ... :confused:

---

### Post by TpyKv on 2008-12-17
> **raylu said:**
> I think there is some confusion in this thread.

Having your system perform sluggishly or lock up is *not* indicative of a kernel panic. You're debgging multiple issues here (and going about it the wrong way, too). Your Num Lock and Caps Lock lights should flash when you have a kernel panic.

Comparing hardware will likely get you nowhere. I suggest poking around in /var/log/ immediately after a kernel panic. Specifically, dmesg*, kern.log*, syslog*, and possibly debug*. "zless" will help you. Posting things that look important from there is likely to get you to a solution faster.

I do have the caps blink, and I have posted numerous log outputs, as requested :

[http://ubuntuforums.org/showthread.php?t=1007191](http://ubuntuforums.org/showthread.php?t=1007191)

After 118 views, we've had no suggestions to help fix it. Is there anything else you can suggest that might get a faster response?

Thank you

---

### Post by ExemplarUbuntu on 2008-12-17
Ok, I can confirm that my laptop doesn't flash the caps-lock led so I think that means it isn't a kernel panic.

The mouse judders to a halt, the screen, mouse and keyboard become unresponsive and the disc led stays on. I have to power down.

-Computer-
Processor		: Celeron (Coppermine)
Memory		: 238MB (170MB used)
Operating System		: Ubuntu 8.10
-Display-
Resolution		: 1024x768 pixels
OpenGL Renderer		: Software Rasterizer
X11 Vendor		: The X.Org Foundation
-Multimedia-
Audio Adapter		: ALI5451 - ALI 5451
-Input Devices-
 Macintosh mouse button emulation
 AT Translated Set 2 keyboard
 PC Speaker
 Power Button (FF)
 Lid Switch
 PS/2 Mouse
 AlpsPS/2 ALPS GlidePoint
 Video Bus
-IDE Disks-
-SCSI Disks-
ATA TOSHIBA MK2018GA
TOSHIBA DVD-ROM SD-R2102

-Version-
Kernel		: Linux 2.6.27-9-generic (i686)
Compiled		: #1 SMP Thu Nov 20 21:57:00 UTC 2008
C Library		: GNU C Library version 2.8.90 (unstable)
Distribution		: Ubuntu 8.10
-Current Session-
Desktop Environment		: GNOME 2.24 (session name: this-is-deprecated)

-PCI Devices-
Host bridge		: ALi Corporation M1644/M1644T Northbridge+Trident 
PCI bridge		: ALi Corporation PCI to AGP Controller
USB Controller		: ALi Corporation USB 1.1 Controller 
IDE interface		: ALi Corporation M5229 IDE 
Multimedia audio controller		: ALi Corporation M5451 PCI AC-Link Controller Audio Device 
ISA bridge		: ALi Corporation M1533/M1535/M1543 PCI to ISA Bridge [Aladdin IV/V/V+]
Bridge		: ALi Corporation M7101 Power Management Controller [PMU]
Ethernet controller		: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 
CardBus bridge		: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support 
CardBus bridge		: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support 
VGA compatible controller		: Trident Microsystems CyberBlade XPAi1

---

### Post by ExemplarUbuntu on 2008-12-17
> **raylu said:**
> I think there is some confusion in this thread.

Having your system perform sluggishly or lock up is *not* indicative of a kernel panic. You're debgging multiple issues here (and going about it the wrong way, too). Your Num Lock and Caps Lock lights should flash when you have a kernel panic.

Comparing hardware will likely get you nowhere. I suggest poking around in /var/log/ immediately after a kernel panic. Specifically, dmesg*, kern.log*, syslog*, and possibly debug*. "zless" will help you. Posting things that look important from there is likely to get you to a solution faster.

I had a look at dmesg, kern.log and syslog and they don't show anything between booting the laptop at 9 am this morning and the crash which happened about 3-4 mins after I started using it this afternoon.

---

### Post by ExemplarUbuntu on 2008-12-17
It hadn't crashed for a few minutes so I started Synaptic, that is almost guaranteed to kill it.

I tried to login to the vconsole but it kept timing out before requesting the password. It's that slow.

This is what I can see in syslog


Dec 17 14:50:01 Toshiba-ubuntu /USR/SBIN/CRON[7542]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Dec 17 14:58:45 Toshiba-ubuntu console-kit-daemon[4613]: WARNING: The program /usr/lib/ConsoleKit/run-session.d/pam-foreground-compat.ck didn't exit within 15 seconds; killing it 
Dec 17 14:58:54 Toshiba-ubuntu acpid: client has disconnected 
Dec 17 15:00:40 Toshiba-ubuntu init: tty1 main process ended, respawning
Dec 17 15:00:41 Toshiba-ubuntu console-kit-daemon[4613]: WARNING: The program /usr/lib/ConsoleKit/run-session.d/pam-foreground-compat.ck didn't exit within 15 seconds; killing it 
Dec 17 15:02:16 Toshiba-ubuntu /USR/SBIN/CRON[7912]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Dec 17 15:02:51 Toshiba-ubuntu acpid: client connected from 4886[0:0] 
Dec 17 15:02:55 Toshiba-ubuntu acpid: client has disconnected 
Dec 17 15:03:53 Toshiba-ubuntu console-kit-daemon[4613]: WARNING: The program /usr/lib/ConsoleKit/run-session.d/pam-foreground-compat.ck didn't exit within 15 seconds; killing it 
Dec 17 15:03:54 Toshiba-ubuntu init: tty1 main process ended, respawning
Dec 17 15:04:01 Toshiba-ubuntu console-kit-daemon[4613]: WARNING: The program /usr/lib/ConsoleKit/run-session.d/pam-foreground-compat.ck didn't exit within 15 seconds; killing it 
Dec 17 15:06:05 Toshiba-ubuntu syslogd 1.5.0#2ubuntu6: restart.

---

### Post by Nixie Pixel on 2008-12-17
> **raylu said:**
> I think there is some confusion in this thread.

Having your system perform sluggishly or lock up is *not* indicative of a kernel panic. You're debgging multiple issues here (and going about it the wrong way, too). Your Num Lock and Caps Lock lights should flash when you have a kernel panic.

Comparing hardware will likely get you nowhere. I suggest poking around in /var/log/ immediately after a kernel panic. Specifically, dmesg*, kern.log*, syslog*, and possibly debug*. "zless" will help you. Posting things that look important from there is likely to get you to a solution faster.
raylu, if you haven't noticed, just about all of us experiencing this issue are newbies.  We are trying to diagnose a Linux problem using tried-and-true Windows troubleshooting methods (at least I am).

What we could really use here is some experienced Linux troubleshooters who can direct us to take exact steps that will help us determine the source of these problems.  I think I might call attention to this thread by posting a new thread asking "how do I troubleshoot a kernel panic," and pointing people here for specific examples.  That might be the best way to get the help we need in here.

Thanks!

---

### Post by the_tazinator on 2008-12-17
If you are looking at the motherboard chip set, I am another on that has the Intel 82801H.

lspci output:
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation Quadro FX 360M (rev a1)
03:01.0 CardBus bridge: O2 Micro, Inc. Cardbus bridge (rev 21)
03:01.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)

---

### Post by ryclegman on 2008-12-17
I have an MSI motherboard and i had crashes, but what seems to have fixed it is hooking up my Ethernet! I haven't had a single crash since iv switched a couple of days ago. I have even been downloading and doing a lot and no crashes! 

I think it may just be Wireless problems! I doubt intel is to blame.

---

### Post by Zetheroo on 2008-12-17
the_tazinator, thanks for the system info.

ryclegman: have you posted your hardware info yet? I really don't see how it could be wireless-related across the board ... maybe it is for you in particular but for many of us its not. Why not just post your hardware info?

---

### Post by Zetheroo on 2008-12-17
> **Nixie Pixel said:**
> raylu, if you haven't noticed, just about all of us experiencing this issue are newbies.  We are trying to diagnose a Linux problem using tried-and-true Windows troubleshooting methods (at least I am).

What we could really use here is some experienced Linux troubleshooters who can direct us to take exact steps that will help us determine the source of these problems.  I think I might call attention to this thread by posting a new thread asking "how do I troubleshoot a kernel panic," and pointing people here for specific examples.  That might be the best way to get the help we need in here.

Thanks!

Hey ... I checked out your blog ... at least the post on Ubuntu/Linux :)
Interesting ... and you raise some valuable points. 

In relation to this issue that we are having here ... even though its a disappointment its not like there is not recourse -- as in Hardy works swell and who needs to upgrade their OS every 6 months?
Tat said it is a real let-down to find that the causes of kernel panics are not recorded more efficiently in Ubuntu. In Windows XP it was very easy to locate the problem program which was causing system hangs and/or crashes. 
I have read a lot on Kernel Panics and how to go about debugging the issue at the root of the problem, however it is all very time consuming and not at all meant to get quick and easy results. I have also chatted on IRC with Linux and Ubuntu users and the general consensus seems to be that kernel panics are not recorded in the logs, but still some keep on repeating the need to look through the logs ... :mad:

So its definitely a place of little comfort and a decent amount of confusion. :(

I reverted to Hardy because I actually use Ubuntu Linux as my No1 OS and have work to do. But I also have Kubuntu 8.10 installed ... and Kubuntu has not hernel panicked on me once yet.

---

### Post by ryclegman on 2008-12-17
I have before...

My computer:
-MSI motherboard
-Nividia 9600 gt
-4 gigs of ddr2 ram
-500 gig sata
-intel core 2 quad - 64 bit
*had linysys wireless pci ralink , but switched to Ethernet and no longer have crashes!

---------
It seems like when ever i crashed it was during a download. I did an memory test and all that stuff and my hardware is juts fine.... It has to be wireless.. No one here that has posted there problem has Ethernet. It always has some sort of wireless card in it....... Ill be posting so far 4 days and no freezes. i used to have 2-3 a day

---

### Post by Zetheroo on 2008-12-17
> **ryclegman said:**
> I have before...

My computer:
-MSI motherboard
-Nividia 9600 gt
-4 gigs of ddr2 ram
-500 gig sata
-intel core 2 quad - 64 bit
*had linysys wireless pci ralink , but switched to Ethernet and no longer have crashes!


Can you post the output of lspci please. Thanks

---

### Post by Mizzou_Engineer on 2008-12-18
> **ExemplarUbuntu said:**
> Ok, I can confirm that my laptop doesn't flash the caps-lock led so I think that means it isn't a kernel panic.

The mouse judders to a halt, the screen, mouse and keyboard become unresponsive and the disc led stays on. I have to power down.

-Computer-
Processor		: Celeron (Coppermine)
Memory		: 238MB (170MB used)

It sounds like your computer started running something that caused it to use up the last of its limited amount of RAM and start swapping to disk. There are other things that can cause that, but a "juddering" cursor that eventually becomes unresponsive and an HDD light that lights up and stays lit in a machine with about 60 MB of free RAM is 99.9% likely to be swapping.

---

### Post by Mizzou_Engineer on 2008-12-18
> **Zetheroo said:**
> pah99, look at that ... its that same Intel 82801 chipset again ....
at the end of the day I just want to know if anyone is having this issue with a different chipset.


I had the kernel panics every time my Broadcom BCM4312 WLAN card would connect to a WPA2 "Enterprise" (PEAP/MSCHAP) AP. However, my laptop is a very new Dell with the 82801**I** southbridge rather than the 82801H southbridge most of you guys are running. After I swapped out the Broadcom WLAN NIC for an Intel 3945, the kernel panics mostly stopped, although it would panic very occasionally.

This brings me to an important point as I think I may be on to something, but I need to do a little explanation first or it won't make a whole lot of sense to anybody who's not a real big hardware geek.

Okay, first some background information. 82801 is Intel's product code for southbridges that use a dedicated link rather than PCI to link the northbridge and southbridge. Intel publicly names these southbridges the I/O Control Hub, aka ICH. This includes every southbridge in a computer with an Intel 810 or later chipset, which you would find in many computers with PIIIs and all later CPUs. Every one of these southbridges has the 82801 model number followed by one to three letters and an ICH model name followed by a number and sometimes some letters.

The first letter after the 82801 is the generation code, and it proceeds alphabetically. This makes the 82801H the eighth-generation southbridge and Intel publicly refers to it as the ICH8. This is the only letter after 82801 that you will see if you look at lspci in most cases.

Most of the southbridges have a second letter and some have a third letter. These extra letters denote certain features the southbridge has. For example, the 82801EB is the "standard" ICH5 southbridge, while the 82801ER allows for RAID and the 82801EBM is the mobile variant. Note that you have to physically look at the chip to see the entire model number with all of the letters in most cases. Intel's public model names vary as well, the 82801EB is ICH5, 82801ER is ICH5-R, and the 82801EBM is ICH5-M.

Intel pairs the southbridges up with varying northbridges to make their chipset. The ones we are interested in here are the 82801H and 82801I:

- 82801H + P965, G965, and Q965 desktop northbridges
- 82801H + some G35 desktop northbridges
- 82801H + GL960, PM965, and GM965 laptop northbridges
- 82801I + G33, Q33, P35, X38, and X48 desktop northbridges and some G35s.
- 82801I + all 4-series mobile chipsets (GL40, GS45, GM45, PM45, GM47)

So I am trying to narrow out where the problem lies- does it affect just the mobile variants of the 82801H/I or does it affect the desktop versions as well? I'd like to see if people with the desktop boards are having the same issues.

---

### Post by ryclegman on 2008-12-18
Heres my  uou put of lspci

> 00:00.0 Host bridge: nVidia Corporation C55 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a2)
00:00.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.7 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:03.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:06.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:07.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
01:00.0 VGA compatible controller: nVidia Corporation Geforce 9600 GT 512mb (rev a1)
02:00.0 Mass storage controller: Silicon Image, Inc. Sil 3531 [SATALink/SATARaid] Serial ATA Controller (rev 01)
04:09.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)


---

### Post by the_tazinator on 2008-12-18
For what it worth, the issues that I am having are occurring on my laptop, but I do have a desktop with 8.10 and have never had an issues out of it. I use both machines about the same amount of time and if any "tweaks" are made, they are made to both my laptop and desktop. The only major difference between them (besides the obvious hardware) is that my laptop has a built-in wireless card.

My belief is that it has something to do with wireless but due to what fixes one machine doesn't fix other is kinda confusing. Plus I can use my laptop all day long as long as I turn the wireless off by using the hardware switch on the side of my laptop. If I turn it on, some point during the day the machine will lock-up. If I try to connect to a WPA2 Network, it immediately locks up.

Here is the hardware specs of my desktop that is NOT having the issues.

00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82562V-2 10/100 Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 RAID bus controller: Intel Corporation 82801 SATA RAID Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)

---

### Post by Daggo on 2008-12-18
I am also experiencing kernel panic with wireless

Broadcom STA wireless driver (default in Ibex)
Kernel 2.6.27-9-generic
Linux-Backports installed
Broadcom 4312 v.1
WPA2 Enterprise PEAP

---

### Post by ryclegman on 2008-12-18
It narrows down every time to wireless..:p

---

### Post by Mizzou_Engineer on 2008-12-18
> **ryclegman said:**
> It narrows down every time to wireless..:p

That would be one big reason why we are not seeing these issues with desktops, even though they use virtually the same chipsets with exactly the same drivers.

So here's where it looks like we stand right now:
1. People with Broadcom BCM43xx cards connecting to WPA2/PEAP networks have an immediate kernel panic on machines with Intel 965/ICH8 and 45 Express/ICH9 hardware.
2. Desktops with the same chipsets as the laptops do NOT have trouble.
3. The laptops with panic issues improve when given a non-Broadcom wireless card and are completely fixed when the wireless is disabled.
4. Desktops with non-Broadcom wireless cards and different chipsets have panic issues as well.
5. Using the same hardware with a different distribution and kernel does NOT result in kernel panics (installing Debian Lenny [2.6.26] on my Dell completely fixed the panic issue as well as lets suspend and resume work.)

It looks like a bug somewhere in the wireless stack used in Ubuntu 8.10 to me rather than an issue with certain chipsets or Linux in general. This problem appears to be worse with Broadcom WLAN cards but has been noted to affect Intel and Ralink cards as well. 

So the $100,000 question is- what *exactly* do all of those have in common? Is there a certain kernel module that all of those cards have loaded that is the problem, such as the various *80211 modules? I think if we find that out, we can help point the devs in the right direction.

Okay, my Dell running on a transplanted Intel 3945 wireless card uses the following modules:
- iwl3945
- firmware_class
- mac80211
- led_class
- cfg80211

I will try to get the Broadcom unit lit. Debian Lenny did not detect the BCM4312 since the 2.6.26 kernel's b43 driver does not support it. I'll install the Broadcom STA driver and get back to you.

---

### Post by ryclegman on 2008-12-18
> **Mizzou_Engineer said:**
> That would be one big reason why we are not seeing these issues with desktops, even though they use virtually the same chipsets with exactly the same drivers.

So here's where it looks like we stand right now:
1. People with Broadcom BCM43xx cards connecting to WPA2/PEAP networks have an immediate kernel panic on machines with Intel 965/ICH8 and 45 Express/ICH9 hardware.
2. Desktops with the same chipsets as the laptops do NOT have trouble.
3. The laptops with panic issues improve when given a non-Broadcom wireless card and are completely fixed when the wireless is disabled.
4. Desktops with non-Broadcom wireless cards and different chipsets have panic issues as well.
5. Using the same hardware with a different distribution and kernel does NOT result in kernel panics (installing Debian Lenny [2.6.26] on my Dell completely fixed the panic issue as well as lets suspend and resume work.)

It looks like a bug somewhere in the wireless stack used in Ubuntu 8.10 to me rather than an issue with certain chipsets or Linux in general. This problem appears to be worse with Broadcom WLAN cards but has been noted to affect Intel and Ralink cards as well. 

So the $100,000 question is- what *exactly* do all of those have in common? Is there a certain kernel module that all of those cards have loaded that is the problem, such as the various *80211 modules? I think if we find that out, we can help point the devs in the right direction.

Okay, my Dell running on a transplanted Intel 3945 wireless card uses the following modules:
- iwl3945
- firmware_class
- mac80211
- led_class
- cfg80211

I will try to get the Broadcom unit lit. Debian Lenny did not detect the BCM4312 since the 2.6.26 kernel's b43 driver does not support it. I'll install the Broadcom STA driver and get back to you.

i am using a desktop and used to receive the bad crashes. I switched to Ethernet and everything is fixed. My wireless card was a linksys ralink too..... and im using a MSI motherboard. that isnt intel chip set or anything. so it seemed like my system isnt like yours. I built my computer. the only intel thing i have is a quad core. It will boil down, like iv been saying, its a problem with wireless in UBUNTU. Everying worked flawlessly with vista...

---

### Post by Mizzou_Engineer on 2008-12-18
> **ryclegman said:**
> i am using a desktop and used to receive the bad crashes. I switched to Ethernet and everything is fixed. My wireless card was a linksys ralink too..... and im using a MSI motherboard. that isnt intel chip set or anything. so it seemed like my system isnt like yours. I built my computer. the only intel thing i have is a quad core. It will boil down, like iv been saying, its a problem with wireless in UBUNTU. Everying worked flawlessly with vista...

I am running Debian Lenny with the same Broadcom STA driver used in Ubuntu and so far no issues. I haven't brought it into school and connected to the WPA2/PEAP network, but I'm on break and not at school, so that will be a little while. If I can do that without locking the computer, then it's pretty surely something specific to Ubuntu.

---

### Post by ExemplarUbuntu on 2008-12-19
> **Mizzou_Engineer said:**
> It sounds like your computer started running something that caused it to use up the last of its limited amount of RAM and start swapping to disk. There are other things that can cause that, but a "juddering" cursor that eventually becomes unresponsive and an HDD light that lights up and stays lit in a machine with about 60 MB of free RAM is 99.9% likely to be swapping.

Synaptic is almost guaranteed to kill it. Everything worked fine with Heron, whatever they did to Ibex has made it like this. Some apps work fine, Firefox will work for a little while. Could there be anything wrong with the file swapping ?

Next question, is there an easy way to back-out Ibex and replace it with Heron ? Every installation upgrade I have done so far has been a one-way trip.

---

### Post by raylu on 2008-12-19
> **Nixie Pixel said:**
> raylu, if you haven't noticed, just about all of us experiencing this issue are newbies.  We are trying to diagnose a Linux problem using tried-and-true Windows troubleshooting methods (at least I am).
In that case, you need to restart your computer about 50 more times :P.

> **Zetheroo said:**
> I have tried looking through my logs right after a kernel panic and have showed them to others as well ... and basically got nowhere at all. Most people also say that a kernel panic and the cause for it would not be visible in the logs ... but that you would have to be logged into the command prompt to see the kernel panic output etc .. I for one do not have the time to sit around waiting for my computer to crash in the prompt ... 

Then again others (such as yourself) tell us to look into the logs ... so its a real puzzle ... :confused:
I'm pretty sure kernel panics should show up in the logs. Regardless, sitting there waiting for a kernel panic is neither likely to induce one nor a good use of time.

EDIT: Wait... I take that back.

> **Zetheroo said:**
> Hey ... I checked out your blog ... at least the post on Ubuntu/Linux :)
Are you talking to me? I don't have anything about *nix on my blog.

> Tat said it is a real let-down to find that the causes of kernel panics are not recorded more efficiently in Ubuntu. In Windows XP it was very easy to locate the problem program which was causing system hangs and/or crashes.
I can locate the problem program: your kernel :P.

> **ExemplarUbuntu said:**
> Next question, is there an easy way to back-out Ibex and replace it with Heron ? Every installation upgrade I have done so far has been a one-way trip.
Try asking that elsewhere (start a new thread).

--

From [this log](http://ubuntuforums.org/showpost.php?p=6342874&postcount=7), I wonder if everyone here is using the mac80211 module?
```
lsmod | grep mac80211
```

---

### Post by ryclegman on 2008-12-21
I think the problem has been solved.
 I got the solution off mint.> Seen same problem. Was due to netword card sharing interrupt with display card.
Solved by moving the network card in a PCI slot that does not share its IRQ line (the 2nd on my mb)
If unsure which slot, try all and check PCI IRQ assignment at boot screen: if IRQ is still shared, power off move card to next PCI slot.


---

### Post by Zetheroo on 2008-12-22
> **ryclegman said:**
> I think the problem has been solved.
 I got the solution off mint.

How does that help Laptop users? :confused:

---

### Post by Zetheroo on 2008-12-22
> **Mizzou_Engineer said:**
> That would be one big reason why we are not seeing these issues with desktops, even though they use virtually the same chipsets with exactly the same drivers.

So here's where it looks like we stand right now:
1. People with Broadcom BCM43xx cards connecting to WPA2/PEAP networks have an immediate kernel panic on machines with Intel 965/ICH8 and 45 Express/ICH9 hardware.
2. Desktops with the same chipsets as the laptops do NOT have trouble.
3. The laptops with panic issues improve when given a non-Broadcom wireless card and are completely fixed when the wireless is disabled.
4. Desktops with non-Broadcom wireless cards and different chipsets have panic issues as well.
5. Using the same hardware with a different distribution and kernel does NOT result in kernel panics (installing Debian Lenny [2.6.26] on my Dell completely fixed the panic issue as well as lets suspend and resume work.)

It looks like a bug somewhere in the wireless stack used in Ubuntu 8.10 to me rather than an issue with certain chipsets or Linux in general. This problem appears to be worse with Broadcom WLAN cards but has been noted to affect Intel and Ralink cards as well. 

So the $100,000 question is- what *exactly* do all of those have in common? Is there a certain kernel module that all of those cards have loaded that is the problem, such as the various *80211 modules? I think if we find that out, we can help point the devs in the right direction.

Okay, my Dell running on a transplanted Intel 3945 wireless card uses the following modules:
- iwl3945
- firmware_class
- mac80211
- led_class
- cfg80211

I will try to get the Broadcom unit lit. Debian Lenny did not detect the BCM4312 since the 2.6.26 kernel's b43 driver does not support it. I'll install the Broadcom STA driver and get back to you.

Umm ... where does my scenario fit into this analysis?
I have the kernel panics with the Atheros chipset in a laptop, which proves to me that its not just the Broadcom or ralink chipsets .... its something more widespread and deeper in the system as far as I can tell.

---

### Post by Zetheroo on 2008-12-22
> **raylu said:**
> 


Are you talking to me? I don't have anything about *nix on my blog.


No I was talking about Nixie Pixel

---

### Post by pah99 on 2008-12-22
Ladies and gentlemen, I believe I have a slight breakthrough... in a bad way. 
I wiped my Ubuntu partition and returned to Windows Vista exclusively, and lo and behold, not 10 minutes ago, guess what happened. Yup, the same damn lock up.
So, what I can conclude from this is that this is NOT an issue with software, but rather is a hardware problem. And I believe that it is due to a conflict... something along the lines of the PCI conflicts ryclegman posted earlier.

---

### Post by Zetheroo on 2008-12-22
> **pah99 said:**
> Ladies and gentlemen, I believe I have a slight breakthrough... in a bad way. 
I wiped my Ubuntu partition and returned to Windows Vista exclusively, and lo and behold, not 10 minutes ago, guess what happened. Yup, the same damn lock up.
So, what I can conclude from this is that this is NOT an issue with software, but rather is a hardware problem. And I believe that it is due to a conflict... something along the lines of the PCI conflicts ryclegman posted earlier.

Hmmm ... and how does me being able to run Kubuntu Intrepid, Ubuntu Hardy and Windows XP Pro on this laptop without a single kernel panic or crash (in Windows) fit into that? 

The only, and I say again, only time I had kernel panics was with Ubuntu Intrepid.

---

### Post by pah99 on 2008-12-22
True, but there are other threads with people complaining of kernel panics using Hardy. Different hardware affects different OS's. I just had a lockup with Vista. Point is, its affecting us all, thus making it a hardware issue.

---

### Post by RogueLeader on 2008-12-23
I've been getting this kernel panic on my laptop recently and I can actually reliably recreate the problem.  First off, the seemingly relevant specs:

Kubuntu Hardy, kernel 2.6.24-22-generic
Dell Inspiron 1720 (is it just me or are there a lot of Dell owners here?)
```
>lspci | grep road
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
```
Here are possibly some relevant modules I have loaded:
ndiswrapper 
ieee80211_crypt_tkip 
ieee80211_crypt

I'm using ndiswrapper as my wireless driver, so no fancy restricted drivers here (so I can connect to a hidden WPA AP using a static IP).

Now, I can recreate the problem by sort of "overloading" the network on all fronts with activity.  A few days ago, I wanted to transfer some large files (totaling 8 GB or so) from my desktop to the laptop in question.  Instead of bog down my home network/router and transfer wirelessly, I just connected the two machines with an Ethernet cable for an ad-hoc transfer.  I began copying the files over and it runs smoothly for a bit.  I began to poke around the web (with FireFox fwiw) also while using my Bluetooth mouse, and all of a sudden everything freezes and I got the flashing Caps/Num locks.  Hmm, that's weird, I thought... so I hard reset and tried again.  This time, I did not do anything else on my laptop while one of the large files was transferring.  It succeeded.  I was content with the results and chalked up the panic as a one-time hiccup.

Fast forward to today, when I attempt another large transfer in a similar fashion.  I begin the transfers and begin to mess around on the web in the meantime.  BAM, another panic.  I begin to read this thread and witnessed the myriad wireless cards/drivers/etc. having the same problem.  For this reason I am also leaning towards Mizzou_Engineer's thoughts of this being an issue deeper than what hardware/driver we are running.  I tried to recreate the problem by following the same steps as above, but without the wired transfer and using a USB wireless mouse and turning off my Bluetooth mouse (BT is on the same kill-switch as my wireless card).  I couldn't evoke a panic despite attempting to generate a ton of wireless traffic.  I tried running many multiple pings (with payloads increased to near the IP limit of 64KB) in terminals and simultaneously going wild, as before, on FireFox.  

After this failure (or was it success?), going back to frantically using my BT mouse during both a roughly 10 MB/s data transfer through wired Ethernet and moderate wireless traffic can get this panic to occur every time.  Occasionally, the wired transfer would freeze, followed by compiz crapping out for a few seconds before the panic.  Other times, the freeze would be instant.  System logs seem to express nothing useful other than incessantly repeating that my BT mouse was found.

So, my question to those of you who get the panic seemingly randomly (i.e. not as soon as you connect to an AP), is do you notice getting the panic during high-volume network usage?  Perhaps during streaming video or something?  Granted, none of you is probably undergoing large transfers over a wired interface like I was, but it is obviously a catalyst for my problem, even if it is ultimately unnecessary to create the bug.  Also, how many of you are using a BT mouse, which could further "tax" Ubuntu's network stack with activity?  Is anyone else experiencing this bug willing to see if they can recreate it using my steps?

So, to recap, I think the problem lies with neither specific wireless chipset, nor drivers, nor wired Eth adapter, nor Bluetooth mice, but with a deadly combination of using all of the above, perhaps at a rate too fast for the kernel.

---

### Post by hanbin973 on 2008-12-23
this is a quite easy problem.

in korean ubuntu forum, it has about 4ways.

I found out one. 

I will translate in to english.



the first way is to put out the ram from the computer for 1~2 sec. Then put the ram into the computer again.

2. put out the computer power line and put it into it again.

3. put out the computer power line and push the power button 3~4times. 



in my case, 1st and the 3rd one worked.

---

### Post by Karpah on 2008-12-24
I'm seeing this every so often on my laptop as well, a Dell Inspiron 1525 running Intrepid.

It might be a wireless issue, or Bluetooth, because my laptop has these whereas my two desktops (also running Intrepid) don't. I doubt it has to do with saturating the network so to speak, because I've seen it just after booting, after I open one program (that doesn't even use the wireless) and start working. Mucho frustrating.

I don't have any Broadcom devices, all Intel. Not sure how much of this is relevant but:

```

becky@amethyst:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
02:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
02:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
0b:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)

```

---

### Post by Retraktor on 2008-12-29
**The Problem**:
I had the same problem on my Thinkpad T61p running Intrepid and using the Intel Wireless 4965 chipset. The kernel panicked quite unpredictably, but only when there was a high amount of network traffic through the wireless card.

**The Fix**:
I found this [[COLOR="Blue"]bug ticket[/COLOR]]("https://bugs.launchpad.net/ubuntu/intrepid/+source/linux/+bug/276990") where someone had a similar problem, only my problem was with 802.11g, not 802.11n. The fourth comment on the bug ticket solved it for me:

> Try compiling this iwlagn module, [http://www.orbit-lab.org/kernel/compat-wireless-2.6/2008/10/compat-wireless-2008-10-01.tar.bz2](http://www.orbit-lab.org/kernel/compat-wireless-2.6/2008/10/compat-wireless-2008-10-01.tar.bz2) .
Extract the archive to your home directory then follow these steps

sudo apt-get install build-essential
cd compat*
make
sudo make install

Then restart your computer. It worked perfectly for me, if it works for more people perhaps the default ubuntu module will be upgraded.

---

### Post by the_tazinator on 2008-12-29
OK, reinstalled Intrepid...again. I am trying an couple of things, one being the suggestion listed above by Retraktor. This did not fix my issue. I tried connecting to both an n and g access point.

---

### Post by arin.chakra on 2008-12-29
I found this thread explaining the problem. It seems to be related to the intel 3945 and 4965 wireless chipsets. 

The solutions should be getting the linux-backports-modules-intrepid package. Which can be installed via:

sudo apt-get install linux-backports-modules-intrepid

here's the link to the thread I found the information on. All credit goes to dhbabey. I hope I haven't broken any forum rules in this post, this being my first one. Good luck to all!

[http://ubuntuforums.org/showthread.php?t=968792&highlight=caps+lock+blinking+intel](http://ubuntuforums.org/showthread.php?t=968792&highlight=caps+lock+blinking+intel)

---

### Post by Zetheroo on 2008-12-29
I really wish people would stop saying that this issue is related to this or that wireless chipset as we have already established here that it is happening to people with a variety of chipsets. Please people ... keep up with the flow of things    ...    ;-)

---

### Post by trumpeteersman on 2008-12-30
The problem for me had just fixed itself.  I have been running without a crash now for 2 weeks.

Things that I remember doing that could be related to the fix:

  Physically switched the wifi switch of and on.
  Ran an ext3 fsck.
  Had a PSP accidentally create wifi interference(Damn PSP crashed my whole computer).
  Turned on my swap(was previously off).

BTW, here are my specs again:

Intel T7100
1GB DDR2 667MHz
Intel GMA X3100
Intel PRO/Wireless 3945ABG

Kernel 2.6.24-21-generic(same since before problem)
xserver-xorg-video-intel 2.2.1 (-1ubuntu13.7)
iwl3945
KDE 3.5.10
Hardy


lspci of the wireless:
```

03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
        Subsystem: Intel Corporation Unknown device 1010
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 218
        Region 0: Memory at df6ff000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [c8] Power Management version 2
                Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
                Address: 00000000fee0300c  Data: 4152
        Capabilities: [e0] Express Legacy Endpoint IRQ 0
                Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-
                Device: Latency L0s <512ns, L1 unlimited
                Device: AtnBtn- AtnInd- PwrInd-
                Device: Errors: Correctable- Non-Fatal- Fatal- Unsupported-
                Device: RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
                Device: MaxPayload 128 bytes, MaxReadReq 128 bytes
                Link: Supported Speed 2.5Gb/s, Width x1, ASPM L0s L1, Port 0
                Link: Latency L0s <128ns, L1 <64us
                Link: ASPM L1 Enabled RCB 64 bytes CommClk+ ExtSynch-
                Link: Speed 2.5Gb/s, Width x1


```

---

### Post by jron on 2008-12-30
Wifi on Alpha 2 kernel 2.6.28-4-generic still crashes my Lenovo S10.

---

### Post by triston666 on 2008-12-30
I had the same problem here, for many times.
Me also a new linux user.

I consantly had to reboot, by powerbutton.
And it wouldnt freeze, when i removed my wireles card.

Last time i tried something like terminal, and then, killall gnome-panel

I still dont know what that was good for.

But had no freeze at all!  

The only freeze i got, is when i go outside.....

Hope this helps a little

---

### Post by ryclegman on 2008-12-30
I still have encountered no freezes after i removes my wireless and ran a Ethernet cord up to it.

---

### Post by jron on 2009-01-02
I just installed Debian's daily build (January 2nd) w/ newly compile Broadcom STA binary drivers (updated December 31st). The system freeze still exists. I'm going to try Fedora now... :(

---

### Post by Beavis6953 on 2009-01-03
I hate to add to the confusion but I too am having the same error. but not only is my caps lock blinking but my scroll lock as well. But i'm running a 8.04 desktop with no wireless cards. I think that the head people at Ubuntu better take a serous look at this issue because a lot of people are looking elsewhere.





Asus P4P-800-SE

---

### Post by psycovic23 on 2009-01-03
I'm having this problem and I'm on an 11b network right now. Happened twice in one day...this is getting out of hand.

---

### Post by Zetheroo on 2009-01-03
Ok... so what does it take for the Ubuntu people to pay some attention to this thread?

---

### Post by ryclegman on 2009-01-03
I know its pretty sad they wont take the step and try and approach this issue. It also turned me away. :[

---

### Post by dadozgb on 2009-01-04
In my expirience freezing is very often connected with a buggy display driver. If someone has a problem with a freezing comp (gui) maybe the best place to look first is a display driver. Trying unistalling property nvidia or ati driver and use linux build in driver can solve this problem if problem is in display driver.

---

### Post by ryclegman on 2009-01-04
I am still putting my money on the wireless issue. I stitched from my wireless to hard wire and no problems at all.... It has to tell you something.

---

### Post by fugyfudy on 2009-01-04
I've had this problem almost every day since I installed Ubuntu. Today alone I had it happen 3 times. This time when I started up after the last freeze, I went into kernel 2.6.27-7 instead of -9 just to see if it helped and I also did the physical switch to turn wireless off and then turned it back on. I was testing some stupid things earlier like if it was my music player and I'm glad to know it isn't. I do have Broadcom Wireless but unlike some of the others in this thread I have AMD and not Intel.

---

### Post by ryclegman on 2009-01-05
I can say that it isnt whether you have intel or not its if you have wireless. No one who has Ethernet has this problem... Only wireless people.

---

### Post by Mizzou_Engineer on 2009-01-05
I had some time off over Christmas and did a little testing of my machine and the Broadcom BCM4312 wireless card:

1a. Ubuntu 8.10 (2.6.27) and the b43 driver: card not detected. No kernel panics or other issues.
1b. Ubuntu 8.10 and the Broadcom wl driver: card works with no encryption, WEP, and WPA/WPA2 Personal but kernel panics with WPA2+PEAP.
2a. Debian Lenny (2.6.26) and the b43 driver: card not detected. No kernel panics or other issues.
2b. Debian Lenny and the Broadcom wl driver: card works with no encryption, does not work with WPA of any sort. No kernel panics or other issues.
3a. Gentoo 2008.0 (2.6.28) and the b43 driver: card not detected. Had multiple network issues.
3b. Gentoo 2008.0 and the wl driver: card not detected (lspci shows it as a BCM4310 USB adapter?!). Multiple network issues.
4a. OpenSUSE 11.1 (2.6.27) and the b43 driver: card not detected. No kernel panics or other issues. 
4b. OpenSUSE 11.1 and the wl driver: card works with no encryption, WEP, and WPA/WPA2 personal but kernel panics when connecting to WPA2+PEAP APs.

The problem doesn't look to be specific to Ubuntu as I have seen the exact same issue in OpenSUSE as well. Basically, it looks like the wl driver doesn't work very well with the 2.6.26 and earlier kernels and works with all but WPA2+PEAP APs in 2.6.27, where it causes a kernel panic immediately on connecting.

Perhaps it's time to ping Broadcom and let them know what's up?

---

### Post by fugyfudy on 2009-01-05
Well switching to kernel -7 seems to have worked for me so far at least.  Like I said, yesterday I had 3 kernel panics and today I've had none.  It's been 28 hours so I don't fully know yet but it is looking promising.

---

### Post by insert_name_here on 2009-01-06
I have this same error.

I do NOT have a Broadcom wireless chip.

I do have the intel chipset, incl. 82801 HD Audio, et al.


```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X1400
02:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
03:00.0 Ethernet controller: Atheros Communications Inc. AR5212 802.11abg NIC (rev 01)
15:00.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller

```

---

### Post by fugyfudy on 2009-01-07
Well it took about 50 hours but I had it happen earlier tonight.  I also had it happen about 30 minutes ago.

Here is the system log from right around when it failed

```
Jan  7 00:52:26 kernel: [  100.216629] eth1: no IPv6 routers present
Jan  7 00:53:38 NetworkManager: <info>  (eth1): supplicant connection state change: 7 -> 3 
Jan  7 00:53:38 NetworkManager: <info>  (eth1): supplicant connection state change: 3 -> 4 
Jan  7 00:53:38 NetworkManager: <info>  (eth1): supplicant connection state change: 4 -> 7 
Jan  7 00:54:38 NetworkManager: <info>  (eth1): supplicant connection state change: 7 -> 3 
Jan  7 00:54:38 NetworkManager: <info>  (eth1): supplicant connection state change: 3 -> 4 
Jan  7 00:54:38 NetworkManager: <info>  (eth1): supplicant connection state change: 4 -> 7 
Jan  7 00:57:38 NetworkManager: <info>  (eth1): supplicant connection state change: 7 -> 3 
Jan  7 00:57:38 NetworkManager: <info>  (eth1): supplicant connection state change: 3 -> 4 
Jan  7 00:57:38 NetworkManager: <info>  (eth1): supplicant connection state change: 4 -> 7 
```

And that was the last of it until I started up again.

Edit: I had it happen at least once again today and my video card also completely crapped out.  It was tough but I managed to go to the menu and cleanly shut it down but when I booted up, on either kernel, it would freeze.  So I ran it in safe mode and there were some problems on one of my partitions. After I booted it up from there I thought that it could have been a problem with Compiz so I turned Compiz Fuision off and have been running for about 7 and a half hours now. If it happens again I really don't know what else to do.

---

### Post by Beavis6953 on 2009-01-07
Ok I think I fixed it. at least for me anyway. I have a desktop (Asus P4p800) with no wireless card. I booted into Gparted live (boot disk available @ [gparted.sourceforge.net]("http://gparted.sourceforge.net") and ran ```
fsck /dev/XXXX
``` to my EXT3 (main file system) it found say 40 or so errors, don't ask me what. and I have been a few days with out a caps lock flashing freeze. I NEVER RECOMMEND RUNNING FSCK TO A MOUNTED DRIVE. I would try it if you caps lock is flashing (& in some cases scroll lock too) What do you really have to loose? Let me know if it doesn't work.

---

### Post by TpyKv on 2009-01-09
Are we any closer to being able to put this one to rest? I've not been using Ubuntu since this started, want to go back to using a decent OS (if anyone know's of one? :) ) 

That's not a nice comment, I'll admit, but these is nothing more annoying that getting nowhere, slowly

---

### Post by fugyfudy on 2009-01-09
Well I've had no luck in anything that I've tried.  If I remember correctly though, this started happening *after* I had installed Ubuntu for the most recent time so I'm going to re install it and see if I get anywhere.

---

### Post by girark on 2009-01-10
ThinkPad R61 with 8.10 here...

Had the same problem with the freezing and the blinking. linux-backports-modules-intrepid fixed it. No crashes for almost a week now. HOWEVER, since doing that, my wireless connection has been spotty. Extremely slow loading web pages, heavy outgoing packet loss in Skype, disconnects regularly.

Any thoughts?

---

### Post by networm1230 on 2009-01-10
possible? Last resort do a clean install of ubuntu. Install the minimal software for functionality on PC. update everything. A word of advice do not run code or scrips that your not shore of.

---

### Post by fugyfudy on 2009-01-10
31 hours and 20 minutes of uptime since I re-installed yesterday.  I'll edit the post if it craps out later.  I'm hoping it doesn't.

---

### Post by networm1230 on 2009-01-10
> **fugyfudy said:**
> 31 hours and 20 minutes of uptime since I re-installed yesterday.  I'll edit the post if it craps out later.  I'm hoping it doesn't.

I hope it works out for you. good lock

---

### Post by fugyfudy on 2009-01-11
Well it happened again.  How could this be going on for so long without finding a solution?

---

### Post by girark on 2009-01-11
I solved the kernel panic on my R61 using linux-backports-modules-install, but it caused new problems with the wireless - [http://ohioloco.ubuntuforums.org/showthread.php?p=6469190](http://ohioloco.ubuntuforums.org/showthread.php?p=6469190).

---

### Post by aherron on 2009-01-12
I've narrowed down the problem to using WPA. When I switched my network to use WEP, the panics went away and all is well. I've heard this is fixed in the -10 kernel and it should be out soon. Till then I guess I'll deal with a little less secure wifi. Going the WEP route also sped up my internets.

---

### Post by fugyfudy on 2009-01-12
Well I installed the backports modules and it still froze on me so I might change my wireless over from encrypted WEP to... *gulp* open WEP if that works. ugh

---

### Post by ryclegman on 2009-01-14
interesting

---

### Post by benjaminchodroff on 2009-01-15
> **Retraktor said:**
> **The Problem**:
I had the same problem on my Thinkpad T61p running Intrepid and using the Intel Wireless 4965 chipset. The kernel panicked quite unpredictably, but only when there was a high amount of network traffic through the wireless card.

**The Fix**:
I found this [[COLOR="Blue"]bug ticket[/COLOR]]("https://bugs.launchpad.net/ubuntu/intrepid/+source/linux/+bug/276990") where someone had a similar problem, only my problem was with 802.11g, not 802.11n. The fourth comment on the bug ticket solved it for me:
This advice sort of worked for me - I had to use the *latest* compat-wireless-2009-01-12.tar.bz2 - the one listed caused me to loose wireless support, but 2009-01-12 is working great so far! No hangs!

---

### Post by fugyfudy on 2009-01-15
> **benjaminchodroff said:**
> This advice sort of worked for me - I had to use the *latest* compat-wireless-2009-01-12.tar.bz2 - the one listed caused me to loose wireless support, but 2009-01-12 is working great so far! No hangs!

Well, that's good enough for me.  I have gone about 27 hours so far and had no freezing but I've also turned off the wireless and locked the laptop many many times to ensure that it didn't freeze.  Compiling now.

---

### Post by jiggz88 on 2009-01-15
> **Izkata said:**
> If you look in other threads, it has been confirmed that this is a problem with the driver for Broadcom wireless cards.

The Windows Broadcom drivers are stable, but the Linux ones are not.  That is the problem as far as anyone can seem figure out.

Yea, I do believe its an issue with broadcom wireless, specifically the 4311's, that have a weird bug in the driver that will cause the system to lock due to hardware fault. Additionally, I have only seen this hardware lockup when I was pushing heavy amounts of data traffic but not enough to cause the kernel to lockup due to network saturation(tickless kernel issue), but on the other hand I've loaded it up with ~800KB/s data and it still didn't thrash. 

WPA2-PSK

HP DV9413cl
AMD Turion64 X2 TL-56 1.8Ghz(1.6Ghz, 800Mhz) 
2GB DDR2-667 | 320GB WD SATA2
Broadcom 4311 B/G wireless

---

### Post by jiggz88 on 2009-01-15
> **aherron said:**
> I've narrowed down the problem to using WPA. When I switched my network to use WEP, the panics went away and all is well. I've heard this is fixed in the -10 kernel and it should be out soon. Till then I guess I'll deal with a little less secure wifi. Going the WEP route also sped up my internets.

if it is fixed in -10, then that would be a great thing as I cant stand any more crashes when in the middle of doing image complications for VM's.

On a side note, sorry about the double post...just noticed this copy of vB doens't have the 'auto join double post' on.

---

### Post by fugyfudy on 2009-01-15
So that didn't work for me. My wireless will work for times but then it disconnects randomly.  I'm not too happy with this.  I did use the newest one.  Might try re installing it but I'm not going to hold my breath.

Edit:
Well it looks like Broadcom updated the driver a while ago
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)
I think I installed it but I'm not the greatest with Linux even though I've used it off and on for years. Here's to hoping that this is the fix.

Well I haven't had it crash but the wireless still disconnects every 30 or so minutes.  I don't know if it is my connection or the messing around I did earlier because it only started today.  But I do have an old modem that may be to blame.  Ah, who knows

---

### Post by fugyfudy on 2009-01-16
Well I remembered I had the Linux-backports-modules so I removed those and restarted with no change.  I think my problem may be that I'm running a secure WEP network due to wanting security and I used to have a Nintendo DS that needed WEP to connect.  
The reason I'm thinking it could be WEP, at least for me, is because when I first start it up it takes a few minutes for it to find my network but during that time I can see all of my neighbors networks, who are all running on WPA or WPA2 personal. I really don't think that is a coincidence so I plan to change my network over to that tomorrow and see if that works.
I hope that this can be sorted out for everyone soon, I know how annoying it is.

Update: well, WPA2 seems to be helping except I still get disconnected if I am using pidgin, which I always have open.  Well I guess it is a sacrifice I have to make if this stops it from freezing.

---

### Post by fugyfudy on 2009-01-16
Sorry for the triple post but I think I fixed everything.  I went to System > Administration > Hardware Drivers, turned off my wireless driver, restarted to the obvious lack of wireless.  From there I installed the Broadcom drivers from source that I linked to earlier and it seems to be working.  The driver isn't activated in the Hardware Drivers window but I am wirelessly connected to my Internet while making this post.  The future is looking really bright.

---

### Post by Zetheroo on 2009-01-18
Why, Why, oh Why do people keep saying things like "this is a Broadcom issue" ??? 

This is happening to people with Intel, Atheros and Broadcom wireless chipsets so for the zillionth time it is NOT a "Broadcom issue". Please people try to pay attention to what others are saying here and not just your particular scenario. 

How about this for a brain-tickler ... 

Ubuntu Intrepid: Kernel Panics 
Kubuntu Intrepid : NO Kernel Panics 


... figure that one out ... :KS

---

### Post by Kossilar on 2009-01-18
Hey folks. I just installed Ubuntu 8.1 on my LG r700 laptop and I'm having exactly the same issue.

Total system failure. Black screen, blinking caps and scroll lock indicators. I can't update the system because it consistently fails before the process can complete. 

No problems in Kubuntu 8.1. Is it possible this is a problem with Gnome?

---

### Post by Zetheroo on 2009-01-18
> **Kossilar said:**
> Hey folks. I just installed Ubuntu 8.1 on my LG r700 laptop and I'm having exactly the same issue.

Total system failure. Black screen, blinking caps and scroll lock indicators. I can't update the system because it consistently fails before the process can complete. 

No problems in Kubuntu 8.1. Is it possible this is a problem with Gnome?

WOW! You too? No issues with Kubuntu Intrepid? ... That is remarkable ..
Can you paste here the output of lspci in the terminal?

Thanks

---

### Post by Kossilar on 2009-01-18
```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:04.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
01:04.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 01)
01:04.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)
06:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
08:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GT (rev a1)
```

From reading previous posts, I am currently assuming that my issue has something to do with my wireless card and WPA encrypted connections which is what I've been using at home. To be clear, my laptop did not experience this problem on Kubuntu 8.1, however I did not attempt to connect to any WPA encrypted connections prior to making this post. Today I changed my system over to Ubuntu 8.1 for other reasons and began experiencing this issue immediately.

I am currently operating under the assumption that the issue has something to do with WPA encrypted wireless connections. Currently I am testing my laptop on an Ethernet cable under Ubuntu 8.1 and running the system updates to see if the problem repeats itself.

Previously the issue occurred within an hour or so of trying to run updates. I will reply to this thread again if I am able to update successfully or if the system locks up again.

---

### Post by Kossilar on 2009-01-18
Alright. So I switched my system over to an ethernet cable rather then using my WPA encrypted wireless connection and the update completed successfully. System hasn't crashed yet, which it was doing fairly frequently during previous attempts over the WPA connection. 

That said, I'm fairly certain that the wireless is in some way responsible for the problems we're all having. Later tonight I'll connect myself to a WEP connection and see if there are further issues. 

I read some stuff in this threat about a new kernel version coming out soon. Does anybody know when that might happen?

---

### Post by d2718 on 2009-01-19
I would like to add my own personal experience to this thread; I hope it's helpful.

First of all:

My system: Compaq Presario v2000

Version (of Ubuntu): 2.6.27.9-generic (8.10, Ibix)

Processor: 1.8 GHz AMD Mobile Sempron 3000+
Memory: 1.25 GB PC2700
Hard drive: ATA Toshiba 40 GB
Host Bridge: ATI RS480
PCI bridge: ATI IXP SB400 PCI-PCI
USB Controller: ATI Inc IXP SB400
ISA bridge: ATI IXP SB400 PCI-ISA
Graphics Card: ATI Radeon XPRESS 200M 5955 (PCIE)
Multimedia audio Controller: ATI IXP SB400 AC'97 Audio Controller
Wireless card: Broadcom BCM4318 [AirForce One 54g] 802.11g
Ethernet: Realtek RTL-8139/8139C/8139C+
Dual Boot: Nope.

I recently installed XUbuntu for the first time on my girlfriend's old laptop, which XP seemed to have killed. I had trouble initially getting my wireless card to work, so I followed the advice this guide:

[WifiDocs/Driver/bcm43xx/Feisty_No-Fluff]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff")

I installed the ndiswrapper, and have the Broadcom card running with the native Windows driver. Modifying the /etc/modprobe.d/ndiswrapper file didn't work for me, though (see Version 0.3 under "Making it Permanent"), and instead I had to modify /etc/init.d/rc.local (see Version 0.2 under same) by adding the following lines:

```

rmmod b43
rmmod b44
rmmod b43legacy
rmmod ssb
rmmod nidswrapper
modprobe ndiswrapper
modprobe ssb
modprobe b44

```

This seemed to work fine for about a day. I went about installing what I thought I'd need and playing with stuff. I shut the computer down last night; I'm pretty sure the only thing I had installed since shutting the computer down the previous time was the text editor SciTE.

This morning when I turned the machine on, right after the progress bar on the XUbuntu loading screen (before the login screen), the screen went dark and the kernel panicked. This happened every time I tried to boot the machine normally; however, booting in Recovery Mode worked just fine (I'm not exactly sure what Recovery Mode really is--I'm new to Ubuntu and there doesn't seem to be any difference in functionality once the OS is up and running).

I spent quite a bit of time browsing various forums today. My problem was odd compared to the others in this thread in that it was a) completely consistent about when it happened, and b) didn't seem to be caused by any upgrade or modification (I started by installing 8.10, and it had worked fine for a couple of days--the only thing that seems like it could have changed it was the installation of a text editor, which seems unlikely). After examining some logs (particularly seeing syslog report this several times right before kernel panics:
```
Jan 19 16:51:06 mr-Dan-gerous NetworkManager: <info>  (wlan0): supplicant manager is now in state 1 (from 0). 
```
), I tried futzing with the wireless settings, and in the end, this seemed to work:

I commented out all of the lines that I had added to /etc/init.d/rc.local except for the one reading "rmmod b43".

Now the machine boots up just fine, the wireless works fine, and I have yet to experience another kernel panic. I have only the vaguest idea why this might work, but it does. If anyone else who followed the Fiesty_NoFluff guide is having this problem, you might try what I tried.

---

### Post by fugyfudy on 2009-01-20
Well, installing the newer wireless driver myself seems to have fixed it seeing as how this is the first time I've gotten an uptime of near 90 hours with this laptop on Ubuntu, and it's still going with no errors as far as I can tell. So I recommend that if anyone is having problems like this, they disable their Wireless driver if Ubuntu automatically had it and install from the card provider's website. If you had to use NDISwrapper or Ubuntu didn't automatically have your driver, I have no clue on fixing that.

Also be sure to blacklist the wireless drivers or else you will need to go through the process of setting up the Broadcom drivers again.  I forgot to do that and I don't want other people to freak out if they do end up trying this.

---

### Post by jejan on 2009-01-21
Same problem here with HP 6715b notebook (BIOS F.0E, Ubuntu 8.10, 2.6.27-9-generic, AMD using ATI Catalyst driver 8.12, Broadcom  BCM4312 802.11a/b/g (rev 02) using wl):

Lock-ups / Freezes with caps lock on.

This problem is dangerous because my ACPI-BIOS also freezes:
When my notebook freezes when fan is off, it stays off! So there is a risk of overheating the system or in the worst case of fire!

In my case my notebook smelled of burned plastic after being in this state for several hours. Notebook-battery also got defective which means that it loses half of its capacity afterwards. Not to mention what else could have happen!

My observation to this problem:
Freezes often occurs when I restart my wlan router. When NM realize disconnection from wlan system freezes.

Edit:
Tried Ubuntu 8.10 32- and 64-bit. Freezes occurs when running in battery mode and when plugged. Even when wlan disabled (pressed hardware-wlan-button, wl module stays loaded)

---

### Post by gotgenes on 2009-01-21
Has anyone here tried disabling Network Manager and instead using another wireless client, or directly using wpa_supplicant? I'm beginning to suspect Network Manager and its applet may be strongly associated with the system freezes I've been experiencing on my own laptop, a Compal HEL 80 with Intel 3945 ABG wireless. I shutdown Network Manager and am using wpa_supplicant and at the moment have not experienced any lockups.

---

### Post by sergiom99 on 2009-01-21
I only got this issue in Kubuntu hardy when on battery and trying to connect  to a WEP network. Any other wifi LANs are ok, I use a WPA2(TKIP+AES) network myself.

---

### Post by Zetheroo on 2009-01-21
> **Kossilar said:**
> Alright. So I switched my system over to an ethernet cable rather then using my WPA encrypted wireless connection and the update completed successfully. System hasn't crashed yet, which it was doing fairly frequently during previous attempts over the WPA connection. 

That said, I'm fairly certain that the wireless is in some way responsible for the problems we're all having. Later tonight I'll connect myself to a WEP connection and see if there are further issues. 

I read some stuff in this threat about a new kernel version coming out soon. Does anybody know when that might happen?

You are right that it has something to do with "Wireless Networking" in general, however I would advise you not to make any drastic changes to your networking or computing environment in an attempt to make this issue go away. I would be very keen to see you try to connect to your WPA encrypted network in Kubuntu 8.10 ... that would bring about some very interesting results either way.

One other interesting thing to note is that both of us (as well as quite a number of others) have systems with the same Intel system chipsets. This issue could be caused by a combination of various factors so its good to stay open to all possibilities. 

Like I said before there are people with Atheros, Broadcom and Intel wireless chipsets all having kernel panics, so this goes beyond it just being a single one in particular. I am thinking its something to do with the Linux modules or such that manage wireless connectivity and data flow.

I wish some Linux devs would present themselves in this thread...

---

### Post by Zetheroo on 2009-01-21
> **jejan said:**
> Same problem here with HP 6715b notebook (BIOS F.0E, Ubuntu 8.10, 2.6.27-9-generic, AMD using ATI Catalyst driver 8.12, Broadcom  BCM4312 802.11a/b/g (rev 02) using wl):

Lock-ups / Freezes with caps lock on.

This problem is dangerous because my ACPI-BIOS also freezes:
When my notebook freezes when fan is off, it stays off! So there is a risk of overheating the system or in the worst case of fire!

In my case my notebook smelled of burned plastic after being in this state for several hours. Notebook-battery also got defective which means that it loses half of its capacity afterwards. Not to mention what else could have happen!

My observation to this problem:
Freezes often occurs when I restart my wlan router. When NM realize disconnection from wlan system freezes.

Edit:
Tried Ubuntu 8.10 32- and 64-bit. Freezes occurs when running in battery mode and when plugged. Even when wlan disabled (pressed hardware-wlan-button, wl module stays loaded)

Wow! Thats pretty scary ... sorry for that ... please be careful and don't burn your laptop out just to use the latest release of Ubuntu. Hardy still works beautifully ... ;)

> **gotgenes said:**
> Has anyone here tried disabling Network Manager and instead using another wireless client, or directly using wpa_supplicant? I'm beginning to suspect Network Manager and its applet may be strongly associated with the system freezes I've been experiencing on my own laptop, a Compal HEL 80 with Intel 3945 ABG wireless. I shutdown Network Manager and am using wpa_supplicant and at the moment have not experienced any lockups.

I did try other networking managers and it was the same. Others as well used Wicd but had the same issues still.

> **sergiom99 said:**
> I only got this issue in Kubuntu hardy when on battery and trying to connect  to a WEP network. Any other wifi LANs are ok, I use a WPA2(TKIP+AES) network myself.

Kubuntu Hardy -- or Intrepid? Whats the output of your lspci in terminal?

---

### Post by jejan on 2009-01-21
Further testing shows that 1 out of 10 times my notebook freezes when i restart my router. Seriously.

My Router: Asus WL-500gP running DD-WRT (v24-preSP2)

Connection: B/G mixed, WPA2 Personal, 32 characters key

If someone can give me a hint how i can isolate this issue...

---

### Post by TpyKv on 2009-01-23
OK this is interesting,

I have been using my laptop as normal, but without my Orange Icon 225 USB "Internet Everywhere" Stick. Everything has been fine….

I installed this last night, and within 5 minutes I had the same crash. 

Definitely something up with Network Manager (in my case , at least)

Going to try WiCD tonight - will let you know….

---

### Post by gotgenes on 2009-01-23
> **Zetheroo said:**
> I did try other networking managers and it was the same. Others as well used Wicd but had the same issues still.
Try just using [wpa_supplicant]("https://help.ubuntu.com/community/WifiDocs/WPAHowTo#WPA%20Supplicant").

[LIST=1]
[*]Configure wpa_supplicant by copying the appropriate file from /usr/share/doc/wpasupplicant/examples/ to your home directory. For most that file is wpa-psk-tkip.conf.
[*]Edit the file with your appropriate settings.
[*]Copy and paste the following code into a file, say, wpa_connect.sh
```
#!/bin/bash
#set -e

# use your appropriate interface, e.g., ath0, wlan0,...
IFACE=wlan0
# path to wpa_supplicant config
WPA_CONF=/path/to/wpa_supplicant.conf

/etc/init.d/NetworkManager stop
pkill wpa_supplicant
pkill dhclient
ifconfig $IFACE down && ifconfig $IFACE up
sleep 1
wpa_supplicant -B -D wext -i $IFACE -c $WPA_CONF
sleep 2
dhclient $IFACE

```
[*]Make executable
```
chmod a+x wpa_connect.sh
```
[*]Run it as sudo
```
sudo ./wpa_connect.sh
```
[*]If after 15-30 seconds you see a line like
```
bound to 172.31.118.170 -- renewal in 1696 seconds.
```
you connected successfully. If not, re-execute the script.
[/LIST]
Please report if this helps prevent system lockup on your computer.

---

### Post by irfan9727 on 2009-01-24
How about different problems? There's many causes of kernel panic!
Umm, for *jejan*, when you boot into ubuntu, are you seeing some sort of text "pci bios bug found"? In other thread, some have freezes because of linux incompatibility with TPM chips. Any possibility of having tpm chip? I'm not having problem at all and and I'm still newbie, but interested in this problem ;) And any chances of Pheonix Bios?

> This is a problem of TRUSTED COMPUTING. Phoenix bios lock the acpi control of your O.S.

Also, someone mentions that nearly all of posters here uses the same sound card. Someone used Kubuntu Interpid, and the problem is gone. Since KDE used different audio mixer, guess, maybe audio mixer problem? ;)

---

### Post by FiReSTaRT on 2009-01-26
I just wanted to chime in with my experiences..  My laptop only freezes when I'm connected to an extremely unstable wireless network. Not connecting to the network from locations where the connection is unstable prevents the problem for me, but I'd like for this issue to be resolved. Broadcom STA driver.

---

### Post by gotgenes on 2009-01-27
> **FiReSTaRT said:**
> I just wanted to chime in with my experiences..  My laptop only freezes when I'm connected to an extremely unstable wireless network.
Likewise, for me. Please try following the directions in [my earlier post]("http://ubuntuforums.org/showthread.php?p=6604609") and see if they help.

---

### Post by lcanelon on 2009-01-28
Hello, am running ubuntu 8.10 kernel 2.6.27, i am having the exact same problem, but i think it has something to do with the bluetooth driver, the last time my system froze, i checked my logs the day after and saw that by the time it froze the last message was the following "hpet1: lost 12 rtc interrupts", today i needed to pair a bluetooth device with my computer (BTW i realized bluetooth doesn't work after the intrepid upgrade), anyways, when i ran /etc/init.d/bluetooth start i checked my logs again and got exactly the same message ("hpet1: lost 12 rtc interrupts"), i think it is  related as my network adapter is an intel 4965

---

### Post by honda882000 on 2009-01-30
I actually switched to Fedora 10 because of this issue (on a Compaq C770US Notebook).  The only way I could get out of the kernel freezes was to do a hard reboot, which is not good for the HD.  Seems to be common within the HP/Compaq family.  Try out Fedora, it might work out for you too.  Until Ubuntu fixes this issue, I am a Fedora fan.  Wifi support for Ath5k cards also work out of box, which is not true with Ubuntu (at least not with my laptop).

---

### Post by juanfer2k on 2009-01-31
it happened to me this mornning, and reading the replies, i may say the problem was the kernel, (doing update) but to me, i guess it was because of the interruption of update process...

I booted (force with power button) and chose the recovery opt. then i had an X issue, wich was fixed automatically with the "fix Xserver opition" in recovery mode.

Upgrading kernel again, Thanks!

---

### Post by Nixie Pixel on 2009-01-31
> **Zetheroo said:**
> Hey ... I checked out your blog ... at least the post on Ubuntu/Linux :)
Interesting ... and you raise some valuable points.
Thanks, I appreciate it - I added a little video regarding that post, by the way.

To the problem here, I was running on the -10 kernel for some time and still had the kernel panics.  It only happened while I had my USB mouse plugged in.  When I stopped using the USB mouse, the kernel panics stopped.  So for me, upgrading to the -10 kernel did not solve the problem.

I have since moved to Jaunty and purchased a new mouse so I won't be able to troubleshoot this any longer.  Good luck - and keep in mind that there may be crashes happening due to more than one problem.

---

### Post by Dex73 on 2009-02-01
I've just switched to 8.10 and have had it happen on my Gateway laptop several times. Turning of power saving options and screen saving features seems to help.

---

### Post by TpyKv on 2009-02-02
I installed Intrepid Kubuntu and it works, perfectly,. only problem is I do not like KDE.

I installed the Gnome Desktop, and the problem re-appeared again....

In another thread (or post) someone said the only common thing is the alsa/pulse audio driver... don't know if Kubuntu doesn't have this? or if there is a way to disable it ASAP? I don't have two minutes Ubuntu Intrepid use before it dies.

Either way I'm jumping ship to Fedora, can't be dealing with all these freezes. In fact I'll give Jaunty a go first... just really frustrates me as Hardy worked fine before, went to Intrepid, it didn't, now have done back to Hardy to have the Intrepid issue come back to haunt me.


Good luck guys and girls, and may the patience (of a saint) be with you.

---

### Post by Dex73 on 2009-02-02
I read somewhere that some wireless drivers and/or chips don't agree with ubuntu. I've disabled my wireless and haven't had it happen again.

---

### Post by ryclegman on 2009-02-03
yha i had this happen with my desktop which WAS wireless, but actually ran a Ethernet cord to it and all the peanut butter sandwiches poof! no more freezes.. ha ha ha Im free of the freezes!

---

### Post by networm1230 on 2009-02-04
> **Nixie Pixel said:**
> Thanks, I appreciate it - I added a little video regarding that post, by the way.

To the problem here, I was running on the -10 kernel for some time and still had the kernel panics.  It only happened while I had my USB mouse plugged in.  When I stopped using the USB mouse, the kernel panics stopped.  So for me, upgrading to the -10 kernel did not solve the problem.

I have since moved to Jaunty and purchased a new mouse so I won't be able to troubleshoot this any longer.  Good luck - and keep in mind that there may be crashes happening due to more than one problem.

Maybe you can try a different Linux Distribution?  [http://www.linux.org/dist/](http://www.linux.org/dist/)

My PC was acting up recently. Like my mouse will go crazy it moves all over the place and all so when I open my browser (Firefox) the web pages go up and down all crazy. to fix this crazy problem I install a other CPU I had a Intel Celeron(P) 325 2.53 GHz I installed a Intel(R) Pentium(R) 4 CPU 2.26GHz. this is a up grade for me. the P4 fix the craziness. I gas the little celeron could not handle my APT/prosses. note: To all clean your PC the physical hardware and the software side to. heat is a big cuss of CPU craziness. now the software side kernel panic Linux  [http://www.dialogic.com/support/helpweb/dxall/tnotes/new/iw1207.htm](http://www.dialogic.com/support/helpweb/dxall/tnotes/new/iw1207.htm)

---

### Post by dca on 2009-02-04
> **Nixie Pixel said:**
>  It only happened while I had my USB mouse plugged in.  When I stopped using the USB mouse, the kernel panics stopped.  So for me, upgrading to the -10 kernel did not solve the problem.


I can confirm the USB mouse issue.  Especially if you have one of those high-speed dealies that has both PS/2 & USB connector for wireless or wired keyboard mouse kit.  Removing the USB and using only the PS/2 solved freezes.

---

### Post by Dex73 on 2009-02-07
I decided to give my wireless another try on my home network with no security, instead of my college"s PSK encrypted network and I haven't had a crash in two days, compared to every few minutes at school. I think it's more of an encryption problem rather than a wireless problem.

---

### Post by Dex73 on 2009-02-07
.

---

### Post by nb56 on 2009-02-08
I am running 8.10 (with all updates) and I have tried both kernels on the standard distribution (Dual Boot Windows 7 beta) on this Dell Inspiron 8200.  Having set up the Broadcom driver for 43xx miniPCI cards the problem started - freezing every 30 - 60 mins.  De-activated this driver, fine on wired LAN and on Belkin PC card for which a driver was found automatically. However, any interaction with the wireless manager risks a lock-up. Using WEP shared key. There is also a PS3 which will act as an access point - this causes problems if I try to access it. Normal router is a Netgear 834.  

lspci reveals the following:
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB Controller #3 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 Go] (rev b2)
02:00.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
02:01.0 CardBus bridge: Texas Instruments PCI4451 PC card Cardbus Controller
02:01.1 CardBus bridge: Texas Instruments PCI4451 PC card Cardbus Controller
02:01.2 FireWire (IEEE 1394): Texas Instruments PCI4451 IEEE-1394 Controller
02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)

Battery operation was fine for the brief time I tried it, but on shut-down earlier today, reference on console indicated a problem related to acpid(spelling? - is this something on power management?) - the PC was not frozen, text was accepted, but no further action was forthcoming.
Not sure if it's relevant, but this PC also freezes on Windows 7, but is absolutely fine on XP and previous Ubuntu (6 - been away for a while). All memory etc tests report no problems.  Will follow this detective story with interest.  I am not getting any activity on Caps lock or other lights blinking when the problem occurs.

---

### Post by nb56 on 2009-02-08
Incidentally, doing lspci -vv reveals everything has this line:
Interrupt: pin A routed to IRQ 11
Is this normal? Everything using IRQ 11 would spell disaster on Windows - I know - this isn't!

---

### Post by ryclegman on 2009-02-11
of the people of who have switched distros, did it fix your problem?

---

### Post by Mizzou_Engineer on 2009-02-12
> **ryclegman said:**
> of the people of who have switched distros, did it fix your problem?

No, it did not. However, switching to OpenSUSE 11.1 *did* fix the problem resuming from suspend-to-RAM that Ubuntu 8.10 had on the GM45 chipset, though.

---

### Post by Nixie Pixel on 2009-02-12
Either purchasing a new mouse or switching to Jaunty fixed my issue.

Also, the issue could have been with my old USB mouse in a -specific USB port-, as I can't recall seeing the kernel panics when I moved the mouse to one of the two other USB ports on my laptop.

But as I have moved on to Jaunty, and have had no more kernel panics, I haven't tried to find further correlation.

---

### Post by networm1230 on 2009-02-13
> **Nixie Pixel said:**
> Either purchasing a new mouse or switching to Jaunty fixed my issue.

Also, the issue could have been with my old USB mouse in a -specific USB port-, as I can't recall seeing the kernel panics when I moved the mouse to one of the two other USB ports on my laptop.

But as I have moved on to Jaunty, and have had no more kernel panics, I haven't tried to find further correlation.

Thats grate! no more panics

---

### Post by Bonsanto on 2009-02-13
1.- My system crashes.
2.- I got many "initramfs" bugs in the start of ubuntu.
3.- I got many many times "fsk" bugs.
4.- I can't open many firefox becouse It makes my system crash.
5.- If I listen music and play freecell, It makes my system crash.
6.- I get many problems when I try to install something. Becouse If it crashes It makes Ubuntu delete a "lib" things, So I have to reinsall all the OS again (I have done 9 times).
7.- I have been looking for the "crash solution" for 1 week and nothing was found.
8.- In WIndows XP, my system dosen't crash, I can leave my pc turned on for weeks and no crash. But in Ubuntu 2 programs = crash.
9.- People said "try with no acpi" I don't know where to type that comand, is too much genereic isn't especific.

---

### Post by TpyKv on 2009-02-14
> **ryclegman said:**
> of the people of who have switched distros, did it fix your problem?



Yes, no problems whatsoever with Fedora...

just trying Intrepid again now as I dont have time to relearn fedora specific commands... takes too long!

---

### Post by ryclegman on 2009-02-16
hmm weird hopefully when jaunty come out all this thread and problem will be forgotten about ;)

---

### Post by pah99 on 2009-02-17
I was wondering if maybe this was related to whether or not you were using 32 or 64 bit. I had x86_64. Anyone else? Or are there people who were using 32bit?

---

### Post by jejan on 2009-02-17
Had a lot freezes under 32 and 64 bit. But since 2.6.27-11-generic (now 32 bit) freezes are (hopefully) gone!

---

### Post by TpyKv on 2009-02-18
What are the chances of getting an official bug developer/ team working on this? It seems to be huge number of people with this problem, and nothing official happening to resolve it? 

Unless I am wrong? Which I certainly hope is the case!!

I no longer take my laptop out with me, it stays at home, I would rather not use it than use it with Vista.....

Somebody, anybody!! PLEASE HELP US!! ):P

---

### Post by d.trott87 on 2009-02-18
> **Dex73 said:**
> I decided to give my wireless another try on my home network with no security, instead of my college"s PSK encrypted network and I haven't had a crash in two days, compared to every few minutes at school. I think it's more of an encryption problem rather than a wireless problem.

I've got nearly the same problem (HP Pavilion dv9000-series with Braodcom BCM4328 W-LAN card).
At home and a friend of mine I have no kernel panics. I got these only at the university.
At home I use WPA2 Personal encryption and the IP never switches for my laptop.
At the university I got the kernel panics every ~10 minutes. This is the same time when I'll get a new IP.

So I can mostly agree with Dex73.

---

### Post by ryclegman on 2009-02-19
you can try Linux mint and it has ndiswrapper pre-installed and then load the windows driver and hope it will fix the issue, or see if a different distro will fix your issue. when i switched to mint which basically is ubuntu it cut the freezes down greatly! I herd fedora is a good fix too?


also did anyone mention the bug today since is was bug smash day?

---

### Post by bull8042 on 2009-02-24
I just wanted to add my findings to this. I have never had a lockup or kernel panic until the 18th or so. I have a Dell 1505 with ATI x1400 and Intel 3945 wireless card. After the updates on the 17th or 18th of Feb, my problems started. I remember the updates included xorg, fglrx, and a half dozen others, but I didn't pay close enough attention to know what they were. The next restart I got a kernel panic 30 seconds to 1 minute after KDE finished loading. To make a long story short, deleting my connections in NetworkManager and not connecting to a network eliminates the lockups entirely.
Connecting to my WPA encrypted network at home occasionally causes kernel panic, but sometimes 2 or 3 minutes after connecting, and only 40% to 50% of the time. Connecting to an open "guest" network at work causes kernel panic 98% of the time and almost immediately.
For me this certainly appears to be directly related to NM/3945 card/ Intel drivers. It will even lockup when booting from the Intrepid live cd IF I try to connect to a network.

---

### Post by TpyKv on 2009-02-26
Wouldn't it be nice to have this problem fixed, surely someone, somewhere, must be able to think of a resolution that doesn't involve using another O/S?

---

### Post by bull8042 on 2009-02-26
> **TpyKv said:**
> Wouldn't it be nice to have this problem fixed, surely someone, somewhere, must be able to think of a resolution that doesn't involve using another O/S?

It just disturbs me a little that there seems to be no little or no interest in this thread. I am guaranteed a lockup if I try to connect to the open network at work. And what is even more disturbing is that R-E-I-S-U-B does nothing for me, so I have no recourse but to do a hard-shutdown. I am scared to even try to connect to any network if I have any of my encrypted partitions mounted or am trying to transfer files.
Please DEVs, a little help here....

---

### Post by ryclegman on 2009-02-27
time to go back to windows or even try OSX86? i know it angers me too, but i couldn't live with the crashes.... Hey bro try the new alpha that just came out for ubuntu ... jaunty jackalope and let us know if it fixed the problem.. cross fingers

---

### Post by Vadi on 2009-02-27
Has this issue been reported in Launchpad?

developers look there, not the forums

---

### Post by ryclegman on 2009-02-28
i asked that question to but got now answers ..... we need to though

---

### Post by gotgenes on 2009-02-28
> **Vadi said:**
> Has this issue been reported in Launchpad?

developers look there, not the forums

If you are experiencing a system freeze *and* you believe it's wireless related *and* you use NetworkManager to connect to your wireless network, please see this bug report and add your hardware and network information:

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/336001](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/336001)

---

### Post by bull8042 on 2009-03-04
> **gotgenes said:**
> If you are experiencing a system freeze *and* you believe it's wireless related *and* you use NetworkManager to connect to your wireless network, please see this bug report and add your hardware and network information:

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/336001](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/336001)

Thank you for entering a great detailed bug report. I added my 2 cents, but so far no one else has bothered. Hopefully, more will chime in and this will go somewhere soon.

---

### Post by TpyKv on 2009-03-04
The problem does not happen in Jaunty Alpha 3.... #
EDIT - yes it does!! doh!

Yet I am unable to use this also because my orange internet stick refuses to work - even Paul at Pharscape cannot help me :(

So as long as you dont have an orange icon 225, please give Jaunty a whirl and let us know how you get on!

---

### Post by pah99 on 2009-03-04
9.04 Alpha 5 is running smooth so far (since release date). Crashes, but not this way.

---

### Post by AegisXLII on 2009-03-05
So no fix has been found for this problem yet?

---

### Post by ryclegman on 2009-03-05
i cant wait till the release of ubuntu! i will be removing this mint and moven back.

---

### Post by pah99 on 2009-03-05
Yeah, unfortunately there was no fix for this. When Ibex first came out I was excited about it, and then ended up having to go back to Vista. But, so far Jaunty is running smooth. I can't wait for the final release.

---

### Post by TpyKv on 2009-03-12
It pains me to say - I'm using Windows 7 Beta (as well as fedora) - and it works, perfectly.

But it's just not Linux, is it

:)

Anyone else found any other good, working O/S's?

---

### Post by pah99 on 2009-03-12
I have to say, I'm wondering if this had anything to do with the hard drive. My old one used to cause (almost) the same types of lock-ups in Vista. I have a new and faster hd now, and am running smoothly. So maybe it was that. I don't know.

---

### Post by spady7 on 2009-03-13
Hi, I have ubuntu 8.10 kernel 2.26.7 and HP 8510w. I have the same issue, I mean sistem freeze, when I try to connect by wifi to vpn cisco and/or I try to use vnc or rdp connection ( using wifi connection) I tried to install backport pacchets... but seems issue is not solved....
Some news about it??? Of course... cap lock light is on when system freeze!!!
Thanks

---

### Post by farlander762 on 2009-03-14
I am running a Gateway M-7315u and I do not have an Intel wireless.  I have been staying in a hotel since I bought this confuser approximately 6 weeks ago and everything has been virtually perfect until two days ago when I had to change hotels.  Both hotels are small and do not have any form of security on their wireless networks.  Not even one of the redirect web pages that makes you agree to any terms.  

lspci and lsusb look like so:

```
lance@Gateway-Ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
[COLOR="Red"]02:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)[/COLOR]
06:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
07:09.0 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 03)
07:09.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)
lance@Gateway-Ubuntu:~$ lsusb
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 04f2:b027 Chicony Electronics Co., Ltd Gateway Webcam
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 002: ID 04f2:0618 Chicony Electronics Co., Ltd 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

I am running Intrepid 64bit, kernel version 2.6.27-11-generic which was the latest one supplied by automatic updates several weeks ago.  In other words, everything should be latest and greatest.  I have seen this lovely little issue twice, once while in Firefox and the other just randomly happened when I moved the mouse while no programs were open.  I did move the mouse into the upper panel area which is set to auto hide so that may have been the catalyst.  

If I am reading this right, here are the last few lines of kern.log before my last crash:```


Mar 13 06:21:12 Gateway-Ubuntu kernel: [ 2078.220113] wlan0: No ProbeResp from current AP 00:1e:58:01:f7:2c - assume out of range
Mar 13 06:21:12 Gateway-Ubuntu kernel: [ 2078.374004] ForceXPAon: 0
Mar 13 06:21:12 Gateway-Ubuntu kernel: [ 2078.614009] ForceXPAon: 0
Mar 13 06:21:13 Gateway-Ubuntu kernel: [ 2078.798023] ForceXPAon: 0
Mar 13 06:21:13 Gateway-Ubuntu kernel: [ 2079.042050] ForceXPAon: 0
Mar 13 06:21:13 Gateway-Ubuntu kernel: [ 2079.050712] ForceXPAon: 0
Mar 13 06:21:13 Gateway-Ubuntu kernel: [ 2079.059307] ForceXPAon: 0
Mar 13 06:21:13 Gateway-Ubuntu kernel: [ 2079.060617] wlan0: authenticate with AP 00:1e:58:01:f7:2c
Mar 13 06:21:13 Gateway-Ubuntu kernel: [ 2079.060699] wlan0: authenticate with AP 00:1e:58:01:f7:2c
Mar 13 06:21:13 Gateway-Ubuntu kernel: [ 2079.260060] wlan0: authenticate with AP 00:1e:58:01:f7:2c
Mar 13 06:21:13 Gateway-Ubuntu kernel: [ 2079.460069] wlan0: authenticate with AP 00:1e:58:01:f7:2c
Mar 13 06:21:14 Gateway-Ubuntu kernel: [ 2079.660056] wlan0: authentication with AP 00:1e:58:01:f7:2c timed out
Mar 13 06:21:23 Gateway-Ubuntu kernel: [ 2089.297257] ForceXPAon: 0
Mar 13 06:21:23 Gateway-Ubuntu kernel: [ 2089.308185] ForceXPAon: 0
Mar 13 06:21:23 Gateway-Ubuntu kernel: [ 2089.546062] ForceXPAon: 0
Mar 13 06:21:24 Gateway-Ubuntu kernel: [ 2089.731067] ForceXPAon: 0
Mar 13 06:21:24 Gateway-Ubuntu kernel: [ 2089.971041] ForceXPAon: 0
Mar 13 06:21:24 Gateway-Ubuntu kernel: [ 2089.982297] ForceXPAon: 0
Mar 13 06:21:24 Gateway-Ubuntu kernel: [ 2089.983592] wlan0: authenticate with AP 00:1c:f0:c0:46:ff
Mar 13 06:21:24 Gateway-Ubuntu kernel: [ 2090.023268] wlan0: authenticated
Mar 13 06:21:24 Gateway-Ubuntu kernel: [ 2090.023278] wlan0: associate with AP 00:1c:f0:c0:46:ff
Mar 13 06:21:24 Gateway-Ubuntu kernel: [ 2090.087174] wlan0: RX ReassocResp from 00:1c:f0:c0:46:ff (capab=0x421 status=0 aid=4)
Mar 13 06:21:24 Gateway-Ubuntu kernel: [ 2090.087182] wlan0: associated
Mar 13 06:21:24 Gateway-Ubuntu kernel: [ 2090.115255] ForceXPAon: 0
Mar 13 06:22:11 Gateway-Ubuntu kernel: [ 2137.555023] ForceXPAon: 0
Mar 13 06:22:12 Gateway-Ubuntu kernel: [ 2137.799020] ForceXPAon: 0
Mar 13 06:22:12 Gateway-Ubuntu kernel: [ 2137.979008] ForceXPAon: 0
```

This network does show up as very weak so maybe that is part of it.

This from daemon.log also looks promising:

```
Mar 13 05:48:53 Gateway-Ubuntu avahi-daemon[4964]: Registering new address record for fe80::222:5fff:fe3d:362a on wlan0.*.
Mar 13 06:21:12 Gateway-Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state change: 7 -> 0 
Mar 13 06:21:12 Gateway-Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state change: 0 -> 2 
Mar 13 06:21:13 Gateway-Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state change: 2 -> 3 
Mar 13 06:21:14 Gateway-Ubuntu NetworkManager: <debug> [1236943274.770463] periodic_update(): Roamed from BSSID 00:1E:58:01:F7:2C (Victorian Inn) to (none) ((none)) 
Mar 13 06:21:23 Gateway-Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state change: 3 -> 0 
Mar 13 06:21:23 Gateway-Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state change: 0 -> 2 
Mar 13 06:21:24 Gateway-Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state change: 2 -> 3 
Mar 13 06:21:24 Gateway-Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state change: 3 -> 4 
Mar 13 06:21:24 Gateway-Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state change: 4 -> 7 
Mar 13 06:21:26 Gateway-Ubuntu NetworkManager: <debug> [1236943286.774589] periodic_update(): Roamed from BSSID (none) ((none)) to 00:1C:F0:C0:46:FF (Victorian Inn)
```

---

### Post by iagsvens on 2009-03-17
I had the same problem, my screen froze frequently and the keyboard lights started blinking (kernel panic). Switching the hard drives to RAID under BIOS and installing a new power supply unit didn't resolve this issue. After replacing the network card I never had this problem again, so I assume it can be attributed to a hardware defect of the network card. Hope this helps anybody!

---

### Post by marcb on 2009-03-18
Some of you (I think it was in this thread) reported that switching to Fedora solved the freezing issues.

Today I got the same freeze in Fedora 10, the second day after installing it. In Ubuntu, installing the -13 kernel seemed to help a little but still had freezes.

---

### Post by Fire_Chief on 2009-03-20
I've had Intrepid on my Thinkpad T60 since it came out and this issue _never_ occurred until last Saturday (March 14th). Since then I've had at least 6 hard lockups identical to what others here have described. For now I've disabled my screensavers (has been happening when I'm away from the computer) and noted a segfault error from the messages log at the time of one of the locks. I'll track further instances but I highly suspect a recently applied update. Just haven't had it happen enough to demand attention yet nor had the time to test the system out.

-Cheers!

---

### Post by grogo on 2009-03-24
I've only ever experienced the issue on laptops, never seen a desktop go into a kernel panic, regardless of the distro or hw.  One suggestion I will offer is to ensure that any old versions of the kernel are removed and you're fully up to date and all dependencies are met in apt-get.

I've made it a habit to only have 1 kernel version installed at any given time and haven't had any issues lately (knock wood).  At one point there was apparently a module conflict for my ethernet controller after a kernel update, after much swearing and checking of cables (wouldn't pick up a DHCP lease from the router) I decided to try cleaning up the system and it all started working... just my 2 cents.

---

### Post by pah99 on 2009-03-24
Just so you all know, this problem doesn't happen in Jaunty. At least it hasn't happened yet. The other reason might be because I changed the hard drive.

---

### Post by farlander762 on 2009-03-25
I'm quite positive it has to do with my wireless networking.  It has only happened to me a few times but after each instance I have checked the logs that I posted above and they look virtually the same as above.  

I am staying in a hotel and have been since I bought this machine.  The problem did not start until I moved to this hotel (2nd hotel since I bought it).  I am at the end of the hall and the router is as far from me as is possible.  The signal bar in Network Manager barely shows me attached at all and sometimes it cannot even connect.  Sometimes it drops connection during use.  

Something to do with dropping the connection and then reconnecting causes the kernel panic.  I might encourage others having this problem to note if they also have a weak wireless signal.

---

### Post by TpyKv on 2009-03-26
Still weeks into this and no working Ubuntu system...., Ubuntu Studio looks nice! but there is another bug relating to the network manager, it wont install!!  

Every Linux distro goes periodically through a downer, partly because our expectations get higher, partly because technology overtakes them, partly because of complacency. I suspect on this ocassion it's the latter. But they will get there. And I'll keep coming back every week to see if I can use Ubuntu again.

---

### Post by birdy on 2009-03-30
I just upgraded to Jaunty Beta, and unfortunately the madwifi wireless (ath_pci) gives me kernel panic freezes even more frequently now (several times a day) than I had before on my Intrepid installation. I suppose a solution could be to switch to the ath5k driver, but unfortunately it doesn't work at all on my system. This is getting very frustrating. I was really hoping that this would have been fixed in Jaunty :-(

---

### Post by pah99 on 2009-03-30
> **farlander762 said:**
> 
Something to do with dropping the connection and then reconnecting causes the kernel panic.  I might encourage others having this problem to note if they also have a weak wireless signal.

I think this may have been the issue, as I have gotten a better router and now have a good connection. But for as long as I can recall, I usually had a bad connection whenever this occured.

---

### Post by TpyKv on 2009-04-02
I have found a Linux OS simuilar to Ubuntu, but with a decent network manager - it is PCLOS (PC Linux OS - Gnome version)

It uses apt-get and synaptic... wireless and compiz work out of the box, only thing I am struggling with is my orange mobile internet stick.

In all fairness, their community support is non existent - it is one of those distro's where you are expected to know how everything works.... 

but if you don't have a mobile internet stick and need a working OS until Ubuntu sorts it's act out, please check out - [http://linuxgator.org/home/index.html](http://linuxgator.org/home/index.html)

---

### Post by TpyKv on 2009-04-03
Finally got somewhere!

Ubuntu Studio does not seem to suffer from the same problems. 

I had an issue with network manager not installing, there is a bug report filed on launchpad, but I installed wicd from source and then used synaptic to remove wicd and install network manager.

I have been throwing everthing at it and it still hasn't crashed once....

Give it a go!

[http://ubuntustudio.org/](http://ubuntustudio.org/)

Edit - Still one day on and no crashes....!!

[http://premium1.uploadit.org/mentholist//ubuntustudio.png](http://premium1.uploadit.org/mentholist//ubuntustudio.png)

Just changed the backdrop, it looks lovely...

---

### Post by ante.blaskovic on 2009-04-07
I had CAPS LOCK blinking problem on my Toshiba laptop(a100-003)  after on of kernel upgrades on 8.10. 

I find one workaround for that, switch off wireless on laptop  while booting. You can switch it ON later, but wait at least for X to start loading ;)

On 9.10alpha I had no problems with it.

---

### Post by kaziem on 2009-04-11
> **mumurlen said:**
> Hi 

Verify you don't have Intel 4965 wireless chipsets

If so follow the release notes for 8.10 and install linux-backports-modules-intrepid

```

sudo apt-get install linux-backports-modules-intrepid
```

[https://wiki.ubuntu.com/IntrepidReleaseNotes#System%20lock-ups%20with%20Intel%204965%20wireless](https://wiki.ubuntu.com/IntrepidReleaseNotes#System%20lock-ups%20with%20Intel%204965%20wireless)

Hope it helps.

I do have an Intel 4965 wireless chipset and I'm experiencing this problem. How can I fix it? Help please! I'm desperate!!

---

### Post by TpyKv on 2009-04-16
I installed the Wicd network manager, which uninstalled the default network manager, so then was able to go back and reinstall the default one and remove wicd at the same time - which solved the problem on Ubuntu Studio...

I tried turning the wireless switch off at boot-up but the switch doesn't work in Ubuntu - only vista - the wireless loads up automatically....

---

### Post by SaintDanBert on 2009-05-18
> **Nixie Pixel said:**
> Hi, I recently installed Ubuntu 8.10 on a Compaq Presario A909US (dual-booting with Vista).  
...
However my system has frozen twice now in the four days I have had it installed - a hard freeze that I needed to hit the power button to get out of.  My Caps Lock indicator was blinking on and off after the freeze happened, both times.
...
~Nix
This happens to me on Hardy 8.04 every time I use an 802.11n network link.

I'm running an Emperor Linux Raven Tablet (Lenovo Thinkpac X61t).
All Hardy LTS updates are applied. Running 4GB ram and Gnome desktop.

BTW -- Where are the blinky indicator messages documented? What does
blinky caps lock mean?  What about blinky num lock or blinky scroll lock?
Not that I've seen these, but I'm a big believer in documenting indicators
rather than having the meaning some arcane secret.

~~~ Saint 0;-/

---

### Post by pah99 on 2009-05-18
> **SaintDanBert said:**
> This happens to me on Hardy 8.04 every time I use an 802.11n network link.

I'm running an Emperor Linux Raven Tablet (Lenovo Thinkpac X61t).
All Hardy LTS updates are applied. Running 4GB ram and Gnome desktop.

BTW -- Where are the blinky indicator messages documented? What does
blinky caps lock mean?  What about blinky num lock or blinky scroll lock?
Not that I've seen these, but I'm a big believer in documenting indicators
rather than having the meaning some arcane secret.

~~~ Saint 0;-/

Update to 9.04. That's all anyone can help you with.

---

### Post by rahul489 on 2009-05-19
I am having this problem only after upgrading to 9.04. 
Linux backport modules doesnot help. 
Happens only when I am using firefox. 

I am spending LOT of time on this but couldnt find a fix.
Any kind of help is appreciated.

---

### Post by pah99 on 2009-05-19
Updating to 9.04 solved the issue for me. You just so happen to be the first to say that this issue is still unresolved in Jaunty. As far as I know, there is no solution. Sorry. I suppose it wouldn't hurt to try firefox 3.5.

---

### Post by grandmaster on 2009-05-31
> **rahul489 said:**
> I am having this problem only after upgrading to 9.04. 
Linux backport modules doesnot help. 
Happens only when I am using firefox. 

I am spending LOT of time on this but couldnt find a fix.
Any kind of help is appreciated.

I'm getting the same.
Brand new install of ubuntu and when i download anything using firefox i get a panic and my caps lock flashes and i have to reboot.

Any help would be appreciated

acer aspire one.
Netbook remix 9.04
Wireless access to internet, i have not yet tried a cable to eliminate the wireless..

GM

---

### Post by kuthulu on 2009-06-06
i had this same problem... ubuntu 9.04 freezes, caps led blinking... i had to power off with the power button

i found it only happened when trying to connect to a WPA-TKIP network, so i changed my router to WPA-TKIP+AES and the problem is gone
this freez doesn't ocurr when connecting to a WEP network

my wireless card is ipw2200

for those with the problem, try setting your router to WEP or better WPA-TKIP+AES, or WPA-AES to see if that helps

good luck

---

### Post by relen on 2009-06-12
Acer Aspire One here also (original model, supplied with HD and Linpus, whatever they called it model-number-wise) - did a completely clean install of 9.04 UNR and got the panic/flashing caps lock after a few minutes out of the blue then (after a complete reinstall) while it was performing updates. 

After reboot I was able to get and install all updates, and since these installed I've had no issues (touch wood), running the machine solidly for several hours.

--R

---

### Post by feistybill on 2009-06-20
Same problem here - random system freezes with blinking led when connected to a wireless AP (my client: wpa, intel 3945, ubuntu's network manager). I got the same problem with Ubuntu 9.04 and with a fresh install of Ubuntu 9.10. Noone seems to have found a solution to this problem yet?

---

### Post by weremichael on 2009-06-27
> **kuthulu said:**
> i had this same problem... ubuntu 9.04 freezes, caps led blinking... i had to power off with the power button

i found it only happened when trying to connect to a WPA-TKIP network, so i changed my router to WPA-TKIP+AES and the problem is gone
this freez doesn't ocurr when connecting to a WEP network

my wireless card is ipw2200

for those with the problem, try setting your router to WEP or better WPA-TKIP+AES, or WPA-AES to see if that helps

good luck

I am giving the WPA-TKIP+AES method a shot. I'll report back later to give a verdict on how well it works.

UPDATE:

That didn't seem to help. I am now trying to turn off all visual effects and see if that resolves the issue.

UPDATE:

That didn't work either. I finally figured it out though. My problem lies with my [Asus OLED driver]("http://lapsus.berlios.de/asus_oled.html"). Once I stopped enabling that, the freezing problem went away. So if you have a G50vt and are running the OLED driver and suffering frequent freezing, the driver might be your problem.

---

### Post by zoomy942 on 2009-07-04
mine had been working fine for a few weeks and now its not :(

---

### Post by ralli on 2009-07-07
I had the same problem on acer aspire one and I solved it by disabling apparmor

sudo /etc/init.d/apparmor stop

Huge amounts of log-entries in syslog stopped and everything worked fine.

If this works for you and you dont want apparmor to bring your system down again, type the following:

/etc/init.d/apparmor stop
update-rc.d -f apparmor remove
apt-get remove apparmor apparmor-utils

---

### Post by zoomy942 on 2009-07-07
> **ralli said:**
> I had the same problem on acer aspire one and I solved it by disabling apparmor

sudo /etc/init.d/apparmor stop

Huge amounts of log-entries in syslog stopped and everything worked fine.

If this works for you and you dont want apparmor to bring your system down again, type the following:

/etc/init.d/apparmor stop
update-rc.d -f apparmor remove
apt-get remove apparmor apparmor-utils

excellent.  what is apparmor for?

---

### Post by bshosey on 2009-07-07
I had this problem when I was using the Broadcom STA Wireless driver. When I switched to the Broadcom B43 Wireless Driver. I have not had this problem after switching the drivers in the Hardware Drivers under the Aministration section in the Gnome System panel menu.

I do run WPA Personal 2 wireless security. I hope this helps.

---

### Post by ralli on 2009-07-08
apparmor is supposed to protect your system from nasty things going on. It controls the access of applications to your ressources. Maybe its possible to configure apparmor, maybe its a bug, I dont know.

Anyhow I had problems with apparmor with other applications and I'm not quite shure if apparmor is really neccessary.

---

### Post by danjl on 2009-07-28
I have the same symptoms; possibly a different problem.  The apparmor soluition didn't work for me but I found a fix.

This problem (freezing and caps lock flashing) occurred after trying to replace the default wifi driver on my Asus Aspire One (from ath5k) to ndiswrapper.  I had accidentally removed the blacklisting of the madwifi driver (ath_pci) (since I tried that too).

In my case this is a kernel panic caused by a driver conflict between ath_pci and ndiswrapper.  I stopped ath_pci:

sudo gedit /etc/modprobe.d/blacklist.conf

and inserted:

blacklist ath_pci
blacklist ath-pci
blacklist ath5k

and the problem went away. (Note: you need working ndiswrapper wireless drivers to do blacklist the above drivers!)

This bug has been reported:

[https://bugs.launchpad.net/netbook-remix/+bug/381336](https://bugs.launchpad.net/netbook-remix/+bug/381336)

I'd recommend that anyone experiencing this problem checks for similar driver conflicts.  (of course, there are many possible reasons for a kernel panic).

---

### Post by tribaldata on 2009-08-12
Experiencing the same issue with my Acer Aspire One, total freeze with blinking CapsLock light.

Network card: AR24x 802.11abg Wireless PCI Express Adapter
Driver: ath5k_pci

I notice that on any high usage of the wireless card the system will totally freeze, any Samba, Firefox streaming is a big no no right now.

I did stop the apparmor like a older post suggested but i still experience the same problem.

Anyone has been successful running the madwifi drivers??

---

### Post by Zetheroo on 2009-08-12
This is really getting VERY VERY frustrating ... to the point that Ubuntu is seriously loosing it's appeal as my main OS!!!

I had been using Hardy still up until about a week ago for the very reason that Intrepid was causing daily Kernel Panics on my laptop ... but I finally decided to switch to Jaunty in the last week .. and what do I get now? ... more Kernel Panics!!!! ARGH!

The worst thing about it is that there seems no straight forward method for troubleshooting a Kernel Panic! WTH?!?

I have the Atheros Madwifi driver activated in my Hardware Drivers dialog. 

If this keeps up (which it probably will) I will have to start using OpenSuse or something ... just because I bloody HAVE TO!! 

> lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
03:00.0 Ethernet controller: Atheros Communications Inc. AR5212 802.11abg NIC (rev 01)
04:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
15:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
15:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
15:00.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
15:00.3 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev ff)
15:00.4 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 11)
15:00.5 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 11)

---

### Post by BillyPrefect on 2009-08-13
Dell Precision M65 -

billy@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation G72GL [Quadro FX 350M] (rev a1)
03:01.0 CardBus bridge: O2 Micro, Inc. Cardbus bridge (rev 21)
03:01.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

Extremely fustrating, running Jaunty, latest kernel, just finished the latest reinstall or else I wouldn't have had time to type this message!

So - is the theory still with the Intel Chipset (82801) or the Intel 3945 wireless or ???

Complete pain in the buttocks!

---

### Post by tribaldata on 2009-08-13
I installed the madwifi-trunk drivers and so far i am stable no freezing. I am also able to stream video and music from firefox, i am still having issue with samba transfer freezing but that might be another issue.

Here his the link to madwifi-trunk 
[http://snapshots.madwifi-project.org/madwifi-trunk-current.tar.gz]("http://snapshots.madwifi-project.org/madwifi-trunk-current.tar.gz")

This is what i did

############################################### 

tar -zxvf madwifi-trunk-current.tar.gz

cd /madwifi/scripts

./madwifi-unload

./find-madwifi-modules.sh $(uname -r)

You will be prompted for removing the old madwifi driver, i suggest removing the old drivers.

cd ..

make

make install

modprobe ath_pci

####################################################

And then restart your system.

Check if the drivers as changed by running "sudo lshw -C network"
Your new driver should say "ath_pci"

Here my specs,
Aspire One
Ubuntu 9.04 Jaunty  "Linux 2.6.28-14-generic"
WirelessCard: AR242x 802.11abg Wireless PCI Express Adapter
driver=ath_pci

---

### Post by Zetheroo on 2009-08-16
tribaldata still no freezes?

I tried installing the madwifi drivers and got no further than "make". Would it make a diff to install the madwifi-trunk package instead?

And I am guessing your using Ubuntu Jaunty?

---

### Post by Harper45 on 2009-08-16
thanks for sharing this information ..

---

### Post by Zetheroo on 2009-08-16
Looks like I fixed my Kernel Panic issue.

Here is what I did:

1. Install linux-restricted-modules-generic so I would have the older ath_pci driver

2. Blacklist ath5k by creating /etc/modprobe.d/blacklist-ath5k.conf with the line:
blacklist ath5k

3. Un-blacklist ath_pci by editing /etc/modprobe.d/blacklist-ath_pci.conf and commenting out the "blacklist ath_pci" line.

4. Reboot

(thanks to kevinbsmith)

My Atheros chipset is:
03:00.0 Ethernet controller: Atheros Communications Inc. AR5212 802.11abg NIC (rev 01)

Running Ubuntu Jaunty

UPDATE: Kernel Panic about 3 hours later!! I am going to buy an Intel Wifi card to replace the Atheros one!

---

### Post by Zetheroo on 2009-08-18
Well after doing a bunch of stuff it seems like I am not experiencing kernel panics. What I did was:

- Installed the madwifi-trunk drivers, which completely screwed up my wireless so I then ...
- Uninstalled the madwifi-trunk drivers, which left me with no wireless capabilities so I ....
- Reinstalled linux-backports-modules-jaunty-generic and some other such packages through Synaptic ...
- Rebooted the laptop
- Enabled the Madwifi driver in Hardware Drivers and rebooted again 

So far about 20+ hours uptime and no freezes!

Again, don't know what the issue is or how I fixed (if I actually did fix it) ...

---

### Post by necronwarrior on 2009-08-18
I used to have the same problem(System freeze + CAPS LOCK key blink) on ubuntu 8.10(It began from that version).
Now on 9.04 I still get the system freeze but the CAPS LOCK key does not blink.I've noticed it mostly (90 % of the times) happens when I am running both firefox and vlc media player. I've also noticed that this happens when either of the two above mentioned programs is running.
I have a lenovo R61 laptop.
kernel version:2.6.28-11-generic

---

### Post by Zetheroo on 2009-08-18
lspci in terminal ... post the output pls.

---

### Post by zoomy942 on 2009-08-19
not sure is it helps, but in 9.10 my problem went away 100%

---

### Post by Bloodstar on 2009-09-09
I recently ran into this problem, myself, running Kubuntu 9.04 on my netbook.

Strangely enough, it only occurs after I've had the lid closed for a while... instead of locking the screen, it locks up the whole thing.

Running lspci lists two of the possible pieces of hardware which people seem to be having issues with:
01:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
03:00.0 Ethernet controller: Attansic Technology Corp. Atheros AR8132 / L1c Gigabit Ethernet Adapter (rev c0)

---

### Post by nowhere@cox.net on 2009-09-09
I've been having the same problem on a T61 laptop with 9.04 (hard hang with blinking caps lock). And I have also noticed that it occurs quite frequently when the lid is closed but also when the machine is idle for a while. It's not 100% though because it happens while actually working on it occasionally.

No mention of kernel panic in any of the logs...

---

### Post by docus on 2009-09-14
I'm getting freezes on my Thinkpad T60.  They seem to happen randomly, a few minutes after log-in.  There doesn't seem to be any pattern - they happen when I'm online and offline, and whether I'm running apps or not.

I installed 9.04 in May and things went very smoothly from then until just two weeks ago.  I have no idea what changed in the last two weeks, as I haven't installed any new programs! 

I was running kernel 2.6.28-11 when the problem first started, then I upgraded to 2.6.28-15 but the problem didn't go away, so I downgraded to 2.6.28-14, but that didn't make any difference either - it still freezes.  

I'm stumped and any help would really be appreciated.  Could upgrading to 9.10 help?  Failing that I might have to ditch Ubuntu as my computer is close to unusable right now :(

---

### Post by docus on 2009-09-15
Well, unfortunately I'm posting this from Windoze XP :( as Ubuntu has deteriorated to the point where it's freezing all the time and I'm having to switch the machine off.  I really hope a solution can be found or that 9.10 fixes this problem.

---

### Post by docus on 2009-09-16
OMG now windoze is freezing up on me!!! I suppose that means it's a hardware fault then :(

---

### Post by birdy on 2009-09-17
Yippee! Finally! The nightmare is over.

I have managed to get the kernel panics to disappear on my Thinkpad T61 running up-to-date Jaunty, including linux-backports-modules-2.6.28-15.

I use the madwifi driver (ath_pci) provided in the repos.

The solution was to unintall Network manager and replace it with Wicd.

Hope this solution is working for someone else.

---

### Post by srulik on 2009-09-21
Also having this awful freezes,
always having something to do with either Transmission/aMule on. 
Using 9.04.

Here's relevant lspci:
Ethernet controller: **Atheros** Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
Ethernet controller: **Realtek** Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by FrancoNero on 2010-06-10
for me this occurs completely randomly in lucid, on a thinkpad t61.... where does this come from?

---

### Post by linux4me on 2010-06-14
> **FrancoNero said:**
> for me this occurs completely randomly in lucid, on a thinkpad t61.... where does this come from?

I ran across this old post while looking for a solution for the kernel panics I've been having in Lucid 64-bit. We should probably start a new thread. If I do, I'll post a link back here, please do the same.

To start troubleshooting the kernel panics (caps lock flashing, system frozen, magic keys don't work), start with these:
[LIST=1]
[*]Go System -> Administrator -> Disk Utilities, select your hard drive, and look at the SMART info to make sure the disk is healthy.
[*]Use a Live CD to run Memtest for several hours to make sure you don't have a memory problem.
[*]If you're using the Nvidia restricted drivers, try reverting to the nouveau driver for a while to see if the kernel panics stop.
[/LIST]
Looking at the system logs (System -> Administrator -> Log File Viewer) has been no help for me since the kernel panics apparently prevent anything from making it into the log.

There is also a lot of mention of wireless drivers potentially causing the hangs. You might try preventing your wireless driver from loading and using wired for a while to see if it solves the problem. Then you'll know it's an issue with the wireless driver. I, however, don't have wireless, so I know that's not it for me.

---

### Post by aa-hcl on 2010-06-27
> **linux4me said:**
> I ran across this old post while looking for a solution for the kernel panics I've been having in Lucid 64-bit. We should probably start a new thread. If I do, I'll post a link back here, please do the same.

To start troubleshooting the kernel panics (caps lock flashing, system frozen, magic keys don't work), start with these:
[LIST=1]
[*]Go System -> Administrator -> Disk Utilities, select your hard drive, and look at the SMART info to make sure the disk is healthy.
[*]Use a Live CD to run Memtest for several hours to make sure you don't have a memory problem.
[*]If you're using the Nvidia restricted drivers, try reverting to the nouveau driver for a while to see if the kernel panics stop.
[/LIST]
Looking at the system logs (System -> Administrator -> Log File Viewer) has been no help for me since the kernel panics apparently prevent anything from making it into the log.

There is also a lot of mention of wireless drivers potentially causing the hangs. You might try preventing your wireless driver from loading and using wired for a while to see if it solves the problem. Then you'll know it's an issue with the wireless driver. I, however, don't have wireless, so I know that's not it for me.

I have installed linux 3 days ago and since then had the same kind of freeze 5 times already, once it totally destroyed the /boot/grub, so i had to re-install everything and the other time it made the ubuntu partition with errors, so had to boot from Live CD to run fsck (or fdisk).

Interesting details (do not know if they are relevant):

1. small icons after rebooting are overlapping
2. it is probably occurs after hibernation
3. It is probably occurs while accessing the internet using wireless....

it is 64-bit 10.04 with very latest updates... 

Checked the disk, all fine; it is dual-boot Dell, never had problems with hardware under Windows.

Any ideas how to fix it?

---

### Post by linux4me on 2010-06-27
I ended up switching to the nouveau (open source) Nvidia driver and the kernel panics haven't recurred. Everything worked flawlessly for a few days, then I started experiencing [this problem]("http://ubuntuforums.org/showthread.php?t=1478787"), which cleared up after a day and hasn't recurred. All seems stable again, though I would feel better if I understood why. I'm still using the nouveau Nvidia driver.

---

### Post by FrancoNero on 2010-06-27
ubuntu seriously should get its act together hardware wise. i mean if it doesnt support a certain type of hardware, make it public that it doesnt and lets move on, but those it does support, it should have freak bugs... I mean cannonical could ask companies to supply hardware for testing couldn't it?

---

### Post by abandonedthe_mulletator on 2010-07-03
I had a blinking caps lock key system freeze problem last week.  I did a hard reboot and now grub is screwed up.  I thought my hard drive got wiped but I was able to boot with a live USB.  My hard drive looks fine but grub is messed.  Here is what it says if I try to boot from the hard drive:
```
grug loading
error: no such partition
grub recovery>
```

Any ideas?

---

### Post by FrancoNero on 2010-07-22
actually on nvidia it's better than during using nouveau

---

### Post by linux4me on 2010-07-22
> **FrancoNero said:**
> actually on nvidia it's better than during using nouveau

I don't know what to make of that. I can't use the nvidia driver without the hangs, but using nouveau my system has been stable for a few weeks now.

---

### Post by bradmayne04 on 2010-08-10
well nixie long time no see lol. i'm using a broadcom 4312 and am having no problems whatsoever. let me know if your still having issues with your wireless and i can give ya a walk through. btw did you ever fix the sql problems on your site?

---

### Post by titotti32 on 2010-10-11
what should i do if my ncomputing server run on hardy crashed like that?
caps lock and scroll lock blinking all day long

i'm so confused
:-k

---

### Post by papaz on 2011-01-01
There is a known bug in ubuntu. This problem is caused by the touchpad when is inactive after boot. So, in the case of a laptop try this:

cd /etc/modprobe.d
gedit blacklist-touchpad.conf


inside file write:

blacklist psmouse

now save the file & exit.

reboot your machine.
From now on use only wired mouse (or a bluetooth one).

---

