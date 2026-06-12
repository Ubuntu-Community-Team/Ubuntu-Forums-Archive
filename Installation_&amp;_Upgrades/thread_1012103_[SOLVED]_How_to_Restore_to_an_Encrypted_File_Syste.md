---
title: "[SOLVED] How to Restore to an Encrypted File System?"
date: 2008-12-15
forum: Installation &amp; Upgrades
---

### Post by jbrice on 2008-12-15
I need to restore a Hardy installation that I have backed up as a backup.tar.bz2 file. Making it a little more complicated is the fact that it is on a laptop using an encrypted file system of the type created by the "Alternate Install" CD. 

So far I have:
- re-installed Hardy from the "Alternate" CD using the encrypted file system option, and the same password and parameters as the original install,
- un-tarred the backup over the new installation, including /boot folder.

On re-booting, it stalls at the point where it should ask for the encryption password. Running the recovery boot shows that the boot process looks for a specific UUID and doesn't find it - presumably it's looking for the original UUID but not finding it as there is now a new encrypted partition with a different UUID.

So, how to fix this? Is there somewhere in the boot partition that holds the UUID?  If so, where?
Or is there a better procedure for restoring an encrypted installation?

TIA

PS - I needed to restore a complete backup to reinstate V8.04 after updating an Inspiron 1525 laptop to V8.10. I made the mistake of believing that it was ready for use. I was wrong as there were insurmountable problems with webcam video and sound level from microphones, etc.

---

### Post by louieb on 2008-12-15
Just a wild guess since I don't use encryption. Boot with a live CD and find your partitions UUID by:
```
sudo blkid
``` 

Now fix the UUID's in  /boot/grub/menu.lst and /etc/fstab.

---

### Post by jbrice on 2008-12-15
Thanks for the suggestions.

> sudo blkid
OK - that gives me the UUIDs


> Now fix the UUID's in /boot/grub/menu.lst and /etc/fstab. 
The grub entries don't use UUIDs, and /etc/fstab is hidden inside the encrypted partition and so couldn't cause a problem at this point in the boot sequence. :(

---

### Post by louieb on 2008-12-15
Grub has to tell the Kernel where the / (root partition) of the files system is. This is done with the root option.

either by UUiD 

```
kernel /boot/vmlinuz-2.6.24-22-generic root=[COLOR=Red]UUID=fdd1413c-1ad8-4353-be07-dcda96b8a21d [/COLOR]ro 
```or by device
```
kernel        /boot/vmlinuz-2.6.24-22-generic root=[COLOR=Red]/dev/sda2[/COLOR] ro 
```in either case make sure its pointing to the correct partition.

BTW: I am assuming you are getting to the GRUB menu when you boot and it hanging after you select Ubuntu. is that correct?  Don't use encryption so don't know when it asks for the encryption keu.

---

### Post by jbrice on 2008-12-16
Thanks again. 

Yes, it is getting as far as the GRUB menu, but the boot code is of the form:
> kernel /boot/vmlinuz-2.6.24-22-generic root=/dev/mapper/machinename-root

So unable to do clever stuff like changing the UUID in the menu.lst. Also, as the encrypted partition is not ext2/3 format, I can't use tune2fs to change the UUID to the one expected in the boot code.

I suspect that the clever stuff - including the expected UUID - is hidden in a customised initrd file. However this is all stretching my knowledge of Linux beyond its elastic limit!

Unfortunately this still leaves me with an unusable laptop. :(

Later....
I think I have done it - here are the steps for anyone else in this position:

1) Reinstall Ubuntu from "Alternate" CD using same parameters (esp. machine name) as backed-up installation,
2) Log into new installation,
3) Update the new installation (so that both this and the backed-up system are using same version Linux kernal),
4) Copy the contents of the /boot folder, /etc/fstab and /etc/crypttab onto an external medium such as a memory stick,
5) Over-write the installation with the backed-up system,
6) If they have been over-written by the restore operation, replace contents of the /boot folder, /etc/fstab and /etc/crypttab with the copies from the external medium (these files contain reference to hard disk UUIDs which will have changed after the re-install),
7) Reboot, and you should now be able to log into your restored installation.

I would any constructive comments on the above, or easier ways of backing-up and restoring an encrypted Ubuntu installation.

---

