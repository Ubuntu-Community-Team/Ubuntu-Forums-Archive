---
title: "Internal 5.25 inch floppy drive isn't working"
date: 2009-11-11
forum: Hardware
---

### Post by compucon on 2009-11-11
I have an internal 5.25 inch floppy drive. all it does is sithere with the red light on and spinning, when i try to format a disk, it says it can't access the drive, i tried logging in as root and changing permissions, but it won't let me, here are the permissions: -r-r-r- Any way, how can i make the thing work!

---

### Post by finwake on 2010-01-26
Wish I could help... at least yours is spinning.

My issue.  Installed an ancient 5.25 from an IBM PCjr.  Can't get it even to spin.  command floppycontroller sees it and speaks about the drive, the 'Computer' menu shows its there, but will not mount.  no spinning of this drive...

someone help us retro-folk.

edit:  one troubling issue:  my mobo BIOS only mentions 3.5 floppy, no mention of changing floppy type nor a Drive B...  that said, and as above Ubuntu "sees" the drive...

---

### Post by mhampson on 2010-03-24
Try:

sudo nautilus

---

### Post by srs5694 on 2010-03-24
A few thoughts:


[list]
[*]Can you access the drive in another OS? For instance, can you use it to boot a DOS floppy, or once you've booted a DOS floppy from another (3.5-inch) drive? If so, you at least know that it's connected correctly and the hardware is working.
[*]Further to the previous point, floppy disks can be connected improperly. When this happens, they can spin continuously or not at all, or sit there with their LEDs lit but do nothing. I even once burned out a 3.5-inch floppy by connecting its power cable upside-down, although 5.25-inch models use more idiot-proof power connectors than the 3.5-inch models.
[*]Some versions of devkit-disks cause floppy disks to spin or seek continuously. Because of this and other problems with that package, I completely removed it on a couple of systems (one Ubuntu, one Fedora). This wasn't easy, since devkit-disks is required by several other tools, but I managed to coerce the systems to work without it. I'm sure some disk-detection functions aren't working as a result, but I don't care, since I dislike those functions anyhow. There may be less radical fixes. If this is the problem, the disk drive should still work properly when you insert a disk; it'll just spin and/or seek needlessly, putting unnecessary wear on the disk and drive mechanism.
[/list]

---

