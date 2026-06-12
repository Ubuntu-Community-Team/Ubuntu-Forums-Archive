---
title: "Success Ubuntu 10.04.2 LTS on HP Mini 110-3101sg"
date: 2011-02-04
forum: Hardware
---

### Post by arwarda on 2011-02-04
Ubuntu 10.04.2 runs very good on my new HP Mini 110-3101sg (also on HP Mini 110-3100sg, -3102sg, -3103sg = models with different colors). Everything works out-of-the-box, with the following exceptions, which require some additional manual configuration:

1. Modify the disk-partitioning (all 4 primary partitions are already in use) to allow Ubuntu to coexist with the preinstalled Windows 7 Starter, (optionally backup and) remove the HP_TOOLS partition:
[http://ubuntuforums.org/showthread.php?t=1400095](http://ubuntuforums.org/showthread.php?t=1400095)

2. The integrated SD/MMC-Card-Reader requires the "PCIE card reader driver for Linux" from the Realtek website, the source code of this driver has to be downloaded from the Realtek website and has to be build for the kernel version:
[http://bisque.linuxsoup.com/?q=node/82](http://bisque.linuxsoup.com/?q=node/82)
[http://218.210.127.131/downloads/downloadsView.aspx?Langid=1&PNid=15&PFid=25&Level=4&Conn=3&DownTypeID=3&GetDown=false](http://218.210.127.131/downloads/downloadsView.aspx?Langid=1&PNid=15&PFid=25&Level=4&Conn=3&DownTypeID=3&GetDown=false)

3. Sound requires an update of ALSA 1.0.21 to 1.0.23 via recompile from sources:
[http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/)

Suspend-to-RAM works. I did not test Hibernate-to-Disk, because I use an encrypted swap-partition, which is incompatible with Hibernate-to disk.

WLAN works, but uses a proprietary driver included with Ubuntu. I did not yet test the ethernet, but I do not expect any bad surprises here.

Fn-Keys work.

Camera works.

Microphone has not yet been tested.

---

