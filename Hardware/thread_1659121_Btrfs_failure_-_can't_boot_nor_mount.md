---
title: "Btrfs failure - can't boot nor mount"
date: 2011-01-03
forum: Hardware
---

### Post by PauGNU on 2011-01-03
Hi all,

I'm having this problem with my computer: the main ubuntu partition is formatted on btrfs and it won't start.

When the system boots, there appear different error messages (I just copy some of them):

> BUG: unable to handle kernel NULL poiner dereference at (null)
ata3.00: error: { UNC }
end_request: I/O error, dev sda, sector 128208481
Pid: 362, comm: btrfs-endio-met Not tainted 2.6.35-23-generic #51-Ubuntu VAIO/VGN-FZ18M


The last line where it stops is:
> ---[ end trace c835da2ca4d0f753 ]---

I've been looking on the Internet to see if there is any reference to these errors (and others that also appear), but there is... nothing.

Also, if I try to mount it from a livecd, it doesn't do anything. When I enter this:
```
sudo mount /dev/sda7 /mnt
```

It just stays there... nothing happens and the system doesn't mount.
I also tried btrfsck and nothing changed. fsck does not work with btrfs filesystems.

How can I at least access to this brfs filesystem?

By the way, Windows is on the same disk and starts normally.

---

### Post by VastOne on 2011-01-03
AFAIK, Btrfs is still in heavy development...

I have tried it in the past few months and have always had the same results, it will not work...

I have decided not to try it again until it becomes the default in Ubuntu

---

### Post by dagoss on 2011-01-03
Have you tried using...

mount -o degraded -t btrfs [DEV] [MOUNT POINT]

---

### Post by puccaso on 2011-08-25
> **dagoss said:**
> Have you tried using...

mount -o degraded -t btrfs [DEV] [MOUNT POINT]


tried it,
still doesnt work

---

