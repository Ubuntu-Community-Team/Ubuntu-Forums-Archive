---
title: "How do I get SATA to hotswap / automount?"
date: 2010-02-20
forum: Hardware
---

### Post by toddk111 on 2010-02-20
I am running Ubuntu64 and I have a SATA hotswap tray.  Currently, the only way my system recognizes a new SATA drive in the hotswap tray is when I reboot.  I'm able to remove the drive after unmounting it but I'd like Ubuntu to detect when I've put a new drive in the tray and automount it (like it does when I plug in an external USB drive) without having to reboot.  Would someone please tell me how to set this up?

Thanks,
Todd

---

### Post by Morbius1 on 2010-02-20
1st: I have no idea
2nd: I really have no idea

I did a general search on google for hot swap sata drives and the darn thing pointed me right back to this forum:
[http://ubuntuforums.org/showthread.php?t=907124](http://ubuntuforums.org/showthread.php?t=907124)

Involves using the package **scsiadd. **Might be worth investigating.

---

### Post by toddk111 on 2010-02-21
Thanks for the reply.  I tried using scsiadd but it doesn't help.  It seems like this should be something simple that should have been resolved long ago.  I mean drives that are supposedly "hot swapable" should just work that way.  I don't mind having to do some initial configuring but I don't want to open a terminal every time I swap out a drive.  It's just frustrating because it seems like it should be able to be configured to work like an external USB drive works (fast and easy plug and play).

If anyone has any ideas, it would be greatly appreciated.
Thanks,
Todd

---

### Post by falconindy on 2010-02-21
What, if anything, is printed to to your system logs when a drive is removed and reattached? Do this:
```
sudo tail -f /var/log/messages
```
And then unplug/plug in a drive. This smells like a udev rule waiting to be written.

Also, what's the output of:
```
zgrep -i hotplug /proc/config.gz
```

---

### Post by toddk111 on 2010-02-21
> **falconindy said:**
> What, if anything, is printed to to your system logs when a drive is removed and reattached? Do this:
```
sudo tail -f /var/log/messages
```
And then unplug/plug in a drive. This smells like a udev rule waiting to be written.

I did this command and then unmounted the drive and unplugged the drive and then plugged it back in but nothing happens in the log file you asked me to tail.

> **falconindy said:**
> Also, what's the output of:
```
zgrep -i hotplug /proc/config.gz
```

Here is what I get:
```
gzip: /proc/config.gz: No such file or directory

```

Any other ideas would be appreciated.  Thanks for the help so far!
-Todd

---

### Post by falconindy on 2010-02-21
Without being able to see the kernel config, I would have to guess that the stock Ubuntu kernel isn't supporting SATA hotplug. You might be in for a recompile.

---

### Post by taurolyon on 2010-02-21
Try running your SATA in ACHI mode. Check your BIOS settings to see if this is possible.

More info: [http://en.wikipedia.org/wiki/Ahci](http://en.wikipedia.org/wiki/Ahci)
> AHCI is separate from the SATA 3Gb/s standard, although it exposes  SATA's advanced capabilities (such as [hot-plugging]("http://en.wikipedia.org/wiki/Hot-plugging") and [native command queuing]("http://en.wikipedia.org/wiki/Native_Command_Queuing")) such that host systems can  utilize them.

---

### Post by toddk111 on 2010-02-22
> **taurolyon said:**
> Try running your SATA in ACHI mode. Check your BIOS settings to see if this is possible.

More info: [http://en.wikipedia.org/wiki/Ahci](http://en.wikipedia.org/wiki/Ahci)

Thanks for the suggestion but I don't have that setting in my BIOS.  I'd really appreciate any other ideas.

---

### Post by exup1000 on 2010-02-24
Hi

many thanks "taurolyon" that suggestion about enabling ACHI has fixed it for me, no need to even have SCSIADD either, UBUNTU detects the drive being added or removed. Nautilus and Places both see it without the need to refresh anything.

Its also had the added benifit of speeding up the GRUB loader and general POSTing of the computer. Plus's all round!

Sadly for "toddk111" that is of no help for you as you state ACHI is not supported.

Cheers all.

---

### Post by taurolyon on 2010-02-26
@exup1000

You are most welcome!

---

### Post by boblogic on 2010-02-27
My motherboard did not support AHCI so I wrote a BASH shell script to do the the job.
I'll post it as an example. You need to have the "sg3_utils" package installed.
I'll include the logging module, and the desktop entry.
/usr/local/bin is probably the best place for it.
It's menu driven and runs in a teminal.
It spins the drive down before removal. Important feature !
Also remove the .txt extesion from the file name.
Set permissions with "chmod 755" on sata_ctl2.sh.

---

### Post by boblogic on 2010-02-27
Oh yeah, I for got to say: "No Warranty Is Implied. Use at your own risk !. Make sure your chipset supports hotswap. Promise chips usually do, VIA, probably not.
Here is the best info I have:
[http://ata.wiki.kernel.org/index.php/Hardware,_driver_status](http://ata.wiki.kernel.org/index.php/Hardware,_driver_status)

---

