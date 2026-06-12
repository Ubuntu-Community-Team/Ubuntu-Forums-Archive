---
title: "cpio is not working properly in repacking initrd.lz for live"
date: 2013-05-10
forum: Hardware
---

### Post by BlaineHeadrick on 2013-05-10
For Ubuntu 12.10 and 13.04 I seem not to be able to repack a initrd.lz file after extracting it with cpio, even if no changes were made to any of the associated files.  

If I copy the initrd.lz file from /casper to a temporary directory, say 'tmp'.  And, then create another directory beneath tmp, we'll say tmp2 and cd to it.   And then, I run the following command from the tmp2 directory: 
[COLOR=#000000][FONT=Verdana]lzma -dc -S .lz ../initrd.lz | cpio -imvd --no-absolute-filenames
[/FONT][/COLOR]
the archive appears to be properly extracted.   But, then I immediately execute the following command to repack it, without changing any of the extracted files:
[COLOR=#000000][FONT=Verdana]find . | cpio --quiet --dereference -o -H newc | lzma -7 > ../initrd.lz
[/FONT][/COLOR]
I receive the following errors trying to repack initrd.lz from ubuntu 12.10:
cpio: ./lib/plymouth/themes/text.plymouth: Cannot stat: No such file or directorycpio: ./lib/plymouth/themes/default.plymouth: Cannot stat: No such file or directory
cpio: ./sbin/mount.ntfs-3g: Cannot stat: No such file or directory
cpio: ./sbin/mount.ntfs: Cannot stat: No such file or directory
cpio: ./etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf: Cannot stat: No such file or directory


And, here are these errors when trying to repack initrd.lz from ubuntu 13.04
cpio: ./lib/plymouth/themes/text.plymouth: Cannot stat: No such file or directorycpio: ./lib/plymouth/themes/default.plymouth: Cannot stat: No such file or directory
cpio: ./sbin/mount.ntfs-3g: Cannot stat: No such file or directory
cpio: ./sbin/rmmod: Cannot stat: No such file or directory
cpio: ./sbin/modprobe: Cannot stat: No such file or directory
cpio: ./sbin/mount.ntfs: Cannot stat: No such file or directory
cpio: ./etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf: Cannot stat: No such file or directory
cpio: ./etc/ld.so.conf.d/x86_64-linux-gnu_EGL.conf: Cannot stat: No such file or directory


What am I missing here?  The version of cpio hasn't changed in years so I believe I have the right version, which is 2.11.
It may be that perhaps a different utility is used here other than cpio?  

Here is a bit of background information for anyone that is curious.   I'm using an old 64bit HP Pavilion a6230n which has an NVidia nForce 430 chipset with GeForce 6150SE on board graphics.  I'm trying to modify the ubuntu 13.04 live cd so that the evil and infamous nouveau display driver:mad: will be disabled at boot time, allowing my recently installed nvidia driver to operate.  And, It works if I boot while holding shift key down and then add to the boot parameters nouveau.blacklist=1.  So, I thought this would be an easy thing to fix.  I already tried to add a line to /etc/modprobe.d/blacklist.conf in the root squash filesystem directory, to no avail.  And, now I'm attempting to add a 'blacklist nouveau' line to the /etc/modprobe.d/blacklist.conf file thats stored in the /casper/initrd.lz file.

TIA


Edit: ok it seems that all the files that are giving errors are symbolic links.

---

### Post by BlaineHeadrick on 2013-05-11
If I unpack initrd.lz and then repack it without making any changes, and then boot casper from a usb drive (I should probably add that I'm dealing with live usb and not live cd, created via the Universal USB Installer from [www.pendrivelinux.com]("http://www.pendrivelinux.com")), it hangs, being unable to run modprobe.  And, then it puts me in a BusyBox prompt.

Can someone explain how to unpack and repack the initrd.lz file associated with live casper for ubuntu 13.04?  (even if it is not related to my problem of being unable to blacklist nouveau on live ubuntu; I should probably open a new thread for that.   Wait, nm I was able to put the boot parameters into /syslinux/cfg.txt, as per [http://askubuntu.com/questions/152847/how-to-access-boot-options-12-04-live-usb](http://askubuntu.com/questions/152847/how-to-access-boot-options-12-04-live-usb) [COLOR=#333333][FONT=Ubuntu][/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]answer #3, which successfully [/FONT][/COLOR]blacklisted nouveau, so that part does indeed work now.)

I tried using 7z en lieu of cpio as suggested by [https://answers.launchpad.net/ubuntu/+source/casper/+question/89310](https://answers.launchpad.net/ubuntu/+source/casper/+question/89310) post #3, to no avail.

The repacked file is about a meg larger than the original.  So, my question becomes: "what utility is used to pack and unpack the initrd.lz file associated with the casper live ubuntu distribution"

---

