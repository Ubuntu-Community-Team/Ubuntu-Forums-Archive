---
title: "upgrading ATI graphics card"
date: 2007-10-01
forum: Hardware &amp; Laptops
---

### Post by G-forze on 2007-10-01
Hi my fellow Ubuntu-users!

I'm hoping for some pointers from you since almighty google doesn't seem to give me any.

The thing is I recently bought a used ATI Radeon X1600 Pro 256 Mb to replace my 9800 Pro 256 Mb. To install it, I only unticked the Enabled-checkbox in Restricted Drivers Manager and rebooted. Then I turned the machine off and went to work.

When I restarted X was messed up so I ran the automated X-configurator and replaced xorg.conf with the file that was created. Once again reboot, and ubuntu started seemingly without problems. Happy to be victorious over X I once again enabled the restricted drivers and rebooted. This time, after the ubuntu-loading-splash went away everything went black. My LCD-monitor turned itself off but the computer kept humming. Nothing I did made any difference. The only thing responding was reset.

Well, after getting this three or four times I went into the "safe mode" in GRUB and got xorg.conf back in shape, but now I run on the default drivers where video isn't that good and compiz doesn't work.

So, my question is simply: How do I get the (right) restricted drivers to work with my new graphics card?

My specs:
AMD Athlon 64 2800+
MSI K8N Neo Platinum
1 Gb RAM
ATI Radeon X1600 Pro 256 Mb

OS in dual boot:
Ubuntu 7.04 32 bit
Windows XP x64

---

