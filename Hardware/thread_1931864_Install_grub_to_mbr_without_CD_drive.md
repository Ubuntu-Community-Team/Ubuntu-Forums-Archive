---
title: "Install grub to mbr without CD drive"
date: 2012-02-26
forum: Hardware
---

### Post by artmind on 2012-02-26
Hi all

I have lenovo x200t without external CD drive. 
Can you please tell me how to install grub to mbr? I install Ubuntu from default pre-install Windows Vista and after configuring and fully satisfaction with my Ubuntu I need to remove Windows. Now I have windows bootloader in my mbr.

---

### Post by ahallubuntu on 2012-02-26
How did you install Ubuntu in the first place without a CD?  Via USB drive?  Can you still boot that?

Otherwise, if you can still boot Ubuntu now, drop into a terminal and try this:

sudo update-grub
sudo grub-install /dev/sda

#(assuming your hard drive with Ubuntu is on /dev/sda and you don't have a RAID or anything odd setup)

That should do it.

If you can't boot Ubuntu off your hard drive anymore but you can boot an Ubuntu CD image via a USB stick, try the chroot method to install Grub:

[https://help.ubuntu.com/community/Grub2#ChRoot](https://help.ubuntu.com/community/Grub2#ChRoot)

---

### Post by artmind on 2012-02-26
> How did you install Ubuntu in the first place without a CD? Via USB drive? Can you still boot that?

I install Ubuntu from Windows Vista. I boot Ubuntu from Windows bootloader.
I want to install Ubuntu bootloader to Master Boot Record of my hardrive and after that delete Windows from my laptop.

> 
sudo update-grub
sudo grub-install /dev/sda

this command doesn't help. Nothing has change

output from update-grub

```

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.0.0-12-generic
Found initrd image: /boot/initrd.img-3.0.0-12-generic
Found Windows Vista (loader) on /dev/sda1
Skipping Windows Vista (loader) on Wubi system
done

```

---

### Post by oldfred on 2012-02-26
You have wubi not a full install. Wubi is a file inside the Window NTFS partition and uses the Windows boot loader to boot. It is easily uninstalled to allow you to revert to Windows if you do not like Ubuntu. Good for testing, but not so good for a long term install. You should not install grub to the MBR.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

HOWTO: migrate wubi install to partition - bcbc 
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

---

### Post by artmind on 2012-02-27
Thank you very much!

I remove Windows and unstick win logo from my laptop )
Ubuntu is great!

---

