---
title: "My floppy is flopping"
date: 2006-07-08
forum: Hardware &amp; Laptops
---

### Post by delta_charlie on 2006-07-08
Hi all, I just installed Ubuntu onto a new computer that was bought with no OS. Lot's of stuff is working but not the floppy drive.

I can boot an old Linux boot floppy so this makes me think the drive and BIOS are talking to each other ok.

If I try to Use Nautilus 2.14.1 and double click on Floppy I get:
Unable to mount the selected floppy drive.

Next I tried a terminal window and:
sudo -i mount -t msdos/dev/fd0 /mnt

This produces the error: /bin/mount: Cannot execute binary file.

I did find mount in the bin director but it was highlighted in a dark color. Don't know what that means.

Any ideas?

Thanks, DC

---

### Post by wpshooter on 2006-07-08
Sounds like you may be installing an older version of Ubuntu.

Is this Breezy or Dapper ?

---

### Post by delta_charlie on 2006-07-08
> ** said:**
> Sounds like you may be installing an older version of Ubuntu.

Is this Breezy or Dapper ?

Hi, I installed this: ubuntu-6.06-alternate-amd64.iso

The computer has a Sempron 2600 AMD 64 CPU so I thought it best to use the amd64 .iso It installed the generic amd64 Kernel.

I'm going to switch back to the Linux box and check the file permissions on mount. I need to get the floppy working so I can try to get the modem working. I need some files from this computer to try and get the modem working. I have two computers but only one monitor so the floppy would also help for moving how-to and other info files.

Thanks, DC

---

