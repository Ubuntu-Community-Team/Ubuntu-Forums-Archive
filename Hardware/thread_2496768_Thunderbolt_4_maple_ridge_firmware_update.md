---
title: "Thunderbolt 4 maple ridge firmware update"
date: 2024-04-11
forum: Hardware
---

### Post by 5urg3 on 2024-04-11
This is definitely going to require someone who is an expert on thunderbolt 

In this guide, it talks about performing Thunderbolt firmware updates 

[https://docs.kernel.org/admin-guide/thunderbolt.html](https://docs.kernel.org/admin-guide/thunderbolt.html)

The problem is, for Maple Ridge TB4 chips on PCs, for some yet unknown reason, write access to the firmware is disabled in the kernel code, and only read access is allowed

In the guide it says firmware updates are not supported on Macs, but this isn’t a Mac, it’s a Maple Ridge Thunderbolt 4 based PC from HP — long shot here but is there any way I can find out who actually wrote this guide and email them?

This is such a specialized topic I am doubtful that I will get any answers just posting on random Linux forums  

This also applies to any Linux distro and any TB4 based PC from any OEM

Here’s the relevant kernel code, you can see Falcon Ridge (and Titan Ridge) allows “icm->can_upgrade_nvm” but scroll down and you’ll see that Maple Ridge does not

[https://github.com/torvalds/linux/blob/master/drivers/thunderbolt/icm.c#L2445](https://github.com/torvalds/linux/blob/master/drivers/thunderbolt/icm.c#L2445)

I am wondering why, and if there is any possible way to get write access to the firmware, and who I could potentially ask about this

Intel have not been helpful at all, and the same goes for HP 

The underlying issue I am experiencing here is that specific NVM firmware versions have compatibility problems with certain end devices 

Once you update using the OEM’s package / utility, there is currently no way to revert…so you’re up &#128169; creek without a paddle, basically

I have posted in the Thunderbolt sub on Reddit, and no one knew the answer, so thought I would ask here 

If there is another sub I could ask in let me know too, thanks 

Lastly, perhaps there is another roundabout way (like not through the Thunderbolt subsystem but through some other mechanism) to be able to flash the correct SPI EEPROM, if anyone is aware of how to do this?

---

### Post by 5urg3 on 2024-04-12
Someone on Reddit showed me this yesterday
[https://git.kernel.org/pub/scm/linux/kernel/git/westeri/thunderbolt.git/commit/?h=next&id=9a966517a83090ee3e26e9a93a92523e2358c5b3](https://git.kernel.org/pub/scm/linux/kernel/git/westeri/thunderbolt.git/commit/?h=next&id=9a966517a83090ee3e26e9a93a92523e2358c5b3)

Looks like I should be able to change one line of code and then I can get it to work

I haven't built a custom kernel in a long long time
I am following these instructions here 

I used apt and downloaded the kernel, changed the thunderbolt file and added the line of code

[https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel](https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel)

I get to -- [COLOR=#333333]fakeroot debian/rules binary-headers binary-generic binary-perarch

And the build fails, the error is

[/COLOR]Debug: /home/nick/linux-oem-6.5-6.5.0/debian/stamps/stamp-install-generic kernel_file arch/x86/boot/bzImage kernfile arch/x86/boot/bzImage install_file vmlinuz instfile vmlinuz
dh_testdir
dh_prep -plinux-image-unsigned-6.5.0-1019-generic
dh_prep: error: Requested unknown package linux-image-unsigned-6.5.0-1019-generic via -p/--package, expected one of: linux-oem-6.5-headers-6.5.0-1019 linux-oem-6.5-tools-6.5.0-1019 linux-oem-6.5-tools-host linux-image-unsigned-6.5.0-1019-oem linux-modules-6.5.0-1019-oem linux-modules-extra-6.5.0-1019-oem linux-headers-6.5.0-1019-oem linux-oem-6.5-lib-rust-6.5.0-1019-oem linux-image-unsigned-6.5.0-1019-oem-dbgsym linux-tools-6.5.0-1019-oem linux-cloud-tools-6.5.0-1019-oem linux-buildinfo-6.5.0-1019-oem linux-modules-ipu6-6.5.0-1019-oem linux-modules-ivsc-6.5.0-1019-oem linux-modules-iwlwifi-6.5.0-1019-oem linux-modules-usbio-6.5.0-1019-oem
dh_prep: error: unknown option or error during option parsing; aborting
make: *** [debian/rules.d/2-binary-arch.mk:132: /home/nick/linux-oem-6.5-6.5.0/debian/stamps/stamp-install-generic] Error 255

If there's an easier way or if someone could help me with this, I would appreciate it!  Thanks!

---

### Post by 5urg3 on 2024-04-14
I figured it out.  Going by the Wiki instructions for the "quicker build" command I was using "binary-generic" -- I was trying to build one of the OEM kernels, so the command needed to be "binary-oem" -- whoops...

---

