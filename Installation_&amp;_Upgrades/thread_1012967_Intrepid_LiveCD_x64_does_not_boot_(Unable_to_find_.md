---
title: "Intrepid LiveCD x64 does not boot (Unable to find live filesystem)"
date: 2008-12-16
forum: Installation &amp; Upgrades
---

### Post by TrinitronX on 2008-12-16
After attempting to boot the Ubuntu 8.10 Intrepid Ibex "ubuntu-8.10-desktop-amd64.iso", I am dumped into an initramfs prompt.  It seems casper is failing to mount the livecd on /cdrom.

I have been having troubles booting the 64 bit livecd's on my AMD Athlon X2 4050e Dual-core system.  I believe the problem lies in either the cdrom drive itself, or there is some reason that my drive is not being mounted during the livecd bootstrap process.

I have tried re-burning the disc again (final time burned at a slower speed 8x), and re-verified it's iso image again on another system before booting.  

With the first (possibly bad) disc burnt at 32x, I did not get dumped into busybox immediately, but instead got some read errors from the drive first:
```

[  70.050980] Buffer I/O error on device sr0, logical block 357904
[  78.308803] end_request: I/O error, dev sr0 sector 1431616
[  78.308856] Buffer I/O error on device sr0, logical block 357904
[  85.123577] end_request: I/O error, dev sr0 sector 1431616
[  85.123627] Buffer I/O error on device sr0, logical block 357904
[  91.938358] end_request: I/O error, dev sr0 sector 1431616

And so on...
```Pressing Ctrl-C at this point dumped me into busybox prompt.  Reading "casper.log" for this disc said:

```
/init: line 1: cannot open /dev/sr0: no such file
/init: line 1: cannot open /dev/sr0: no such file
/init: line 1: cannot open /dev/sr0: no such file
.... SNIP...
Unable to find a medium containing a live file system
```I decided this disc may be a bad burn, so I tried another burn, this time at 8x speed.  After burning, I re-read the disc on a windows machine, and used cygwin with "readcd.exe" to dump an ISO file.  I checked md5sums and it was identical to the original source ISO.

With the 8x disc, I am dumped into buysbox.  Reading the "casper.log" file shows:

```
mount: mounting /dev/scd0 on /cdrom failed: Invalid argument
mount: mounting /dev/scd0 on /cdrom failed: Invalid argument
mount: mounting /dev/scd0 on /cdrom failed: Invalid argument
...SNIP (Repeated MANY times)...
mount: mounting /dev/scd0 on /cdrom failed: Invalid argument
Unable to find a medium containing a live file system
```Is there something wrong with my drive?  This system has been able to boot the i386 disc for Ubuntu 6.10 Edgy Eft fine!  Currently the system has an install of gentoo x64, which was put in place by it's previous owner.  I wish to switch it to ubuntu x64.

Any magic boot flags that may help in this case?

---

### Post by aheckler on 2008-12-16
I'm not sure what the problem is here, but you may be able to get around it entirely by booting from a USB drive to install Ubuntu.

---

### Post by TrinitronX on 2008-12-16
Today I decided to double check the cable connections inside the machine, and noticed that the cdrom drive's jumper settings were set to Master.  This should not have mattered, as it was the only drive on that IDE cable, and it was on the end (the correct position).

I changed it to use cable select, and like magic, it didn't drop me into busybox!

However.... now I'm getting a gdm login screen for the livecd??  I've checked online, and there seems to be no answer I could find for this new problem.

Tried ubuntu with no password, that doesn't work.

Why does the livecd do this??  The previous owner of this system forgot to change his root password before he gave it to me, and I've been trying to get a 64 bit livecd to run on this thing so I can chroot in and reset that password.  A 32 bit livecd does not work for this task.  I planned to check out his install, and see what drivers for this system that I might need before installing ubuntu.

So, if the livecd happens to be mounting the drive currently in the system and grabbing its /etc/passwd & /etc/shadow files for some reason, I don't even know the password for his system.  It really shouldn't be doing this... it's a LIVECD!!

Like I said, md5sums check out for this disk.  I also ran the verify disk option in the system with cable select on, and it checked out.  This problem is definitely a bug with the livecd.


EDIT: Just checked all the ttys using Ctrl+Alt+F# keys, and on F8, it shows the following error:
```

* Enabling additional executable binary formats binfmt-support
Can't locate Tie/Hash.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /usr/lib/perl/5.10/POSIX.pm line 71.
BEGIN failed--compilation aborted at /usr/lib/perl/5.10/POSIX.pm line 71.
Compilation failed in require at /usr/sbin/update-binfmts line 22.
BEGIN failed--compilation aborted at /usr/sbin/update-binfmts line 22.
                                                                       [[COLOR=Red]fail[/COLOR]]
```The livecd is missing a perl module?

---

### Post by TrinitronX on 2008-12-19
After further inspection, it seems that the LiveCD was not being read correctly by my drive.

After using unetbootin to create a bootable USB drive from the ubuntu .iso in windows (as I couldn't reliably do so from within the Live CD with my cdrom drive), the disk was able to boot correctly.

I was able to successfully install ubuntu x64 bit onto the system using my cool new USB live thumbdrive!

:biggrin:

---

