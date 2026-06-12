---
title: "ThinkPad T60p and hotswap ultrabay"
date: 2007-02-27
forum: Hardware &amp; Laptops
---

### Post by tperica on 2007-02-27
Hi to all.
How can I use my Ultrabay 2nd HDD adapter?
I tried with hotswap but seems that it's not working. PATA, HDD - IBM part, Fujitsu Model-MHV2100AH

Couple days ago I completely switch from Win XP to Ubuntu Linux 6.10
I was sys admin for Win platform around 10y. No more Wins on my HDD! Problem is, I need to do a lot of configs to have everything up and running. Don't want to loose good vibe! he he

[SIZE="3"][FONT="Arial"]
tomislavp@propaganda:~$ hotswap
I/O warning : failed to load external entity "/etc/hotswaprc"
hotswap 0.4.0
Copyright 2001 Tim Stadelmann
This program is free software, licensed under the conditions of the
GNU General Public License version 2, or (at your option), any later
version.

There is currently no IDE device configured.  (Floppy disk drives,
batteries, and 'travel modules' are not managed by this utility.  If
you want to swap such a module, you should remove it now.)

Would you like to insert an IDE device into the module bay? y
Please insert the new device into the module bay and press RETURN.

hotswap: opening IDE device failed: No such file or directory[SIZE="2"][/SIZE][/FONT][/SIZE]g

---

### Post by scoot1212 on 2007-02-28
I am looking to do the same.  I recently installed 7.04 herd 4 (i believe).  If I have my 2nd hdd in and I go to Places:Computer, I'll see my 2 partitions on that drive and when I click either partition it asks for the admin password and will mount it.  Can you see if that functionality is in 6.10?  I am going to revert back to 6.10.  VMware is to damn slow under 7.04, under 6.10 it flies.
Good luck,
Scott

---

### Post by tperica on 2007-03-01
To switch to Linux? Well definitely i am not going back! I have VMware too and i am planning to use it for ASP development. That's the only thing I am missing.

Well, no, actually I can not see my 2nd HDD(Ultrabay) at all. Tried to do search via Google, but can't find anything.

Thanks Scott, will let you know if i find anything.


cheers
tomislav

---

### Post by scoot1212 on 2007-03-01
I've been a windows sys admin for about 9 years and I'm toying with the idea of ditching windows and going to linux admin.  I use ubuntu as my host for vmware and pretty much everything else.  I use XP rarely.  I just upgraded 7.04 to 2.6.20-9 and vmware is much much faster.  good luck.
Scott

---

### Post by redebord on 2007-03-20
Hey folks...
Just made the switch to Ubuntu 6.10 this last weekend on my T40 thinkpad.  Having the same trouble getting the 2nd HDD in the ultrabay to be recognized.  Have searched around the net and not found anything conclusive on how to address this.  Have either of you found a fix for this yet?  Thanks in advance,

redebord

---

### Post by tperica on 2007-03-21
Not really, but i fond something that could be helpful. Since i am newbie, it's too difficult at the moment.

[http://www.thinkwiki.org/wiki/How_to_hotswap_UltraBay_devices](http://www.thinkwiki.org/wiki/How_to_hotswap_UltraBay_devices)
[http://forum.thinkpads.com/viewtopic.php?t=9944&highlight=hotswap](http://forum.thinkpads.com/viewtopic.php?t=9944&highlight=hotswap)

As soon i will have more info i will post something

cheers
tomislav

---

### Post by armalite on 2007-03-26
I don't have a ThinkPad, instead I have a Fujitsu Siemens Lifebook C, which has a similar bay, like the one found in ThinkPad. The only difference is that i can't use ibm_acpi kernel module.

I just upgraded from Edgy to Feisty. In Edgy, using hotswap and gnome-hotswap-applet i was able to do eject the cd-rom drive and swap the 2nd battery in without problems at all.

In Feisty, like Tperica already said here above, hotswap stopped working. I read through the links provided and I think it's because from Feisty (better: starting from some kernels between Edgy and Feisty) ata_piix is loaded instead ide-disk. Hotswap package is written for ide-disk module, i think, hence the error.

Anyway there's a good news in that: ata_piix doesn't freeze my pc if I eject the cd-rom drive (in edgy hard freeze happened when doing that, see [http://www.ubuntuforums.org/showthread.php?t=252564](http://www.ubuntuforums.org/showthread.php?t=252564)). It only doesn't reload the drive as soon as it is reinserted in bay, and i have to call:

```
# echo 0 0 0 >  /sys/class/scsi_host/host1/scan
```

to let system rescan the ide bus and recognize the cd-rom drive.

I just miss a little gnome applet doing that with some easy clicks...

EDIT: Just found out that what in edgy was /dev/hda & /dev/hdc (1st hard disk and cd-rom bay), now is /dev/sda and /dev/scd0. And no, they aren't Sata, just plain old Pata on ICH4 chipset. After tweaking 2 symlinks hda/hdc to sda/scd0, i got a step further and hotswap now recognizes the cd-rom drive. But can't unregister the IDE device complaining that "ioctl isn't correct for this device", or something like that (just translated from localized stderr).

---

### Post by vazzeroni on 2007-05-27
I'm sure you could add that line to the ACPI script that gets called when you dock... I'm going to figure this out later today, I hope. This way it would happen automatically without you having to do anything at all.

---

### Post by armalite on 2007-06-11
I used acpi_listen but didn't saw anything.

Can you please give me some hints in how to look for such acpi event? Dmesg and /var/log/messages shows nothing about the drive being reinserted in the bay.

---

