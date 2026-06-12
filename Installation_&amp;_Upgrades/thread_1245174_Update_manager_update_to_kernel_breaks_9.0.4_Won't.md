---
title: "Update manager update to kernel breaks 9.0.4? Won't boot."
date: 2009-08-20
forum: Installation &amp; Upgrades
---

### Post by olddave1 on 2009-08-20
Hi,

Been using 9.0.4 with Eclipse as my development platform for a few months, great so far. I let it do an Update Manager run first thing after updating Firefox. xul-runner and an update to the kernel (2.6.28-15? cannot remember exactly, whatever was latest last nite) showed as corrupted, so searched the forum and based on a post deleted these .deb packages from /var/caches and did the update again. Rebooted and got:
"ACPI: Aborted because junk in compressed archive"
"crc error" 
"Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)"

So hit the forum search again, tried LiveCD and ran memtest, fsck (no errors found), both mem and disk OK. Reseated the RAM, removed the DVD drive and so on through all suggestions in forum messages. No result. Then tried Partition Editor on the /dev/sda1 a ext3 partition using check, from LiveCD, no errors. 

So am now at the point where I do not what to have to restore various thongs from back up and reinstall my development tools and would like to revert to what was there before or a different kernel or something. Any route forward. Sadly back to Windoze for my work in the meantime.

Thx.

David

---

### Post by PmDematagoda on 2009-08-20
Did you try booting Ubuntu by selecting an older kernel from the GRUB menu?

---

### Post by olddave1 on 2009-08-20
Oh forgot also reinstalled grub to be sure, but this is happening after grub runs I assume. Also the caches dir I mention, I know it is not right, but not having a booting system cannot check it.

Is there a resource somewhere that describes each step in the boot process, what can go wrong at each point on the timeline and links to what can be done about it?

Thx.

David

---

### Post by olddave1 on 2009-08-20
That is the trouble when it runs trouble free for a few months, you forget simple things like hitting Esc when Grub is counting down. Select previous version of the kernel and it boots fine. Thx!

Advice on deleting the latest kernel? 

Not sure but I notice that Firefox is still at 3.5.1 which appears to have connection problems, thus my desire to upgrade to 3.5.2 ( apart from the big javascript speedups in this version), so does 3.5.2 depend on this latest kernel 2.6.28-15?

Thx.

David

---

### Post by gibbylinks on 2009-08-20
[quote=olddave1;7817405]Hi,

Been using 9.0.4 with Eclipse as my development platform for a few months, great so far. I let it do an Update Manager run first thing after updating Firefox. xul-runner and an update to the kernel (2.6.28-15? cannot remember exactly, whatever was latest last nite) showed as corrupted, so searched the forum and based on a post deleted these .deb packages from /var/caches and did the update again. Rebooted and got:
"ACPI: Aborted because junk in compressed archive"
"crc error" 
"Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)"

I get exactly the same errors with this kernel, but it boots fine when I pick the previous kernel from GRUB.

I'm running Ubuntu 9.04 and no development stuff. Can't even run compiz on my Tosh laptop. :P

Any ideas ?

---

### Post by j_winn on 2009-08-21
I'm having the same problem mentioned above, but I cannot boot using any of the older kernels listed in Grub. I can get recovery mode to boot, but it tells me that my password is incorrect when I try to log in. I know my password is correct, though.

Any ideas?

Thanks

---

