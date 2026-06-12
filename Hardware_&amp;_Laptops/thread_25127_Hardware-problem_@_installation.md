---
title: "Hardware-problem @ installation"
date: 2005-04-09
forum: Hardware &amp; Laptops
---

### Post by Tronic on 2005-04-09
Hi there!

I got a Asus Terminator 2 with the ATI IXP200 chipset.
I also got two CD-Burners (one DVD/CD-RW COMBO and a Plextor 48X CD-RW burner)

When the installation program starts to load modules and detect the hardware it stops when it comes to Loading module 'ide-cd' for 'Linux ATAPI CD-ROM'...

I have try'd to disable the other CD and trixed with them... with no result.
Maybe the ISO is broken? Im going to reburn it.

The CDs have worked well in Ubuntu 4.10 and with Slackware and all the other dists out there (well atmost thos who I have tested)

Maybe I should try to install Ubuntu 4.10 and then upgrade it to 5.10?

BTW! as you know you can press alt + F3 and F4 to se what the installationprogram are doing. When I do this theres no errors, its just standing still at:
insmod /lib/modules/2.6.10-6-386/kernel/drivers/ide/ide-cd.ko .

And in alt + F4 it says:
udev[10949]: creating device node ' /dev/ide/host0/bus1/target0/lun0/cd'

---

