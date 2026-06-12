---
title: "Blank screen hang on bootup with Ryzen 7840U iGPU with Noble"
date: 2024-08-18
forum: Hardware
---

### Post by vishalrao on 2024-08-18
See [https://bugs.launchpad.net/ubuntu/+bug/2077266](https://bugs.launchpad.net/ubuntu/+bug/2077266) for the issue details and upvote the bug if you're affected too.

Pasting the bug description here:

TLDR - Looks like the amdgpu module is included in the Jammy kernel images but not in Noble.

Hello!

I have a laptop with the AMD Ryzen 7840U CPU which has a 780M iGPU running both Jammy-based and Noble-based distro elementary OS releases.

This issue occurs only with the Noble and not Jammy edition.

Upon bootup with the ```
quiet splash
``` params there is just a blank screen and apparent hang which is prevented if I remove the ```
splash
``` option and then I get the expected login screen just fine.

Note that I ran the following command on both Jammy and Noble:

```
sudo lsinitramfs /boot/initrd-6.8xxxxx | grep amdgpu
```

And I see the amdgpu module is present in the Jammy image but not the Noble image.

So I appended "amdgpu" to the ```
/etc/initramfs-tools/modules
``` file and did:

```
sudo update-initramfs -uk all
```

Which resolves the issue for me with Noble as well.

Note both my Jammy and Noble installs are on the same kernel version currently 6.8-xxx-40 although the amdgpu module is included in the Jammy image but not the Noble one.

Thank you!

---

### Post by #&amp;thj^% on 2024-08-18
i added myself to it as well:
```
 sudo lsinitramfs /cdrom/casper/initrd | grep amdgpu
[sudo] password for me: 
/usr/bin/unmkinitramfs: 64: cannot open /cdrom/casper/initrd: No such file
/usr/bin/unmkinitramfs: 57: cannot open /cdrom/casper/initrd: No such file
/usr/bin/unmkinitramfs: 38: cannot open /cdrom/casper/initrd: No such file
cpio: premature end of archive

```
It has carried over to " oracular 24.10 x86_64" as well.

---

