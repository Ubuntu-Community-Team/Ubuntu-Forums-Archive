---
title: "Won't boot with 2.6.31-14, ok with 2.6.28-15. Could use some help to report bug."
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by zoubidoo on 2009-10-29
After upgrading from 9.04 to 9.10 the system won't boot.  I'm not sure how to describe the problem well enough to create a bug report so a bit of input would be appreciated.

After grub I see the ubuntu logo in white then the screen flashes various colours.  Video looks pretty screwed up.  "Starting up..." appears and flickers before the screen is unusable again.

With an older kernel it boots, although the screen with the boot progress bar is also pretty screwed up.

So how do you describe that in a more useful way and how should the bug be reported?

Cheers,
Z.


$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 9.10
Release:	9.10
Codename:	karmic

$ uname -a
Linux vortex 2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:49:34 UTC 2009 i686 GNU/Linux

$ lspci | grep -i vga
01:00.0 VGA compatible controller: nVidia Corporation NV28 [GeForce4 Ti 4200 AGP 8x] (rev a1)

$ dpkg -l '*nvidia*' | grep '^ii'
ii  nvidia-173-modaliases                      173.14.20-0ubuntu5                                         Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-185-modaliases                      185.18.36-0ubuntu9                                         Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-96-kernel-source                    96.43.13-0ubuntu6                                          NVIDIA binary kernel module source
ii  nvidia-96-modaliases                       96.43.13-0ubuntu6                                          Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-common                              0.2.15                                                     Find obsolete NVIDIA drivers
ii  nvidia-glx-96                              96.43.13-0ubuntu6                                          NVIDIA binary Xorg driver
ii  nvidia-settings                            180.25-0ubuntu1                                            Tool of configuring the NVIDIA graphics driv

---

### Post by Stille on 2009-10-29
I have a similar problem, only for me, booting with the .31 kernel grinds to a halt on a flickering "stopping the Firestarter firewall   stopping NTP server ntpd   Restarting OpenBSD Secure Shell server sshd" . Booting with the .28-16 kernel works, with a screwed up progress bar.

---

### Post by zoubidoo on 2009-10-29
Solved it with help from [http://www.economyofeffort.com/2009/10/upgrade-to-karmic-boot-screen-flickers-no-x-nvidia-driver/](http://www.economyofeffort.com/2009/10/upgrade-to-karmic-boot-screen-flickers-no-x-nvidia-driver/)

Do:

```

sudo dpkg-reconfigure nvidia-96-kernel-source
```

But it must be done from the kernel you want to run, not an older one.  So you might need to run in recovery mode.  Or log into a terminal (CTRL+ALT+F1)

HTH
Z.

---

