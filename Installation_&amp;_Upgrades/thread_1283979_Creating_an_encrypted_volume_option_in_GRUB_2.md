---
title: "Creating an encrypted volume option in GRUB 2"
date: 2009-10-06
forum: Installation &amp; Upgrades
---

### Post by heffalump on 2009-10-06
What would I need to add to "/etc/grub.d/40_custom" to create a GRUB boot menu option that would load my Ubuntu install that's on an encrypted drive?  The initrd and kernel files are on hd(1,5) but the actual encrypted partition resides in hd(1,1).

Any help will be appreciated!

---

### Post by heffalump on 2009-10-06
So after some experimenting, I've made a little bit of progress.  The following seems to be getting me to the point of entering my password, which successfully unlocks /dev/sdb1 and then it attempts to mount /dev/sdb1, at which point it fails to do so.  I receive the error "mounting /dev/sdb1 on /root failed: No such device" and I am ultimately dumped into BusyBox.

> 
menuentry "Ubuntu Server 9.04 - Encrypted" {
        set root=(hd1,5)
        linux /vmlinuz-2.6.28-11-server root=/dev/sdb1
        initrd /new-initrd
}


I've also tried setting the root argument to "/dev/mapper/sdb1_crypt" which is put there once the drive is decrypted.  This results in the same error, even though I can see that /dev/mapper/sdb1_crypt exists, once I get into BusyBox.  If I try to mount from inside BusyBox, by typing "mount /dev/mapper/sdb1_crypt /root" then I am given the error of "Invalid argument."

I'm hoping that figuring out what the "root" argument should be set to will be the end of this.

Again, any insight would be appreciated!

---

### Post by heffalump on 2009-10-07
> menuentry "Ubuntu Server 9.04 - Encrypted" {
set root=(hd1,5)
linux /vmlinuz-2.6.28-11-server root=/dev/mapper/logical--volume-root
initrd /new-initrd
} 

It turns out that my current volume group and my original volume groups had identical names.  I fired up 9.10 and executed "sudo cryptsetup luksOpen /dev/sdb1 904-crypt"  This seemed to execute perfectly fine.  However "sudo vgscan" revealed that the volume group had a duplicate name, so I renamed the old volume group using the UUID.

To obtain the UUID, I typed "sudo vgdisplay"
Once I had this, I just typed "sudo vgrename (the UUID) (new volume group name)"
Afterwards, typing "sudo vgscan" revealed no errors.

So upon booting, I went my normal route and got into BusyBox.  From here, I checked /dev/mapper/ and there was a new entry titled "(new volume group name)-root"  I set my kernel root parameter to the path of that entry and it fired up, right away.

However...upon going back to 9.10, I was greeted with a bunch of fsck errors.  I'm not sure if that was the cause, but I am not going to push my luck.  Booting into recovery mode and running fsck, then booting normally seemed to fix this.

---

