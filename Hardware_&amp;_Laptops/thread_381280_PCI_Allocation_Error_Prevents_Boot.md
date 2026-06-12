---
title: "PCI Allocation Error Prevents Boot"
date: 2007-03-10
forum: Hardware &amp; Laptops
---

### Post by k4zzy on 2007-03-10
Hello.

I've just installed ubuntu-server on my Dell PowerEdge 2300, and I'm having a problem when booting up into the new install.

The install went well, as far as I can tell. I have two partitions (ext3 mounted on "/", boot flag on; and swap, boot flag off). I'm using software RAID 0 on 6 drives (5 active, 1 spare). When I startup the machine, I get the following message:

```
Starting up ...
[42949376.670000] PCI: Cannot allocate resource region 4 of device 0000:00:07.1
```

The startup hangs after this. The only indication of any activity is an apparent read cycle of all the 6 disk drives. The hard drive activity LEDs are visible on the front of the machine, and each one flashes for a second (from #0-5, in that order).

I've tried a few different boot options from the install CD (ie, acpi=off, noapic, etc), and it doesn't seem to make a difference. I've searched for some solutions, and the only thing I can find is something about a conflict with an internal graphics card (which this machine has). They say to turn it off in the BIOS of the machine, but I can't find any options for that.

If anybody has some suggestions or can point me to a solution, I'd be most grateful.

Thanks,
Brandon

---

### Post by k4zzy on 2007-03-10
It looks like device 00:07.1 is:

IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)

Hope that helps. :)

---

### Post by k4zzy on 2007-03-13
No suggestions so far? I would really like to get this working. Here's some more information that might be relevant.

I had ubuntu-server running on this machine before I went through with a clean install, and I vaguely remember this error popping up as well, before the boot process continued. If I remember correctly, then that would probably point to a boot error that isn't necessarily related to this PCI error. Is there a possibility grub didn't get installed, or something along those lines?

---

### Post by Thisbetom on 2007-04-09
bump?  Same problem...

---

### Post by Delstrego on 2007-09-22
I'm having a very similar problem. I've tried booting from the 7.04 live cd and it just flashes a very similar message (unable to allocate PCI memory) and then boots into busybox. I tried using the non-live cd installer from the download page and got it installed but when I try to boot it just flashes the message again, too fast to read, and then the screen goes black, doesn't even go into busybox. I tried installing Debian too, and got it to partially work but X didn't work. Anyone have any ideas? I'd really like to switch to Ubuntu.

---

### Post by dcstar on 2007-09-22
> **k4zzy said:**
> 
..........
I've tried a few different boot options from the install CD (ie, acpi=off, noapic, etc), and it doesn't seem to make a difference. I've searched for some solutions, and the only thing I can find is something about a conflict with an internal graphics card (which this machine has). They say to turn it off in the BIOS of the machine, but I can't find any options for that.
.........

You may have to install another video card to get the option to disable the internal card - or the BIOS has an "Advanced" mode you have to use to do such things.

---

