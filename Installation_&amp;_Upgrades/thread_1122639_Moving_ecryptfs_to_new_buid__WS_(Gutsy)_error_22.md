---
title: "Moving ecryptfs to new buid / WS (Gutsy) error 22"
date: 2009-04-11
forum: Installation &amp; Upgrades
---

### Post by craigtyson on 2009-04-11
OK I have been going mad for the last few days trying to get a Private directory to mount after a rebuild of my laptop.

What I was getting when trying to mount the directory was this:-


Unable to get the version number of the kernel
module. Please make sure that you have the eCryptfs
kernel module loaded, you have sysfs mounted, and
the sysfs mount point is in /etc/mtab. This is
necessary so that the mount helper knows which
kernel options are supported.

Make sure that your system is set up to auto-load
your filesystem kernel module on mount.

Enabling pass phrase-mode only for now.

Then error 22 [-22] when continued and no decrypted mount.

The solution.

1. Do an update of everything

sudo apt-get update

2. Install ecryptfs-tools

sudo apt-get install ecryptfs-tools

3. Load the ecryptfs module

sudo modprobe -v ecryptfs

4. mount your Private directory

sudo mount -t ecryptfs ~/Private ~/Private

5. Select Pass phrase

6. input your pass phrase (has to be the correct one you used in the old system)

7. sleect encryption type that you used before

8. no no pass through (unless you want to)

9. Read the warning but type "yes" you want to mount

10. Would you like to avoid this in the future type "yes"

That's it folks.

C

---

### Post by craigtyson on 2009-05-10
OK Big warning.  If like many who were running Gutsy until the support finished at the new release, then

MAKE SURE YOU COPY EVERYTHING OUT OF YOUR ENCRYPTED AREA (UNENCRYPTED) BEFORE YOU UPGRADE.

The newer versions of ecryptfs have a bug fix which means that you will not be able to mount your old encrypted area.

would have been nice if that one was in the upgrade notes hu.

C

---

