---
title: "Backport util-linux from 23.04 to 22.04?"
date: 2023-06-21
forum: Hardware
---

### Post by luckyknight on 2023-06-21
[COLOR=#1F2328][FONT=-apple-system]I am running Ubuntu 23.04 (amd64) on my laptop and have formatted a disk using ext4. The version of fsck in Ubuntu 23.04 is from util-linux 2.38.1

I have then plugged this disk into a different box that is running Ubuntu 22.04 (arm64) on a Orange PI 5B.

When I try to mount the disk automatically on my Orange Pi 5B using /etc/fstab I get the following error:[/FONT][/COLOR]
[COLOR=#1F2328][FONT=-apple-system]/dev/xxx has unsupported feature(s): FEATURE_C12
[/FONT][/COLOR]
[COLOR=#1F2328][FONT=-apple-system]Could fsck tools be backported to 22.04? e.g. in jammy-backports?[/FONT][/COLOR]
[COLOR=#1F2328][FONT=-apple-system]The version included in 22.04 is fsck from util-linux 2.37.2

I  could wipe the disk and reformat, but I've already transferred all my backups to it.[/FONT][/COLOR]

---

### Post by ian-weisser on 2023-06-22
> **luckyknight said:**
> [COLOR=#1F2328][FONT=-apple-system]Could fsck tools be backported to 22.04? e.g. in jammy-backports?[/FONT][/COLOR]

Well, that seems to assume a solution without actually looking for the bug first. It might work, or it might not, or it might make the bug more complex.

Usually it's better to clearly identify and then fix the actual bug.

Try seeing if the bug has been reported in Launchpad. Also do a bit of experimenting -- see if there is an easier way to expose the bug. Add that to the bug report (if any). If the bug has not been reported yet, then please do so.

---

### Post by luckyknight on 2023-07-03
Created a bug here:
[https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/2025176](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/2025176)

---

### Post by Holger_Gehrke on 2023-07-03
As a workaround you could take a look at the file system features activated for that file system with 'tune2fs -l /dev/xxx' on both systems and then deactivating the feature that the newer system understands but the older one doesn't using 'tune2fs -O ^feature_name /dev/xxx'. In a [bug-report for NixOS]("https://github.com/NixOS/nixpkgs/issues/229450") FEATURE_C12 turned out to be 'orphan_file', but that was with e2fsck 1.46.6 and 1.47.0, Ubuntu 22.04 uses 1.46.5 AFAIK and I don't know what 23.04 uses.

Holger

---

### Post by luckyknight on 2023-07-17
Thanks for the workaround! I had another go at this, and simply upgraded e2fsprogs from lunar

[COLOR=#000000][FONT=&quot]wget [http://ftp.de.debian.org/debian/pool/main/e/e2fsprogs/e2fsprogs_1.47.0-2_arm64.deb](http://ftp.de.debian.org/debian/pool/main/e/e2fsprogs/e2fsprogs_1.47.0-2_arm64.deb)[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]wget [http://ftp.de.debian.org/debian/pool/main/e/e2fsprogs/libext2fs2_1.47.0-2_arm64.deb](http://ftp.de.debian.org/debian/pool/main/e/e2fsprogs/libext2fs2_1.47.0-2_arm64.deb)
[/FONT][/COLOR]
Installed those and it's working now from /etc/fstab

---

