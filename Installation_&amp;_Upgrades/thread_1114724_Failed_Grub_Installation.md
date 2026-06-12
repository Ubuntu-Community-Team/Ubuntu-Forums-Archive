---
title: "Failed Grub Installation"
date: 2009-04-03
forum: Installation &amp; Upgrades
---

### Post by risingsun on 2009-04-03
Hi all,

Yesterday I was trying to setup a dual boot on my system (it was actually debian rather than ubuntu but the question relates to grub) but I think I managed to fubar it. 

More a catalogue of errors really, in that I tried installing the distro to the same hard drive as windows and on first attempt to boot after installation I was presented with the message "Operating System not Detected"

Now I did actually manage to fix this by reinstalling again on a second hard disk with no OS so that grub now loaded properly if I booted from disk2. However upon trying to boot into windows on disk1 from grub, now on disk 2, I received the message "BootSector Write. Virus! Continue Y/N" Selecting No gave a grub error of 23 or 29, I cannot remember which. Now I think this message is from the Boot Sector Protection in the Bios (which I foolishly forgot I had.) and I suspect it may well be what broke the first attempt to install grub. 

However I wanted to ask whether there could actually be a virus or if some legitimate attempt to write on disk1 triggered the protection and it was a default message. I'm unfortunately a bit paranoid when it comes to these things but since the only thing that happened between this message being here and not being here was two debian installs I can't see where an attack would have originated from. Is it possible that this was just an attempt by windows to fix the mbr on disk 1 (since disabling boot sector protection for one run and booting from disk1 after loading windows once with grub first now loads straight into windows without the "operating system not found" error message as it was previously) or possibly grub doing something - i.e. something legitimate was occuring rather than a virus? I tried running a boot time scan with Avast! antivirus which I think might scan the mbr but I'm unsure of whether it scans it or not, though it did return clean.

Thanks in advance for any comments or advice. :)

---

### Post by dandnsmith on 2009-04-03
Did you include 'makeactive' as part of the grub configuration list when arranging to boot into Windows?
If so, it would cause an attempt to change the first block on that HDD (which holds boot code, partition table for that disk, and some other odd bits) - this would trigger the message.

The 'makeactive' won't be needed anyway, as the Windows partition will already be marked as active, and grub doesn't really care about it.

---

### Post by risingsun on 2009-04-03
I'd have to check when I get access to my machine at home but I hadn't touched the configuration list at the time so if it's there by default it's possible. Would it still be present or is it a one-off change? I haven't received the message since I disabled and then re-enabled the Boot Sector Protection to get Windows to boot. 

Whatever it was that was trying to write had apparently fixed the boot record on that drive though since it turned a broken boot record on the drive into one that booted straight into windows, which is why I suspected it may have been windows trying to fix the mbr on HDD1 when loaded from grub on HDD2 (if this is possible, I always thought you needed the CD) since I've heard stories of it overwriting grub installations on the same HDD in the past.

---

### Post by dandnsmith on 2009-04-03
Hmm!
Now I'm not sure.
I think that the menu.lst/grub.conf doesn't normally get changed (except by you editing it, or a fresh linux install).
The repair by Windows sounds interesting - but I don't recall reading of it (I'd expect to do it via the recovery console, as you say).
What I don't know is - will grub not bother with the 'makeactive' if it is already active (I would have thought it would, but have never tested it).

---

### Post by risingsun on 2009-04-03
It occurred to me I'd only looked at grub error 23 so far so I ahd a quick check of grub error 29 (unfortunately I couldn't remember which error it actually was.) 

Since Grub error 29 turns out to be a disk write error, is it possible grub was the program that was trying to write to the boot sector of HDD1, maybe to fix the bootable flag or the mbr record or something, since HDD had been rendered unbootable before then (or rather a bootable partition in the form of windows existed but nothing was seeing it - hence the error message "No Operating System detected")

---

