---
title: "Upgrading my hard drive"
date: 2008-03-25
forum: Hardware &amp; Laptops
---

### Post by w1z4rd on 2008-03-25
My laptop hard disk crashed, so I installed Ubuntu onto my external  usb hard drive. I am going to be putting a new drive into my laptop, and I was wondering whats the best way to copy everything I have on the external so it will be working on my local drive.

Can I just install ubuntu on the new drive, then copy and paste just about everything from the USB drive to the new internal drive?

What do I need to take into account?

---

### Post by mssever on 2008-03-26
If your USB drive is one of the *NIX formats (ext2/3, etc.), then you should be able to do a cp -ra to copy the files to your hard drive. The -a option is essential, as it preserves permissions. Then, you'll need to re-run grub to make your drive bootable. I don't remember the commands for Grub, but you should be able to find them easily enough. You don't need to install in this case; Just do the above from the Live CD.

If your USB drive is one of the Windows formats (FAT, NTFS), you're screwed. The Windows formats don't preserve permissions or symlinks (because Windows doesn't use symlinks and Windows permissions are totally different), so that data was lost when you backed up. You'll have to reinstall, but you can probably still copy your $HOME across.

---

### Post by w1z4rd on 2008-03-27
I have no interest in fat or ntfs... so thanks for the advice!

---

