---
title: "Don't want LILO, want GRUB! (or: how to uninstall?)"
date: 2009-03-19
forum: Installation &amp; Upgrades
---

### Post by schmoo2x on 2009-03-19
Hi, everyone!

I'm sure the answer to this will be obvious once I see it, BUT here goes:

I'm working on setting up a server with a RAID configuration. I had, on a previous configuration, installed LILO configured to point to **/dev/md0** for the bootup. Having changed the drive that **/** is mounted to **/dev/sda1**, I had installed grub in the Ubuntu Server installer disc, with the assumption that it would overwrite the MBR to boot using GRUB to **/dev/sda1**. 
I finish the install, no errors, reboot, and LILO starts looking for **/dev/md0** (which, of course, doesn't exist).

Long story short, how to I get rid of LILO so that GRUB can work its magic with my server?

Thanks for all the help! I know, I'm still learning...

---

### Post by dandnsmith on 2009-03-20
Sounds like you didn't overwrite the bootloader in the MBR of the disk.
You'd have to have installed it to **/dev/sda**, rather than **/dev/sda1**, I think.
I'd almost forgotten, but the arrangements are different in LILO from GRUB.

Are you OK with that, or should I be ferreting out the details of the commands you have to run? I think you can do a repair of just the boot, starting from the installation CD.

---

### Post by schmoo2x on 2009-03-20
sadly, i'm not entirely sure how to do that - i'm pretty new to dealing with bootloaders, usually it "just works."

How would I go about overwriting the MBR from the Hardy Server install disc? I'm assuming it's something in Rescue mode?

---

### Post by schmoo2x on 2009-03-20
OK, I figured it out - using the Server install disc, I booted into rescue mode with **/dev/sda1** as root. on the next screen, it has an option for re-install GRUB. I hadn't tried this before, since i thought I had been doing the same thing in the regular install script, but apparently, the GRUB install in the installer doesn't overwrite the MBR, even after formatting the HDD (anyone know why? that's kind of odd)

At any rate, after running that GRUB install to (hd0), it booted great.

yay GRUB!

---

### Post by dandnsmith on 2009-03-21
Hmmm!
An interesting query, to which I've no more answer than to my own situation (already resolved) in which I installed Ubuntu 8.10 and my MBR bootloader was overwritten.
I'd feel a lot happier if there was a standard query screen during installation as to whether to install the bootloader and, if so, where to install it.
Come to think of it, I once had an install which claimed it was writing the bootloader, but didn't.

---

