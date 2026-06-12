---
title: "How to AUTOMATICALLY get User Permissions on Hard Drive in eSATA &amp; USB Dock when on??"
date: 2009-06-05
forum: Hardware
---

### Post by OzzyFrank on 2009-06-05
Hi. I just connected a hard drive via one of those USB/eSATA docks that have the drive standing on end, and it would not even let me mount it, let alone create and delete files. This was using the [COLOR="#0000ff"]**eSATA**[/COLOR] cable, which I think makes a difference (since I have dealt with USB hard drives before, and they at least mount when clicked on, even if I've had to tinker to get full permissions after that).

I happened to be in Windows for once when I thought I'd try my new dock and no surprise it did not even detect the drive had been connected when I used the eSATA connection (thought I may as well use the faster connection since my motherboard has an eSATA port, and was curious to see if Windows XP picked it up). When I connected it via USB, all was fine, and though I haven't tried that in Ubuntu, I guess there won't be much of an issue there. Anyway, once I had booted into Ubuntu I was keen to see if the hard drive via eSATA would be picked up in Nautilus, and no surprise that in Ubuntu it was.

Anyway, since I previously had that drive in a caddy and had it mounting at boot, and since I had also given it an **fstab** entry using its **uuid**, I did a quick **[COLOR="Indigo"]sudo mount -a[/COLOR]** in a terminal and it was mounted fine. But it begs a few questions, being:

**[COLOR="DarkRed"]1) How do I get it to mount automatically when turned on (ie: plugged into the dock) without having to use the terminal to mount it?[/COLOR]** By "mount automatically" I mean to say that would be preferable, but even just being able to mount it by clicking on it in the Places menu would be fine. This can be using fstab entries, since the next question covers other people, especially newbies.

[COLOR="Purple"]**2) How can people who have not added their drive to fstab (like newbs who just expect to be able to plug in a drive in a similar dock and be able to use it) do the same?**[/COLOR] I have the benefit of knowing about **fstab** and the use of **uuids**, not to mention how to **mount** drives via commands (and how to have made a **mount point** for it), but those new to Linux wouldn't.

**[COLOR="Blue"]3) How do I or anybody else _unmount_ the drive without resorting to the terminal?[/COLOR]** Not surprisingly, I don't have permission to unmount the drive via the eject button in Nautilus, which is kind of a pain, and more so for newbies wanting to swap drives (or just try out the USB connection, like I wanted to). Actually, make that "surprisingly", as I just realised that when I had that drive in the caddy and mounting at boot via fstab, I could in fact unmount it via the eject button! [Hopefully an answer to the first two questions means this is not even an issue]

Thanks in advance...

---

### Post by OzzyFrank on 2009-06-22
Any ideas?

---

### Post by GabFromDenver on 2009-06-25
I'd try the option "user" in your fstab (4th field), This would allow the user who mounted the partition to umount it as well.

---

### Post by OzzyFrank on 2009-07-02
> **GabFromDenver said:**
> I'd try the option "user" in your fstab (4th field), This would allow the user who mounted the partition to umount it as well.

What would be the correct syntax/usage of this? I assume one would remove ***defaults***, so what should be added along with ***user***? Does ***rw*** need to be added to allow read-write, or is ***user*** enough for this? Any additional info would be welcome. Cheers

---

