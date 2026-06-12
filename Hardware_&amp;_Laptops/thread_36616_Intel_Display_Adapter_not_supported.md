---
title: "Intel Display Adapter not supported?"
date: 2005-05-24
forum: Hardware &amp; Laptops
---

### Post by interleaf2 on 2005-05-24
I have an Asus P5GDC-V motherboard with an integrated Intel Graphics Media Accelerator 900 as my display adapter.  This doesn't seem to be supported by the Ubuntu 5.04 distribution.

Are there any plans to support it in the future?

The integrated NIC by Marvell / Yukon / Syskonnect is also not supported and causes the Ubuntu installation to hang unless it is disabled in BIOS.  I planned to add the latest SysKonnect driver later, but with the display not supported either, I guess I am swimming upstream with Ubuntu and will have to try a different distro.

I have tried Fedora Core 3, which supports the display adapter very well, but it is a nightmare trying to install the NIC driver because they have moved the linux kernel source directories and the driver installation script gets all confused by this. 

I came to Ubuntu because I thought the NIC driver would be easier to install with a more traditional directory structure, but without a graphical display I have gone backwards rather than forwards.

I guess I'll try SUSE 9.2 next. Sigh.  Any suggestions would be appreciated.

---

### Post by kenworth on 2005-05-24
I have a similar problem with my Dell inspiron laptop. Tried Mandrake 10.1 - it works a treat. I still want Ubuntu, but have to wait for my post to be solved my someone who knows what to do.

 :)

---

### Post by jluckett79 on 2005-10-07
I know that this was an old post but in case anyone brings it up during a search (like I did):

> I have an Asus P5GDC-V motherboard with an integrated Intel Graphics Media Accelerator 900 as my display adapter. This doesn't seem to be supported by the Ubuntu 5.04 distribution.

I also have this graphics card and it seems to be detected properly in the latest Breezy release.  However, I don't think that 3D acceleration yet works with the out-of-the-box driver.

> The integrated NIC by Marvell / Yukon / Syskonnect is also not supported and causes the Ubuntu installation to hang unless it is disabled in BIOS.

This seems to be working for me in the latest Breezy release.  I did need to turn off ACPI (acpi=off) when booting, however.  This was a carry-over from another distribution that I had been using.  I have not yet tried leaving ACPI on in this release.

---

