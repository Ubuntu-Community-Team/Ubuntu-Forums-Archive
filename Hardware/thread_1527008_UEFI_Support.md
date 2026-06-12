---
title: "UEFI Support"
date: 2010-07-08
forum: Hardware
---

### Post by atanamir on 2010-07-08
Hi everyone,
 
Hopefully this is the correct forum to which this thread belongs. I've been trying to get UEFI booting working on various intel motherboards (non-mac). Using the bleeding (2.7.35-RC4) kernel along with the experimental branch of grub-efi, I've gotten it working on several computers (as opposed to zero computers with the current lucid kernel, so I'm forced to use unstable stuff out of necessity).
 
However, I need to get it working on all the machines I have before I can continue with what I'm trying to do. On several of the machines, after grub hands over control to the kernel, the system hangs with a blank screen. Numlock does not cause the LED to light, no observable activity on disks or anything. I've tried all sorts of kernel boot options:
 
loglevel=7 earlyprintk=vga vga=771 debug=all, video=vesafb acpi=force agp=off, etc. (in different combinations, not all at once).
 
However, the only one that guarantees that it will boot is 'noefi'. However, this flag disables exactly the modules which I need to use (as /sys/firmware/efi is not present after bootup).
 
How can I even start to debug this problem, as I have no seeable kernel panics or any text at all on the screen? Must I resort to serial-port-based kernel debugging?
 
Given that it boots perfectly with the noefi flag, I'm guessing its a problem with the kernel more than it is with grub.
 
Thanks for the help.
atanamir

---

### Post by oldfred on 2010-07-08
I am curious on how this works, as I hope my next system is efi.

How have you partitioned drive. Is it gpt with efi boot partition? And does it then also require a separate grub_bios partition. I did convert one small drive to gpt and created a bios_grub partition and it worked without any issues but that is still BIOS based. Does your EFI allow choosing MBR or GPT partitioning?

---

### Post by atanamir on 2010-07-09
To follow the EFI spec, you have to partition your drive as GPT.  What I basically did was:

[  FAT32 (100MB) ] [ SWAP (500MB) ] [  LINUX (xxx GB)   ]

Of course, the first partition is set to boot.  

The installation process went as follows (I'm a litlte anal about bloat, so I hand-did everything)

1. boot into liveCD
2. apt-get install debootstrap
3. mkfs.ext4 /dev/sdb3
4. mount /dev/sdb3 /tmp/lucid
5. debootstrap lucid /tmp/lucid
6. mount --bind /dev /tmp/lucid/dev
7. mount -t proc proc /tmp/lucid/proc
8. chroot /tmp/lucid 
9. edit sources.list with the special ubuntu-kernel ppa
10. apt-get install linux-image-2.6.35-7-generic grub-efi
11. compile grub from the experimental branch (there are memalloc bugs in the current trunk)
12. grub-mkimage -O x86_64-efi -o BOOTX64.EFI `find . -name '*.mod' -exec basename {} .mod \;`
13. mkfs.vfat -F 32 /dev/sdb1 
14. mount /dev/sdb1 /tmp/efi
15. cp BOOTX64.EFI /tmp/efi/EFI/BOOT
16. grub-mkconfig
17. Edit mkconfig, cp grub.efi /tmp/efi/boot/grub/grub.cfg

That's more or less, ROUGHLY, what I did, in the least amount of described steps.

---

### Post by oldfred on 2010-07-09
I think you are the first I have seen in the forums with efi that is not apple mac based which is different than your configuration. I have not followed the apple threads so perhaps someone there may know more. 

Since you may be working with bugs and they are trying to update grub for efi you may want to open a bug or volunteer to test grub efi.

We have had only a few even with gpt partitions, so I did an install on one drive with them just to have some idea of gpt and grub.

GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

srs5694 is often in the forums, he knows gpt very well but I do not know if he has used efi or not.

---

### Post by atanamir on 2010-07-09
Alright, thanks.

Honestly, I just kind of wanted some pointers into how I could debug a kernel that's not giving me any output.  Motherboards nowadays don't even have serial ports anymore, so I can't really even do a serial console.  

I'm pretty sure grub-efi is OK, as the same configuration boots up with 'noefi', and efi itself works fine on motherboard X but not Y.  So I want to see what the problem is on Y, but since I don't have any output, that's not possible at this point.

Should I open a thread in a different forum, perhaps?

Thanks for the replies, oldfred.

---

### Post by oldfred on 2010-07-09
Do not know where else to look.

If you are using noefi, is that not just reverting to BIOS type boot and grub?

You could try PM to srs5694, I do not know if he accepts PMs or not. Many do not, but he is the author of gdisk to replace fdisk for gpt drives.

---

### Post by DanaG on 2010-08-06
Hmm, for me, the problem lies with it failing to find the initramfs image.

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/612432](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/612432)

---

### Post by cocoa117 on 2010-08-13
> **atanamir said:**
> Alright, thanks.

Honestly, I just kind of wanted some pointers into how I could debug a kernel that's not giving me any output.  Motherboards nowadays don't even have serial ports anymore, so I can't really even do a serial console.  

I'm pretty sure grub-efi is OK, as the same configuration boots up with 'noefi', and efi itself works fine on motherboard X but not Y.  So I want to see what the problem is on Y, but since I don't have any output, that's not possible at this point.

Should I open a thread in a different forum, perhaps?

Thanks for the replies, oldfred.

Can't you try it on a virtual machine? VirtualBox for example, it provide EFI(not sure if it is UEFI) boot, test it with that it will gives you more information, then play with real motherboard.

---

