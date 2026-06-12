---
title: "Device Manager unable to detect DVD Writer"
date: 2005-07-10
forum: Hardware &amp; Laptops
---

### Post by wired4praize on 2005-07-10
Hi there! Am a newbie to Linux. Just installed 5.04 and for most parts am quite happy except for the optical drive problems I am facing.

Motherboard: Abit AV8-3rd Eye
Chipset: VIA KT800 Pro
Optical drives:
1) LG GSA-4163B @ A04 firmware (master)
2) Lite-On DVD-ROM SOHD-167T (slave)

I followed the Unofficial Ubuntu 5.04 Starter Guide to install the necessary codecs and multimedia players but I think my problem is even more fundamental than that.

The device manager is unable to detect my LG DVD writer. I can, however, see my Lite-On DVD-ROM. Reading CDs from the Lite-On is fine but not DVDs. Needless to say, I can't read anything off the LG. Places --> Computer shows only 1 CDROM/DVDROM drive. Device only shows /dev/hdd. I can mount/umount CDs on the Lite-On.

The LG works fine under Windows XP (I have dual boot) and the Phoenix BIOS detects it OK.

Any idea why:
1) Am unable to detect the LG optical drive? It works and can even burn DVDs under XP.
2) Why DVDs won't play on my Lite-On? They work fine under XP.

I've searched other forums and there's even a site that says that the LG works without any drivers. The dip switch is hardset to "MASTER". While the Lite-On is set to "SEL". Appreciate any help I can get. Thanks in advance.

Freddy

---

### Post by wired4praize on 2005-07-11
Performing either of the following did the trick (i.e. the device manager can see both optical drives):
1) Do not alllow "boot from CD" at BIOS level or
2) Connect the LG drive as the slave (for some reasons master doesn't work)

However, GnomeBaker failed to work on the LG GSA-4163B and DVD movies didn't play either (although the same DVD played OK on the Lite-On).

I get the following error messages:

"There is no input plugin available to handle 'dvd:/'.
Maybe MRL syntax is wrong of file/stream source doesn't exist."

and

"The source can't be read. Maybe you don't have enough rights for this, or source doesn't contain data"

Burning a CD yielded the following message amongst others
"cdrecord: There are unsettled issues with Linux-2.5 and newer. If you have unexpected problems, please try Linux 2.4 or Solaris. "

Anyone encountered this before?

---

