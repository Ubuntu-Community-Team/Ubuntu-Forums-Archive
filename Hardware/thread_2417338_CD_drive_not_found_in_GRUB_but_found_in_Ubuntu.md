---
title: "CD drive not found in GRUB but found in Ubuntu"
date: 2019-04-22
forum: Hardware
---

### Post by vlitzanov-z on 2019-04-22
So I'm trying to have an option on GRUB where I can boot from CD, but running "ls" on the GRUB console only finds my floppy drive and my disk drives. No CD. What's weird is that when I continue to Ubuntu, it finds it just fine. I've messed around with the BIOS, but nothing has helped so far.

If it helps, "lshw" in Ubuntu returns the the logical name as:

```
/dev/sr0
/dev/cdrom
```

but neither of them is listed in GRUB.

---

### Post by mobeustech on 2019-04-22
Booting to the CD/DVD is usually a function of the BIOS/UEFI configuration.

---

### Post by vlitzanov-z on 2019-04-22
Yes, but I want to try to create a menu entry for GRUB to boot from, which many other forums have shown to be possible. I just can't find the device when using GRUB console

---

### Post by yancek on 2019-04-22
Not sure if the link below is accurate, if it is then this is not doable with Grub2.

[https://askubuntu.com/questions/311568/boot-from-cd-drive-in-grub2](https://askubuntu.com/questions/311568/boot-from-cd-drive-in-grub2)

Don't see much in the Grub2 manual, link below but it would see that you would replace the standard drive/partition entry (hd0,1) with (cd).  I seem to recall reading a post where someone used (cd0) rather than cd??  I remember trying this years ago with Grub Legacy but don't think I ever got it to work.  You should be able to easily boot the iso file itself rather than putting it on a CD/DVD.

[https://www.gnu.org/software/grub/manual/grub/grub.html#Device-syntax](https://www.gnu.org/software/grub/manual/grub/grub.html#Device-syntax)

---

### Post by vlitzanov-z on 2019-04-22
Well, that sucks. I've tried cd0 as well, so it's most likely the first case. I am using Grub2.

---

### Post by vlitzanov-z on 2019-04-22
Why is there support in the older one but not in the new one? That is something they should have left in.

---

### Post by yancek on 2019-04-23
You might take a look at the post here at the forums, link below, which has some suggested options.  Also, oldfred suggests in that post booting directly from an iso which can be done with Grub and eliminates the need for a CD or DVD.

[https://ubuntuforums.org/showthread.php?t=2369466](https://ubuntuforums.org/showthread.php?t=2369466)

---

### Post by oldfred on 2019-04-23
I do have this in my notes. But stopped booting from DVD/CD years ago. Changed to flash drives, then usually direct boot of ISO from another hard drive or flash drive.

Add to 40_custom:
      ```
 #BIOS Boot whatever is in the CD drive

menuentry "CD on (cd0)" {
 insmod udf
set root=(cd0)
chainloader +1 
 } 

   # UEFI Boot whatever is in the CD drive
menuentry "CD on (cdrom/dvd)" {
  insmod udf 
  set root=(cd0)
chainloader /EFI/BOOT/grubx64.efi 
 }     

```

---

