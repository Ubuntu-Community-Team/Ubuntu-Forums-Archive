---
title: "Strange boot error msg hangs my ubuntu. (ACPI EC?)"
date: 2008-08-03
forum: Hardware
---

### Post by camilo.olea on 2008-08-03
Hi everyone,

I have a laptop, sony vaio VGN-N350FE, wich came with that abomination they call windows vista. Obviously, I decided to install ubuntu. So, I installed an older version I had lying around, and then did the upgrade thing. Boom. It did not upgrade correctly, and when I rebooted the machine it hangs with this message:

[35.706919] ACPI: EC: acpci_ec_wait timeout, status = 0, expect_event = 1
[35.706967] ACPI: EC: read timeout, command = 128

No idea what this is. Curiously, if at boot I select "failsafe mode", it loads, then it asks me if it should continue loading normally, I say yes, and then it loads fine. 

So anyway I downloaded the latest ubuntu, burnt it to a cd, rebooted to install it clean, and boom, the same error message, and it hangs there.

Did the corrupted install might have damaged something? Any help here will be greatly appreciated, I really have no idea whats going on.

Thanks
Camilo

---

### Post by phidia on 2008-08-03
It sounds like you have acpi problems. The newer kernel that Hardy comes with may be the cause-I don't know. 
You can pass a boot option to the kernel like noapci and hopefully that will get you running.
For more on boot options take a look at [this]("https://help.ubuntu.com/community/BootOptions").

---

### Post by camilo.olea on 2008-08-04
Hi, thank you so much for this info. I'll take a look.

Again, thanks.

Cheers!

---

### Post by vladuz976 on 2008-08-25
Did you manage to get this fixed somehow? I get exactly the same error. Also have a rather new Vaio laptop. Would really appreciate your response, thanks.

---

### Post by IntuitiveNipple on 2008-08-25
This is/was a known bug which has been fixed in the latest kernel release updates for Hardy. Intrepid isn't affected.

```

$ git log --pretty=format:"%h %ci %s" Ubuntu-2.6.24-19.37..HEAD -- drivers/acpi/ec.c 
40e55e8 2008-07-14 14:44:52 -0400 UBUNTU: ACPI: EC: Some hardware requires burst mode to operate properly
bdbcd26 2008-07-14 14:44:44 -0400 UBUNTU: ACPI: EC: Do the byte access with a fast path

$ git-describe --contains 40e55e8f3bb15
Ubuntu-2.6.24-20.37~3

```

The bug report is "[[Hardy] ACPI Embedded Controller (EC) stops boot when kernel boot 'quiet' option is enabled or AC power is connected](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/191137)"

If you have an older kernel that is affected there is a simple work-around - remove the "quiet" option from the kernel command line parameters in the GrUB menu (/boot/grub/menu.lst).

When Starting the PC press Escape to access the GrUB menu. Highlight the kernel entry, press E to edit it, select the kernel line, press E to edit that, move to the end of the line and delete the "quiet" option. Press Enter then B to boot that entry.

---

