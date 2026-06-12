---
title: "What graphics driver should I use?"
date: 2010-07-16
forum: Hardware
---

### Post by ixifx on 2010-07-16
I have a Compaq Presario V2000.  From running lspci, I see that I have an:

ATI Technologies Inc Radeon XPRESS 200M 5955

According to the ATI/AMD [website]("http://support.amd.com/us/gpudownload/windows/Legacy/Pages/integrated_mce-xp.aspx?type=2.7&product=2.7.2.3.2&lang=English") :

AMD has moved a number of DX9 ATI Radeon™ graphics accelerators products to a legacy driver support structure.  This change impacts Windows XP, Windows Vista, and Linux distributions.  AMD has moved to a legacy software support structure for these graphics accelerator products in an effort to better focus development resources on future products.

I tried installing Catalyst from Synaptic, but when I try running it I get

There was a problem initializing Catalyst Control Center Linux edition.  It could be caused by the following.

No ATI graphics driver is installed, or the ATI driver is not functioning properly.
Please install the ATI driver appropriate for you ATI hardware, or configure using aticonfig.

I tried running aticonfig but get

aticonfig: No supported adapters detected

so I'm not really sure what to do here... I vaguely recall a command to see if 3d rendering was turned on, but can't for the life of me remember the command and can't seem to find it searching the forums.

any help would be greatly appreciated =)

---

### Post by ixifx on 2010-07-17
so as usual I continued looking for answers after I made my post, and I read somewhere that the last version of ubuntu to support this video card was 8.04 so I installed that and sure enough on my first boot jockey pops up with the restricted drivers for it.

so... how would I go about finding out what specific driver version is installed?  I would ultimately like to be able to use these drivers with a newer release of ubuntu.

---

