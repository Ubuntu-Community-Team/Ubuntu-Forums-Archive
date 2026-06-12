---
title: "Booting an Ubuntu Live CD image from the hard disk with GRUB2: &quot;CDROM not ready.&quot;"
date: 2009-09-02
forum: Installation &amp; Upgrades
---

### Post by runesvend on 2009-09-02
Hi everyone.

I'm trying to boot a Live CD image of Ubuntu 8.04, which resides on a hard drive, using GRUB2.

The booting seems to go fine initially, and is only interrupted about 30 seconds into the boot process with messages saying:

```
sr0: CDROM not ready. Make sure there is a disc in the drive.
```

So it seems some program is trying to access my CDROM drive even though I'm booting from an ISO file which is on a hard disk partition.

Does anyone have any ideas as to what's going on and how to fix it?

Here's the script I've created (per the instructions here: [Grub 2 - Ubuntu Wiki]("https://wiki.ubuntu.com/Grub2")) in "/etc/grub.d/" which is called "50_bootiso" and adds a new item to the GRUB menu when I run *update-grub*:

```
echo "Adding custom 'boot from iso'-item to the GRUB boot menu" >&2
cat << EOF

menuentry "Ubuntu 8.04 iso from hard drive (ubuntu-8.04.3-desktop-i386.iso)" {
  loopback loop (hd0,3)/ubuntu-8.04.3-desktop-i386.iso
  linux    (loop)/casper/vmlinuz boot=casper isofrom=(hd0,3)/ubuntu-8.04.3-desk$

  initrd   (loop)/casper/initrd.gz
}

EOF
```

So the problem seems not to be the actual booting of the image file, but rather letting Ubuntu know that nothing is accomplished by accessing my CDROM drive, all the files are in the ISO image...

---

### Post by SumyTheSlayer on 2009-10-17
```

menuentry "Ubuntu 9.04 'Jaunty Jackalope' Live - Release i386" {
    set root=(hd0,3)
    loopback loop /ubuntu-9.04-desktop-i386.iso
    linux (loop)/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper iso-scan/filename=/ubuntu-9.04-desktop-i386.iso splash noeject noprompt --
    initrd (loop)/casper/initrd.gz
}
```

I played a bit lately with GRUB2 and I made myself a bootable USB... a NTFS partition for the iso files, and a <100MB partition for GRUB2...

try the code above, it should work for you
i also managed to get LinuxMint to work in this way, with others (debian) i'm having the same problem as you, it does not see "mounted CDROM"...

---

