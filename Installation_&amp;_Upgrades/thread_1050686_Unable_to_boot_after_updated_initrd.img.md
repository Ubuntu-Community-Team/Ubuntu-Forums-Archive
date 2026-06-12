---
title: "Unable to boot after updated initrd.img"
date: 2009-01-25
forum: Installation &amp; Upgrades
---

### Post by John Wiersba on 2009-01-25
I just installed quite a number of new packages on a completely up-to-date 
Intrepid 8.10, using synaptic.  Installation went without problems.  When I
reboot, I see:
[INDENT]
Boot from (hd0,0) ext3 ...<UUID>...
Starting up ...
Loading, please wait ...
<CLEAR SCREEN>
usb 2-1: device not accepting address 2, error -71
usb 2-0:1.0: unable to enumerate USB device on port 1
[/INDENT]

After rebooting from a rescue environment, I checked /boot and saw that
initrd.img-2.6.27-9-generic had been changed by synaptic.  Luckily, I had 
backed up the previous version of initrd.img-2.6.27-9-generic, so I renamed
the bad one and was able to boot from the previous version.

This error is completely repeatable.  However, my hard disk is 
luks-encrypted, so no logs are saved in /var/log.  I do see other copies of
these same error messages in /var/log/syslog (from a successful boot into my
luks-envryped LVM root disk).

So, my questions:
[LIST=1]
[*]What caused this error?
[*]How can I help debug this error?
[*]How can I fix it other than by using a previous version of initrd.img?
[*]How can I tell which changes were made to initrd.img-2.6.27-9-generic
that caused it to fail to be able to boot?  I presume the changes were made
because of newly loaded modules, but maybe it's something else.  Is there
something I can diff between the two versions of initrd.img?
[/LIST]

Thanks in advance!

---

### Post by John Wiersba on 2009-01-29
I've solved the problem and filed a bug report: [https://bugs.launchpad.net/ubuntu/+source/edubuntu-artwork/+bug/323011]("https://bugs.launchpad.net/ubuntu/+source/edubuntu-artwork/+bug/323011")

Here's the history:

My laptop has two partitions: boot and a LUKS-encrypted LVM partition.

The problem started a few days back.  After installing a number of new packages with synaptic and rebooting, grub hung before asking for my LUKS passphrase.  So, I knew the problem had to be in one of the changed files in /boot (since my LUKS-encrypted partition hadn't been unlocked yet). Investigation showed that only initrd.img-2.6.27-9-generic had changed.  I restored initrd.img from a backup and was able to boot.

Two days ago, Update Manager installed a new kernel 2.6.27-11 which contained changes to every file in /boot (System.map, abi, config, initrd.img, vmcore, vmlinuz) and again I was unable to boot into the new kernel (it aborted with a different error message before asking for my LUKS passphrase).  After fixing up /boot/grub/menu.lst, I was able to boot into my old kernel.

Poking around with google I was able to pick apart the contents of initrd.img with the following command:  "gunzip <initrd.img-VERSION | cpio -di".  Comparing the bad initrd.img with the good one using diff -r, I determined that the only difference was in usr/lib/usplash/usplash-artwork.so inside initrd.img.

Using "updatedb; locate usplash-artwork" I was able to find that /usr/lib/usplash/edubuntu-splash.so was the same file as contained in initrd.img.  Using "apt-file search edubuntu-splash" I determined that edubuntu-artwork-usplash contained the offending file.
 
After I removed the edubuntu-artwork-usplash package, I corrected the symlinks in / to initrd.img and vmlinuz and tried running "sudo dpkg-reconfigure linux-image-$(uname -r)" which I had found from google. That produced a correct initrd.img.  I was also able to fix 2.6.27-11 by hardcoding the appropriate value into the dpkg-reconfigure command line, after having again modified /vmlinuz and /initrd.img to point to the -11 version.

For the record, here is what I saw when the boot hung:
   
    Boot from (hd0,0) ext3 ...<UUID>...
    Starting up ...
    Loading, please wait ...
    <CLEAR SCREEN>
    usb 2-1: device not accepting address 2, error -71
    usb 2-0:1.0: unable to enumerate USB device on port 1

---

