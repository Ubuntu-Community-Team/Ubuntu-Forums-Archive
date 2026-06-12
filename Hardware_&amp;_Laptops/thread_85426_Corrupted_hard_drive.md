---
title: "Corrupted hard drive?"
date: 2005-11-02
forum: Hardware &amp; Laptops
---

### Post by Plank117 on 2005-11-02
Whenever I boot intu Ubuntu I get an HDIO input output/error. What could have caused this? I was installing KDE but then halted the install, so could that have been it? Gnome won't start, so I'm using a school computer to post this. Does anyone have any suggestions?

---

### Post by darkmatter on 2005-11-03
Could you please tell us your system specs, and the exact error if possible...

If we are to help you diagnose/find a solution, it will require more information.

---

### Post by bernecky on 2008-04-09
I have observed a similar problem with Hardy Heron recently. As of 2008-04-09,
the failure mode is as follows:

Following a soft reboot (e.g., from little-green-man menu) , rebooting stalls at
"waiting for root file system" for several minutes, then drops into an initramfs(?)
prompt, with the error message ata_id[4091] main: HDIO_GET_IDENTITY failed for
/dev/.tmp-8-16.

Earlier, a hard reboot (reset button) would fix things, as would a boot with the
"recovery mode" kernel. 

As of 2008-04-08, its behavior changed a bit:

- boot up at power-on stalls.
- soft reboot stalls as  above
- hard reset stalls as above.

Booting the "recovery mode" kernel appears to repair things, at least until
next time.

This doesn't help much, I know, but it might get the other chap back on the air.

This system is a two-core AMD Opteron, running 64-bit Hardy Heron, with
bleeding edge patches and the proprietary NVIDIA graphics driver for an ASUS
EN86000GT dual-monitor setup.

rbe@rattler:~$ uname -a
Linux rattler 2.6.24-15-generic #1 SMP Mon Apr 7 16:37:53 UTC 2008 x86_64 GNU/Linux

[email]bernecky@acm.org[/email]

---

