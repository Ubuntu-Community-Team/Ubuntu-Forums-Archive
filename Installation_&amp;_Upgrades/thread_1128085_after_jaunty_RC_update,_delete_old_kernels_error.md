---
title: "after jaunty RC update, delete old kernels error"
date: 2009-04-17
forum: Installation &amp; Upgrades
---

### Post by jm.mico on 2009-04-17
Hello,

I installed some time ago Jaunty Alpha1,..., and updated several times until got RC version. Now I wanted to tidy up my grub boot list, and tried to remove some old kernels, here is the error I get:

<<
jmico@dell:~$ sudo apt-get remove  linux-image-2.6.28.[2-9]-*
Reading package lists... Done
Building dependency tree
Reading state information... Done
Note, selecting linux-image-2.6.28-8-generic for regex 'linux-image-2.6.28.[2-9]-*'
Note, selecting linux-image-2.6.28-6-generic for regex 'linux-image-2.6.28.[2-9]-*'
Note, selecting linux-image-2.6.28-3-rt for regex 'linux-image-2.6.28.[2-9]-*'
Note, selecting linux-image-2.6.28-9-generic for regex 'linux-image-2.6.28.[2-9]-*'
The following packages will be REMOVED:
  linux-image-2.6.28-6-generic linux-image-2.6.28-8-generic linux-image-2.6.28-9-generic
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
After this operation, 336MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 112383 files and directories currently installed.)
Removing linux-image-2.6.28-6-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms
rmdir: failed to remove `/lib/modules/2.6.28-6-generic/updates/dkms': No such file or directory
rmdir: failed to remove `/lib/modules/2.6.28-6-generic/updates': No such file or directory
run-parts: executing /etc/kernel/prerm.d/last-good-boot
/etc/kernel/prerm.d/last-good-boot: 3: /usr/sbin/kernel-helper: not found
run-parts: /etc/kernel/prerm.d/last-good-boot exited with return code 127
Failed to process /etc/kernel/prerm.d at /var/lib/dpkg/info/linux-image-2.6.28-6-generic.prerm line 267.
dpkg: error processing linux-image-2.6.28-6-generic (--remove):
 subprocess pre-removal script returned error exit status 2
Removing linux-image-2.6.28-8-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms
rmdir: failed to remove `/lib/modules/2.6.28-8-generic/updates/dkms': No such file or directory
rmdir: failed to remove `/lib/modules/2.6.28-8-generic/updates': No such file or directory
run-parts: executing /etc/kernel/prerm.d/last-good-boot
/etc/kernel/prerm.d/last-good-boot: 3: /usr/sbin/kernel-helper: not found
run-parts: /etc/kernel/prerm.d/last-good-boot exited with return code 127
Failed to process /etc/kernel/prerm.d at /var/lib/dpkg/info/linux-image-2.6.28-8-generic.prerm line 267.
dpkg: error processing linux-image-2.6.28-8-generic (--remove):
 subprocess pre-removal script returned error exit status 2
Removing linux-image-2.6.28-9-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms
rmdir: failed to remove `/lib/modules/2.6.28-9-generic/updates/dkms': No such file or directory
rmdir: failed to remove `/lib/modules/2.6.28-9-generic/updates': No such file or directory
run-parts: executing /etc/kernel/prerm.d/last-good-boot
/etc/kernel/prerm.d/last-good-boot: 3: /usr/sbin/kernel-helper: not found
run-parts: /etc/kernel/prerm.d/last-good-boot exited with return code 127
Failed to process /etc/kernel/prerm.d at /var/lib/dpkg/info/linux-image-2.6.28-9-generic.prerm line 267.
dpkg: error processing linux-image-2.6.28-9-generic (--remove):
 subprocess pre-removal script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.28-6-generic
 linux-image-2.6.28-8-generic
 linux-image-2.6.28-9-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
jmico@dell:~$
>>

What am I doing wrong? What should I do to fix that?

The kernels are still there, or at least, that is what update-grub script says when I run it:

Found linux image: /boot/vmlinuz-2.6.28-11-generic
Found initrd image: /boot/initrd.img-2.6.28-11-generic
Found linux image: /boot/vmlinuz-2.6.28-9-generic
Found initrd image: /boot/initrd.img-2.6.28-9-generic
Found linux image: /boot/vmlinuz-2.6.28-8-generic
Found initrd image: /boot/initrd.img-2.6.28-8-generic
Found linux image: /boot/vmlinuz-2.6.28-7-generic
Found initrd image: /boot/initrd.img-2.6.28-7-generic
Found linux image: /boot/vmlinuz-2.6.28-6-generic
Found initrd image: /boot/initrd.img-2.6.28-6-generic
Found linux image: /boot/vmlinuz-2.6.27-11-generic
Found initrd image: /boot/initrd.img-2.6.27-11-generic
Found linux image: /boot/vmlinuz-2.6.27-9-generic
Found initrd image: /boot/initrd.img-2.6.27-9-generic
Found linux image: /boot/vmlinuz-2.6.27-7-generic
Found initrd image: /boot/initrd.img-2.6.27-7-generic


Thanks!

---

### Post by zvacet on 2009-04-18
You can remove them from synaptic.Other way is 

```
sudo apt-get --purge remove packagename
```

or 

```
sudo dpkg --remove --force-remove-reinstreq packagename
```

---

### Post by jm.mico on 2009-04-19
Hello,

Thanks for your suggestions, however none of them worked. Here the results:

<<
sudo apt-get --purge remove linux-image-2.6.28-6-generic
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  linux-image-2.6.28-6-generic*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 112MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 112385 files and directories currently installed.)
Removing linux-image-2.6.28-6-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms
rmdir: failed to remove `/lib/modules/2.6.28-6-generic/updates/dkms': No such file or directory
rmdir: failed to remove `/lib/modules/2.6.28-6-generic/updates': No such file or directory
run-parts: executing /etc/kernel/prerm.d/last-good-boot
/etc/kernel/prerm.d/last-good-boot: 3: /usr/sbin/kernel-helper: not found
run-parts: /etc/kernel/prerm.d/last-good-boot exited with return code 127
Failed to process /etc/kernel/prerm.d at /var/lib/dpkg/info/linux-image-2.6.28-6-generic.prerm line 267.
dpkg: error processing linux-image-2.6.28-6-generic (--purge):
 subprocess pre-removal script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.28-6-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
>>

and the other variant:
<<sudo dpkg --remove --force-remove-reinstreq linux-image-2.6.28-6-generic
(Reading database ... 112385 files and directories currently installed.)
Removing linux-image-2.6.28-6-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms
rmdir: failed to remove `/lib/modules/2.6.28-6-generic/updates/dkms': No such file or directory
rmdir: failed to remove `/lib/modules/2.6.28-6-generic/updates': No such file or directory
run-parts: executing /etc/kernel/prerm.d/last-good-boot
/etc/kernel/prerm.d/last-good-boot: 3: /usr/sbin/kernel-helper: not found
run-parts: /etc/kernel/prerm.d/last-good-boot exited with return code 127
Failed to process /etc/kernel/prerm.d at /var/lib/dpkg/info/linux-image-2.6.28-6-generic.prerm line 267.
dpkg: error processing linux-image-2.6.28-6-generic (--remove):
 subprocess pre-removal script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.28-6-generic
>>


and ... synaptic says:
<<
E: linux-image-2.6.28-6-generic: subprocess pre-removal script returned error exit status 2
>>

So, #?

Thanks again.

uname -r reports:
Linux dell 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64 GNU/Linux

---

### Post by ittiam on 2009-04-19
From your posted logs, I dont see dependency issues but generally while removing a old linux kernel image, the restricted modules for that kernel also needs to be removed, they need to be removed first.

So you can give the following a shot

```
sudo apt-get remove linux-restricted-modules-2.6.28-[2-9]-*
```

After this you can try removing/purging your image and see what happens.

---

### Post by jm.mico on 2009-04-20
Hello again,

Thanks for the tip. But again, does not work:

<<
jmico@dell:~$ sudo apt-get remove linux-restricted-modules-2.6.28-[2-9]-*
[sudo] password for jmico:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Note, selecting linux-restricted-modules-2.6.28-3-rt for regex 'linux-restricted-modules-2.6.28-[2-9]-*'
Note, selecting linux-restricted-modules-2.6.28-8-generic for regex 'linux-restricted-modules-2.6.28-[2-9]-*'
Note, selecting linux-restricted-modules-2.6.28-6-generic for regex 'linux-restricted-modules-2.6.28-[2-9]-*'
Note, selecting linux-restricted-modules-2.6.28-9-generic for regex 'linux-restricted-modules-2.6.28-[2-9]-*'
E: Couldn't find package linux-restricted-modules-2.6.28-[2-9]-*
jmico@dell:~$ sudo apt-get remove linux-restricted-modules-2.6.28-8-generic
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package linux-restricted-modules-2.6.28-8-generic is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 55 not upgraded.
jmico@dell:~$ sudo apt-get remove linux-restricted-modules-2.6.28-6-generic
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package linux-restricted-modules-2.6.28-6-generic is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 55 not upgraded.
jmico@dell:~$ sudo apt-get remove linux-restricted-modules-2.6.28-9-generic
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package linux-restricted-modules-2.6.28-9-generic is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 55 not upgraded.
jmico@dell:~$ sudo apt-get remove linux-restricted-modules-2.6.28-3-generic
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package linux-restricted-modules-2.6.28-3-generic
>>

Seems like I do not have the restricted-modules package installed. :-?

Waiting for some light...


Thanks againg people!

Juanma.

---

### Post by ittiam on 2009-04-21
You can try doing a force remove and see what happens

```
sudo apt-get -f remove package_name
```

---

### Post by jm.mico on 2009-04-24
Hello ittiam,

Your suggestion did not work. Same output...

> 

jmico@dell:~$ sudo apt-get -f remove linux-image-2.6.28-6-generic
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  linux-image-2.6.28-6-generic
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 112MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 115458 files and directories currently installed.)
Removing linux-image-2.6.28-6-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms
rmdir: failed to remove `/lib/modules/2.6.28-6-generic/updates/dkms': No such file or directory
rmdir: failed to remove `/lib/modules/2.6.28-6-generic/updates': No such file or directory
run-parts: executing /etc/kernel/prerm.d/last-good-boot
/etc/kernel/prerm.d/last-good-boot: 3: /usr/sbin/kernel-helper: not found
run-parts: /etc/kernel/prerm.d/last-good-boot exited with return code 127
Failed to process /etc/kernel/prerm.d at /var/lib/dpkg/info/linux-image-2.6.28-6-generic.prerm line 267.
dpkg: error processing linux-image-2.6.28-6-generic (--remove):
 subprocess pre-removal script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.28-6-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

Any other ideas?

---

### Post by ittiam on 2009-04-26
[https://bugs.launchpad.net/ubuntu/+source/grub/+bug/272885](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/272885)

The above link might help you in resolving your problem. It was a bug and has been updated in the new the grub version (0.97)

According to the bug report I guess you are using grub2 instead of grub but for removing linux images there is a grub dependency. You see the cycle.

---

### Post by jm.mico on 2009-04-26
Thanks!!

Indeed, I had the same issue. I remember that I upgraded to grub2 since I am running on ext4 fs. According to the post you've linked, removing (and not purging) the grub while the update produced the bug.

I moved over by installing grub, removing the old kernels and then reinstalling grub2.

Thanks for the information, my old kernels are now uninstalled.

Juanma.

---

