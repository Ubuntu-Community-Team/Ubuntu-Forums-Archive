---
title: "NFS hangs after upgrade to Intrepid"
date: 2008-12-22
forum: Installation &amp; Upgrades
---

### Post by oldtimer_3478 on 2008-12-22
I have a remote filesystem mounted via NFS.   After upgrading to 8.10, the NFS mount hangs after periods of inactivity.   This causes an ls into the filesystem to hang, and it also causes df to hang.

The only cure is to run 'umount -f <mount_point>' a few times, then remount it.   After that it works fine for a while.

It was working fine in Hardy and previous.

Any ideas how to fix it?

---

### Post by martinkingsley on 2009-01-03
Hi

First timer so please be gentle.

I have just had similar problem, hence how I found your post.

Setup
HP Pavilion Desktop as client PC.
Old 300MHz PC running FreeNAS providing NFS shared drive.
Connected via Netgear WLAN Router.

On upgrading HP to Intrepid ripping CDs with Sound Juicer started falling over, rate of reading CD > zero and locked up, only way out forced quit. Pings to NAS box were still ok. Manually copying files in nautilus and on command line resulted in same symptoms, freeze of the application and only way out via forced quit. Even ls of the directory would cause freeze once the fault had occurred in another application, the same as your describing. Your umount suggestion seemed to recover the situation but only for reading the nfs when remounted, any attempt to write would cause same failure.

Looking in System Monitor > Processes would show the offending process with Status, Uninterruptible and Waiting Channel, rpc_wait_bit_killable. Searching on this came up with all sorts of scary discussions about kernel bugs. I could see this state occur as Sound Juicer ground to a halt.

Then I tried another client, a Dell Laptop. It worked fine!

Comparison of /etc/fstab from both computers showed that HP had wsize (or rsize, can't quite remember) set differently 16394 rather than 16384. Also checking man page for nfs seemed resonable, though not mandatory, that this should set to multiple of 1024. 

So changed fstab to 16384.
Unmounted
Remounted

and now seems to be working fine, have manually copied one or two files no problem and just finished ripping second CD.

So suggest you check rsize and wsize in fstab and make sure they are multiples of 1024.

All sounds a bit implausible, SW should be able to round down a number to 1924 without any problem but it seems to be working for me.

Hope this helps.

---

### Post by martinkingsley on 2009-01-04
Hi again

Seems Yesterdays experience was a red herring, it seemed too good to be true. Worked fine for the rest of the day however when restarted both FreeNAS server and Ubuntu client today the same problem resulted.

So anyone else got any ideas?

How to investigate further?

Is there enough evidence here to raise a bug report?

M.

---

### Post by gggg123 on 2012-01-22
May I kindly point out that it is posixly correct behaviour that the machine hangs. See
 
[https://bugzilla.kernel.org/show_bug.cgi?id=42626](https://bugzilla.kernel.org/show_bug.cgi?id=42626)
 
Posix defines that any process reading a stat() call of a file within nfs written to hangs until the write is completed.
So if your system hangs for half an hour because it waits for the nfs write to be completed - that's defined to be correct.

---

### Post by oldos2er on 2012-01-22
Closed, necromancy.

---

