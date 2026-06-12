---
title: "mdadm volumes not persistent after reboot"
date: 2008-10-22
forum: General Help
---

### Post by Cr0n_J0b on 2008-10-22
Hey everyone.  I'm working through a particularly distressing issue.  I have several RAID volumes that are loaded on my system.  I set them all up using the mdadm --Assemble command.  They all work fine while the system is running, but after a reboot they are no longer showing up.  I have to re-assemble them each time.  I know on my other systems that these volumes should stay together after a reboot, but for some reason they aren't.  I don't have a raidtab file or any volume configuration files, but i never needed those in the past.

Any help would be appreciated.

thanks

I HAVE SOLVED THIS.  SEE THE LAST POST.  THANKS FOR THE HELP

---

### Post by fjgaude on 2008-10-22
I think you have mdadm, not the old raidtab tools. They left us many years ago.

You might have a race issue, with the md in the kernel not being ready to auto assemble the arrays during the boot time. You might try putting a delay to lag:

```
/usr/share/initramfs-tools/init   # to stop a race condition with md
   157 maybe_break **mount**
   158 sleep 5
   159 log_begin_msg "Mounting root file system..."
```

```
sudo /usr/sbin/update-initramfs -uk all    # run to rebuild the image
```

I have no idea how large your arrays are. Maybe the "5" second delay can be either increased or decreased dependning upon how much time is needed. Also the edit line numbers may be off, depending on your Ubuntu version.

On the other hand, this might not be your problem. What version of the kernel are you using?

---

### Post by Cr0n_J0b on 2008-10-22
thanks for the response.  i'm on the lastest version of the kernel and I am using mdadm not raidtools.  The strange thing is that this used to work fine.  I set it up on my last server and everything was great, but moving to the new server and newer version of ubuntu 8.04...it's gotten odd.  I have another server with a similar config that works fine.

---

### Post by Cr0n_J0b on 2008-10-24
Well, I think I now know what the problem is...I just don't know how to fix it.

Evidently, when I reboot my system, the device IDs get switched around.  I have 11 SATA drives attached to the system and for some reason everytime I boot the drive devices get swapped around.  has anyone seen this?  Is there something I can do about it?

thanks

---

### Post by fjgaude on 2008-10-24
Well, **mdadm** doesn't use device names to assemble arrays, but uses the UUID that it put on each drive at array creation time. Each array and its associated drives have the same UUID and this UUID has nothing to do with the UUIDs that the system creates to mount a drive. So...

I know of nothing that stops the BIOS or Linux from moving names and drives around. The UUID system setup some years ago fixed any boot problem that might and has occurred with drives being named differently each time a change occurred in the drive allocation. I hope I'm clear with this.

I can't think of anything to suggest for your issue.

---

### Post by PreviousN on 2008-10-25
I have this same problem. In the past I had to run

sudo modprobe md
sudo mdadm --assemble --scan
sudo mount -a

I added md to my /etc/modules file, and theoretically everything should be hunky dory. But it isn't. I ALWAYS have to run mdadm --assemble --scan. 

I added the sleep 5 to my initram and rebuilt it. I'll update with whether or not that fixed the problem (doubtfully).

Either way, I'd like to hear if this ever gets resolved. KTHXBYE

---

### Post by fjgaude on 2008-10-25
I'm sure you two have a line in your /etc/fstab files that mount the arrays, eh?

---

### Post by Cr0n_J0b on 2008-11-02
SOLVED:

Thanks for all the help on this one.  I finally found the solution after much configuration and reconfiguration.

The issue here is that I rebuilt my server which changes the "homehost" variable or something.  The Arrays will not automatically rebuild unless this is reset.

to fix, just stop your array or reboot and then build them with these options.  You won't lose any data and the arrays will now come back up on reboot.

mdadm -A <md-device> <components> --homehost=<somestring> --update=homehost

here is the reference link:

[http://marc.info/?l=linux-raid&m=122425704627176&w=2]("http://marc.info/?l=linux-raid&m=122425704627176&w=2")

Thanks go to Daniel for his help to another user on the linux-raid lists.

---

### Post by fjgaude on 2008-11-03
I'll have to remember this as I move arrays from one machine to another which have different names. Thanks for the heads-up.

---

