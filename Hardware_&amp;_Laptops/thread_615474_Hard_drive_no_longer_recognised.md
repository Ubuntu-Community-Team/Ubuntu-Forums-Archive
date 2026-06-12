---
title: "Hard drive no longer recognised"
date: 2007-11-17
forum: Hardware &amp; Laptops
---

### Post by mattheweast on 2007-11-17
Hi,

I have a Thinkpad T43 laptop ([https://wiki.ubuntu.com/LaptopTestingTeam/ThinkpadT43-1871](https://wiki.ubuntu.com/LaptopTestingTeam/ThinkpadT43-1871)) which I recently sent back to IBM to be repaired. The hard drive was acting funny (sometimes it would boot normally, and sometimes it would show "operating system not found"), and the screen had stopped working.

I just got it back and everything appears to work - Windows has been restored on the hard drive and everything boots normally. I don't have details of what repairs were done, except that they did a BIOS update too.

Now, Ubuntu doesn't detect my hard disk - I've tried both 7.04 and 7.10 (both of which I had run on the laptop before it broke) and the live CD runs beautifully but the installer's partitioner doesn't detect any hard drive. Neither does gparted, and /dev/hda and /dev/sd* don't exist.

I can't attach the output of dmesg because the forum software says it is too large. So I've uploaded it here: [http://mdke.org/tmp/dmesg2.txt](http://mdke.org/tmp/dmesg2.txt).

The error appears to be:
> 
[   16.044000] ata1: device not ready (errno=-16), forcing hardreset


Anyone have any idea what's going on? I doubt this is a hardware issue given that Windows boots regularly. Could the BIOS update have caused a problem? AFAIK this is a common laptop and a common hard disk.

UPDATE: the problem doesn't appear to be 100% reproducible: out of 5 boots or so, I've discovered that on one occasion, /dev/sda was present. The dmesg from the successful boot is at [http://mdke.org/tmp/dmesg.txt](http://mdke.org/tmp/dmesg.txt).

---

### Post by Akre on 2007-11-17
I'll be suprised if this is the same problem I've got with toshiba g20 recently. And beacouse dmesg says that ata_piix takes care (at least i think so) of your drive this could be your problem.

Try this
in boot choice: choose f6 and append to kernel options line:

Code:

```
break=mount
```

remove splash and quiet.

Computer will boot to initramfs, then:
Code:

```
rmmod ata_piix
rmmod ahci
modprobe ahci
modprobe ata_piix
exit
```

If this sees harddrives then I've got solutions outlined in g20 thread.
anyway: ahci is a correct module to serve your hdd. This could be diffrent for your machine.

EDIT: if this is not reproductible this is another reason to belive this is the same problem. That was case in toshiba g20 laptop as well. Machine will boot okay in about 5% chances

---

### Post by ubuntu_demon on 2007-11-17
If it's indeed ata_piix then here's some information.

Try blacklising ata_piix as a kernel boot option. You have to add "ata_piix.blacklist=yes" without the quotes.

You can also remove "quit splash" from your kernel boot options if you want to easily see all information flying by.

If blacklisting of ata_piix works you can make it permanent by adding it to your /etc/modprobe.d/blacklist :
$ sudo gedit /etc/modprobe.d/blacklist

I learned about this kernel boot option here (you can also do it in the installer) :
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/120316/comments/7](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/120316/comments/7)

---

### Post by ubuntu_demon on 2007-11-17
You can also try this [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/120316/comments/6](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/120316/comments/6)

But instead of pressing F6 you need to edit the kernel boot option during boot by pressing "e" in grub.

I'm guessing that you are experiencing a bug related to :
[https://bugs.launchpad.net/ubuntu-jeos/+bug/163113](https://bugs.launchpad.net/ubuntu-jeos/+bug/163113)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/33269](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/33269)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/120316](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/120316)
[https://bugs.launchpad.net/ubuntu/+bug/163140](https://bugs.launchpad.net/ubuntu/+bug/163140)

---

### Post by mattheweast on 2007-11-17
Thanks for these replies.

Akre - those commands from initramfs didn't work, I received the same errors.

Ubuntu_demon - I'll try the blacklist, but it doesn't seem right to me, since that is the module I was using with 7.10 before I sent the laptop to be repaired... Those bugs seem different to my problem: they have different error messages.

I had a reply on my blog here - [http://www.mdke.org/?p=93#comment-3955](http://www.mdke.org/?p=93#comment-3955) - if that helps people diagnose what the problem might be. Unfortunately I didn't have that config option in my BIOS so I couldn't amend it.

---

### Post by mattheweast on 2007-11-17
The ata_piix.blacklist=yes boot option didn't work - same error and the module appears to have loaded anyway...

---

### Post by joey on 2007-11-17
Matt,

Head into your bios settings and attempt to locate the ICH8 controller entry under the disks section.  Put it into ACHI mode. Save and reboot and try the install again.

Joey

---

### Post by mattheweast on 2007-11-17
Joey,

Thanks for the reply, but as per the blog post linked above, I don't have those BIOS settings...

Still no resolution so far.

---

### Post by kleeman on 2007-11-17
Not related to this issue at all is it?

[http://www.thinkwiki.org/wiki/Problem_with_non-ThinkPad_hard_disks](http://www.thinkwiki.org/wiki/Problem_with_non-ThinkPad_hard_disks)

You could presumably find out what the exact make of the hard drive is through windows.

Failing this I would start investigating passing options to the sata module which controls the hard drive (ata_piix perhaps?)
Windows may be more forgiving of suspect hardware in this case.

---

### Post by mattheweast on 2007-11-17
Hi Kleeman,

I don't think it's related: the hard disk seems to be the same model as the original laptop had. I think it's probably the same disk.

---

### Post by quidpro on 2007-11-17
Windows XP? Vista? You might go in and make sure that the System Restore feature is off. Especially with Vista. I don't know if XP does the same thing, but it's worth a try as well. Is there some software maybe from IBM that takes care of backups to a hidden partition?  I'd check that too.

---

### Post by mattheweast on 2007-11-18
It's Windows XP. There is a hidden partition with rescue things on it. I don't think these can be causing the problem, because:

1. Both were the same when I used Ubuntu previously and didn't cause a problem.
2. They are just partitions, and Ubuntu isn't recognising the disk at all.

thanks again for the reply though.

---

### Post by az on 2007-11-18
> **mattheweast said:**
> 
Anyone have any idea what's going on? I doubt this is a hardware issue given that Windows boots regularly. Could the BIOS update have caused a problem? AFAIK this is a common laptop and a common hard disk.

UPDATE: the problem doesn't appear to be 100% reproducible: out of 5 boots or so, I've discovered that on one occasion, /dev/sda was present. The dmesg from the successful boot is at [http://mdke.org/tmp/dmesg.txt](http://mdke.org/tmp/dmesg.txt).

Do you happen to have a windows installation disk?  I wonder if you boot from it, would it be able to reliably detect your disk at the partitioning phase?  Until you select a partition onto which to install windows, it will not touch your disk, so you are safe to try this a few times.

Also, it is an option to revert your BIOS back?

---

### Post by ubuntu_demon on 2007-11-19
Did you try modprobing ide-generic real early in the following way ?
[https://bugs.launchpad.net/ubuntu-jeos/+bug/163113/comments/10](https://bugs.launchpad.net/ubuntu-jeos/+bug/163113/comments/10)

---

### Post by joey on 2008-03-20
One of the things you could try if you still have this problem is grabbing a low level format utility and wiping the disk.

---

