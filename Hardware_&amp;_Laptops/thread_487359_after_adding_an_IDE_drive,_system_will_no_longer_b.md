---
title: "after adding an IDE drive, system will no longer boot"
date: 2007-06-29
forum: Hardware &amp; Laptops
---

### Post by gnychis on 2007-06-29
Hey all,

I have a minimal server install of Feisty Fawn setup on a desktop computer with a total of 5 drives.  When installing, I only had two of the drives plugged in and setup a RAID-0 which was successful.  I did not want to plug the others in and risk damaging them while setting up my RAID.

So after the install, the computer booted perfectly fine and I was able to use Ubuntu.

So then I started plugging in the other drives.

The RAID-0 uses 2 SATA drives.  The remaining three drives are a single SATA, and two IDE drives.

The computer boots just fine if I plugin the third SATA drive, it renames my two RAID devices from /dev/sda and sdb to sdb and sdc ... the new SATA then becomes /dev/sda and the RAID is still detected and the machine boots flawlessly.

However when I plugin either or both of my IDE hard disks, the GRUB screen shows, and then when it tries to boot I get a blank screen with a blinking cursor and nothing happens within the 5 minutes I've waited.

If I reboot and unplug the IDE drives, all is good again.

What might cause this?  I have an IDE cd-rom drive plugged in that works just fine with the SATA drives but is on a different IDE bus.

Thanks!
George

---

### Post by geraldm on 2007-06-29
You have basically two different installs, one on IDE?, and most recently only on RAID.
The computer BIOS is apparently set to boot from IDE first.  Look into your system
and see if your BIOS has an option to boot from the RAID first, and IDE later.
That would be the easiest, IMHO.
grub should be capable of booting either, but it is easiest to use a menu in grub
and that is usually edited in.  grub can also work without a menu with its editor
but that much harder.
Good luck,
Gerald

---

### Post by gnychis on 2007-06-29
hmmm okay maybe i need to be more specific

there is only a single Linux install, and its on the RAID0 disks (two SATA)

all other disks are linux partitions, with no boot options on them at all

Heres what it looks like:

```

SATA 0 -> RAID0 disk 1 (with bootable /boot partition)
SATA 1 -> RAID0 disk 2
SATA 2 -> linux partition disk
IDE 0    -> linux partition disk
IDE 1    -> linux partition disk

```

Whenever I plugin IDE 0 or IDE 1, it *still* gets to my GRUB screen just as it does when they are not plugged in, and it is infact my Ubuntu GRUB screen... however once it passes the grub screen and tries to actually boot, i get a blank screen with a blinking cursor.

I edited the grub screen and got to the grub prompt by editing the "root (hd0,0)" line.  Using tab completion to examine the hard drives after I plugin the IDE drives, heres the change:

Without IDE:
```

hd0 = SATA 0
hd1 = SATA 1
hd2 = SATA 2

```

With IDE drives:
```

hd0 = SATA 0
hd1 = IDE 1
hd2 = IDE 2
hd3 = SATA 1
hd4 = SATA 2

```

So with the IDE drives plugged in, GRUB sees them between the two RAID hard drives.  I don't see how this would make a difference though, /dev/md0 is constructed using superblocks and neither of the other drives have a superblock on them.

The key is that root is set to (hd0,0) and is the same in both cases...

What grub displays for what I am trying to boot is:
```

root (hd0,0)
kernel /vmlinuz-2.6.20-16-generic root=/dev/md0 ro quiet splash
initrd /initrd.img-2.6.20-16-generic
quiet
savedefault

```

- George

---

### Post by geraldm on 2007-06-29
grub needs the count to be correct, that is, in the order that it
discovers them.  This means the (hdN,X) N must be the right number,
and the same disk would have a different number, depending on
how many disks are present/removed in the sequence leading up to
it.  What you installed as (hd0, ) becomes quite different with the other
disks inserted.  You are destined to find the right number!
Also, I believe you would have to pass the root= parameter as
shown in your code.

Gerald

---

### Post by IntuitiveNipple on 2007-06-29
I think the issue you've got is that you've effectively broken the RAID-0 stripe.

Using a LiveCD what report to you get with:
```
$ fdisk -ul /dev/sd0
```
Does the disk-size or  the partition boundaries exceed the end of the physical drive?

I've seen situations in the past where a RAID-0 stripe that spans 2 disks breaks a system because if the 2nd drive is moved the logical sectors of the virtual drive (/dev/md0) are looked for on the 2nd drive but aren't found.

With the complication of the RAID-0 stripe you'd be better off installing afresh with all drives plugged in.

If that isn't feasible then you'll need to boot from the LiveCD, get the 2 drives mounted via md as /dev/md0 (so you can see the logical drives you have already defined) and then 'officially' convert the logical drive(s) to physical (you will have to shrink the used space on the logical drive to fit on the first drive only).

Then you should be able to boot the system.

From there you can redefine the RAID-0 stripe and this time use the correct drive designations.

It might be possible to be sneaky and simply alter the current MD configuration from the LiveCD so it looks for the 2nd drive in the RAID-0 stripe at hd3 not hd1.
I suspect to do this you'll need to open the boot initrd image and alter the definitions in there, then rebuild the initrd image, as well as editing the settings in root.

Let us know how you get on.

---

### Post by gnychis on 2007-06-29
okay so I tried doing a fresh install with all of the drives plugged in and get the same problem, plus an additional problem

so will all of the drives plugged in, during the install here is what it looks like:

```

hd0 = IDE 1
hd1 = IDE 2
hd2 = SATA 0
hd3 = SATA 1
hd4 = SATA 2

```

The way the installer had things setup, is that all devices were recognized as /dev/sd*, even though the first two should be /dev/hd* since they are IDEs.

So I went through with the setup, and install boot on (hd2,0) which was /dev/sdc1, or the special /boot partition on the first disk of the RAID0.  All went perfectly fine, and I rebooted.

Well, once I reboot it goes back to the order I observed before when booting:
```

hd0 = SATA 0
hd1 = IDE 1
hd2 = IDE 2
hd3 = SATA 1
hd4 = SATA 2

```

So now an additional problem is introduced, though of course easy to fix... GRUB now has the root set to (hd2,0), when in fact it is on (hd0,0).  So I used 'e' to edit the line and change it to (hd0,0) and attempt to boot.  It tries, but I get the same exact result... a blank screen with a blinking cursor.

what do you suggest I try in this situation?

Thanks for the responses!

---

### Post by gnychis on 2007-06-29
one more quick piece of information... i extracted the initrd from my boot partition and the very first line of the initrd script is:

echo "Loading, please wait..."

I see this line when the IDE drives are unplugged, but do not see it when they are plugged in.  This leads me to believe that initrd is never extracting and running.

---

### Post by gnychis on 2007-06-29
ok and one more piece...

with all of the drives plugged in, if i select the recovery mode, which has the *exact* same options as my normal mode except it adds 'single' ... the system boots.  It mounts my RAID0 and everything.

However if I remove 'single', it goes to the blank screen with a flashing cursor again.

Both instances are loading the *exact* same kernel image and initrd image.

Any ideas as to why it would load with 'single' ?  All of my devices are still detected.

When i do not use 'single' i see absolutely *no* kernel output and 'quiet' and 'splash' are not specified.

---

### Post by gnychis on 2007-06-29
solved... i removed the 'savedefault' option from GRUB ... *sigh*

---

